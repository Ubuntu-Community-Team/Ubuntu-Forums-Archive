---
title: "POP3/IMAP Hotmail access via UBUNTU"
date: 2008-10-08
forum: General Help
---

### Post by ashlah on 2008-10-08
Hello all,

I have been using evolution mail client to access my gmail account, it works like a charm. Simply input pop servers and a few clicks away from your inbox.

Now, I've tried to access my hotmail account, it's proving to be difficult.
Apparently hotmail has blocked all free access to POP3 as of 2004? Anyway, i have done some research and ended up install inetd with hotway and hotsmtp.

This also dosn't seem to work :|

any ideas? 
Thanks!

---

### Post by sir_cheats_a_lot on 2008-10-08
if i remember right its been that way since 2002.  from what i read the mail server checks your passport id to see if you are on a premium account or not.  If you don't have a premium account you get blocked. Basically, if you want to use an email app to get to it instead of using the webmail like everyone else.. you HAVE to pay.

---

### Post by ad_267 on 2008-10-08
It won't work in Windows either.

---

### Post by sir_cheats_a_lot on 2008-10-08
also after googling "pop3 settings for hotmail"
i found this : 
[http://mailcall.spaces.live.com/Blog/cns!CC9301187A51FE33!44348.entry](http://mailcall.spaces.live.com/Blog/cns!CC9301187A51FE33!44348.entry)

so from the sounds of things this could change sometime in the future.

---

### Post by JavaZava on 2009-04-06
I was cheking on this too. And I found that when Hotmail became Windows Live Hotmail, Pop3 was enaibled again. I tried with IMAP, but i wasn't successfull. Here is the information you need for POP3:

    * POP Server: pop3.live.com
    * POP SSL: Yes
    * User: Your Windows Live ID (yourname@hotmail.com)
    * Password: The one you use to get to your Hotmail account
    * SMTP Server: smtp.live.com
    * Autentication? Yes (Same User and Password)
    * TLS/SSL: Yes

That's all. Whith this you can recieve via POP, but not via IMAP.

---

### Post by lisati on 2009-04-13
> **JavaZava said:**
> I was cheking on this too. And I found that when Hotmail became Windows Live Hotmail, Pop3 was enaibled again. I tried with IMAP, but i wasn't successfull. Here is the information you need for POP3:

    * POP Server: pop3.live.com
    * POP SSL: Yes
    * User: Your Windows Live ID (yourname@hotmail.com)
    * Password: The one you use to get to your Hotmail account
    * SMTP Server: smtp.live.com
    * Autentication? Yes (Same User and Password)
    * TLS/SSL: Yes

That's all. Whith this you can recieve via POP, but not via IMAP.

Now where did the "Thanks" button go to? (Yes I know it has been disabled. Thanks anyway!)

---

### Post by DeMus on 2009-04-13
> **ashlah said:**
> Hello all,

I have been using evolution mail client to access my gmail account, it works like a charm. Simply input pop servers and a few clicks away from your inbox.

Now, I've tried to access my hotmail account, it's proving to be difficult.
Apparently hotmail has blocked all free access to POP3 as of 2004? Anyway, i have done some research and ended up install inetd with hotway and hotsmtp.

This also dosn't seem to work :|

any ideas? 
Thanks!

If Microsoft doesn't want to be helpful by supporting POP and IMAP then why still use Hotmail, or MSN or Live? Switch to Gmail which does work. I use Gmail through IMAP and it works fantastic. I can watch mail everywhere, it's fast, looks good. No, no MS for me.

---

### Post by whitethorn on 2009-04-13
Another cool feature of Gmail, if you have different emails services which allow Pop mail, you can get gmail to go and download your messages from different emails, and tag them with a certain name. That way you don't need to check all your accounts just gmail.  :)

---

### Post by Gone fishing on 2009-04-13
I check my MSN hotmail using Ubuntu using Thunderbird and the Webmail and Hotmail add ons. It isn't POP or IMAP but make Thunderbird treat the account like a POP account downloading the mail etc and putting it into a local folder.

---

### Post by paraglider on 2009-09-11
Thanks!!!

---

### Post by sopadeajo on 2009-09-11
Reading this thread i have learnt (i did not know it) that i can access my yahoo web mail via POP3.I have already wrongly configured Evolution.How to reconfigure it? New to Ubuntu



[http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html)

use the following mail server settings:  
[LIST]Yahoo Incoming Mail Server (POP3) - pop.mail.yahoo.com (port 110)
[/LIST]
 
[LIST]Yahoo Outgoing Mail Server (SMTP) - smtp.mail.yahoo.com (port 25)







[/LIST]

---

### Post by akakingess on 2009-09-11
> **DeMus said:**
> If Microsoft doesn't want to be helpful by supporting POP and IMAP then why still use Hotmail, or MSN or Live? Switch to Gmail which does work. I use Gmail through IMAP and it works fantastic. I can watch mail everywhere, it's fast, looks good. No, no MS for me.

+1 for me on Gmail, switched when Yahoo demanded a premium account to do POP access.

---

### Post by jrusso2 on 2009-09-11
> **sopadeajo said:**
> Reading this thread i have learnt (i did not know it) that i can access my yahoo web mail via POP3.I have already wrongly configured Evolution.How to reconfigure it? New to Ubuntu



[http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html)

use the following mail server settings:  
[LIST]Yahoo Incoming Mail Server (POP3) - pop.mail.yahoo.com (port 110)
[/LIST]
 
[LIST]Yahoo Outgoing Mail Server (SMTP) - smtp.mail.yahoo.com (port 25)


 









[/LIST]


These settings are the ones that currently work, plugins no longer is needed for Hotmail/Windows Live Mail

Incoming Server (POP3 Server): pop3.live.com
Incoming Server POP Port: 995
Incoming Server POP SSL Encryption: Yes (On or Required)

Outgoing Server (SMTP Server): smtp.live.com
Outgoing Server SMTP Port: 25
Outgoing Server Authentication: Yes (On &#8211; Use POP username and password or Hotmail credentials)
Outgoing Server TLS or SSL Secure Encrypted Connection: Yes (On or Required)

---

