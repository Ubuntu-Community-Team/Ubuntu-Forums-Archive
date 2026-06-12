---
title: "Creating a VAILD Cert for Apache 2 SSL"
date: 2008-08-17
forum: General Help
---

### Post by ev5unleash1 on 2008-08-17
I have my SSL fully up and running but I would like to know how to create a VALID Certificate browsers say it's invalid and give my clients a hard time while trying to go on a secure connection. I've went through many tutorials but they all don't work with 8.04 or they have me create a invalid certificate. Would someone please help me on how to create a valid certificate?
[B]
Server info[/B]

Ubuntu 8.04
Apache 2 + PHP 5 + MySQL + OpenSSL

---

### Post by tdcdodger on 2008-08-29
The reason that the browser is complaining is because the cert is self-signed. This means that it has not been validated by a CA. CA's are companies like Verisign that certify the identity of the server administering the certificate. The CA acts as a third party between the Server and Client, ensuring intgrity of the cert.

Basically, to get the browser to stop complaining, you need to pay big $$$ like $250/yr to have a CA certify your cert. Good Luck.

---

