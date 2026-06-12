---
title: "Samsung NF310"
date: 2010-12-04
forum: Hardware
---

### Post by jschall1 on 2010-12-04
Just wanted to leave a report on the Samsung NF310, and at the same time I'm looking for help with an issue with it:

Everything here was tested on Kubuntu amd64 with kubuntu-ppa.
**What works:**
WiFi (install closed-source driver through Ubuntu's closed driver installer GUI)
Webcam (works out of the box, at least with Skype)
Bluetooth (as far as I can tell - I don't have many devices)
Multitouch touchpad (set up [this script]("http://pastebin.ca/2010282") to run when you log in)
Desktop effects work well in KDE. I thought performance was a pinch better after installing ppa:ubuntu-x-swat/x-updates
Audio, including microphone. You'll have to unmute capture to use mic, that's it. Speakers are great for a netbook.
Suspend works great, everything seems to come back.
Ethernet works.
Most Fn-keys, but samsung-tools from ppa:voria/ppa is required or the Fn key will never get released and will lock up the keyboard.

**What wasn't tested:**
The card reader. I have every confidence that it will work fine, because it's just a damn card reader.
VGA output. I have every confidence that it will work fine, because it worked on another netbook I had with the same intel graphics.
Hibernate. If suspend works, I'm guessing this'll work.

**What doesn't work:**
The screen brightness control. This works from the KDE battery applet and partially works from KDE's power management daemon. To get that far, I had to install samsung-backlight from ppa:voria/ppa.
However, the fn-keys that adjust brightness simply do not work. KDE's brightness OSD (on-screen display) pops up when I press them, but it does not change the brightness.
Additionally, there's odd behavior from KDE's power management daemon when "dim display after x minutes of inactivity" is set. I set it to 1 minute, and it seems to dim the display every minute whether or not it had dimmed the display the previous minute. So, it ends up taking the brightness all the way down in less than 10 minutes. It then fails to restore the brightness to the original value.

If anyone can help me with the brightness issues, it would be appreciated, but I have the sneaking suspicion that I'm going to have to wait on a BIOS update on this one.

---

### Post by jschall1 on 2010-12-10
Bump, still no solution found for backlight issues.

---

### Post by Ludes on 2010-12-12
Hi,

Install samsung-tools, samsung-backlight and udev from ppa Voria worked for me (Ubuntu Maverick x32 on nf310).

Hope it helps.

---

### Post by jschall1 on 2010-12-12
> **Ludes said:**
> Hi,

Install samsung-tools, samsung-backlight and udev from ppa Voria worked for me (Ubuntu Maverick x32 on nf310).

Hope it helps.

I've already got all those installed. The keys just don't work, they bring up the on-screen display but they don't change the brightness. I've fixed it for now by binding the keys to a script. I am using KDE.
Do your brightness keys work?

---

### Post by giocondus on 2010-12-19
The solution to brightness is here, at post #3 [http://www.voria.org/forum/viewtopic.php?f=3&t=516&start=0&hilit=r510](http://www.voria.org/forum/viewtopic.php?f=3&t=516&start=0&hilit=r510)
It worked for me, I have a NF310 with Ubuntu 10.10 installed.
Hope it works also for you :)
Matteo.
P.S. how did you enable multitouch? I can't understand "the set up [this script]("http://pastebin.ca/2010282") to run" thing. Should I add the script to startup programs? Thanks.

---

### Post by jschall1 on 2010-12-19
> **giocondus said:**
> The solution to brightness is here, at post #3 [http://www.voria.org/forum/viewtopic.php?f=3&t=516&start=0&hilit=r510](http://www.voria.org/forum/viewtopic.php?f=3&t=516&start=0&hilit=r510)
It worked for me, I have a NF310 with Ubuntu 10.10 installed.
Hope it works also for you :)
Matteo.
P.S. how did you enable multitouch? I can't understand "the set up [this script]("http://pastebin.ca/2010282") to run" thing. Should I add the script to startup programs? Thanks.

Yeah, I don't use gnome any more but I think you want system->preferences->session to make it run when you start your gnome session.
So, copy it into gedit, save it as whatever, make the file executable, add it in system>preferences>session.

Brightness didn't work for me. I'm thinking KDE problem. Worked around it already by assigning the keys to a script that changes the brightness.

---

### Post by mjhuurre on 2011-01-06
> **jschall1 said:**
> 
Multitouch touchpad (set up [this script]("http://pastebin.ca/2010282") to run when you log in)


For me the link gives just "**That is an invalid ID, or the post has expired.**"

Could you point the correct URL or just paste the script here? 

Just bought the NF310 and checking out what is needed to make it work with Ubuntu.

---

### Post by jschall1 on 2011-01-06
> **mjhuurre said:**
> For me the link gives just "**That is an invalid ID, or the post has expired.**"

Could you point the correct URL or just paste the script here? 

Just bought the NF310 and checking out what is needed to make it work with Ubuntu.

```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
```

---

### Post by Whitefall on 2011-02-04
Brightness control and the other Fn keys worked without problems for me (using Gnome) after installing the ppa Voria packages.

Suspend using the Suspend key (Fn-Esc) seems to work fine (about 7 seconds to suspend, 3 seconds to wake up), however suspending by closing the lid is unreliable; sometimes it doesn't work at all, sometimes it takes a long time. Also the netbook sometimes goes into sleep when plugging out the power cable, even if the battery is fully charged.

That multitouch hack seems to work only until the next suspend, you'd have to run it again after every wakeup.

---

### Post by jschall1 on 2011-02-04
> **Whitefall said:**
> Brightness control and the other Fn keys worked without problems for me (using Gnome) after installing the ppa Voria packages.

Suspend using the Suspend key (Fn-Esc) seems to work fine (about 7 seconds to suspend, 3 seconds to wake up), however suspending by closing the lid is unreliable; sometimes it doesn't work at all, sometimes it takes a long time. Also the netbook sometimes goes into sleep when plugging out the power cable, even if the battery is fully charged.

That multitouch hack seems to work only until the next suspend, you'd have to run it again after every wakeup.

I don't have the above problems in kubuntu.
I did switch to ubuntu once and figured out how to fix the multitouch. I've since switched back to kubuntu, so I don't have the file for you, but I'm pretty sure you want to create a HAL fdi file.

---

### Post by Whitefall on 2011-02-12
The suspend issue seems to be caused by this bug:
[http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg31142.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg31142.html)
[https://bugzilla.kernel.org/show_bug.cgi?id=17081](https://bugzilla.kernel.org/show_bug.cgi?id=17081)

The first suspend by closing the lid always works, but afterwards /proc/acpi/button/lid/LID0/state still shows "closed", and the next time the lid is closed it fails to suspend.

---

### Post by jschall1 on 2011-02-14
> **Whitefall said:**
> The suspend issue seems to be caused by this bug:
[http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg31142.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg31142.html)
[https://bugzilla.kernel.org/show_bug.cgi?id=17081](https://bugzilla.kernel.org/show_bug.cgi?id=17081)

The first suspend by closing the lid always works, but afterwards /proc/acpi/button/lid/LID0/state still shows "closed", and the next time the lid is closed it fails to suspend.

Hmm. Never had a problem suspending by closing the lid.

---

### Post by dirtyhabanero on 2011-02-24
Hey guys, great posts. Just bought an NF310 today and am installing Ubuntu 10.10 Netbook right now. Just wanted to see if you guys had any trouble getting the computer to boot from a USB drive. Seeing as I couldn't find much information out there, except here which is in Dutch, 

[http://forum.ubuntu-nl.org/installatie/installatie-ubuntu-10-04-10-10-op-samsung-nf-310-mislukt/?action=printpage](http://forum.ubuntu-nl.org/installatie/installatie-ubuntu-10-04-10-10-op-samsung-nf-310-mislukt/?action=printpage)

I did want to put it up again for any future users. I did have a bit of trouble booting from the USB and I think it had something to do with my thumb drive being a SDHC rather than a flash drive. Attempted to install Maverick Netbook Ed. from the SDHC but the computer did not even find it during the bootup stage. Did the same with a Flash drive, Lexar 8GB, and it was recognized and in slot 6:! Will see if SDHC thumb drives work once it is installed.

My one question when booting from another device (CD-ROM, USB), is it better to re-prioritize the boot order in the BIOS settings and set USB HDD to the top(first boot device), or better to just press the ESC button once the initial "Samsung" screen has finished and then select the device to boot from?

I never really enjoy playing with the BIOS settings but if I have to, then so be it! :twisted:

---

### Post by dirtyhabanero on 2011-04-30
Hey, anyone installed Natty onto their samsung?

I did so just to other day and I seem to be having trouble with the brightness again. I installed the samsung-tools (which appears to have been updated) so the Fn keys are working, but if I try using the laptop on battery power, the screen does some weird brightness adjust thing where it tries to adjust itself if the screen is idle for about 1 min - this is once I'm logged in and everything.

Anyone having this issue or just me?

edit:
So I may have found a solution. The problem seems to arise when on battery power. If the computer is idle, the brightness level is dropped - to save power or something. But when this happens, something goes wrong. In any case, the link below has half a solution. Now when computer is idle, the brightness is dimmed and that's that. Now I just need to find out how to stop it from dimming
[http://www.voria.org/forum/viewtopic.php?p=4750#p4750](http://www.voria.org/forum/viewtopic.php?p=4750#p4750)

I've posted in this thread since it is about Samsung NF310 and the brightness.

---

### Post by jonsson on 2011-04-30
I got my NF310 in the mail the other day and installed Kubuntu Natty on it last night (32 bit, from scratch, whole disk). Most things seem to work out of the box.

I had to install a proprietary driver for wifi (GUI did this with two clicks). Before that it seemed to work and I could see the networks around me but it wouldn't connect to one. Seems to work now, though I have only tried an unencrypted network yet.

The Fn brightness controls do not work. KDE seems to recognise them but they have no effect. It seems to stay on full brightness though and that's nearly always what I want anyway so I'll not bother with this for now.

One really odd thing it does is that it suspends whenever I plug the power cord in/out. It wakes up without problems afterwards but obviously it misinterprets some signal?

Touchpad seems to work out of the box, including multi tap. I have no experience with this since I'm used to a pointing stick but I looked at the settings and the things that are set seem to work, e.g. 2 finger scroll, tap with 2 fingers for middle mouse button etc

---

### Post by jonsson on 2011-04-30
One more thing. I cannot see the GRUB menu. It says something about video mode not set and goes black. The next thing I see is the password prompt for my encrypted disk.

And no that I think about video, desktop effects won't work out of the box. I can live without them but would prefer to have them.

---

### Post by crowolfbook on 2011-06-08
I installed ubuntu 10.10, samsung-tools, samsung-backlight and udev from ppa:voria, and the shortcuts seem to work, but for the normal keys the fn button is still locked (so when I press u, it actually types 4). Thing is, my layout is azerty (belgian keyboard), so I'm not sure if that is of any influence. Help is much appreciated.

---

### Post by crowolfbook on 2011-06-09
some more info: i don't have the problem on the login screen, meanwhile I upgraded Ubuntu to the latest version, still no luck

---

### Post by crowolfbook on 2011-06-10
So, I found the problem (this is going to sound so lame): my num lock was turned on, so Fn+F11 fixed it... Here's to the noobs in this world!

---

