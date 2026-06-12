---
title: "Sendmail question"
date: 2008-11-20
forum: General Help
---

### Post by cearlp on 2008-11-20
After using Synaptic Package Manager to install sendmail and then restarting Ubuntu (8.04) I get an icon on the tool bar that that says "Requesting a network address from the wired network". The icon is a little blue arrow that keeps going around in a circle as if it is waiting for a response.  Trying to send a message with the PHP mail function timesout so I imagine sendmail is not completely installed correctly.  Any ideas will be appreciated.

---

### Post by cmnorton on 2008-11-20
Enter ifconfig at an X-term (command line). Do you have an IP address? If not, that's your first problem.

Does php mail depend on mailutils? 

Try sending mail at the command line using 

mail -s "test" [EMAIL="whoami@someplace.com"]whoami@someplace.com[/EMAIL] < /dev/null

You might need to install mailutils.

Edit:
--------------------
ps -ef | grep sendmail 

will tell you if sendmail is running or not. You'll see something like this:

 ps -ef | grep sendmail
root      6888     1  0 11:12 ?        00:00:00 sendmail: MTA: accepting connections

---

### Post by cearlp on 2008-11-21
Thank you cmnorton, I did need to install mailutils when I tried your 'mail -s' suggestion, but I had already done  a ifconfig and a ps -ef to see if sendmail was active. It was but I had no display of sendmail: MTA: accepting connections. Also the IP address I expected was shown in the ifconfig output. The circling icon on the tool bar finally changes to a static icon indicating 'Wired network connection', although it takes over 5 minutes for that to occur, and though I get no indication of a failure nothing is ever received from a mail -s command or from a PHP mail function.
Are there any logs I can look at to see exactly what is taking place?

---

### Post by cmnorton on 2008-11-21
sudo /etc/init.d/sendmail restart

What happens?

There are a family of mail logs under

/var/log/mail.*

Suggest looking in those.

---

### Post by cearlp on 2008-11-21
Restarting sendmail completes after 1 min 15 secs, BUT, the mail logs have some interesting stuff.
i get basically two messages over and over. One from sm-mta and the other from sm-msp-queue.
They say "My qualified hostname (earl-desktop) unknown; sleeping for retry"   and
"unable to qualiify my own domain name (earl-desktop) -- using short name" and "status=Deferred connection refused by 127.0.0.1"
The I got messages from mta; one saying starting daemon, one saying to=earl  status=Sent, one saying from=earl@earl-desktop and another one saying relay=localhost (127.0.0.1) but ms-msp-queue still gives me the "uunable to qualify my own domain name" message.
The status=Sent message was the mail -s message sent several hours previous to the restart, so I guess it's working but only with a lot of retries because of the unqualified hostname/domain name problem.

---

### Post by cmnorton on 2008-11-22
This sounds like an /etc/hosts file - related problem. Are you just trying to send email off your system, or are your errors indicating an external system?

---

### Post by cearlp on 2008-11-22
Yes, I'm just sending an email using the mail function in PHP. As I said, it is working now that I installed mailutils, but it takes about three minutes for sendmail to activate when I first boot up and it takes an average of a minute and 15 seconds for a mail command to complete, for example when I do a mail -s from the command line, or when the mail function is called in the PHP script.
Nothing in the logs indicate anything about a remote server. The /etc/hosts file has the following:
127.0.0.1   localhost
127.0.1.1   earl-desktop
followed by the lines for IPv6 capable hosts.

---

### Post by cmnorton on 2008-11-22
This is a just a guess, but how much RAM do you have in this system? See if you can add to or max it.

---

