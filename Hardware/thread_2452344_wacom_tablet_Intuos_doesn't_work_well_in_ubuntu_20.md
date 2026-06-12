---
title: "wacom tablet Intuos doesn't work well in ubuntu 20.04"
date: 2020-10-20
forum: Hardware
---

### Post by bustamanteguevara on 2020-10-20
I use a wacom tablet Wacom Intuos. Sometimes it works fine sometimes it has the following isue. It maps the screen to half of the tablet. So that the drawing region is very reduced and drawings are deformed. 

The tablet model is CTL-4100.


These are the fixes I have tried. 

1. Stop and restart the controller 

user@user-Latitude-5491:~$ lsmod | grep wacom
wacom                 118784  0
usbhid                 57344  1 wacom
hid                   131072  5 i2c_hid,wacom,usbhid,hid_multitouch,hid_generic


user@user-Latitude-5491:~$ sudo rmmod wacom
user@user-Latitude-5491:~$ sudo modprobe wacom

doesn't fix the problem. 

2. Reinstall wacom drivers 

user@user-Latitude-5491:~$ sudo rmmod wacom
user@user-Latitude-5491:~$ sudo modprobe wacom

Didn't work. 

3. Installed [https://github.com/linuxwacom/xf86-input-wacom](https://github.com/linuxwacom/xf86-input-wacom), 

Didn't work. 

4. Added the ppa [[FONT=Calibri]http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu[/FONT]]("http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu")

now every time I run *sudo apt update* I get the error message 

[LEFT][COLOR=windowtext][COLOR=windowtext][FONT=Calibri]Err:12 [/FONT][/COLOR][[FONT=Calibri]http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu[/FONT]]("http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu")[COLOR=windowtext][FONT=Calibri] focal Release [/FONT][/COLOR]
[/COLOR]
[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]  404  Not Found [IP: 91.189.95.83 80][/FONT][/COLOR][/COLOR]
[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]Reading package lists... Done[/FONT][/COLOR][/COLOR]
[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]E: The repository '[/FONT][/COLOR][[FONT=Calibri]http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu[/FONT]]("http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu")[COLOR=windowtext][FONT=Calibri] focal Release' does not have a Release file.[/FONT][/COLOR][COLOR=windowtext][FONT=Calibri] 
[/FONT][/COLOR][/COLOR][/LEFT]


So. At this point I would like to delete that ppa, and just patiently wait that the bug gets fixed by the ubuntu developers. 

Questions: 

1. Any idea of what I can do to get the tablet to work? 

2. How do I delete the ppa so that the system doesn't try to update from there anymore. 

Thanks for the help!

---

### Post by ajfidelis on 2020-10-23
I followed these steps a lot of times, and I'm still in the same point.

---

### Post by johnklemen on 2021-01-31
Unfortunately I'm expieriencing exactly the same issues with my brand new intuos - if anyone found a solution in the mean while, I'd be glad to hear it!

---

### Post by CelticWarrior on 2021-01-31
> [COLOR=#000000]2. Reinstall wacom drivers[/COLOR]

[COLOR=#000000]user@user-Latitude-5491:~$ sudo rmmod wacom[/COLOR]
[COLOR=#000000]user@user-Latitude-5491:~$ sudo modprobe wacom[/COLOR]

[COLOR=#000000]Didn't work.[/COLOR]

That isn't a reinstallation and even if it was, reinstalling the same non-working drivers doesn't fix issues in Linux.

> [COLOR=#000000]3. Installed [/COLOR][https://github.com/linuxwacom/xf86-input-wacom](https://github.com/linuxwacom/xf86-input-wacom)[COLOR=#000000],[/COLOR]

[COLOR=#000000]Didn't work.[/COLOR]


"Didn't work" is meaningless. Please describe what you did exactly, what were the expected results and what happened instead.

> [COLOR=#000000]4. Added the ppa [/COLOR][[FONT=Calibri]http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu[/FONT]]("http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu")

[COLOR=#000000]now every time I run [/COLOR][I]sudo apt update I get the error message

[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]Err:12 [/FONT][/COLOR][[FONT=Calibri]http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu[/FONT]]("http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu")[COLOR=windowtext][FONT=Calibri] focal Release[/FONT][/COLOR]
[/COLOR]
[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]404 Not Found [IP: 91.189.95.83 80][/FONT][/COLOR][/COLOR]
[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]Reading package lists... Done[/FONT][/COLOR][/COLOR]
[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]E: The repository '[/FONT][/COLOR][[FONT=Calibri]http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu[/FONT]]("http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu")[COLOR=windowtext][FONT=Calibri] focal Release' does not have a Release file.[/FONT][/COLOR][COLOR=windowtext][FONT=Calibri]
[/FONT][/COLOR][/COLOR]
[COLOR=windowtext][COLOR=windowtext][FONT=Calibri]
[/FONT][/COLOR][/COLOR]
[/I]

That PPA has no updates since 2015. It doesn't support your Ubuntu release.
Yes, you should remove it.

---

### Post by johnklemen on 2021-01-31
I found the solution here: [https://askubuntu.com/questions/1269297/wacom-co-ltd-intuos-bt-m-stopped-working-corectly](https://askubuntu.com/questions/1269297/wacom-co-ltd-intuos-bt-m-stopped-working-corectly)

Press the left and the right button simultaneously until the LED blinks twice - after that everything was fine. (The Tablet was in Android mode before - don't ask me in which mode it is now!)

---

