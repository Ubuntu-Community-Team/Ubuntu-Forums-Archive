---
title: "Can't Install Lexmark z2390 Printer Driver"
date: 2015-04-02
forum: Hardware
---

### Post by anon_private on 2015-04-02
[INDENT] 							I am having  a problem.

I downloaded the driver zip file and extracted it to find the sh file.

On clicking the sh file The script started and there came a point when I was asked for the administrator password.

On typing this, I received the message that the password was incorrect. I  re-typed the password and received the same message. It is correct

Interestingly, on typing a wrong password the programme appeared to  start but the installation  bar that monitored the extend of the  installation remained at zero for ages. It did not move at all. 

The sh file has good integrity as indicated when running from the command prompt.

Regarding the administrator password, I used the same password that I  always use when downloading updates from Muon and without a porblem.

Can you advise.

Thanks.

Ps. I assume that I need to be online during the installation process.
PPS. As mentioned previously, there are other UBUNTU downloads.


UPDATE

I have typed UBUNTU rather than my password.
The programme appears to accept this password, but the Progress bar is still at zero.

I also tried deleting the zip and sh files, and downloading another zip  file from a similar site. I have the same problem with the sh file from  this package.

The sh file has good integrity, as indicated when running this file from the Command Prompt. 						[/INDENT]

---

### Post by dino99 on 2015-04-02
does not know if you need to make the sh execuatable, or add youruser into some group; maybe  try something like that.

---

### Post by anon_private on 2015-04-03
I am in Group

Group has Read and Write facilities

File is executable


Ps

Despite the fact that I can install updates in Muon using my password.  It looks like for other purposes that my password is not recognised.

How can I re-instate my password so that it will function on all occasions.

If the password does not work, in say terminal, I am not sure how I can  re-instate it because I will need to know the password to re-instate it.


UPDATE

I tried this command

```
andrew@andrew-Dell-DM061:~$ sudo echo success
[sudo] password for andrew: 
success
andrew@andrew-Dell-DM061:~$
```

I was using the wrong command, Terminal instead of konsole.

I started konsole and then ran sudo konsole. My password worked.

I ran the the printer shell programme using ./ etc and the Lexmark  screen appeared, a couple of clicks on and the printer driver started to  install, but it stopped installing about halfway through. I was unable  to copy the Lexmark screen output because it would not scroll.

I have copied the output from the konsole screen in case it helps.

```
 	Code:
 	andrew@andrew-Dell-DM061:~$ sudo konsole
[sudo] password for andrew: 
Error: "/var/tmp/kdecache-andrew" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
andrew@andrew-Dell-DM061:~$ Error: "/tmp/kde-andrew" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-andrew" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-andrew" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-andrew" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-andrew" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-andrew" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-andrew" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-andrew" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-andrew" is owned by uid 1000 instead of uid 0.
```

At least I am getting further than previously

---

### Post by Vladlenin5000 on 2015-04-03
Bad news... The script you're using is too old. It was written for Ubuntu 10.10 at the latest. And the Lexmark software has GTK2 dependencies. It simply cannot run in modern Ubuntus...

Try selling it on eBay and buy a newer, better, relatively cheaper, Eco-friendlier, etc. supported modern printer.

---

### Post by anon_private on 2015-04-03
I would rather keep the printer and find a driver to run it under kubuntu 14.04

If all the functions are not available that would still be suitable

Any suggestions

Universal driver?
Generic driver?

---

### Post by Vladlenin5000 on 2015-04-04
No, there isn't.

---

### Post by aikishugyo on 2015-04-07
Hi Andrew,
I think you must be the person that posted on Usenet a couple of days ago---it would help it you would have pasted the URL of this thread.
Anyhow, the suggestion I gave there earlier today, also here for good measure:
Run a VM or some other system with a supported Debian or Ubuntu version, and make that your dedicated print server machine.
Other people have to do the same thing for their older printers on Windows systems just the same, like ALPS for example.

---

