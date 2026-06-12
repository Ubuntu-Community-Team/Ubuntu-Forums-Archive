---
title: "Thunderbird - Can't Send Emails"
date: 2008-08-16
forum: General Help
---

### Post by broken tibula on 2008-08-16
Hello! I'm using TB 2.0.0.16 on Ubuntu 8.04, and I can't send emails. I can download them just fine, but no sending. I have three Yahoo! accounts, and have Webmail 1.3.2 and Webmail - Yahoo 1.3.4 (with BETA Website checked). The message I receive when I try to send an email is:

**An error occurred while sending mail. The mail server responded: negative vibes. Please verify that your email address is correct in your Mail preferences and try again.**

Error console reads:

[b]HttpComms3.js: callback : Exception : NS_ERROR_NOT_AVAILABLE.
Error message: Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIHttpChannel.responseStatus]
697[/b]

I have no antivirus or firewalls. My SMTP and POP ports are above 1024, and are set to use TLS, if available (I tried changing it to "Never", but it didn't do any good).  I was able to send emails up until last week, and then it suddenly stopped.  Please help!

---

### Post by sstusick on 2008-08-16
Yahoo doesn't provide pop3/imap access to non-paying customers. To gain such access, Yahoo wants $29/year. 

A bummer, I know. If you want a provider with free acccess, try gmail. It's the best email provider I've used.

---

### Post by broken tibula on 2008-08-16
Yeah, but it worked fine up until last week.  I know that Yahoo didn't revoke POP3/IMAP access a week ago, so it doesn't make sense.  Plus, my mother uses TB with Yahoo and doesn't have any problems at all (granted, she's on Windows XP, but nonetheless).  

Do you have any ideas for solutions, other than switching to Gmail?

---

### Post by spacedoggy on 2008-08-16
I had this problem with my isp, my sending mail server is ok, but my mail provider prevented sending mails through any other mail server but their own, so i changed my outgoing mail server to that of my isp, leaving incomming mail server set as my hosting company.

they said it was spam prevention measure but I'm sure it's part of the domestic spying power trip western governments are riding on these days.

Check your ISP hasn't changed mail policies lately.

---

### Post by sstusick on 2008-08-16
Well that is strange. 

I have no idea what's wrong then, sorry.

---

### Post by broken tibula on 2008-08-16
All right.  Someone over on the Mozilla support forums suggested that it might be a problems with my ISP, too, so I'm going to look into that.  Thanks for all the help!

---

