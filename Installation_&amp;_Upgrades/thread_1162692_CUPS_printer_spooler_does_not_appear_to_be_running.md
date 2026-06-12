---
title: "CUPS printer spooler does not appear to be running"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by daaussie on 2009-05-18
Any help please, I need a quick answer on this.

"CUPS printer spooler does not appear to be running"

I get the above message after 9.04 didnt pick up the printers connected. 

It did work for all printers, including CUPS-PDF from a plain install of 9.04.

However when I used remastersys to create a clone disc for install of 9.04 + programs onto other workstations. When I used the troubleshoot, it says that the service is turned off. But when I go to services, the CUPS printer spooler is ticked ON. I switched off, and switched back on but that doesn't work.

---

### Post by daaussie on 2009-05-18
sorry to bump this along, but i need an answer thanks):P

---

### Post by pierrevw on 2009-05-19
Hi 

I also used remastersys and now i get the same message
any luck fixing the problem?

---

### Post by daaussie on 2009-05-19
no, also what i find a bummer is that remaster only installs the apps i had on and not the settings which is my whole reason for doing remastersys. 

I also found that the scanner function and scanner work, its just printer functionality which suffers. but obviously ubuntu knows my scanner/printer unit is there!:o

---

### Post by pierrevw on 2009-05-19
if you use the localhost:631 in firefox do you also get the following:
could not connect to remote server.

---

### Post by pierrevw on 2009-05-19
Hi 

I got it to work again:p

1) I went to /etc/cups/ssl and deleted both files

2) I ran the following command:
Code:
/etc/init.d/cups start 

3) then went to system`administration`printing and viola!!:popcorn:

---

### Post by daaussie on 2009-05-19
good stuff !!! 
i did get that problem with the localhost:631, will try your fix.

Thanks

Hope others find our posts useful

---

### Post by daaussie on 2009-05-19
Well I tried to delete (I have 2 folders and 1 file under SSL), but it won't allow me to move to garbage...

I tried the other command but it said FAIL to start

How'd you get around the above?

---

### Post by pierrevw on 2009-05-19
the only way i know is to log in as root

1. go to System>Administration>Users and Groups>Unlock>select root>properties. make sure that "set password by hand "is ticked
and then put in a password that you will remeber.Press OK.
2. go to System>Administration>Login window>security and tick "Allow 
   system administrator login.Close the window
3. log out and log in as username:root and the password you entered previously. Be carefull when you log in as root because you will have read and write access to all the files.
4. delete the two files in /etc/cups/ssl  and log out again.
5. log in as normal user and open terminal. in terminal type sudo /etc/init.d/cups start. It should be ok now.

---

### Post by daaussie on 2009-05-20
I tried your way but couldn't get it to work (too noob) - I will try again though.

Also, before i try again did you see these folders under ETC/SSL?
1 certs - folder
2 private - folder
3 openssl.cnf - file

You mentioned 2 files, but thats all i see.

I also tried sudo apt-get remove CUPS
and then sudo apt-get install CUPS
but it fails when reinstalling...

---

### Post by citro_cell on 2010-02-05
> **pierrevw said:**
> Hi 

I got it to work again:p

1) I went to /etc/cups/ssl and deleted both files

2) I ran the following command:
Code:
/etc/init.d/cups start 

3) then went to system`administration`printing and viola!!:popcorn:

Thanks!!  I couldn't find my printer icon anywhere so I used the troubleshoot function in the printer configuration folder and it found that CUPS wasn't running.  I am using Karmic Koala 9.10.

The suggestion works flawlessly, but in order to delete these files via GUI, I used the terminal to open the nautilus file manager as super-user
```
gksudo nautilus
```
Thanks again!!

---

### Post by hockeytux on 2010-06-09
Ive got the same problem on Lucid now... Printing troubleshooting says 'The CUPS print spooler does not appear to be running. To correct this, choose System -> Administration -> Services from the main menu and look for the 'cups' service.'

Well, problem is there are no 'Services' in my admin menu - now what?

Btw, CUPS is installed, ive checked in Synaptic.

Any help would be greatly appreciated.

---

### Post by hockeytux on 2010-06-10
bump

Surely Im not the only person who has got problems with CUPS and printing...

---

### Post by teilnehmer on 2010-06-10
hockeytux, 

CUPS has problems in 10.04 which supposedly have something to do with upstart, not with CUPS itself (see [here]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172")). They're still trying to track this one down. The problem is that without known cause, CUPS sometimes won't start on boot. 

If your problem is related, you will find that entering
```
runlevel
```
yields "unknown" and entering the Virtual Consoles (Strg+Alt+F[1-6]; you can get back to your desktop with (Strg+Alt+F7) does not give you a command line to enter anything. These things seem to somehow correlate, if I understood the bug report correctly. 

If your account can sudo, you can open a terminal and enter
```
sudo /etc/init.d/cups start
```
This will start CUPS. After that, you might be able to print or at least enter localhost:631 to configure stuff. 

Good luck!

---

### Post by hockeytux on 2010-06-20
Thanks, that did the trick. I didnt have to configure anything after I ran that command.

Funnily enough my printer had worked once (!) before I manually activated CUPS, so it does seem to start on boot occasionally...

---

### Post by teilnehmer on 2010-06-21
Glad to hear it worked! The "it works sometimes" is part of the bug. The people discussing in the bug report fear it could be a race condition (timing of different processes randomly decides wether it works or not), which obviously would be pretty bad. I assume a random thing is hard to spot...

Please be aware that, until the bug is dead, you'll have to manually start cups whenever you find it's not working amd you want to print.

---

### Post by pleurastic on 2012-01-07
Post 14 fixed mine.  Thanks.

---

