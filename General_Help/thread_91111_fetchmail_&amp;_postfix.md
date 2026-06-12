---
title: "fetchmail &amp; postfix"
date: 2005-11-16
forum: General Help
---

### Post by DaveBentham on 2005-11-16
Hello

On my Ubuntu Breezy Badger 'puter, I want to run fetchmail/postfix but I can't get them going. I have very simple requirements. I want to access a handful of email accounts from one ISP. Ultimately, two of these accounts are for another Windows 'puter on the network. But for now, I just want to fetch them. I have been led to believe postfix is simpler than sendmail and is the usual Ubuntu mail thingy.

I can get fetchmail to quiz the ISP email server and it itself I think is OK, but I get the following error to "fetchmail -v -f '/root/.fetchmailrc'"

reading message [email]xxx.xxx@pop.ntlworld.com[/email]:1 of 15 (6872 octets)
fetchmail: SMTP connect to localhost failed
fetchmail: POP3> QUIT
fetchmail: POP3< <html>
fetchmail: SMTP transaction error while fetching from NTLworld
fetchmail: 6.2.5 querying NTLworld (protocol POP3) at Wed Nov 16 19:26:43 2005: poll completed
fetchmail: Query status=10 (SMTP)
fetchmail: normal termination, status 10

I think this is to do with Postfix's SMTP client not listening correctly on the SMTP port...

I have had to add this line to /etc/postfix/master.cf:

smtp      unix  -       -       n       -       -       smtp

Is that good enough? Alas, I dont know much about this: am I even asking the right question?

Cheers
Dave

---

### Post by jliedeka on 2005-11-16
I don't have the "n" for chroot but the unix entry was there when I installed it.

I use fetchmail to grab my mail from my ISP, Postfix uses procmail to stick it in a Maildir, then Courier IMAP serves it up on my network.  I use either Thunderbird on my laptop or mutt to read the mail locally.  I was able to get all that working in a couple of hours.  Ubuntu really makes it easy.

     Jim

---

### Post by DaveBentham on 2005-11-17
Thanks Jim

...but I changed my 'chroot' setting for the smtp client and it made no difference.

I know this should be easy - my setup is very simple so I dont understand why it doesn't work. 

Dave

---

### Post by jliedeka on 2005-11-17
Do you have a mynetworks=127.0.0.0/24 (or similar) in your main.cf?  Have you tried connecting to smtp with telnet on the local machine?

Try this:
1. log into your box where postix is running (or open a shell if it's the machine you are on now)

2. type "telnet localhost 25" or "telnet 127.0.0.1 25"

3.  If you get connected, type quit to get out.

Do you get a connect string like "Connected to localhost.localdomain"?  Your server name may be something other than localhost.localdomain.

If not, you want to make sure postfix is running and listening to port 25.  Make sure your firewall and/or tcpwrappers (hosts.allow/hosts.deny) aren't getting in the way.  There may be something in you syslog or mail.log (in /var/log) that will suggest the nature of the problem.

---

### Post by DaveBentham on 2005-11-18
Thanks Jim for your help on this...

When I first installed Postfix, I installed it just for local machine, instead of for Internet/network config. But when I re-installed it (which I did a few times) correctly, I didn't fully uninstall it as it left the config files from the first install! Anyway, I have done it properly now and it now works. Hooray. :) 

Dave

---

