---
title: "Router - SMTP Problem"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by wolphin on 2005-07-04
Hi,

I have a Linksys WAG54G wireless router at home, and when I try to access my email accounts it always gives me errors. Apart from the fact that I can't yet access the account from my Ubuntu laptop (because I can't get my Linksys WPC54G to work with it, and when I tried the LAN it didn't work either!), I have tried accessing the account on other computers but they all give errors saying that they cannot connect to the account. It is an email account supplied by my ISP, and as usual it uses STMP for sending and IMAP for receiving. Would I need to unblock SMTP (port 25) in my router's configuration? The only problem is that there is no option for "unblocking" a port, only forwarding it. What if I wanted to send emails from more than one computer?

The exact error is as follows (from Mozilla Thunderbird 1.0.2):
> 
An error occurred while sending mail. The mail server responded: 5.7.1
<xxxxxxxxx@hotmail.com>...Relaying denied. Please verify that your email address is correct in your Mail preferences and try again.
This happens when I try to send an email to any account, not just Hotmail ones. Oh, and I can receive email perfectly, so I don't think there are any problems with IMAP  :grin: 

-- Wolphin

---

### Post by wolphin on 2005-07-04
Can someone please reply? I love Ubuntu and everything about it, but I really would appreciate a bit of help when I ask for it. at least one of you must know the answer to this simple question: how do I achieve the ability to send mail? Thanks in advance,

Wolphin

---

### Post by asimon623 on 2005-07-04
Yea, try port fowarding.

---

### Post by wolphin on 2005-07-04
[QUOTE=asimon623]Yea, try port fowarding.[/QUOTE]
 Ye, but if I did I would only be able to forward the port to one computer. This would mean that only the computer which I'm forwarding the port to will be able to send emails, but what would I do if I wanted to send emails from more than one computer? Thanks again,

Wolphin

---

### Post by aledie on 2005-07-15
How if your ISP just blocks the 25 port for security reasons? Mine does. Just try to click around in your Evolution (Account Editor-->Sending Email):
1. Try to set ports 465 or 587 as SMTP ports, you do it this way, for example:
Host: smtp.web.de:587 or smtp.web.de:465
2. If it still doesnt work after that, try to experiment a bit with authentication/security settings for SMTP

---

