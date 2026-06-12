---
title: "Thunderbird + Ibex = No sending"
date: 2008-11-01
forum: General Help
---

### Post by Greyed on 2008-11-01
I did a fresh install of Ibex inside a VBox VM then moved over my home directory from the Heron VM.  TBird refused to send mail.  I deleted my profile, recreated from scratch and gave it another go.  It sent one message and has since refused to send mail.

The error message is generic, basically telling me a problem occurred but not *what* the problem is.  It helpfully suggested I check the server settings which I know are 100% correct.

Since I control the mail server I ran a tail on the logs to see if TBird is even touching my server.  It isn't.  I know it isn't blocked as a telnet to port 25 works just fine.

The version in the Heron VM is still working fine which is mildly amusing since both are 2.0.0.17 according to launchpad.

Has anyone else experienced this problem inside a VM or out?

---

### Post by russlar on 2008-11-01
Double check Thunderbird's smtp settings. Sounds like it's either trying to send on a port other than 25, or it's pointing at a different mail server

---

### Post by Greyed on 2008-11-01
Well, it is sending to port 2525.  Of course that is because some places like to block port 25.  Trust me, SMTP settings are correct for 3 reasons.  

1: I run the SMTP server so know those settings are correct.  
2: This problem started with a copy of the thunderbird profile which is still working on the 8.04 VM.  
3: It reemerged on the new profile on the 8.10 VM on the second message sent.  If it were a settings issue the first message would fail.  

Also, another probably related issue.  It cannot save drafts, either.  This is with IMAP, not a local account.

---

### Post by ju2wheels on 2008-11-02
Im not sure if its related or not but its something that just started popping up as an error for me in the last few days from what appears to be a change in the way google's imap servers handle authentication.

If you check your account settings, under the "Server Settings" tab, the "user name" field used to be specified as "user_name@gmail.com" but for some reason this method stopped working recently. It now needs to be specified as just "user_name" in order for authentication with the servers to work. This field is the only place where you enter it the short way instead of the full email address.

As I said im not sure if its related to the problem your experiencing or not but give it a go and see.

Edit: Also for the SMTP server settings, the port is not 25 for gmail, it is 587 and be sure to enable TLS.

---

### Post by Greyed on 2008-11-02
It is definitely confined to TBird.  I setup the same account on KMail and all works well.

---

### Post by ju2wheels on 2008-11-02
Can you post a screen or describe your smtp configuration for your gmail account if outgoing mail for gmail is the only thing that is broken.

On the attachments, youll see how my outgoing smtp server is configured. Also if you have more than one account in Thunderbird, you should create one SMTP server in the Outgoing Servers for each account. In the account settings for each account, you should then select the proper corresponding outgoing SMTP server from the drop down list as shown in the second photo.

---

### Post by Greyed on 2008-11-02
Uhm, I don't use GMail and never said that in my original message.  In fact I have stated twice that I run the mail server to which TBird refuses to connect.  That is how I know it isn't even attempting to connect.

---

### Post by ju2wheels on 2008-11-02
Ill take doofus points for that one, thats what I get for answering questions at 4 in the morning.

Ok next question, which IP is your mail server bound to (localhost, the actual IP of the machine, or both) and which one are you trying to connect to through the Thunderbird client? 

Edit: Implied in that question is have you tried connecting from both the machine running the mail server and another machine in the network if one is available?

---

### Post by Greyed on 2008-11-02
> **ju2wheels said:**
> Ill take doofus points for that one, thats what I get for answering questions at 4 in the morning.

Heh, go to bed.  You'll see why i say that in a second.  ;)

> Ok next question, which IP is your mail server bound to (localhost, the actual IP of the machine, or both) and which one are you trying to connect to through the Thunderbird client? 

External.  It is a leased Xen VM that hosts my domain.

> Edit: Implied in that question is have you tried connecting from both the machine running the mail server and another machine in the network if one is available?

Yup.  Sensible questions except I've pointed out that my 8.04 VM still connects perfectly fine, TBird connected and sent one message on a new profile in the 8.10 machine, a telnet to the SMTP port from the 8.10 machine worked and KMail from the 8.10 machine worked.  Because of those factors I am 100% positive that it the problem is TBird and not my connection, the VM, the server or the configuration.

Since I can't offer to FTP you some Mt. Dew to wake up go to bed.  Noone should be tackling oddball TBird questions at 4am without caffiene.  ;)

---

### Post by Greyed on 2008-11-03
I ran TBird from a terminal in the latest attempt to figure this out.  No messages to the terminal when sending mail.  It is as if it isn't even trying.

---

