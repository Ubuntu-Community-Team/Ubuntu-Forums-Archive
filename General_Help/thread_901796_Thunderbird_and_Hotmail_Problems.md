---
title: "Thunderbird and Hotmail Problems"
date: 2008-08-26
forum: General Help
---

### Post by dcast on 2008-08-26
Hi I have set up Thunderbird to work with my hotmail account, however I do not seem to be able to send messages. I get the following error: 

"Sending of message failed. 
Te message could not be sent because connecting to SMTP server localhost failed. The server may be unavailable or is refusing SMTP connections. Please verify that your SMTP server setting is correct and try again, or else contact your network administrator."

Not sure why I would be able to receive email in Thunderbird but not send it? Thanks  for your help in advance.


DCast.

---

### Post by SammerHammer on 2008-08-26
Hotmail doesn't use POP or IMAP (to the best of my knowlege), so you I dont think you can send messages through an email client. If it did, you probably need to configure your ports.

---

### Post by dcast on 2008-08-26
I believe that it does use POP and IMAP as well as SMTP, I did have to configure some ports but only because Linux was blocking those lower than 1024. My messages are all received in Thunderbird, I just can't send them out. I know that it is possible to configure Thunderbird with Hotmail fully, I just seem to be having a problem that google provided no solution for. Thanks for your reply, any more ideas?

DCast.

---

### Post by SammerHammer on 2008-08-26
> **dcast said:**
> I believe that it does use POP and IMAP as well as SMTP, I did have to configure some ports but only because Linux was blocking those lower than 1024. My messages are all received in Thunderbird, I just can't send them out. I know that it is possible to configure Thunderbird with Hotmail fully, I just seem to be having a problem that google provided no solution for. Thanks for your reply, any more ideas?

DCast.
Maybe this could be of help?
[http://lifehacker.com/software/hotmail/check-hotmail-using-thunderbird-34583.php](http://lifehacker.com/software/hotmail/check-hotmail-using-thunderbird-34583.php)

---

### Post by dcast on 2008-08-27
Yeah I have the WebMail and WebMail-Hotmail add-ons installed, and I followed the WebMail setup page. Still not sure what the problem is.

---

### Post by dcast on 2008-08-27
This is the error message that comes up.

---

### Post by SammerHammer on 2008-08-27
> **dcast said:**
> This is the error message that comes up.
It says in that error that the server could be refusing SMTP connections, and the Lifehacker article i linked to verifies that (I think); this means that Hotmail only works as webmail, and not with a email client.

Why dont you just dump Hotmail altogether? Make a Gmail account (gmail is much better than hotmail, believe me), and configure it so that your hotmail messages get forwarded to it.
That way, you have the safety and features of Gmail+T-Bird, while still getting your Hotmail messages.

I'm not a salesperson for gmail, but its security, and 7 GB -and growing- storage space is quite attractive.

---

### Post by mirchichamu on 2008-08-27
> **SammerHammer said:**
> It says in that error that the server could be refusing SMTP connections, and the Lifehacker article i linked to verifies that (I think); this means that Hotmail only works as webmail, and not with a email client.

Why dont you just dump Hotmail altogether? Make a Gmail account (gmail is much better than hotmail, believe me), and configure it so that your hotmail messages get forwarded to it.
That way, you have the safety and features of Gmail+T-Bird, while still getting your Hotmail messages.

I'm not a salesperson for gmail, but its security, and 7 GB -and growing- storage space is quite attractive.

But hotmail messages cannot be forwarded to gmail? If it can be, then how?
I want to do that. I shall be thankful.

---

### Post by SammerHammer on 2008-08-28
> **mirchichamu said:**
> But hotmail messages cannot be forwarded to gmail? If it can be, then how?
I want to do that. I shall be thankful.

Create a gmail account, and during creation it'll ask you if you want to forward your old emails to gmail.

---

### Post by dcast on 2008-08-28
Hotmail will not forward its emails to other accounts, otherwise this whole process would be easy. Microsoft doesn't have forwarding as an option. I decided to change my email address to my gmail address which I have had for some time, but had never used. GMail and Thunderbird was extremely easy. Thanks for all of your help.

---

