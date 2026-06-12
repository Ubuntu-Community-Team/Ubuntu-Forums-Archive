---
title: "Delay between emails sent by postfix"
date: 2008-11-02
forum: General Help
---

### Post by mihaiv77 on 2008-11-02
Hi,

I followed instructions from: [http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)
to use postfix to send mails trough gmail.com using sendmail.

My problem is when my bugzilla uses sendmail to send mails to specified addresses.
From time to time my gmail account is locked i suppose this is because it sends too many emails in a short period of time.

In the mail log file i have:
postfix/error[6910]:...status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.gmail.com[209.85.135.111] said: 535-5.7.1 Username and Password not accepted. Learn more at ?535 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) e10sm16942073muf.14)

And i must use that link to unlock the gmail account (it ask me for a captcha).

Do you have any idea how to implement some delays between emails wen postfix sends the email?
I see(searching on net) that postfix uses a queue (/usr/sbin/postqueue).

I don't have experience with linux so i don't know how to approach this.

Thank you,
Mihai

---

### Post by mihaiv77 on 2008-11-04
Hi,

Do you know a more specialized forum for this question?
Now i am waiting for postfix mailinglist (postfix-users) subscription. I don't know if it the right place to ask a question.

Mihai

---

### Post by mihaiv77 on 2008-11-04
I somebody find this thread trough google...:

i received an answer from [email]postfix-users@postfix.org[/email]:

[I]/etc/postfix/main.cf:
    smtp_destination_rate_delay = 60
    relay_destination_rate_delay = 60

References:

[http://www.postfix.org/postconf.5.html#transport_destination_rate_delay](http://www.postfix.org/postconf.5.html#transport_destination_rate_delay)
[http://www.postfix.org/postconf.5.html#default_destination_rate_delay](http://www.postfix.org/postconf.5.html#default_destination_rate_delay)

Wietse[/I]

and 

[I]And if you discover that you are still seeing the "locked account"
problem where you have to re-enter the captcha code then try changing
your gmail password to something that the gmail password page accepts as
at least a STRONG (not FAIR or GOOD) password.

We are seeing our customers who use google apps hosted email having to
re-enter the captcha code and they definitely don't send emails out too
fast (individual, non-tech users on low bandwidth connections). It
happens only to customers who were set up on the hosted address with a
weak/poor/fair password. When they set a better password it stops happening.

Gerald [/I]

---

### Post by imacamper on 2009-05-26
Thanks for your follow up as I found thread via Google. This helped.

Cheers,

Drew

---

