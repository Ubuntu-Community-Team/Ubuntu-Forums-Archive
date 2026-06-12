---
title: "Thunderbird and SMTP won't work"
date: 2008-11-12
forum: General Help
---

### Post by FHS_ on 2008-11-12
I recently switched from Windows XP to Ubuntu 8.04 and managed to get all my Outlook Express mails to Thunderbird.

The problem is, I can recieve mail but not send.

I use the same settings (I use Telia here in Sweden) as I did when I used OE and it worked then, but not on Thunderbird.

mailin.telia.com (pop, incoming) - port 110
mailout.telia.com (smtp, outgoing) - port 25

What's wrong? I haven't been able to use my mail in two months..

---

### Post by _sAm_ on 2008-11-12
I don't have the answer but came across this site; [http://www.bluerange.se/nav4413_7412F02623214471BB699F279D43BBCB](http://www.bluerange.se/nav4413_7412F02623214471BB699F279D43BBCB)

"*Flertalet internetleverantörer stänger numera port 25. Detta innebär att det inte längre går att skicka e-post med någon annan smtp-server än leverantörens egen.*"

And for Telia the settings are; 
Telia - mail1.telia.com, mailout.telia.com (Port 465  och SSL), smtprelay1.telia.com

---

### Post by Shwefty on 2008-11-12
Agreed!  My yahoo mail works, but not one from an exchange account for sending.  It just isn't ever able to connect to the SMTP server.

---

### Post by FHS_ on 2008-11-12
> **_sAm_ said:**
> mailout.telia.com (Port 465  och SSL)

That did the trick! Finally!
Thank you so very much, you made my day! :grin:

---

