---
author: mcleanbyron
ms.assetid: D677E126-C3D6-46B6-87A5-6237EBEDF1A9
description: Use this method in the Windows Store submission API to delete an existing add-on submission.
title: Delete an add-on submission
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, Windows Store submission API, add-on submission, delete, in-app product, IAP
---

# Delete an add-on submission




Use this method in the Windows Store submission API to delete an existing add-on (also known as in-app product or IAP) submission.

## Prerequisites

To use this method, you need to first do the following:

* If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.
* [Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method. After you obtain an access token, you have 60 minutes to use it before it expires. After the token expires, you can obtain a new one.

## Request

This method has the following syntax. See the following sections for usage examples and descriptions of the header and request body.

| Method | Request URI                                                      |
|--------|------------------------------------------------------------------|
| DELETE    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId}``` |

<span/>
 

### Request header

| Header        | Type   | Description                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Authorization | string | Required. The Azure AD access token in the form **Bearer** &lt;*token*&gt;. |

<span/>

### Request parameters

| Name        | Type   | Description                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| inAppProductId | string | Required. The Store ID of the add-on that contains the submission to delete. The Store ID is available on the Dev Center dashboard.  |
| submissionId | string | Required. The ID of the submission to delete. This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [Create an add-on submission](create-an-add-on-submission.md).  |

<span/>

### Request body

Do not provide a request body for this method.

<span/>

### Request example

The following example demonstrates how to delete an add-on submission.

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621230023 HTTP/1.1
Authorization: Bearer <your access token>
```

## Response

If successful, this method returns an empty response body.

## Error codes

If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.

| Error code |  Description   |
|--------|------------------|
| 400  | The request parameters are invalid. |
| 404  | The specified submission could not be found. |
| 409  | The specified submission was found but it could not be deleted in its current state, or the add-on uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported). |

<span/>

## Related topics

* [Create and manage submissions using Windows Store services](create-and-manage-submissions-using-windows-store-services.md)
* [Get an add-on submission](get-an-add-on-submission.md)
* [Create an add-on submission](create-an-add-on-submission.md)
* [Commit an add-on submission](commit-an-add-on-submission.md)
* [Update an add-on submission](update-an-add-on-submission.md)
* [Get the status of an add-on submission](get-status-for-an-add-on-submission.md)
