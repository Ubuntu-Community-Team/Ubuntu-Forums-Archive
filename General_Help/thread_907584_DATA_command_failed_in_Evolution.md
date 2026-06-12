---
title: "DATA command failed in Evolution"
date: 2008-09-01
forum: General Help
---

### Post by eadwacer on 2008-09-01
This is a description of a problem I had, and the solution I found. I originally posted this as a question, then almost immediately found (part of) the answer. I am leaving this up in case others have a similar problem:

I had an intermittent problem with Evolution email. Every now and then, when I tried to send someone a URL, I'd get the following error message:

........
Error while performing operation.

DATA command failed: m81KaHU3003670 This message does not comply with required standards.
.........

I RTFInternets and found some discussions, but nothing conclusive. It looks like an SMTP error, but the 14 digit number isn't standard SMTP, and is different each time. 

In the latest occurrence I had a list of five URLs I was sending to a short list of about five friends. When I got the error, I went through and sent the top three URLs on their own, OK. Then I tried to send this one:

[http://www.theinquirer.net/gb/inquirer/news/2008/09/01/why-nvidia-chips-defective](http://www.theinquirer.net/gb/inquirer/news/2008/09/01/why-nvidia-chips-defective)

...and got the error. There is no extra text in the email, not even a .sig, and no attachments.

Based on other discussions, I tried starting an Evolution debug log:
evolution --debug=/tmp/evolution.log and
CAMEL_DEBUG=all evolution >& /tmp/evolution.log

...in both cases, all that the log file said was "CalDAV Eplugin starting up ..."

This wasn't a critical problem, and it only shows up in about 1% of my emails, but it's a pain when it does, because I have to try each URL to see which one causes it.

Update 1: Turned out, all of the people on the list were on my university mailserver. On a hunch, I tried sending it to a friend not on the .edu, and it worked. So the problem is the downstream mail server. I'll post more as I find out.
Update 2: Further testing shows it's my local ISP. The message won't go to anyone who isn't on centurytel.
Update 3 and final: Centurytel tech chat was their usual helpful selves - finger point to linux, and they don't support it. [insert rant]

---

