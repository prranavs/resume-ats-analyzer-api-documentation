
# Resume ATS Analyzer API Documentation

## Overview

The Resume ATS Analyzer API helps candidates tailor their resumes for job applications by leveraging AI to evaluate and optimize resumes based on a job description. The API returns an ATS compatibility score, highlights matching skills, and generates improved resume versions.

Our backend utilizes powerful AI models to:
- Analyze resumes against job descriptions.
- Generate optimized versions of resumes for better ATS performance.
- Provide insights into skill matches, gaps, and improvements.

All endpoints require authentication via RapidAPI headers.

---

## Base URL

```
https://resume-ats-analyzer.p.rapidapi.com
```

---

## Endpoints

### 1. Generate Optimized Resume

**Endpoint:**
```
POST /api/analyze/generate-optimized-resume
```

**Description:**
Uploads a resume file and returns an ATS-optimized version of the resume in `.docx` format.

**Headers:**
- `X-RapidAPI-Key`: *Your API key*
- `X-RapidAPI-Host`: `resume-ats-analyzer.p.rapidapi.com`
- `Content-Type`: `multipart/form-data`

**Body (Form Data):**
- `resume`: File (`.pdf` or `.docx`)

**Response:**
```json
{
  "message": "Optimized resume generated",
  "file_url": "https://..."
}
```

---

### 2. Analyze Resume Against Job Description

**Endpoint:**
```
POST /api/analyze
```

**Description:**
Uploads a resume and job description, returns ATS score and feedback summary.

**Headers:**
- `X-RapidAPI-Key`: *Your API key*
- `X-RapidAPI-Host`: `resume-ats-analyzer.p.rapidapi.com`
- `Content-Type`: `multipart/form-data`

**Body (Form Data):**
- `resume`: File (`.pdf` or `.docx`)
- `jobDescription`: Text or file

**Response:**
```json
{
  "ats_score": 78,
  "feedback": "The resume aligns well with the job description. However, 3 out of 10 skills are missing..."
}
```

---

### 3. Test Route

**Endpoint:**
```
GET /api/test/status
```

**Description:**
Returns service status. Use this to verify API connectivity.

**Headers:**
- `X-RapidAPI-Key`: *Your API key*
- `X-RapidAPI-Host`: `resume-ats-analyzer.p.rapidapi.com`

**Response:**
```json
{
  "status": "ok",
  "uptime": "9999 hours"
}
```

---

## Pricing Plans (via RapidAPI Hub)

| Plan   | Monthly Price | Requests Included | Overage Price |
|--------|---------------|-------------------|----------------|
| BASIC  | $0            | 15                | $1/request     |
| PRO    | $19           | 2,499             | $1/request     |
| ULTRA  | $49           | 9,999             | $2/request     |
| MEGA   | $79           | 19,999            | $3/request     |

---

## Support & Contact

Have questions or need help?

📧 **Email**: support@resumeoptimizerpro.com

🌐 **Website**: [resumeoptimizerpro.com](https://resumeoptimizerpro.com)

---

## Example Code (Axios)

```js
const axios = require('axios');
const FormData = require('form-data');
const fs = require('fs');

const form = new FormData();
form.append('resume', fs.createReadStream('./your_resume.pdf'));

const options = {
  method: 'POST',
  url: 'https://resume-ats-analyzer.p.rapidapi.com/api/analyze',
  headers: {
    ...form.getHeaders(),
    'X-RapidAPI-Key': 'your-api-key',
    'X-RapidAPI-Host': 'resume-ats-analyzer.p.rapidapi.com',
  },
  data: form,
};

axios.request(options)
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```

---

## Terms

By using this API, you agree to not abuse or scrape data. Monitor usage and respect rate limits.
