---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Pilot API!


# Form Instances


<!-- CREATE FORM INSTANCE -->
## Create Form Instance

`POST https://subjects/<SUBJECT_ID>/visits/<VISIT_ID>/forms/<FORM_ID>/instances`

### Description
This endpoint is only used to create log entries, ie to create formInstances for multiSubmit forms.  
Non-multiSubmit forms are eagerly created.

### Query Parameters

Parameter | Default | Description
----------|---------|------------
includes  |         | tasks%2C%20subjects

### Return Statuses
201 CREATED

> Example JSON response:

```json
{
  "formInstances": [
    {
      "fields": {
        "1878": {
          "issues": [],
          "name": "ILTPER",
          "reasonForChange": null,
          "value": "NO"
        }
      },
      "id": "12445",
      "locked": null,
      "signature": null,
      "struckOut": false,
      "subjectId": "119",
      "taskId": null,
      "visitId": "1252"
    }
  ],
  "subjects": [
    {
      "address": {
        "city": "63611326E506FDF",
        "state": "FB",
        "street1": "28B94E7B3B49BFC",
        "street2": "8EC2E912CE2F030",
        "zip": "47667"
      },
      "age": 18.0,
      "bestTimeToCall": "9A803708A3",
      "caretaker": null,
      "currentVisit": {
        "category": "treatment",
        "completed": false,
        "disabled": false,
        "displayDate": "2018-08-23T22:15:00+00:00",
        "displayDateType": "present",
        "id": "1796",
        "isUnscheduled": false,
        "name": "Visit 5",
        "status": "in_progress"
      },
      "disable": null,
      "dob": "2000-01-24",
      "email": "119@trialspark.com",
      "emergencyContact": null,
      "firstName": "49E67FBB21",
      "formattedTotalPaymentValue": "92.25",
      "hasSSN": false,
      "id": "119",
      "lastName": "23009E73F0",
      "lastPayment": {
        "appointmentId": "444",
        "checkNumber": null,
        "createdAt": "2018-08-20T22:33:42.238547+00:00",
        "formattedValue": null,
        "id": "126",
        "notes": null,
        "toCaretaker": false,
        "type": null,
        "visitId": "1796"
      },
      "lastVisitId": "1714",
      "lastVisitSummary": {
        "displayDate": "1994-02-24T08:36:41.858640+00:00",
        "displayDateType": "estimate",
        "name": "Telephone Visit"
      },
      "name": "49E67FBB21 23009E73F0",
      "notes": [],
      "numberOfCompletedVisits": 6.0,
      "numberOfVisits": 11,
      "phone": "5609754840",
      "protocolId": "9",
      "protocolNodeTags": [
        "Node 1"
      ],
      "protocolSummary": {
        "id": "9",
        "tag": "WB01-204",
        "visitDefSummaries": [
          {
            "id": "83",
            "isUnscheduled": false,
            "name": "Screening Visit"
          }
        ]
      },
      "relevantStaffSummaries": [
        {
          "firstName": "39297CE0C6",
          "id": "1",
          "lastName": "7CB1412CA6",
          "roleType": "coordinator"
        }
      ],
      "siteId": "37",
      "siteSummary": {
        "id": "37",
        "name": "Agho (Waters Place)",
        "protocolSummaries": [
          {
            "id": "9",
            "tag": "WB01-204",
            "visitDefSummaries": [
              {
                "id": "83",
                "isUnscheduled": false,
                "name": "Screening Visit"
              }
            ]
          }
        ]
      },
      "status": "treatment",
      "subjectVisits": [
        {
          "appointmentSummaries": [
            {
              "end": "2005-11-04T18:59:46.956092+00:00",
              "eventId": "224",
              "id": "158",
              "notes": [],
              "notify": "subject",
              "physicianId": "56",
              "rescheduledCount": 0.0,
              "staffId": "75",
              "staffPaymentCompleted": true,
              "start": "1982-11-08T15:39:06.653295+00:00",
              "status": "canceled"
            }
          ],
          "category": "screening",
          "completed": true,
          "disabled": false,
          "displayDate": "1994-01-10T08:36:41.858640+00:00",
          "displayDateType": "present",
          "id": "1250",
          "isUnscheduled": false,
          "name": "Screening Visit",
          "status": "ready_for_review"
        }
      ],
      "tag": "320EC",
      "treatmentAssignedDate": "2018-08-21",
      "upcomingAppointmentSummary": null
    }
  ],
  "tasks": [
    {
      "completedAt": "2018-05-29T21:04:59.452827+00:00",
      "form": {
        "description": null,
        "formSections": [
          {
            "description": null,
            "formFields": [
              {
                "computed": null,
                "config": {},
                "id": "1878",
                "name": "ILTPER",
                "question": "Was a serum insulin test collected?",
                "renderIf": null,
                "restrictToRoleTypes": [],
                "type": "YES_NO",
                "validations": [
                  {
                    "expression": "[\"exists\", \"{{ $value }}\"]",
                    "id": "1646",
                    "message": "Field must be filled out",
                    "type": "required"
                  }
                ]
              },
              {
                "computed": null,
                "config": {},
                "id": "1879",
                "name": "INSULIN_RES",
                "options": [
                  {
                    "acceptsInput": false,
                    "id": "1238",
                    "label": "Not Taken",
                    "value": "NT"
                  },
                  {
                    "acceptsInput": true,
                    "id": "1239",
                    "label": "Result",
                    "value": "RESULT"
                  }
                ],
                "question": "Insulin (mlU/L)",
                "renderIf": "[\"==\", \"{{ ILT.ILTPER }}\", \"YES\"]",
                "restrictToRoleTypes": [],
                "type": "RADIO",
                "validations": [
                  {
                    "expression": "[\"or\", [\"not\", [\"==\", \"{{ ILT.ILTPER }}\", \"YES\"]], [\"exists\", \"{{ $value }}\"]]",
                    "id": "1647",
                    "message": "Field must be filled out",
                    "type": "required"
                  }
                ]
              },
            ],
            "id": "395",
            "name": null,
            "title": null
          }
        ],
        "id": "137",
        "label": "Serum Insulin Test",
        "multiSubmit": false,
        "name": "ILT",
        "scope": "visit",
        "signatureDef": null,
        "table": null,
        "title": "Serum Insulin Test"
      },
      "formInstance": {
        "fields": {
          "1878": {
            "issues": [],
            "name": "ILTPER",
            "reasonForChange": null,
            "value": "NO"
          }
        },
        "id": "12445",
        "locked": null,
        "signature": null,
        "struckOut": false,
        "subjectId": "119",
        "taskId": null,
        "visitId": "1252"
      },
      "hasIssues": false,
      "id": "16824",
      "locked": null,
      "name": "Serum Insulin Test",
      "requiresPI": true,
      "saved": true,
      "status": "completed",
      "taskDefId": "213",
      "type": "form",
      "visitId": "1252"
    }
  ]
}
```





<!-- UPDATE FORM INSTANCE -->
## Update Form Instance

`PATCH https://subjects/<SUBJECT_ID>/visits/<VISIT_ID>/forms/<FORM_ID>/instances/<INSTANCE_ID>`

### Description
This endpoint updates formInstances for all types of formInstances

### Post Parameters
Parameter | Type | Description
----------|---------|------------
fields | Object | ```{ fieldId: { issues: [Issue], name, reasonFrChange, value }, ... }```
id | string |
locked | boolean |
struckOut | boolean
subjectId| string |
taskId | string |
visitId | string |

### Query Parameters
Parameter | Default | Description
----------|---------|------------
fields  |         | tasks%2C%20subjects

### Return Statuses
200 OK

> Example JSON response:

```json
{
  "formInstances": [
    {
      "fields": {
        "1878": {
          "issues": [],
          "name": "ILTPER",
          "reasonForChange": null,
          "value": "NO"
        }
      },
      "id": "12445",
      "locked": null,
      "signature": null,
      "struckOut": false,
      "subjectId": "119",
      "taskId": null,
      "visitId": "1252"
    }
  ],
  "subjects": [
    {
      "address": {
        "city": "63611326E506FDF",
        "state": "FB",
        "street1": "28B94E7B3B49BFC",
        "street2": "8EC2E912CE2F030",
        "zip": "47667"
      },
      "age": 18.0,
      "bestTimeToCall": "9A803708A3",
      "caretaker": null,
      "currentVisit": {
        "category": "treatment",
        "completed": false,
        "disabled": false,
        "displayDate": "2018-08-23T22:15:00+00:00",
        "displayDateType": "present",
        "id": "1796",
        "isUnscheduled": false,
        "name": "Visit 5",
        "status": "in_progress"
      },
      "disable": null,
      "dob": "2000-01-24",
      "email": "119@trialspark.com",
      "emergencyContact": null,
      "firstName": "49E67FBB21",
      "formattedTotalPaymentValue": "92.25",
      "hasSSN": false,
      "id": "119",
      "lastName": "23009E73F0",
      "lastPayment": {
        "appointmentId": "444",
        "checkNumber": null,
        "createdAt": "2018-08-20T22:33:42.238547+00:00",
        "formattedValue": null,
        "id": "126",
        "notes": null,
        "toCaretaker": false,
        "type": null,
        "visitId": "1796"
      },
      "lastVisitId": "1714",
      "lastVisitSummary": {
        "displayDate": "1994-02-24T08:36:41.858640+00:00",
        "displayDateType": "estimate",
        "name": "Telephone Visit"
      },
      "name": "49E67FBB21 23009E73F0",
      "notes": [],
      "numberOfCompletedVisits": 6.0,
      "numberOfVisits": 11,
      "phone": "5609754840",
      "protocolId": "9",
      "protocolNodeTags": [
        "Node 1"
      ],
      "protocolSummary": {
        "id": "9",
        "tag": "WB01-204",
        "visitDefSummaries": [
          {
            "id": "83",
            "isUnscheduled": false,
            "name": "Screening Visit"
          }
        ]
      },
      "relevantStaffSummaries": [
        {
          "firstName": "39297CE0C6",
          "id": "1",
          "lastName": "7CB1412CA6",
          "roleType": "coordinator"
        }
      ],
      "siteId": "37",
      "siteSummary": {
        "id": "37",
        "name": "Agho (Waters Place)",
        "protocolSummaries": [
          {
            "id": "9",
            "tag": "WB01-204",
            "visitDefSummaries": [
              {
                "id": "83",
                "isUnscheduled": false,
                "name": "Screening Visit"
              }
            ]
          }
        ]
      },
      "status": "treatment",
      "subjectVisits": [
        {
          "appointmentSummaries": [
            {
              "end": "2005-11-04T18:59:46.956092+00:00",
              "eventId": "224",
              "id": "158",
              "notes": [],
              "notify": "subject",
              "physicianId": "56",
              "rescheduledCount": 0.0,
              "staffId": "75",
              "staffPaymentCompleted": true,
              "start": "1982-11-08T15:39:06.653295+00:00",
              "status": "canceled"
            }
          ],
          "category": "screening",
          "completed": true,
          "disabled": false,
          "displayDate": "1994-01-10T08:36:41.858640+00:00",
          "displayDateType": "present",
          "id": "1250",
          "isUnscheduled": false,
          "name": "Screening Visit",
          "status": "ready_for_review"
        }
      ],
      "tag": "320EC",
      "treatmentAssignedDate": "2018-08-21",
      "upcomingAppointmentSummary": null
    }
  ],
  "tasks": [
    {
      "completedAt": "2018-05-29T21:04:59.452827+00:00",
      "form": {
        "description": null,
        "formSections": [
          {
            "description": null,
            "formFields": [
              {
                "computed": null,
                "config": {},
                "id": "1878",
                "name": "ILTPER",
                "question": "Was a serum insulin test collected?",
                "renderIf": null,
                "restrictToRoleTypes": [],
                "type": "YES_NO",
                "validations": [
                  {
                    "expression": "[\"exists\", \"{{ $value }}\"]",
                    "id": "1646",
                    "message": "Field must be filled out",
                    "type": "required"
                  }
                ]
              },
              {
                "computed": null,
                "config": {},
                "id": "1879",
                "name": "INSULIN_RES",
                "options": [
                  {
                    "acceptsInput": false,
                    "id": "1238",
                    "label": "Not Taken",
                    "value": "NT"
                  },
                  {
                    "acceptsInput": true,
                    "id": "1239",
                    "label": "Result",
                    "value": "RESULT"
                  }
                ],
                "question": "Insulin (mlU/L)",
                "renderIf": "[\"==\", \"{{ ILT.ILTPER }}\", \"YES\"]",
                "restrictToRoleTypes": [],
                "type": "RADIO",
                "validations": [
                  {
                    "expression": "[\"or\", [\"not\", [\"==\", \"{{ ILT.ILTPER }}\", \"YES\"]], [\"exists\", \"{{ $value }}\"]]",
                    "id": "1647",
                    "message": "Field must be filled out",
                    "type": "required"
                  }
                ]
              },
            ],
            "id": "395",
            "name": null,
            "title": null
          }
        ],
        "id": "137",
        "label": "Serum Insulin Test",
        "multiSubmit": false,
        "name": "ILT",
        "scope": "visit",
        "signatureDef": null,
        "table": null,
        "title": "Serum Insulin Test"
      },
      "formInstance": {
        "fields": {
          "1878": {
            "issues": [],
            "name": "ILTPER",
            "reasonForChange": null,
            "value": "NO"
          }
        },
        "id": "12445",
        "locked": null,
        "signature": null,
        "struckOut": false,
        "subjectId": "119",
        "taskId": null,
        "visitId": "1252"
      },
      "hasIssues": false,
      "id": "16824",
      "locked": null,
      "name": "Serum Insulin Test",
      "requiresPI": true,
      "saved": true,
      "status": "completed",
      "taskDefId": "213",
      "type": "form",
      "visitId": "1252"
    }
  ]
}
```
