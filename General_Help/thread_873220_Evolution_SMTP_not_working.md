---
title: "Evolution SMTP not working"
date: 2008-07-28
forum: General Help
---

### Post by codeking on 2008-07-28
I've just configured a new account on evolution connecting to an email on my website.  The IMAP works fine, but upon sending a message i get the following error:

> Error while performing operation.

Could not connect to mail.otherroaddesign.com: No route to host   

I've already configure 3 other email accounts, (not ones on my website) and they all work fine.

I've contacted my host, and they confirmed that the SMTP was working fine.

Any help decoding what that error message means and how to fix it?

---

### Post by RuleMaker on 2008-07-28
You have to specify the port number after the server address.
mail.otherroaddesign.com:<port number>
You may also need to use SSL and/or password authentication.

---

### Post by codeking on 2008-07-28
Hosting support told me to change the port.  Seemed to work.

---

### Post by Majestic Jim on 2008-12-09
> **RuleMaker said:**
> You have to specify the port number after the server address.
mail.otherroaddesign.com:<port number>

Thanks, this was the answer I needed. My ISP blocks the regular smtp port, so you have to use the alternate smtp service using port number 587.

---

