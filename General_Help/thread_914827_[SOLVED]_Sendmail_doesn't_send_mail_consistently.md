---
title: "[SOLVED] Sendmail doesn't send mail consistently"
date: 2008-09-09
forum: General Help
---

### Post by gkaragoulis on 2008-09-09
So I have an Ubuntu Desktop machine setup with sendmail in order to send out confirmation e-mails after some automatic processes run.  This works fine most of the time, but every once-in-a-while I go to work and find that no mail has been sent for the past 2 days, and the mail queue is stacked with the e-mails it should have sent the days before.

The important parts of my syslog tell me that when the mail is failing there's both a "stat=Deferred" and a "relay=<server>" flag, and the server indicated doesn't exist, so I am very suspicious of this.

The way I've fixed this in the past is:
a.) Restart the computer
b.) Wait long enough and eventually it starts working again

I would like to be able to know what's happening though so I can just fix it.  Any ideas?

---

### Post by HalPomeranz on 2008-09-09
Things that would help the rest of us debug your problem:

1) The contents of your /etc/mail/submit.mc and /etc/mail/sendmail.mc files

2) If you can catch the system when the problem is happening, the output of "sudo /usr/sbin/sendmail -Ac -bp" and "sudo /usr/sbin/sendmail -bp" (these two commands dump information about the contents of your mail queues, including any error status)

---

### Post by gkaragoulis on 2008-09-09
Thank you for your reply

I solved my problem.  After installing webmin (to help me configure sendmail...I'm not too good with config files yet) I found that my computer was set to send mail directly, rather than through our dedicated mail server.  So it kind of chose for itself how it wanted to relay the message (probably by querying the DNS server).  So I changed that to send all mail directly to our primary mail server and the problems went away.

---

