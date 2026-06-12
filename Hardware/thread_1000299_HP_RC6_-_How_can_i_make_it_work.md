---
title: "HP RC6 - How can i make it work?"
date: 2008-12-02
forum: Hardware
---

### Post by yachoo on 2008-12-02
Hallo,
I just bought a new laptop and installed Ubuntu 8.10 on it.
It's hp dv5-1170ew.
There is this small remote control on it (hp rc6). I would like to make it work, but I have no idea how to do this. I know that lirc can make some ir devices work. I tried to configure it somehow. Here is what I did:
1) I tried to configure hardware.conf and lircd.conf in /etc/lirc directory
2) I found out that if lirc_serial module is loaded, then i have /dev/lirc0 file - so i guess this is the right module.
3)```
yachoo@yachoo:~$ lshal|grep lirc
udi = '/org/freedesktop/Hal/devices/platform_lirc_serial_0'
  info.linux.driver = 'lirc_serial'  (string)
  info.product = 'Platform Device (lirc_serial.0)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_lirc_serial_0'  (string)
  linux.sysfs_path = '/sys/devices/platform/lirc_serial.0'  (string)
  platform.id = 'lirc_serial.0'  (string)
```
4) Neither irrecord nor irw responding to any buttons on remote.
5) Interesting thing: one button worked out of the box. That is the one that change the video output. Probably this is the hardware thing and it's avoiding any software.

You can probably see that I have no idea what to do next.
Please help me :)

---

### Post by efm on 2008-12-04
Hi,
I have exactly the same situation,
although my notebook is dv6910. It was working few weeks ago (on 8.04 as
well as 8.10), but suddenly it stopped working.
If you have solved the problem, please let me know,
thank you

---

### Post by benpaka on 2008-12-12
Exactly the same probleme and still no solution...

I'm using hp dv5 1073ez.

---

### Post by Davie In Dubai on 2008-12-13
I've been searching for two days on how to get the HP DV1000 Irda port working with LIRC without any luck.  I then found the original 'thin' remote that came with it and found it works without any software needed.

It's marked as an RC6 device and I guess it maps directly from the Irda port to the keyboard/USB bus as some sort of hardware input device - but I can't seem to find any HowTos on getting it configured in Ubuntu (specifically XBMC) to map the remote buttons to something useful.

D.

---

### Post by yachoo on 2008-12-15
It works for me now after installing new BIOS :)
Only Play button send no keycode, but I configured Vista-button to be a play button :P

---

### Post by Xcerca on 2009-01-04
> **yachoo said:**
> It works for me now after installing new BIOS :)
Only Play button send no keycode, but I configured Vista-button to be a play button :P


how did you configure the buttons to do what you need to do , the vol and play buttons worked out of the box for me, and the full screen button works also.  but i ran irw and lirc isn't even installed,   where do you goto to cinfigure this ,  i have the HP RC6 and the ir reciver built into the front

:o when i push the next button in banshee it open up the add podcast window

thanks

UPDATE:   well about 4 min after my first post i went to System>Pref>Keyboard Shortcuts , there you can just edit the keyboard shortcut and when it says enter shortcut for what you want to do ex. press cntrl+alt+whatever you can just push one of the buttons on the ir remote and it will register

i hope that helps

---

### Post by beeejay77 on 2009-02-12
> **Xcerca said:**
> how did you configure the buttons to do what you need to do , the vol and play buttons worked out of the box for me, and the full screen button works also.  but i ran irw and lirc isn't even installed,   where do you goto to cinfigure this ,  i have the HP RC6 and the ir reciver built into the front

:o when i push the next button in banshee it open up the add podcast window

thanks

UPDATE:   well about 4 min after my first post i went to System>Pref>Keyboard Shortcuts , there you can just edit the keyboard shortcut and when it says enter shortcut for what you want to do ex. press cntrl+alt+whatever you can just push one of the buttons on the ir remote and it will register

i hope that helps
I have hp dv5 1110ew. For me one button worked out of the box. That is the one that change the video output.

By the way - HP RC6 product nameis HP Mobile Remote Control.

I upgraded bios to F13A
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68129-1&lc=en&dlc=en&cc=us&lang=en&os=2064&product=3829664](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68129-1&lc=en&dlc=en&cc=us&lang=en&os=2064&product=3829664)

but this do not help.

I do not know if it is possible toconfigure RC6 with lirc. It is working withot lirc - but just one button.

---

### Post by beeejay77 on 2009-02-13
Suddenly it started working for me. I do not know why. All the buttons are working but play, rewind,forward. I can not assign those 3 buttons in System > Preferences > Keybord shortcuts. 

I was fighting with sound over hdmi and here are changes i did:

1. I followed this guide:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490) 
- unistalled nvidia packages with purge - in synaptic
- unistalled linux-restricted-modules and linux-restricted-modules-common packages with purge - (be carefull because my wifi driver was restricted one and i have to connect by cable)
- restarted system on vesa video drivers and reconfigured xorg.conf - there is some wizard at the start of system
- installed "sudo sh NVIDIA-Linux-x86-180.29-pkg1.run" and nvidia-xconfig

2. Installed ALSA from snapshot:
sudo sh ./AlsaUpgrade-1.0.x-rev-1.16.sh -snap

3. I installed again linux-restricted-modules and linux-restricted-modules-common

4. I rebooted and my remote control started to work. 

I still do not know what is responsible for working of this remote control.

---

### Post by beeejay77 on 2009-02-18
I removed LIRC to check if RC6 depends on it.

My RC6 got back to one button working (that for switching display) state.

I than installed LIRC again, but my RC6 still is not working.

I tryed procedure with Alsa and nvidia reinstall, but that not helps.

I guess it depends on keyboard and have something with touch sensible buttons. My "play" button _did not_ work from remote, but _worked_ touch sensible button. My "stop" button _worked_ from remote, but _did not_ worked touch sensible button.

---

### Post by remu on 2009-02-21
I have an HP dv4, and the remote that came with it works fine under Vista, however, it doesn't work under Ubuntu. Any ideas?

Also, were you able to get audio out through your HDMI port?

---

### Post by beeejay77 on 2009-02-22
> **remu said:**
> I have an HP dv4, and the remote that came with it works fine under Vista, however, it doesn't work under Ubuntu. Any ideas?

Also, were you able to get audio out through your HDMI port?
My remote started to work. I have installed lirc, gnome-lirc-properties, lirc-x, inputlirc. I still do not know why and how it is working. As it works it is easy to connect remote buttons with functions in System>Preferences>keyboard shortcuts. 

My sound over HDMI is not working. Below is thread on alsa developer maillist:
[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-February/014702.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-February/014702.html)

You can try things they tell me to do. Maybe it will work for You.

---

### Post by remu on 2009-02-22
> **beeejay77 said:**
> My remote started to work. I have installed lirc, gnome-lirc-properties, lirc-x, inputlirc. I still do not know why and how it is working. As it works it is easy to connect remote buttons with functions in System>Preferences>keyboard shortcuts. 

My sound over HDMI is not working. Below is thread on alsa developer maillist:
[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-February/014702.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-February/014702.html)

You can try things they tell me to do. Maybe it will work for You.

Installing those didn't seem to work for me. Could you provide a screenshot of your gnome-lirc-properties window? I don't know what to select there. Maybe thats whats missing, I don't know.

---

### Post by beeejay77 on 2009-02-24
gnome-lirc-properties window:
Manufacturer:Linux Input Device
Model:AT translated set 2 keyboard
X use supplied remote control

---

### Post by grogo on 2009-03-16
For anyone having this issue on a HP Pavilion Laptop:

1 - Please clearly state your exact model.  The dv6xxx / dv7xxx / dv9xxx ARE NOT the same as the dv4-xxxx / dv5-xxxx / dv7-xxxx units.

2 - For those using the dv6xxx etc units, update your BIOS and it should work based what I've seen on the internet and personal experience with a dv6627ca under 8.04 and 8.10.

3 - Anyone who's managed to get this to work on a dv4/dv5/dv7 please let us know how!

---

### Post by remu on 2009-03-16
I have a dv4-1000, Would love to know if/how it can work!

---

### Post by beeejay77 on 2009-03-17
> **grogo said:**
> For anyone having this issue on a HP Pavilion Laptop:

1 - Please clearly state your exact model.  The dv6xxx / dv7xxx / dv9xxx ARE NOT the same as the dv4-xxxx / dv5-xxxx / dv7-xxxx units.

2 - For those using the dv6xxx etc units, update your BIOS and it should work based what I've seen on the internet and personal experience with a dv6627ca under 8.04 and 8.10.

3 - Anyone who's managed to get this to work on a dv4/dv5/dv7 please let us know how!
I have hp dv5 1110ew. I still do not know why it is working. It is sometimets working, sometimes not.It is strongly connected with touch sensible buttons located over the top of keyboard. Those touch sensible buttons sometimes stuck - mainly sound +/-. I have effect like sound is going up and down without touching any button.

---

### Post by epidemiks on 2009-03-27
i have a dv5 1139tx
i had some functionality until i installed lirc.
now only the video output button works. :(

---

### Post by epidemiks on 2009-03-28
got most of the buttons back by updating bios

here's the link for my dv5 1139tx 
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68741-1&lc=en&dlc=en&cc=au&product=3834832&os=2093&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68741-1&lc=en&dlc=en&cc=au&product=3834832&os=2093&lang=en)

---

### Post by dima206 on 2009-05-12
I have DV5-1007tx, my remote still not working.
If any one can post his correct /etc/lirc/hardware.conf
TNX

---

### Post by wwitthoff1 on 2009-07-26
Just went through this same thing with my dv6000z.  I found out that the RC6 (HP: HSTNN-PRO7), is handled in Ubuntu Jaunty (9.04) as a combination of keyboard and XF86 commands.  The picture attached is the ExpressCard remote in question.  Assigning the buttons letters, from left to right, top to bottom, here is how Ubuntu "sees" the button presses.

A) XF86Sleep (Power)
B) XF86Display (Monitor Switch)
C) XF86AudioMedia (QuickPlay)
D) *Not Assigned* (DVD)
E) Alt + Super L (Media Center)
F) Page Up (Channel Up)
G) XF86AudioStop (Stop Button)
H) Shift + Ctrl + B (Rewind)
I) XF86AudioPlay (Play/Pause)
J) Shift + Ctrl + F (Fast Forward)
K) Page Down (Channel Down)
L) XF86AudioPrevious (Previous Chapter)
M) Up (Nav Up)
N) XF86AudioNext (Next Chapter)
O) Left (Nav Left)
P) Return (Nav OK)
Q) Right (Nav Right)
R) Backspace (Return)
S) Down (Nav Down)
T) Menu (i)
U) XF86AudioLowerVolume (Speaker with one line)
V) XF86AudioMute (Speaker with "no" symbol)
W) XF86AudioRaiseVolume) (Speaker with 3 lines)

Sorry if this revives a old post, but knowledge knows no age.  I can't speak for the most recent version of the ExpressCard remote as it wont work with my laptop.  These are without lirc installed.

---

### Post by efm on 2009-10-31
@wwithoff1:
is your remote working? how do you know the assignment of every button?

thank you

---

### Post by ticapix on 2010-01-17
> **yachoo said:**
> It works for me now after installing new BIOS :)
Only Play button send no keycode, but I configured Vista-button to be a play button :P
Hi

I have the same problem.
The rc6 inputs are recognized as if the keyboard keys were pressed, except for the Play/Pause button that doesn't respond.

---

### Post by Darvenkry on 2010-03-14
Well with regards to wwithhoff1 post, is there a way to change how ubuntu sees the buttons. Ie. change wat keyboard button corresponds to each button on the remote. their must be some sort of config file. Anyone know where it is so we can just change the values.

---

