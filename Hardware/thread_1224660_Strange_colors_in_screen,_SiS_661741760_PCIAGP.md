---
title: "Strange colors in screen, SiS 661/741/760 PCI/AGP"
date: 2009-07-27
forum: Hardware
---

### Post by DionB on 2009-07-27
Greetings,

I first want to say that I am completely new and had much trouble with Ubuntu. It took me an entire day to get wireless working, and now I have moved on to the next problem.

I have really strange colours in my screen. Most pictures and colours aren't displayed how they should. Most have lines running through them. It looks a bit like a tv that has no signal. 

This is what the lspci says about my video card:
```
VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```I have tried many things that people recommend on the internet. I can't even remember everything I did. I tried for example to sudo gedit /etc/x11/xorg.conf. When it opened it was already empty, wich I found weird. I filled in what I got from an example, and it said: Could not find file: /etc/x11/xorg.config . I downloaded all kinds of SiS drivers, but I don't know how to get them working.

I am totally lost in what to do now. Is there anyone that can help me out?

Thanks

EDIT: I'm using Ubuntu 9.04

---

### Post by komputes on 2009-07-27
This issue has been reported and confirmed. I have attempted to contact the driver maintainer but have not received a response. Feel free to subscribe to this bug and mark it as affecting you, as attention will only be paid to the bug if the numbers are there backing it up.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/317658](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/317658)

Meanwhile you can use the following as a workaround:

>            please try adding sisfb to /etc/modules to solve this issue.

1) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/modules"
 2) The editor will open. Add the following line to the bottom (without quotes):
"sisfb"
 3) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/X11/xorg.conf"
 4) In Section "Device" make sure there is a line specifying the sis driver:
        Driver "sis"


The files should end up looking similar to this:


 == /etc/modules ==
fuse
lp
sisfb
== ==

 == /etc/X11/xorg.conf ==
Section "Device"
        Identifier      "Video Device"
        Driver          "sis"
EndSection
 Section "Monitor"
        Identifier      "Configured Monitor"
EndSection
 Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Video Device"
EndSection
== ==

        


---

### Post by DionB on 2009-07-28
Thank you very much! This indeed helped my problem, all the weird colours are gone.

---

### Post by strangequarks on 2010-01-05
Hi, I had the same problem, and just tried the first two steps of your solution:

1) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/modules"
2) The editor will open. Add the following line to the bottom (without quotes):
"sisfb"

I saved the file and restarted the computer and it's all fine now! Didn't do anything with xorg.conf. 

Thank you v much!

---

### Post by nightwolf2k5 on 2010-02-25
Hi,

I have exactly the same problem and posted a thread too [http://ubuntuforums.org/showthread.php?t=1399237](http://ubuntuforums.org/showthread.php?t=1399237) to which unfortunately i could not get a response.

After around 6 or 7 restarts, the display works normally. But if i restart again, the same problem would occur.

I have somehow (just by trial and error) found a workaround to this. But i am really not sure if it can be called a workaround because it is just a temporary solution.

When you get a working display... instead of a shut down.. just hibernate. When you switch the system back up again, the display should be normal.
Like i said, this is just a temporary solution until you would require restarting the system after an update or something like that.

---

### Post by ajslay on 2010-02-26
wow i finaly found an answer to this problem! thanks for this thread lol. i was having the same problem on my brothers 3 year old emachines laptop, im gonna see if this works. thanks

---

### Post by mibdata on 2010-05-11
Tenta alt+f2 "metacity -c –replace"

aqui resolveu.

---

