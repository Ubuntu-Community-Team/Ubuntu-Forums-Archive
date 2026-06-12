---
title: "Printing error message cups-waiting-for-job-completed"
date: 2015-07-12
forum: Hardware
---

### Post by paulnewall on 2015-07-12
When I print I get the error message above. But the print works fine. So it seems there is not actually an error.
Perhaps the message is just for information?

Does everyone who prints get this message? Or it it just with kodak printers?

It might be helpful if the message was not reported as an error if nothing is wrong.

---

### Post by guyl6308 on 2015-09-26
> **paulnewall said:**
> When I print I get the error message above. But the print works fine. So it seems there is not actually an error.
Perhaps the message is just for information?

Does everyone who prints get this message? Or it it just with kodak printers?

It might be helpful if the message was not reported as an error if nothing is wrong.

I see this message also, but only for some documents that I print, not all, (and always the same ones). I am using Ubuntu-Mate 15.04

I have been trying to find out why and how to fix this. Or should we just ignore it?

Anybody knows anything about this?

---

### Post by tgalati4 on 2015-09-26
It could be a printer driver issue with the Kodak printer.  I have seen that error message with HP printers on a degraded network connection.  The printer will typically send a job-completed status message which cups then relays to a notification "Job Completed".  If that message is not received after a certain period of time, then cups will print the "Waiting for Job Completion".

Do you have any other printers on the network that you can test with?  Does it happen on every print job?  

You can look through the log files in /var/log/cups to see if there are any other messages.

---

### Post by amd-64 on 2015-11-13
Is this the same bug.  [https://bugzilla.redhat.com/show_bug.cgi?id=1207154](https://bugzilla.redhat.com/show_bug.cgi?id=1207154)

---

### Post by weatherman2 on 2015-11-13
Yes, I have had exactly the same problem with several printers in Ubuntu 12.04 - two Canon and one HP.  You print and you get a CUPS error message but it prints anyway.  Clearly not specific to a Kodak driver.

---

