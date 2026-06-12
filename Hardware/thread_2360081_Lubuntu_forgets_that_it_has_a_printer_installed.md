---
title: "Lubuntu forgets that it has a printer installed"
date: 2017-05-01
forum: Hardware
---

### Post by russed2 on 2017-05-01
I can succesfully install a printer in live Lubuntu 16.04 LTS, and it works fine. But few minutes after printing, Lubuntu forgets that it has a printer installed, and I must turn the printer off and on again in order to make it appear. it is very annoying.

Any ideas?
Best regards.

---

### Post by DuckHook on 2017-05-02
Need more info. At least:

[LIST=1]
[*]What make/model of printer?
[*]How did you "install" it? (What steps taken etc.)
[*]Is it connected by USB or network?
[*]Does your particular printer need its own drivers and, if so, were they installed?
[*]What is your system HW specs?
[*]You mention that this happens in a Live session. Do you have any permanent install you can use? If so, do you have the same problem?
[/LIST]
Please understand that it is impossible to help with the minimal info that you have provided.

---

### Post by russed2 on 2017-05-02
> **DuckHook said:**
> Need more info. At least:

[LIST=1]
[*]What make/model of printer? 
[*]How did you "install" it? (What steps taken etc.) 
[*]Is it connected by USB or network? 
[*]Does your particular printer need its own drivers and, if so, were they installed? 
[*]What is your system HW specs? 
[*]You mention that this happens in a Live session. Do you have any permanent install you can use? If so, do you have the same problem? 
[/LIST]
Please understand that it is impossible to help with the minimal info that you have provided.

Thank you
1- Epson Stylus XP-211
2- First, I install cups, because it seems to be necessary for printing, but it is not installed by default in the Live Cd. Then I install the manufacturer drivers, only one .deb file. 
3- Yes, it is connected by USB.
4- I think I answered that in the point # 2.
5- What is your system HW specs? I don't know, I shoud check it.
6-This happens in a Live session, I haven't a permanent installtion.

I think the problem is in cups. It seems to be required to print, but it is not installes by default in the Live Cd. I think that printing is not foreseen in the Live cd.
Few minutes after printing, the printer disappears. I go to System Tools, Printing, and it says not connected, I click in the button Connect, and nothing happens.
The only solution is to turn the printer off and on again.

---

### Post by DuckHook on 2017-05-02
It is more than possible&#8212;indeed probable&#8212;that your problems are a result of trying to set this up on a LiveUSB session. Such sessions are meant only for testing purposes and reside entirely in RAM. Since the install media is not writable, any additional services (CUPS) and drivers must also reside only in RAM. They will not survive a powerdown. I'm surprised that you can stand it, since operating in this way requires you to reinstall the CUPS service and driver every time you boot.

I would recommend that you create a full install. If you don't want such an install on your system HDD, you can try installing onto a USB drive or stick. A 16 GB stick is the minimal requirement, but are dirt cheap these days (32 GB would be better). Such a system may run like molasses, but at least it will allow you to install apps, services and drivers persistently.

---

### Post by Bucky Ball on 2017-05-03
> **DuckHook said:**
> It is more than possible—indeed probable—that your problems are a result of trying to set this up on a LiveUSB session. Such sessions are meant only for testing purposes and reside entirely in RAM. Since the install media is not writable, any additional services (CUPS) and drivers must also reside only in RAM.

++++1. The 'Try Ubuntu' session is intended for just that, trying Ubuntu, not for installing and setting up printers and other hardware, or anything really much more complex than 'taking a test drive' and seeing if you like it.

---

### Post by russed2 on 2017-05-03
> **DuckHook said:**
>  in this way requires you to reinstall the CUPS service and driver every time you boot.
Thank you, DuckHook.
That's why I'm working in a customized Lubuntu live cd, whit all that already installed, just for my personal use.


>  you can try installing onto a USB drive or stick.
If I burned a cd or dvd, or use a USB drive or stick to instal every linux distro that I try, I was financially ruined long time ago.


Maybe Bucky Ball is right, maybe I'm pushing the limits too far.


Oh, by the way, I forgot about LSB (Linux Standard Base).
This particular driver requires lsb installed.


The first time that I tried to install the printer, after realizing that I needed cups in order to get the Add button enabled in the printer managment applet, and I installed it, I tried to install the downloadable driver suggested, 201304w. Once I accepted the license and clicked the Forward button, It hanged up, It continued forever, it never finished. I later discovered that that was probable due to the lacking of lsb, but in never gave me an error message, nor hint nor warning.


The next time, after installing the dependencies, cups and lsb, instead of downloading the driver, I used the debian package that I already downloaded for Kubuntu. It is the same file, the same version.


I said that printing is not fully foreseen in the Live session because cups isn't installed, and you can't add a new printer without it. It's okay for me, it's fine. I guess that a lightweight OS needs some sacrifices, and I wouldn't really change that.


It was pretty fast and easy to get the printer installed and workinkg. It is just that there is this tiny little, insignificant detail.


It seems for me that, after a couple of minutes, cups turns the connection off. If I run the system-config-printer, even as root, the printer is gone, it says "Not connected" and I click the Connect button, I have to choose localhost, the only cups server, and I click the Connect button, and it says error, "Failed to connect to server".
What's going on?
I would be happy if I just could keep the connection to localhost alive, I mean, to keep the printer in the system's printers list. It is that too much for ask?


Which are my system's specifications that you need to know, and, if you really need them, how could I figure out them?

---

### Post by russed2 on 2017-05-03
Update:
Searching for Cups connection problems, I found this page:


[https://forums.linuxmint.com/viewtopic.php?t=51175](https://forums.linuxmint.com/viewtopic.php?t=51175)


By issuing this terminal command:


sudo /etc/init.d/cups restart


The printer reappeared in the system's printers list, in System Tools > Printers. It is still there after a while, so this seems to be a solution. So, I think this thread can be marked as Solved.


By the way, I can now access to cups' configuration page, at [http://localhost:631](http://localhost:631), which I could not before issuing the cups restart command.


I would be very thankful If I could get some help on the other subjects.

---

### Post by Bucky Ball on 2017-05-03
> **russed2 said:**
> I would be very thankful If I could get some help on the other subjects.

Which other subjects? If they are not related to the printer issue you should post a new thread as they will have nothing to do with the title or subject of this solved support thread.

You can mark as solved from the Thread Tools drop down menu, top right of page. Good luck. ;)

---

### Post by russed2 on 2017-05-05
> **Bucky Ball said:**
> you should post a new thread
I already did that, as you suggested here [https://ubuntuforums.org/showthread.php?t=2360069#2](https://ubuntuforums.org/showthread.php?t=2360069#2)
I would settle for just having the username field of the greeter login already filled, Kubuntu style, so I just would need to enter the password. Instead of help I only received critizes seemingly almost complaining why the hell do I want that.


> You can mark as solved from the Thread Tools drop down menu, top right of page. Good luck. 
Well, I wouldn't say solved yet.
Yes, that command to restart cups worked, but just for a while.
I kept searching and found what seems to be a better solution.
First, it's necessary to edit the line ExecStart=/usr/sbin/cupsd -l under the [Service] section of the file /lib/systemd/system/cups.service, replacing the -l parameter (run on demand, default), by the -f parameter (run on foreground, execute cupsd --help for details). So, this is how that line looks:


ExecStart=/usr/sbin/cupsd -f 


Second, you have to reload the daemon:


sudo systemctl daemon-reload


And finally, cups must be restarted:


sudo systemctl restart cups.service


It has been uninterruptedly running from start for 58 minutes now, so I guess it is working.


This is not a Lubuntu problem, but a well known cups' bug affecting Xenial 16.04 family of Ubuntu's.

---

### Post by Bucky Ball on 2017-05-05
> **russed2 said:**
> Well, I wouldn't say solved yet.
Yes, that command to restart cups worked, but just for a while.

Then 'unsolve' it the same way you marked it as solved if you want support with it as you won't get much continuing to ask questions on a solved thread. You'll find 'mark thread unsolved' in the Thread Tools.

---

