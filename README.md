# Inherited_Digital_KYC
In the loan management system KYC(Know Your Customer) is mandatory policy. Now in the process of KYC the important part is to match the selfie uploaded by the customer with the photo identity proof authorized by the government of India. As this was an Inherited Digital KYC system we do basic format checks of the document and save them to our s3 bucket.<br>

This Inherited Digital KYC also known as DKYC2 (In Aditya Birla). The main purpose of this DKYC2 is to collect the proof of address and proof of identification in a required format and save them to our database. We save all of the documents in AWS s3 bucket. Initially DKYC2 had following flows:

> 1) CKYC Flow:
>> In this flow request body should have proof of address document and customer photo in jpeg/png format. If they are not in required format, then we will respond with an error message like "Unsupported Image Type". Or else we will extract all the required details from xml and save them to our s3 bucket.
> 3) OKYC Flow:
>> In this flow request body should have XML document or XML zip. If request body have XML zip then we will try to extract xml from zip and if it fails, we will give an error like "Unable to extract zip". If we are able to extract xml document from zip, then we will check whether the provided xml is valid or invalid. If provided xml is invalid, then we will return an error as "Invalid XML". If xml is valid, then we will do xml signature validation. If the document fails xml signature validation, then error will be "XML Signature Validation Failure", else we will extract all the required details from xml and save them to our s3 bucket.
> 4) IKYC Flow:
>> In this flow request body should have proof of address document and customer photo in jpeg/png format. If they are not in required format, then we will respond with an error message like "Unsupported Image Type". Or else we will extract all the required details from xml and save them to our s3 bucket.
> 5) DGKYC Flow:
>> In this flow request body should have XML document. Now we will check whether the provided xml document is valid or invalid. If provided xml is invalid, then we will return an error as "Invalid XML". If xml is valid, then we will do xml signature validation. If the document fails xml signature validation, then error will be "XML Signature Validation Failure", else we will extract all the required details from xml and save them to our s3 bucket.
