---
title: "Sytem Freeze on Resume from Suspend/Standby/Sleep"
date: 2008-08-29
forum: General Help
---

### Post by Altay_H on 2008-08-29
Occasionally, on resume from Suspend, my system will completely freeze. The usual screen is displayed asking for my password, but it doesn't respond to anything. My [built-in] keyboard doesn't work at all; not even the lights turn on when I press Caps Lock or Num Lock. My [built-in touchpad] mouse also fails to respond to anything. It has an on/off button with an LED, and even that doesn't respond while frozen. The screen, however, looks exactly as it should. The cursor flashes properly and the mouse pointer is displayed, it just doesn't react to any input. I'm forced to use the power switch to turn if off. Oddly though, I can't reproduce this problem consistently. It tends to occur on the second or third time I suspend since my last reboot. I don't think it has ever occurred on the first resume since the last reboot. It's consistent enough to be a significant inconvenience though. I'd say about 40% of the time I resume from Suspend it just freezes as previously described. The other 60% of the time it works without problems. Any suggestions, ideas, or advice is greatly appreciated. Thanks.

---

### Post by mssever on 2008-08-29
> **Altay_H said:**
> Occasionally, on resume from Suspend, my system will completely freeze. The usual screen is displayed asking for my password, but it doesn't respond to anything. My [built-in] keyboard doesn't work at all; not even the lights turn on when I press Caps Lock or Num Lock. My [built-in touchpad] mouse also fails to respond to anything. It has an on/off button with an LED, and even that doesn't respond while frozen. The screen, however, looks exactly as it should. The cursor flashes properly and the mouse pointer is displayed, it just doesn't react to any input. I'm forced to use the power switch to turn if off. Oddly though, I can't reproduce this problem consistently. It tends to occur on the second or third time I suspend since my last reboot. I don't think it has ever occurred on the first resume since the last reboot. It's consistent enough to be a significant inconvenience though. I'd say about 40% of the time I resume from Suspend it just freezes as previously described. The other 60% of the time it works without problems. Any suggestions, ideas, or advice is greatly appreciated. Thanks.
Suspending sometimes causes parts of the system to crash. Can you SSH in?

---

### Post by Altay_H on 2008-08-30
I'm not familiar with SSH. I'm assuming you mean accessing the frozen computer via some sort of networked computer. I wouldn't know how to do it, but if there's some sort of guide I'll give it a try.

---

### Post by mssever on 2008-08-31
See Wikipedia for an explanation of SSH. To SSH into your box, you first need an SSH server on that machine: ```
sudo aptitude install openssh-server
```Then you can access your machine from somewhere else on the network: ```
ssh youruser@your.hostname.or.ip.address
```If you've done everything right, you should get a shell connection to the other machine, where you can do pretty much anything that you could do from a terminal on the host machine.

For the purposes of this thread, the most important fact is whether you can establish an SSH connection in the first place. Secondarily, you can use a process monitor such as htop to deduce what might have crashed.

---

### Post by Altay_H on 2008-10-04
I'm working on getting ssh to work. It's a bit more difficult for me using ssh on Vista on one computer.

Anyway, I wanted to point out a new observation I had recently. I disabled the password requirement for resuming from standby, and I noticed that all the programs resumed correctly. Even nm-applet displayed itself re-establishing a connection with my wireless network. All the processes resumed perfectly, but my keyboard and mouse would not respond to anything. Only the power button does anything. The odd thing is, it brings up the interactive shutdown menu correctly when pressed once. Of course, I had little choice but to hold it down and force the power off, but it means that the problem lies with the system recognizing my keyboard and mouse after resuming from standby.

Oh, and here's my lspci in case it's of any use:
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I'm using 32-bit Hardy Herron.

---

### Post by mssever on 2008-10-04
If you've got openssh-server set up on your Linux box, then you should be able to SSH in, provided you know the box's IP address. For a Windows SSH client, I recommend PuTTY.

Another option is VNC. You can configure your Linux box to accept VNC connections (System > Preferences > Remote Desktop), then install a VNC viewer on your Windows box and connect. TightVNC is the Windows VNC client I know, but there are others.

Either option should allow you to at the minimum reboot cleanly. Using SSH, you could also try restarting various system services (listed in /etc/init.d) and see if that cures things. On my machine, dbus sometimes needs to be restarted after resuming from suspend.

Aside from those suggestions, I really don't know how to troubleshoot your problem.

---

### Post by Altay_H on 2008-10-05
Alright. I managed to ssh in successfully. This time when I resumed from standby I just lost all sound. I don't know what to do from my other computer though. You suggested restarting program in /etc/init.d. There are a bunch there. I suspect cron might have something to do with it, because it was freezing consistently (well, twice in a row) when a cron task was scheduled to execute while the computer was on standby. If killing cron doesn't do it though, what can I do? Is there any way to figure out which process is causing the problem? Which one do the keyboard and mouse rely one?

---

### Post by mssever on 2008-10-05
The keyboard and mouse MIGHT be controlled in this case by X, in which case doing /etc/init.d/gdm restart would cure the problem (note that restarting gdm will kill any GUI program that may be running). But that's only a guess, because I really don't know what the real problem is. Likewise for the sound, you can try restarting pulseaudio, which might or might not work. Other possible culprits include hal and dbus, but that list is by no means exhaustive.

I really can't suggest a way to find out what the problem is other than trying stuff. Oh, I do know one thing: Look in your logs (/var/log), especially syslog and daemon.log and see if there are messages about some program that's crashing.

Even if you don't get the program sorted out and you're forced to reboot, you can do that in the proper way from SSH: ```
sudo reboot
```

---

### Post by xreaper on 2008-10-05
hey, just something random you might want to try.
set your screensaver to one of the 'GL' pre-installed ones, and then untick the "lock screen when computer is idle". then, after the screensaver is on for a couple of seconds, move the mouse. can you please let me know if the screen freezes? 

If it does freeze on the screensaver, it usually means you have a problem with the drivers for your graphics card. more common in ATI graphics cards than NVIDIA.

---

### Post by Altay_H on 2008-10-05
> **mssever said:**
> doing /etc/init.d/gdm restart would cure the problem (note that restarting gdm will kill any GUI program that may be running). But that's only a guess, because I really don't know what the real problem is.
How exactly would you suggest I restart it?
These commands?
```

killall gdm

/etc/init.d/gdm
```
Is there a way to restart it other than killing it then starting it back up?

> **mssever said:**
> I really can't suggest a way to find out what the problem is other than trying stuff. Oh, I do know one thing: Look in your logs (/var/log), especially syslog and daemon.log and see if there are messages about some program that's crashing.
I'll take a look at those logs and post them here next time it freezes. Lately it's been resuming correctly consistently. Hopefully I can reproduce the problem, or perhaps it's resolved itself.


> **xreaper said:**
> hey, just something random you might want to try.
set your screensaver to one of the 'GL' pre-installed ones, and then untick the "lock screen when computer is idle". then, after the screensaver is on for a couple of seconds, move the mouse. can you please let me know if the screen freezes? 
I tried it out with a bunch of different GL screensavers. GLMatrix worked without issues. GLKnots messed up a bit, but then corrected itself. GLSnake and GLText worked without issues. GLSlideshow actually froze up, but when I moved the mouse everything resumed correctly. None of them actually froze up my system in any way.

> **xreaper said:**
> If it does freeze on the screensaver, it usually means you have a problem with the drivers for your graphics card. more common in ATI graphics cards than NVIDIA.
I am using an ATI graphics card which required me to enable its drivers to get it working. I haven't had any noticeable issues with the card yet though.

---

### Post by mssever on 2008-10-05
> **Altay_H said:**
> How exactly would you suggest I restart it?
These commands?
```

killall gdm

/etc/init.d/gdm
```Is there a way to restart it other than killing it then starting it back up?
Do ```
sudo /etc/init.d/gdm restart
```All the scripts in /etc/init.d work that way. They accept, at the minimum, the arguments start, stop, and restart. Some scripts accept aditional arguments, which you can discover by reading the scripts. But start, stop, and restart should be sufficient for the purposes of this thread.

---

### Post by Altay_H on 2008-10-22
Well, it took a while to finally reproduce the problem. It's happened about 4-5 times, but either at incredibly inconvenient times, or when I wasn't sure what the frozen computer's IP address was (because conky was blocked by a window) so I couldn't ssh in. I'm finally in, and the keyboard and mouse are frozen.

I ran the following command with the following results:
```
:~$ sudo /etc/init.d/gdm restart
[sudo] password:
 * Stopping GNOME Display Manager...
 * Starting GNOME Display Manager...
:~$
```

The GNOME Desktop exited, and brought me back to my login screen. My keyboard and mouse are still locked though, so I can't log back in from the locked computer. Any ideas? Is there something else I should try, or should I just reboot it?

Here are the contents of /var/log/user.log
```

Oct 20 09:55:57 altay-laptop gnome-power-manager: (altay) Suspending computer. Reason: The power button has been pressed.
Oct 20 12:22:44 altay-laptop pulseaudio[11297]: module-alsa-sink.c: Got POLLERR from ALSA
Oct 20 12:22:44 altay-laptop last message repeated 12 times
Oct 20 12:22:50 altay-laptop gnome-power-manager: (altay) Resuming computer
Oct 20 12:23:13 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 20 12:23:13 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 20 12:23:13 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 20 12:23:13 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 20 12:28:36 altay-laptop gnome-power-manager: (altay) Suspending computer. Reason: The power button has been pressed.
Oct 20 12:28:52 altay-laptop pulseaudio[11297]: module-alsa-sink.c: Got POLLERR from ALSA
Oct 20 12:28:54 altay-laptop gnome-power-manager: (altay) Resuming computer
Oct 20 12:28:57 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 20 12:28:57 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 20 12:28:57 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 20 12:28:57 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 20 12:30:50 altay-laptop dhcdbd: Started up.
Oct 20 12:30:52 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 20 12:30:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 20 12:30:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 20 12:30:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 20 12:30:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 20 12:31:25 altay-laptop pulseaudio[6200]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 20 12:31:25 altay-laptop pulseaudio[6200]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 20 14:01:19 altay-laptop gnome-power-manager: (altay) Suspending computer. Reason: The power button has been pressed.
Oct 21 04:48:52 altay-laptop pulseaudio[6200]: module-alsa-sink.c: Got POLLERR from ALSA
Oct 21 04:48:52 altay-laptop last message repeated 5 times
Oct 21 04:48:52 altay-laptop gnome-power-manager: (altay) Resuming computer
Oct 21 04:48:52 altay-laptop gnome-power-manager: (altay) suspend failed
Oct 21 04:48:53 altay-laptop gnome-power-manager: (altay) Resuming computer
Oct 21 04:48:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 21 04:48:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 21 04:48:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 21 04:48:58 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 21 04:49:46 altay-laptop gnome-power-manager: (altay) Suspending computer. Reason: The power button has been pressed.
Oct 21 04:51:36 altay-laptop dhcdbd: Started up.
Oct 21 04:51:39 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 21 04:51:42 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 21 04:51:42 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 21 04:51:42 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 21 04:51:42 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 21 04:52:20 altay-laptop pulseaudio[6197]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 21 04:52:20 altay-laptop pulseaudio[6197]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 21 08:11:29 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 21 08:11:29 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 21 08:11:29 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 21 08:11:29 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 21 08:11:34 altay-laptop gnome-power-manager: (altay) Suspending computer. Reason: The power button has been pressed.
Oct 21 13:08:27 altay-laptop gnome-power-manager: (altay) Resuming computer
Oct 21 13:08:33 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 21 13:08:33 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 21 13:08:33 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 21 13:08:33 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 21 20:22:50 altay-laptop gnome-power-manager: (altay) Suspending computer. Reason: The power button has been pressed.
Oct 22 01:28:01 altay-laptop gnome-power-manager: (altay) Resuming computer
Oct 22 01:28:04 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 22 01:28:04 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 22 01:28:04 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 22 01:28:04 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 22 12:09:37 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Oct 22 12:09:46 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Oct 22 12:09:46 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Oct 22 12:09:46 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Oct 22 12:09:46 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Oct 22 12:09:46 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Oct 22 12:10:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 22 12:10:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 22 12:10:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 22 12:10:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

```

The keyboard and mouse stopped working at Oct 22 01:28:01.


Well, I have the power button set up to place the computer in suspend. I ended up pressing the power button to suspend it to see if resuming from suspend would change anything, but instead of resuming from suspend the BIOS resumed from startup. Of course, after the "reboot" the keyboard and mouse were working perfectly again. I've noticed that I only encounter this problem when I leave my computer suspended for a considerable time; typically about 5 hours.

---

### Post by EvilRobotDrew on 2008-10-22
I have the exact same issue with my laptop (compaq v2000, 1.8GHz AMD Turion™ 64 Mobile Technology ML-34, 2048mb RAM, ATI RADEON® XPRESS 200M IGP w/ 128mb shared video memory, Hardy Heron 8.04). Unfortunately it seems to happen to me at school more then anywhere else (probably because that is where i suspend my laptop the most) so i haven't been able to SSH in and take a look. 

i hope that someone knows a fix, this issue isn't enough to make be re-install windows, but it is very very annoying all the same, especially because there is no rhyme or reason to when it decides to lockup, it is random.

---

### Post by mssever on 2008-10-23
This definitely looks to me like a bug. I don't know of a fix. The best I can suggest is a way (or two) to get some good data for filing a bug report on Launchpad.net.

I'm wondering if your problem is caused by either hal or dbus. The way to test that would be to SSH in next time you have a problem, and do something like:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/hal restart
sudo /etc/init.d/gdm start
```If that doesn't fix things, then try restarting dbus by repeating the avoce commands substituting dbus for hal. Note that it's possible that one or both of those commands might end up disabling your network card and breaking your SSH session. Notice any errors or other relevant information.

Also, generally the most interesting logfile for general troubleshooting is /var/log/messages and /var/log/syslog, not so much /var/log/user.log. In this case, /var/log/daemon.log and /var/log/kern.log might also be relevant.

---

### Post by inveriarity on 2008-10-23
I have a similar problem, though it seems a bit more extreme. I run a Satellite Toshiba A135-S4427 with Hardy Heron 8.04 Suspending causes it to lose touch altogether.  I get an empty screen with one blinking cursor in the upper left corner.  I have no touchpad or keyboard input.  

Would the SSH approach work with this problem?  It seems that the entire system fails to resume after being suspended, so I am at a loss as to track this down further.  Many similar bug reports have been filed on Launchpad.

~Invers

---

### Post by Altay_H on 2008-10-23
> **mssever said:**
> sudo /etc/init.d/gdm stop
sudo /etc/init.d/hal restart
sudo /etc/init.d/gdm start

I'll give that a try next time I can. I don't know if it's relevant, but I often receive the error in the image below when I resume from suspend. Ironically, it only appears if the computer suspended and resumed correctly. It never appears when my computer freezes.


> **EvilRobotDrew said:**
> I have the exact same issue with my laptop (compaq v2000, 1.8GHz AMD Turion™ 64 Mobile Technology ML-34, 2048mb RAM, ATI RADEON® XPRESS 200M IGP w/ 128mb shared video memory, Hardy Heron 8.04).
Interestingly, the only hardware our computers have in common is the ATI RADEON XPRESS 200M graphics card.

> **EvilRobotDrew said:**
> i hope that someone knows a fix, this issue isn't enough to make be re-install windows, but it is very very annoying all the same, especially because there is no rhyme or reason to when it decides to lockup, it is random.
Do you encounter this error when you only suspend your computer for a short period of time (a couple minutes or less) or only when it's been in suspend for a long period of time? I didn't notice until I tried to reproduce the error and I couldn't get the computer to freeze on resume when I repeatedly suspended and resumed.

---

### Post by mssever on 2008-10-23
> **Altay_H said:**
> I'll give that a try next time I can. I don't know if it's relevant, but I often receive the error in the image below when I resume from suspend. Ironically, it only appears if the computer suspended and resumed correctly. It never appears when my computer freezes.I get that message, too, though it's often repeated twice. But I only rarely have problems (in my case, dbus crashes every once in a while).

> Interestingly, the only hardware our computers have in common is the ATI RADEON XPRESS 200M graphics card.That might be relevant, especially if you're both using the same graphics driver.

---

### Post by EvilRobotDrew on 2008-10-23
I have noticed that the longer I keep it suspended the more chance i have of seeing the error; although i have seen it happen occasionally after fairly short suspensions (eg. 20 mins between classes) and have had no problems after very long suspensions (eg. 4 hours or more). The weirdest thing about this problem is that it seems almost random, although i haven't seen it the last few days. *knocks on wood*

i assume that you are using the restricted driver for your videocard also? is there another driver i could download and test if the error occurs there, or because the driver is restricted are we stuck until ATI updates?

---

### Post by Altay_H on 2008-10-23
> **EvilRobotDrew said:**
> i assume that you are using the restricted driver for your videocard also? 
I believe so. Under Hardware Drivers it's listed as "ATI accelerated graphics driver."



EDIT: It just happened again. I was messing with my wireless trying to get it to work without ndiswrapper, so I couldn't ssh in yet again. However, I can confirm that it happens even with short suspends. It couldn't have been in suspend for more than about 15 minutes.

---

### Post by Altay_H on 2008-10-25
It happened again, but slightly differently differently. This time it failed to suspend when I tried to suspend it. The screen turned black, but then it returned immediately. I tried again, and it suspended correctly (Roughly 19:00:00). Then when I returned from suspend in about 15 minutes it froze (Roughly 19:15:00). I was able at ssh in successfully.

/var/log/messages contains:
```

Oct 25 18:41:48 altay-laptop kernel: [    7.174456] Registered led device: b43-phy0:tx
Oct 25 18:41:48 altay-laptop kernel: [    7.174824] Registered led device: b43-phy0:rx
Oct 25 18:41:48 altay-laptop kernel: [    7.175004] Registered led device: b43-phy0:radio
Oct 25 18:41:48 altay-laptop kernel: [    7.214392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 25 18:42:01 altay-laptop kernel: [   27.517417] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 25 18:42:07 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Oct 25 18:42:07 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Oct 25 18:42:07 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Oct 25 18:42:07 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Oct 25 18:42:07 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Oct 25 18:57:33 altay-laptop -- MARK --
Oct 25 19:17:33 altay-laptop -- MARK --
Oct 25 19:37:33 altay-laptop -- MARK --

```

/var/log/syslog contains:
```

Oct 25 18:56:17 altay-laptop kernel: [  889.843860] wlan0: switched to long barker preamble (BSSID=00:90:4c:7e:00:64)
Oct 25 19:04:10 altay-laptop kernel: [ 1365.823621] wlan0: RX deauthentication from 00:90:4c:7e:00:64 (reason=7)
Oct 25 19:04:10 altay-laptop kernel: [ 1365.823629] wlan0: deauthenticated
Oct 25 19:04:10 altay-laptop NetworkManager: <info>  Supplicant state changed: 0
Oct 25 19:04:11 altay-laptop kernel: [ 1366.826838] wlan0: authenticate with AP 00:90:4c:7e:00:64
Oct 25 19:04:11 altay-laptop kernel: [ 1366.828405] wlan0: RX authentication from 00:90:4c:7e:00:64 (alg=0 transaction=2 status=0)
Oct 25 19:04:11 altay-laptop kernel: [ 1366.828411] wlan0: authenticated
Oct 25 19:04:11 altay-laptop kernel: [ 1366.828416] wlan0: associate with AP 00:90:4c:7e:00:64
Oct 25 19:04:11 altay-laptop NetworkManager: <info>  Supplicant state changed: 1
Oct 25 19:04:11 altay-laptop kernel: [ 1366.830687] wlan0: RX ReassocResp from 00:90:4c:7e:00:64 (capab=0x401 status=0 aid=6)
Oct 25 19:04:11 altay-laptop kernel: [ 1366.830693] wlan0: associated
Oct 25 19:17:01 altay-laptop /USR/SBIN/CRON[11215]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 25 19:37:33 altay-laptop -- MARK --

```

/var/log/daemon.log contains:
```

Oct 25 18:42:07 altay-laptop avahi-daemon[5111]: New relevant interface wlan0.IPv4 for mDNS.
Oct 25 18:42:07 altay-laptop avahi-daemon[5111]: Registering new address record for 192.168.1.4 on wlan0.IPv4.
Oct 25 18:42:08 altay-laptop NetworkManager: <info>  Clearing nscd hosts cache.
Oct 25 18:42:08 altay-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))
Oct 25 18:42:08 altay-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Oct 25 18:42:08 altay-laptop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled.
Oct 25 18:42:08 altay-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 25 18:42:09 altay-laptop ntpdate[10377]: adjust time server 91.189.94.4 offset -0.445152 sec
Oct 25 18:42:10 altay-laptop avahi-daemon[5111]: Registering new address record for fe80::290:4bff:feeb:3c8a on wlan0.*.
Oct 25 19:04:10 altay-laptop NetworkManager: <info>  Supplicant state changed: 0
Oct 25 19:04:11 altay-laptop NetworkManager: <info>  Supplicant state changed: 1

```

/var/log/kern.log contains:
```

Oct 25 18:42:01 altay-laptop kernel: [   27.517110] wlan0: associated
Oct 25 18:42:01 altay-laptop kernel: [   27.517417] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 25 18:42:19 altay-laptop kernel: [   45.701473] wlan0: no IPv6 routers present
Oct 25 18:51:05 altay-laptop kernel: [  574.289513] wlan0: switched to short barker preamble (BSSID=00:90:4c:7e:00:64)
Oct 25 18:56:17 altay-laptop kernel: [  889.843860] wlan0: switched to long barker preamble (BSSID=00:90:4c:7e:00:64)
Oct 25 19:04:10 altay-laptop kernel: [ 1365.823621] wlan0: RX deauthentication from 00:90:4c:7e:00:64 (reason=7)
Oct 25 19:04:10 altay-laptop kernel: [ 1365.823629] wlan0: deauthenticated
Oct 25 19:04:11 altay-laptop kernel: [ 1366.826838] wlan0: authenticate with AP 00:90:4c:7e:00:64
Oct 25 19:04:11 altay-laptop kernel: [ 1366.828405] wlan0: RX authentication from 00:90:4c:7e:00:64 (alg=0 transaction=2 status=0)
Oct 25 19:04:11 altay-laptop kernel: [ 1366.828411] wlan0: authenticated
Oct 25 19:04:11 altay-laptop kernel: [ 1366.828416] wlan0: associate with AP 00:90:4c:7e:00:64
Oct 25 19:04:11 altay-laptop kernel: [ 1366.830687] wlan0: RX ReassocResp from 00:90:4c:7e:00:64 (capab=0x401 status=0 aid=6)
Oct 25 19:04:11 altay-laptop kernel: [ 1366.830693] wlan0: associated

```

I tried restarting both hal and dbus. Below are my results:
```

altay-laptop:~$ sudo /etc/init.d/gdm stop
 * Stopping GNOME Display Manager...                                     [ OK ]
altay-laptop:~$ sudo /etc/init.d/hal restart
 * Restarting Hardware abstraction layer hald                            [ OK ]
altay-laptop:~$ sudo /etc/init.d/gdm start
 * Starting GNOME Display Manager...                                     [ OK ]

```
At this point my keyboard and mouse were still locked, so I tried restarting dbus.

```

altay-laptop:~$ sudo /etc/init.d/gdm stop
 * Stopping GNOME Display Manager...                                     [ OK ]
altay-laptop:~$ sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer hald                              [ OK ]
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ]
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ]
 * Stopping System Tools Backends system-tools-backends                  [ OK ]
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ]
 * Stopping network connection manager NetworkManager
 
```
 Stopping the network connection manager broke my ssh connection, forcing me to restart.

---

### Post by mssever on 2008-10-27
Rats. I don't see anything even remotely helpful in your logs.

---

### Post by felipou on 2008-10-29
I have the exact same problem as Altay_H, only it happens all the time. I haven't been able to successfully resume from suspend a single time.

My laptop is a HP TX 2510us, 2.1GHz AMD Turion™ X2 ZM-80, 3GB RAM, ATI Radeon HD 3200 Graphics RS780M w/ 128mb shared video memory, running Ubuntu 8.10 Intrepid Ibex Beta.

I haven't tried ssh yet, when i get home i'll get the logs and post here.

I'm also considering in updating the ATI driver manually, installing version 8.10 from the ATI website, do you guys think it would make a difference?

---

### Post by Altay_H on 2008-10-30
Well, it happened again at a convenient time (at exactly 12:37, in case that's relevant), so I'm posting the four relevant logs again:

/var/log/messages
```

Oct 30 12:37:01 altay-laptop kernel: [    8.522624] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:70:a3:47, IRQ 20
Oct 30 12:37:02 altay-laptop kernel: [    9.670617] input: b43-phy0 as /devices/virtual/input/input10
Oct 30 12:37:02 altay-laptop kernel: [    4.996538] [drm] Loading R300 Microcode
Oct 30 12:37:03 altay-laptop kernel: [    5.998867] Registered led device: b43-phy0:tx
Oct 30 12:37:03 altay-laptop kernel: [    5.999079] Registered led device: b43-phy0:rx
Oct 30 12:37:03 altay-laptop kernel: [    5.999219] Registered led device: b43-phy0:radio
Oct 30 12:37:03 altay-laptop kernel: [    6.037029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 12:37:05 altay-laptop kernel: [   15.651921] eth0: link up, 10Mbps, full-duplex, lpa 0x4061
Oct 30 12:37:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 30 12:37:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 30 12:37:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 30 12:37:08 altay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

```


/var/log/syslog
```

Oct 30 12:37:09 altay-laptop NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
Oct 30 12:37:09 altay-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 30 12:37:10 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:10 altay-laptop avahi-daemon[5104]: Registering new address record for fe80::20f:b0ff:fe70:a347 on eth0.*.
Oct 30 12:37:10 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:13 altay-laptop ntpdate[15384]: no server suitable for synchronization found
Oct 30 12:37:15 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:18 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:19 altay-laptop kernel: [   29.580392] eth0: no IPv6 routers present
Oct 30 12:37:21 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:52 altay-laptop last message repeated 12 times
Oct 30 12:38:56 altay-laptop last message repeated 22 times
Oct 30 12:39:57 altay-laptop last message repeated 20 times
Oct 30 12:41:00 altay-laptop last message repeated 19 times
Oct 30 12:42:01 altay-laptop last message repeated 18 times
Oct 30 12:42:53 altay-laptop last message repeated 18 times
Oct 30 12:44:06 altay-laptop last message repeated 23 times

```


/var/log/kern.log
```

Oct 30 12:37:02 altay-laptop kernel: [    9.978113] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
Oct 30 12:37:02 altay-laptop kernel: [    4.996538] [drm] Loading R300 Microcode
Oct 30 12:37:03 altay-laptop kernel: [    5.996499] b43-phy0 debug: Chip initialized
Oct 30 12:37:03 altay-laptop kernel: [    5.996968] b43-phy0 debug: 30-bit DMA initialized
Oct 30 12:37:03 altay-laptop kernel: [    5.998867] Registered led device: b43-phy0:tx
Oct 30 12:37:03 altay-laptop kernel: [    5.999079] Registered led device: b43-phy0:rx
Oct 30 12:37:03 altay-laptop kernel: [    5.999219] Registered led device: b43-phy0:radio
Oct 30 12:37:03 altay-laptop kernel: [    5.999259] b43-phy0 debug: Wireless interface started
Oct 30 12:37:03 altay-laptop kernel: [    6.036351] b43-phy0 debug: Adding Interface type 2
Oct 30 12:37:03 altay-laptop kernel: [    6.037029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 12:37:05 altay-laptop kernel: [   15.651921] eth0: link up, 10Mbps, full-duplex, lpa 0x4061
Oct 30 12:37:19 altay-laptop kernel: [   29.580392] eth0: no IPv6 routers present

```


/var/log/daemon.log
```

Oct 30 12:37:09 altay-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Oct 30 12:37:09 altay-laptop NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
Oct 30 12:37:09 altay-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 30 12:37:10 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:10 altay-laptop avahi-daemon[5104]: Registering new address record for fe80::20f:b0ff:fe70:a347 on eth0.*.
Oct 30 12:37:10 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:13 altay-laptop ntpdate[15384]: no server suitable for synchronization found
Oct 30 12:37:15 altay-laptop dhclient: Discarding packet with bogus hlen.
Oct 30 12:37:46 altay-laptop last message repeated 11 times
Oct 30 12:38:47 altay-laptop last message repeated 21 times
Oct 30 12:39:49 altay-laptop last message repeated 21 times
Oct 30 12:40:55 altay-laptop last message repeated 20 times
Oct 30 12:41:57 altay-laptop last message repeated 16 times
Oct 30 12:42:53 altay-laptop last message repeated 22 times
Oct 30 12:44:06 altay-laptop last message repeated 23 times
Oct 30 12:45:08 altay-laptop last message repeated 15 times
Oct 30 12:46:09 altay-laptop last message repeated 17 times
Oct 30 12:46:59 altay-laptop last message repeated 17 times

```

I guess I'm just going to shut down the computer because restarting hal and dbus didn't work last time. Let me know if you have any new ideas.

I plan to upgrade to Intrepid Ibex relatively soon via clean install, probably on its own partition at first. I'll see if that changes the issue in any way. Perhaps it will solve the problem, but I'm convinced it's linked to the ATI driver, so it probably won't.

---

### Post by mssever on 2008-11-04
Today, after upgrading to Intrepid, I got a freeze with similar symptoms. In my case, when I resumed, I had a black screen with only the mouse pointer. The mouse and keyboard didn't work. I closed the lid in an attempt to sleep again and re-wake up. But the machine didn't sleep.

I solved it by SSHing in and running htop to see what processes were running. I discovered that my screensaver, euphoria, was consuming 100% of my CPU. When I killed the screensaver, my laptop beeped a few times and went to sleep (presumably because of my earlier attempt to put it to sleep). When I resumed the second time, everything came up normally.

I have no idea if my problem was the same as the others in thsi thread, but I thought it worth mentioning.

By the way, I have an Intel graphics card and use the open source driver.

---

### Post by Altay_H on 2008-11-05
Interesting. It sounds slightly different than my problem, but next time I'll try looking at htop and/or killing gnome-screensaver.

I upgraded Intrepid Ibex via clean install on a separate partition of the same computer, so I currently have both Intrepid and Hardy. Unfortunately Hardware Drivers simply won't work in Intrepid (it just freezes when I click Activate, the terminal version says something about a proxy), so I can't use the ATI driver in Intrepid. Resuming from sleep in Intrepid causes my graphics to mess up, which would presumably be solved if I could install the driver.

---

### Post by mssever on 2008-11-05
> **Altay_H said:**
> Interesting. It sounds slightly different than my problem, but next time I'll try looking at htop and/or killing gnome-screensaver.In my case, killing gnome-screensaver wouldn't have helped, because it was working fine. It was the screensaver itself that was hung. In case you aren't aware, screensavers are actually standalone programs; gnome-screensaver merely starts and kills the screensaver programs. Since I use the Euphoria screensaver, the process I killed was euphoria.

> I upgraded Intrepid Ibex via clean install on a separate partition of the same computer, so I currently have both Intrepid and Hardy. Unfortunately Hardware Drivers simply won't work in Intrepid (it just freezes when I click Activate, the terminal version says something about a proxy), so I can't use the ATI driver in Intrepid. Resuming from sleep in Intrepid causes my graphics to mess up, which would presumably be solved if I could install the driver.
I'm having some graphics-related trouble with Intrepid, as well, even though I have different hardware. Perhaps the new Xorg is still buggy.

---

### Post by EvilRobotDrew on 2008-11-06
I haven't had the problem manifest itself since i installed Intrepid *knock on wood*. I have other slight annoyances with 8.10, but i haven't had any problem with graphics.

if/when the problem reoccurs i will be try to ssh in an post some logs (but here's to hoping the problem is fixed).

-Drew

---

### Post by d4rk_rebel on 2008-12-02
Did this issue ever get resolved?  I am having the same problem (ATI 2600 Pro) I just replaced Vista with Ubuntu, so I am new at a lot of this stuff.  Any ideas?

---

### Post by mssever on 2008-12-02
> **d4rk_rebel said:**
> Did this issue ever get resolved?  I am having the same problem (ATI 2600 Pro) I just replaced Vista with Ubuntu, so I am new at a lot of this stuff.  Any ideas?
Basically, you'll need to follow through the troubleshooting steps in previous posts. Altay_H ended up reinstalling, so the cause of his/her trouble remains unknown. My problem was probably unrelated.

---

### Post by EvilRobotDrew on 2008-12-03
i still haven't fixed it, i plan on going back to 8.04 after finals. if you figure something out, let us know.

---

### Post by Altay_H on 2008-12-11
I managed to get my graphics card driver working in Intrepid Ibex, and now I have this problem again. Without the driver, my windows have strange borders around them upon resuming which only go away when I restart. With the driver, it occasionally freezes on resume.

If I manage to SSH in again, I'll try killing the screensaver. Any idea what name the "Blank Screen" screensaver goes by?

---

### Post by mssever on 2008-12-11
> **Altay_H said:**
> I managed to get my graphics card driver working in Intrepid Ibex, and now I have this problem again. Without the driver, my windows have strange borders around them upon resuming which only go away when I restart. With the driver, it occasionally freezes on resume.Those strange borders are probably caused by Compiz. If you disable Compiz, you can probably run just fine without those drivers. Of course, I find that living without Compiz is quite a trial. :)

> If I manage to SSH in again, I'll try killing the screensaver. Any idea what name the "Blank Screen" screensaver goes by?
My guess is that the blank screen is simply the absence of a screensaver. I say that because when the password dialog comes up, any running screensaver is killed and replaced with a blank screen. If the dialog times out or is cancelled, the screensaver is restarted from scratch. So apparently there's a black window layered behind the screensaver window.

You can test this for yourself, though, by starting the screensaver, then SSHing into the box and examining the processes owned by your user.

---

### Post by Altay_H on 2008-12-11
Well, I managed to cause my system to freeze and SSH in. Here is the list of all of the running processes:

```

  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:10 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  129 ?        00:00:00 cqueue
  133 ?        00:00:00 kseriod
  175 ?        00:00:00 pdflush
  176 ?        00:00:01 kswapd0
  218 ?        00:00:00 aio/0
 1083 ?        00:00:00 ksuspend_usbd
 1084 ?        00:00:00 khubd
 1185 ?        00:00:00 ata/0
 1191 ?        00:00:00 ata_aux
 1202 ?        00:00:00 khpsbpkt
 1205 ?        00:00:00 scsi_eh_0
 1209 ?        00:00:00 scsi_eh_1
 1536 ?        00:00:00 knodemgrd_0
 2071 ?        00:00:00 kjournald
 2246 ?        00:00:00 udevd
 2558 ?        00:00:00 kpsmoused
 2562 ?        00:00:00 kmmcd
 2564 ?        00:00:00 tifm
 2585 ?        00:00:00 pccardd
 8139 tty4     00:00:00 getty
 8140 tty5     00:00:00 getty
 8149 tty2     00:00:00 getty
 8151 tty3     00:00:00 getty
 8153 tty6     00:00:00 getty
 8318 ?        00:00:00 acpid
 8362 ?        00:00:00 kondemand/0
 8427 ?        00:00:00 syslogd
 8476 ?        00:00:00 dd
 8478 ?        00:00:00 klogd
 8501 ?        00:00:00 dbus-daemon
 8522 ?        00:00:00 slmodemd
 8541 ?        00:00:00 avahi-daemon
 8542 ?        00:00:00 avahi-daemon
 8571 ?        00:00:00 sshd
 8603 ?        00:00:00 atieventsd
 8633 ?        00:00:00 cupsd
 8794 ?        00:00:01 nmbd
 8796 ?        00:00:00 smbd
 8817 ?        00:00:00 winbindd
 8825 ?        00:00:00 winbindd
 8836 ?        00:00:00 winbindd
 8863 ?        00:00:00 winbindd
 8868 ?        00:00:00 ntos_wq
 8870 ?        00:00:00 ndis_wq
 8871 ?        00:00:00 wrapndis_wq
 8894 ?        00:00:00 smbd
 8938 ?        00:00:01 hald
 8943 ?        00:00:00 b43
 8950 ?        00:00:00 console-kit-dae
 9017 ?        00:00:00 hald-runner
 9037 ?        00:00:00 hald-addon-inpu
 9042 ?        00:00:00 hald-addon-cpuf
 9043 ?        00:00:00 hald-addon-acpi
 9057 ?        00:00:00 hald-addon-stor
 9104 ?        00:00:00 bluetoothd
 9109 ?        00:00:00 btaddconn
 9111 ?        00:00:00 btdelconn
 9133 ?        00:00:00 krfcommd
 9159 ?        00:00:00 NetworkManager
 9167 ?        00:00:00 wpa_supplicant
 9169 ?        00:00:00 nm-system-setti
 9197 ?        00:00:00 gdm
 9198 ?        00:00:00 gdm
 9203 tty7     00:01:31 Xorg
 9235 ?        00:00:00 system-tools-ba
 9270 ?        00:00:00 atd
 9298 ?        00:00:00 cron
 9414 tty1     00:00:00 getty
 9428 tty7     00:00:00 Xorg
 9496 ?        00:00:00 x-session-manag
 9628 ?        00:00:00 ssh-agent
 9631 ?        00:00:00 dbus-launch
 9632 ?        00:00:00 dbus-daemon
 9635 ?        00:00:09 pulseaudio
 9638 ?        00:00:00 gconf-helper
 9640 ?        00:00:03 gconfd-2
 9647 ?        00:00:00 seahorse-agent
 9649 ?        00:00:00 gnome-keyring-d
 9655 ?        00:00:00 gvfsd
 9656 ?        00:00:00 gnome-keyring-d
 9660 ?        00:00:02 gnome-settings-
 9661 ?        00:00:06 metacity
 9666 ?        00:00:00 gvfs-fuse-daemo
 9675 ?        00:00:14 gnome-panel
 9677 ?        00:00:14 nautilus
 9681 ?        00:00:00 bonobo-activati
 9701 ?        00:00:03 gnome-screensav
 9703 ?        00:00:00 gvfs-hal-volume
 9705 ?        00:00:00 gvfsd-burn
 9707 ?        00:00:00 gvfs-gphoto2-vo
 9713 ?        00:00:00 gvfsd-trash
 9717 ?        00:00:00 trashapplet
 9729 ?        00:00:02 multiload-apple
 9732 ?        00:00:00 gnome-keyboard-
 9736 ?        00:00:03 sensors-applet
 9739 ?        00:00:00 mixer_applet2
 9742 ?        00:00:00 fast-user-switc
 9744 ?        00:00:00 nm-applet
 9745 ?        00:00:00 trackerd
 9746 ?        00:00:02 vino-server
 9747 ?        00:00:00 bluetooth-apple
 9750 ?        00:00:00 evolution-alarm
 9753 ?        00:00:00 tracker-applet
 9757 ?        00:00:00 python
 9763 ?        00:00:00 update-notifier
 9765 ?        00:00:00 .startconky
 9773 ?        00:00:01 gnome-power-man
 9787 ?        00:00:00 evolution-data-
 9796 ?        00:00:00 evolution-excha
 9873 ?        00:00:13 conky
10253 ?        00:00:00 swiftfox
10265 ?        00:00:00 run-mozilla.sh
10270 ?        00:05:37 swiftfox-bin
10467 ?        00:00:01 gnome-terminal
10469 ?        00:00:00 gnome-pty-helpe
10470 pts/1    00:00:00 bash
10640 ?        00:00:01 notification-da
11386 pts/2    00:00:00 bash
11417 pts/2    00:00:00 rtcwake
11735 ?        00:00:00 pdflush
12215 pts/2    00:00:00 wakeup.sh
12403 ?        00:00:00 ipolldevd
12405 pts/2    00:00:03 vlc
12414 ?        00:00:00 dhclient
12541 ?        00:00:00 sshd
12561 ?        00:00:00 sshd
12576 pts/3    00:00:00 bash
12617 pts/3    00:00:00 ps
```

And here's the list of the processes being run by me:
```

  PID TTY          TIME CMD
 9496 ?        00:00:00 x-session-manag
 9628 ?        00:00:00 ssh-agent
 9631 ?        00:00:00 dbus-launch
 9632 ?        00:00:00 dbus-daemon
 9635 ?        00:00:18 pulseaudio
 9638 ?        00:00:00 gconf-helper
 9640 ?        00:00:03 gconfd-2
 9647 ?        00:00:00 seahorse-agent
 9649 ?        00:00:00 gnome-keyring-d
 9655 ?        00:00:00 gvfsd
 9656 ?        00:00:00 gnome-keyring-d
 9660 ?        00:00:03 gnome-settings-
 9661 ?        00:00:06 metacity
 9666 ?        00:00:00 gvfs-fuse-daemo
 9675 ?        00:00:17 gnome-panel
 9677 ?        00:00:15 nautilus
 9681 ?        00:00:00 bonobo-activati
 9701 ?        00:00:04 gnome-screensav
 9703 ?        00:00:00 gvfs-hal-volume
 9705 ?        00:00:00 gvfsd-burn
 9707 ?        00:00:00 gvfs-gphoto2-vo
 9713 ?        00:00:00 gvfsd-trash
 9717 ?        00:00:00 trashapplet
 9729 ?        00:00:02 multiload-apple
 9732 ?        00:00:00 gnome-keyboard-
 9736 ?        00:00:03 sensors-applet
 9739 ?        00:00:00 mixer_applet2
 9742 ?        00:00:00 fast-user-switc
 9744 ?        00:00:00 nm-applet
 9745 ?        00:00:00 trackerd
 9746 ?        00:00:02 vino-server
 9747 ?        00:00:00 bluetooth-apple
 9750 ?        00:00:00 evolution-alarm
 9753 ?        00:00:00 tracker-applet
 9757 ?        00:00:00 python
 9763 ?        00:00:00 update-notifier
 9765 ?        00:00:00 .startconky
 9773 ?        00:00:01 gnome-power-man
 9787 ?        00:00:00 evolution-data-
 9796 ?        00:00:00 evolution-excha
 9873 ?        00:00:15 conky
10253 ?        00:00:00 swiftfox
10265 ?        00:00:00 run-mozilla.sh
10270 ?        00:06:22 swiftfox-bin
10467 ?        00:00:02 gnome-terminal
10469 ?        00:00:00 gnome-pty-helpe
10470 pts/1    00:00:00 bash
10640 ?        00:00:01 notification-da
11386 pts/2    00:00:00 bash
12215 pts/2    00:00:00 wakeup.sh
12405 pts/2    00:00:06 vlc
12561 ?        00:00:00 sshd
12576 pts/3    00:00:00 bash
12845 pts/3    00:00:00 ps

```

Any idea which ones I should try killing?

---

### Post by mssever on 2008-12-11
I'd say to start with gnome-screensaver, and if that doesn't work, just start picking processes you own and killing them (be careful not to kill the ssh process or the shell you're using or you'll be booted out).

If nothing works after all that, try restarting gdm: ```
sudo service gdm restart
```
Or killing X. Or whatever else seems to still be alive...

(htop is a great tool for this job)

---

### Post by d4rk_rebel on 2008-12-13
Altay_H, did a fresh Install fix the sleep problem?  Just want to make sure before I go through the install.  Thanks

---

### Post by Altay_H on 2008-12-13
> **d4rk_rebel said:**
> Altay_H, did a fresh Install fix the sleep problem?

No. I have so far been unable to fix the problem in any way. Disabling my graphics card driver might solve the freeze problem (it never froze the few times I suspended with the graphics driver disabled), but it has graphics issues on resume without the driver, so it's not a solution at all.

---

### Post by EvilRobotDrew on 2008-12-14
i installed Fedora 10, and sleep doesn't work correctly there either, although it is not the same issue as in Ubuntu.

---

### Post by Altay_H on 2008-12-19
I have some interesting new information. I recently borrowed a USB mouse and tried plugging it into my computer while it was "frozen." It worked. If I plug in a USB device while the built-in keyboard and mouse are unresponsive the USB device works, but the built-in keyboard and mouse remain frozen.

I'm going to try leaving the USB device plugged in and see if it becomes unresponsive when the computer freezes. My guess is that if the device is plugged in when the computer freezes, it won't respond until it's unplugged and plugged back in. However, so far I have been unable to reproduce the problem while the USB mouse was plugged in.


Update:
I managed to reproduce the problem with the USB mouse plugged in. Strangely, although both the built-in keyboard and mouse were frozen, the USB mouse worked. Interestingly, I could turn the built-in mouse on/off with its power button when I plugged the USB mouse in earlier, which I haven't been able to do before. This time, after about a minute the USB mouse froze (although this mouse has a bad battery and is glitchy, and it was on a carpeted surface, so it may have been the mouse, not Ubuntu) and I was unable to turn the built-in mouse on/off.

---

### Post by mssever on 2008-12-20
This thread has been around a while and stretches over several pages, so I no longer remember whether the machine in question is a laptop. If it is, it's probable that the built-in keyboard and mouse are both PS/2 devices, not USB. PS/2, of course, isn't designed to be hot-pluggable. So there might be a problem with the subsystem that handles PS/2.

It would be interesting to find out whether your USB mouse actually was the problem when it quit working (if my theory is correct, it probably was). It would also be interesting to try plugging in a USB keyboard.

---

### Post by Altay_H on 2008-12-20
> **mssever said:**
> This thread has been around a while and stretches over several pages, so I no longer remember whether the machine in question is a laptop. If it is, it's probable that the built-in keyboard and mouse are both PS/2 devices, not USB. PS/2, of course, isn't designed to be hot-pluggable. So there might be a problem with the subsystem that handles PS/2.
It's a moderately old laptop (2004), so I wouldn't be surprised if it was PS/2. Interestingly though, it doesn't have any PS/2 ports. That doesn't mean the built-in devices aren't PS/2, but it seems strange to me that devices with internal PS/2 connections don't have external PS/2 ports. Is there any way I can find out whether the connections are PS/2 or USB?

> **mssever said:**
> It would be interesting to find out whether your USB mouse actually was the problem when it quit working (if my theory is correct, it probably was). It would also be interesting to try plugging in a USB keyboard.
I'm not sure what you mean by the USB mouse being the problem. The problem does not occur consistently with the USB mouse plugged in, and it occurs just as often without it plugged in. Unfortunately I don't currently have access to a USB keyboard, but I'm sure I can get my hands on one in a week or so. I'll let you know whether or not the USB keyboard works. I'd be surprised if it doesn't, considering the USB mouse worked.


Also, regarding the graphics card driver (FGLRX), I've disabled it and my computer resumes from standby without the strange white borders. I don't know whether that was from when I had the Visual Effects set to normal or whether the problem just went away, but I'm going to see if I can recreate this problem with my graphics card driver disabled. If I can, it's probably not the graphics card driver. If I can't... well, it doesn't really prove anything, but it's more likely the fault of the graphics card driver.

---

### Post by mssever on 2008-12-20
> **Altay_H said:**
> It's a moderately old laptop (2004), so I wouldn't be surprised if it was PS/2. Interestingly though, it doesn't have any PS/2 ports. That doesn't mean the built-in devices aren't PS/2, but it seems strange to me that devices with internal PS/2 connections don't have external PS/2 ports. Is there any way I can find out whether the connections are PS/2 or USB?
My laptop is only a year old, and it has a PS/2 touchpad and TrackPoint. I can't tell what the keyboard is, but I'm pretty sure it's NOT USB. Use lsusb to list all USB devices. Finding PS/2 is a bit harder. I ended up doing ```
lshal | less
```and searching through the results (grepping doesn't provide sufficient context).

Since there's limited space for external PS/2 ports, they might not be present even if the internal devices are PS/2. My laptop has no PS/2 ports, either.

---

### Post by drs305 on 2008-12-21
Altay_H,

When my laptop resumes from suspend I have similar symptoms to yours. Everything looks ok but the system appears frozen. 

Today I discovered a partial fix. My system wasn't totally frozen, it was just the touchpad and keyboard. The tab and Enter keys worked ok. To restore the keyboard I had to select the FN and Numlock/Delete keys (Lenovo N300). As soon as I did this the keypad started working and I could log in and continue working - to some extent. Despite all the good ubuntu wiki pages on touchpads (synaptics), I have been unable to restore the touchpad by any method.

Just thought you might check to see if it's a lack of keyboard inputs that makes your system appear frozen.

---

### Post by Altay_H on 2008-12-21
> **mssever said:**
> My laptop is only a year old, and it has a PS/2 touchpad and TrackPoint. I can't tell what the keyboard is, but I'm pretty sure it's NOT USB. Use lsusb to list all USB devices. Finding PS/2 is a bit harder.
Well, my touchpad is definitely PS/2. I'm not sure what my keyboard is either, but it's not USB. What did this imply? You said something about a problem with the subsystem that handles the PS/2. Is there any way to test this idea?



> **drs305 said:**
> Just thought you might check to see if it's a lack of keyboard inputs that makes your system appear frozen.
I thought I already established this. I mean, I wouldn't be able to SSH in if the system actually froze. Also, the cursor would not continue to flash (as described in the first post) if the system actually froze. The keyboard and mouse simply both fail simultaneously. Strangely though, external mice don't seem to have any problems even when the built-in keyboard and mouse fail.

---

### Post by mssever on 2008-12-22
> **Altay_H said:**
> Well, my touchpad is definitely PS/2. I'm not sure what my keyboard is either, but it's not USB. What did this imply? You said something about a problem with the subsystem that handles the PS/2. Is there any way to test this idea?
Probably. Especially if you could trigger a reload of whatever was at fault. But this is a subject area I really don't know about, since I've never had to troubleshoot potential PS/2 problems. I don't even know if this is a HAL issue, a kernel issue, a udev issue, or something else.

---

### Post by drs305 on 2008-12-22
> **Altay_H said:**
> I thought I already established this. I mean, I wouldn't be able to SSH in if the system actually froze. Also, the cursor would not continue to flash (as described in the first post) if the system actually froze. The keyboard and mouse simply both fail simultaneously. Strangely though, external mice don't seem to have any problems even when the built-in keyboard and mouse fail.


That is what I meant and what I tried to describe. My system was NOT frozen - it only *appeared* frozen because the keyboard was not making any inputs. The system was fully capable of receiving inputs - it just wasn't because the keyboard wasn't sending any until I re-enabled it.

**Edit added:** You symptoms appear to be very much like mine. Do you keys have extra designations on them for FN combinatins to adjust brightness, volume, etc? (Not the special extra buttons; on my machine some keys have dual purposes.) See if you can find an FN key combination that restores your keyboard.

---

### Post by jay li on 2008-12-22
All I can tell you is just 2 things. 

First, move on to ubuntu 8.10 to get more stability & bugs fix. 
Secondly, consider to replace the ATI graphic controller with nvidia. 

PS This one cause me nothing but pain on any system I'd ever try.

---

### Post by Altay_H on 2008-12-22
> **mssever said:**
> But this is a subject area I really don't know about, since I've never had to troubleshoot potential PS/2 problems. I don't even know if this is a HAL issue, a kernel issue, a udev issue, or something else.
So what should I do? Should I just wait until someone who does know about PS/2 problems finds this thread? Do you think I'd be better off looking for additional help on an irc?

Just out of curiosity, do you know what the media buttons on a laptop are connected to? Are they typically part of the keyboard, or do they tend to be their own units? My laptop has 7 extra buttons: 4 by the keyboard and 3 by the mouse. I'm just wondering because if they're not directly connected to the keyboard or mouse then that means I have a third unit failing as well.


> **jay li said:**
> First, move on to ubuntu 8.10 to get more stability & bugs fix.
I'm already using Ubuntu 8.10. When this thread started I was using 8.04, but that was because this thread started back in August.


> **jay li said:**
> Secondly, consider to replace the ATI graphic controller with nvidia.
Are you suggesting I use an nvidia driver instead of an ATI driver, or are you suggesting I replace my ATI graphics card with nvidia? If you're suggesting the latter, I don't think that's a reasonable suggestion for a 4-year-old laptop. Also, my sister has a similar laptop with an nvidia graphics card, and although it doesn't suffer from the same problems as my ATI card, it has its own problems.



I have some interesting new information. I disabled my graphics card driver and the problem reoccurred. I guess this rules out my theory that it was somehow directly connected to the graphics card driver. The problem was exactly the same with the graphics card driver disabled. The built-in mouse and keyboard froze, but the mouse plugged in via USB worked as well as it normally does.

---

### Post by jay li on 2008-12-22
In that case, search for proper driver.

---

### Post by Altay_H on 2008-12-22
> **jay li said:**
> In that case, search for proper driver.
I'm not sure what you mean. Are you suggesting that there's a better driver for the ATI Radeon Xpress 200M than FGLRX?

---

### Post by jay li on 2008-12-22
I meant, search if you can find an update for your ATI driver at ATI website, and you can start from here: [COLOR="Blue"]_***[http://www.amd.com/gb-uk/SupportDrivers/ProcessorSupport/0,,15218_15219,00.html](http://www.amd.com/gb-uk/SupportDrivers/ProcessorSupport/0,,15218_15219,00.html)***_[/COLOR]

---

### Post by mssever on 2008-12-22
> **Altay_H said:**
> So what should I do? Should I just wait until someone who does know about PS/2 problems finds this thread? Do you think I'd be better off looking for additional help on an irc?You can try IRC, you can try Google, you can try waiting, or you can look for an appropriate mailing list (related to the specific package that might be at fault--Google might be able to help you there) and ask there. Sometimes mailing lists have more knowledgable people on them. They aren't necessarily as friendly, though. Be sure that you demonstrate that you did your homework before asking.

> Just out of curiosity, do you know what the media buttons on a laptop are connected to? Are they typically part of the keyboard, or do they tend to be their own units? My laptop has 7 extra buttons: 4 by the keyboard and 3 by the mouse. I'm just wondering because if they're not directly connected to the keyboard or mouse then that means I have a third unit failing as well.I assume that they're part of the keyboard, but I don't really know.

> I have some interesting new information. I disabled my graphics card driver and the problem reoccurred. I guess this rules out my theory that it was somehow directly connected to the graphics card driver. The problem was exactly the same with the graphics card driver disabled. The built-in mouse and keyboard froze, but the mouse plugged in via USB worked as well as it normally does.
It appears to me now that your problem is probably unrelated to your video driver. And it's a but difficult to swap video cards in a laptop.

---

### Post by Altay_H on 2008-12-23
> **jay li said:**
> I meant, search if you can find an update for your ATI driver at ATI website, and you can start from here: [COLOR="Blue"]_***[http://www.amd.com/gb-uk/SupportDrivers/ProcessorSupport/0,,15218_15219,00.html](http://www.amd.com/gb-uk/SupportDrivers/ProcessorSupport/0,,15218_15219,00.html)***_[/COLOR]
Unfortunately they don't have a driver for my graphics card. They go all the way back to the X300 series, but my card is a Radeon Xpress 200M. My card has a page, but no drivers: [http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14628,00.html?redir=Xpr01](http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14628,00.html?redir=Xpr01)


> **mssever said:**
> You can try IRC, you can try Google, you can try waiting, or you can look for an appropriate mailing list (related to the specific package that might be at fault--Google might be able to help you there) and ask there.
Which specific packages might be at fault? I'm not really sure what controls PS/2 devices. Is it evdev?

---

### Post by mssever on 2008-12-26
> **Altay_H said:**
> Which specific packages might be at fault? I'm not really sure what controls PS/2 devices. Is it evdev?
I can't even find the evdev package. My first guess would be hal or a related package. My second guess would be udev. My third guess would be some kernel package (linux-*). But those are just guesses, since I don't know what controls PS/2 devices, either.

(I apologize for the delay in responding. I'm visiting my parents for Christmas and they don't have Internet access. I'm in Starbucks right now. :))

---

### Post by NoBugs! on 2009-01-06
Does this help:
[http://www.insidesocal.com/click/2008/10/i-think-ive-fixed-my-ubuntu-80.html](http://www.insidesocal.com/click/2008/10/i-think-ive-fixed-my-ubuntu-80.html)
It says it can be fixed by setting it to never suspend automatically.

---

### Post by drs305 on 2009-01-06
> **NoBugs! said:**
> Does this help:

It says it can be fixed by setting it to never suspend automatically.

I had never been able to get my desktop or laptop to resume correctly from suspend. Everyone's system is different, but these three steps seem  to have solved it for me.

First, as NoBugs! mentioned, I set the power management to never put the computer to sleep (System, Preferences, Power Management).

Second, in my grub menu.lst, to enable the synaptics touchpad to work upon resume (which it never did before), I added the option "i8042.reset".

Third, to allow my network to resume (also frozen on previous resumes) I added this line to /etc/pm/config.d//00sleep_module:
```

SUSPEND_MODULES="forcedeth"  #  "forcedeth" is the result of "sudo lshw | grep eth" 

```
I found these suggestions scattered around the ubuntu forums, so if you need more information on any of these 'solutions' you can search these forums.

---

### Post by Altay_H on 2009-01-06
> **NoBugs! said:**
> Does this help:
[http://www.insidesocal.com/click/2008/10/i-think-ive-fixed-my-ubuntu-80.html](http://www.insidesocal.com/click/2008/10/i-think-ive-fixed-my-ubuntu-80.html)
It says it can be fixed by setting it to never suspend automatically.
Unfortunately, no, because I already have it set to never suspend automatically. I'm fairly certain that's the default setting.


> **drs305 said:**
> 
Second, in my grub menu.lst, to enable the synaptics touchpad to work upon resume (which it never did before), I added the option "i8042.reset".

Before I start messing around with something like my grub menu.lst, could you let me know exactly how to add it to the file? I'm not very familiar with menu.lst and would rather get it right the first time.



> **drs305 said:**
> 
Third, to allow my network to resume (also frozen on previous resumes) I added this line to /etc/pm/config.d//00sleep_module:
I haven't had my network fail to resume yet, so I won't bother with this setting for now.

---

### Post by mssever on 2009-01-06
> **Altay_H said:**
> Before I start messing around with something like my grub menu.lst, could you let me know exactly how to add it to the file? I'm not very familiar with menu.lst and would rather get it right the first time.
Add it to the end of the defoptions line. For example, in my menu.lst, I have the following line: ```
# defoptions=splash quiet
```Just add i8042.reset after any other options already on the line. (I Googled for i8042.reset and came up with [this page]("http://74.125.77.132/search?q=cache:wQNZGzZePmEJ:https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768+i8042.reset&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a") as the second result.) After you edit menu.lst (and save the file), you need to run ```
sudo update-grub
```to apply the changes. You'll have to reboot before the changes will take effect.

---

### Post by drs305 on 2009-01-06
> **Altay_H said:**
> Before I start messing around with something like my grub menu.lst, could you let me know exactly how to add it to the file? I'm not very familiar with menu.lst and would rather get it right the first time.


If you follow msserver's post, the end result will be something like the following, which is the first menu option section in my grub menu.lst:
```
kernel   /boot/vmlinuz-2.6.27-9-generic root=UUID=9d42-0823c698a757 ro splash vga=795 [COLOR="DarkRed"]i8042.reset[/COLOR]
```

To edit menu.lst, make a backup and open with a text editor:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 
gksudo gedit /boot/grub/menu.lst

```

Make the change as suggested by msserver and then save the file and run the sudo update-grub command. When you run this command, the first choice will be "install the package maintainer's version" but the second one will be highlighted. Choose the first/top option.

If you follow msserver's post, the end result will be something like the following, which is the first menu option section in my grub menu.lst:
```
kernel   /boot/vmlinuz-2.6.27-9-generic root=UUID=9d42-0823c698a757 ro splash vga=795 [COLOR="DarkRed"]i8042.reset[/COLOR]
```

---

### Post by Altay_H on 2009-02-12
Well, I'm back after just over a month and much has changed. I've installed Arch Linux on one partition of my hard drive. Ubuntu is still installed, but I'm primarily messing around with Arch for the time being.

Interestingly, despite the fact that I'm running Arch Linux without X the problem is reoccurring. I'm quite certain this rules out that it could be related in any way to GNOME or flgrx.

I just changed my menu.lst file to include i8042.reset. I'll see if the problem continues to occur. I'll post the results later.

Out of curiosity, what does the i8042.reset option in GRUB do?

---

### Post by drs305 on 2009-02-13
> **Altay_H said:**
> Out of curiosity, what does the i8042.reset option in GRUB do?

Welcome back Altay. ;-)

i8042 is the controller for older keyboards - so this command included in grub instructions resets the i8042 keyboard controller.

---

### Post by Altay_H on 2009-02-15
I tried it out and it's still freezing up on me. I used a script to automatically suspend for 30 seconds, resume for 100 second, then repeat the process indefinitely. It managed to get through 18 iterations before freezing up on the resume. I pasted the code below, in case it's relevant in any way.
```
#!/bin/sh

# Script to test the reliability of rtcwake

a=0;

while [ $a -eq 0 ]
do
# Set t equal to 30 seconds after now
t=`date +%s`;
t=$(($t+30));

echo $t;

# Set rtcwake to 30 seconds after now and suspend
rtcwake -l -t $t -m on &
pm-suspend;

# Pause for 100 seconds between each iteration
sleep 100;

# Output a log
echo "$t\n" >> /home/altay/log.txt

# Kill rtcwake if it's still around
killall rtcwake;
done

```

It's not particularly well written, but it works. What I thought was interesting was that the script failed at all. I mean, the keyboard and mouse are what we assumed are the only components that fail. However, this script failed after 18 iterations. I don't know whether or not I could SSH into it in this state. I'll try running some more tests later today. I suppose this means that the keyboard and mouse are not the only components failing. It's nice to be able to test it out using Arch Linux, because I hardly have anything running at all. I'm not using Ndiswrapper, GNOME, or even X, so the problem is quite deep.



> **drs305 said:**
> i8042 [...] resets the i8942 keyboard controller.
Is that a typo? Why is it i8042 if it resets the i8942 controller?

---

### Post by drs305 on 2009-02-15
> **Altay_H said:**
> Is that a typo? Why is it i8042 if it resets the i8942 controller?

Yes it was. Corrected.

---

### Post by Altay_H on 2009-02-15
Well, I just ran a slightly modified version of my script. This time it's set to have the computer sleep for 30 second, then wait 30 seconds, then repeat. Also, it will try to both "killall" rtcwake and "kill -9" rtcwake upon resume.

This time it didn't fail at all. It went through 107 iterations from 15:08 to 18:59. At first it was taking roughly 65 seconds per iteration, but by the time I stopped it each iteration took roughly 195 seconds. I'm not entirely sure why this is, but it doesn't seem that relevant to me.

I think the reason my previous attempt failed was that the keyboard/mouse problem occurred, but the script continued on as usual. Then rtcwake froze in such a way that killall failed to kill it, leaving my computer in a frozen state. Of course, this doesn't explain why my computer was able to go through 107 successful iterations of suspending and resuming without having the keyboard or mouse fail once.

Other theories are welcome.


UPDATE:
I ran the script again. This time it went through 140 iterations from 12:21 to 18:04 before I stopped it. It just doesn't seem to be failing. I don't know if the problem is gone or if it just isn't occurring now. I'll report further troubles as/if they occur.


UPDATE:
I'm now using pm-suspend and rtcwake on a daily basis. I'll post any problems if they occur, but it seems to be solved now.

---

### Post by agave on 2009-02-28
> 
I'm now using pm-suspend and rtcwake on a daily basis. I'll post any problems if they occur, but it seems to be solved now.

Altay_H, could you post how you solved it? how do you use pm-suspend and rtcwake?

---

### Post by Altay_H on 2009-03-01
> **agave said:**
> Altay_H, could you post how you solved it? how do you use pm-suspend and rtcwake?
Just to clarify, pm-suspend and rtcwake are *not* ways to solve the problem but rather ways to try to cause it. I'm using them to try to induce the problem, but it hasn't occurred since I last posted.

What solved the problem was probably the i8042.reset option in GRUB. I can't say that for certain though, because the problem occurred once after I set that option.


In case you actually want to use pm-suspend and/or rtcwake:

pm-suspend is a program to suspend your computer indefinitely. Essentially it's the same as clicking the menu at the top right and choosing "Suspend." You can run it with the following command:
```
sudo pm-suspend
```

rtcwake is a program to wake your computer up from sleep after a given period of time. You can either tell it to wake a certain number of seconds after you issue the command, or you can give it an epoch time at which you want it to wake. If you're interested in a script that can handle rtcwake for you take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=938533&page=2").

---

### Post by Altay_H on 2009-05-06
The problem is finally back. It's frustrating how arbitrary this problem is. I've configured my system to dual boot Arch Linux and Ubuntu 8.10. I recently installed Ubuntu 9.04, so I'm now triple booting my system with all three.

After installing Ubuntu 9.04 the problem occured in my Arch Linux install. What makes the problem even stranger is that I'm running an *extremely* basic Arch Linux install. I am not running X. I do everything via CLI.

This means the problem is not being caused by the graphics card or anything related to the desktop environment. I tried killing some unnecessary programs, and it looks like the problem only occurs when sshd is running. I'll do some more tests to ensure reliability.


I just realized that since installing Ubuntu 9.04 changed my grub settings it might have removed the i8042.reset option from grub. I'll update this thread with relevant information.

---

### Post by Falcon1002 on 2009-05-07
Hello! On my Dell Latitude D531 with an ATI Radeon 1270. I had the same problem -- no keyboard and no mouse when I resumed from suspend. I eventually did a fresh install of 8.10 and the problem went away so I kept carefully updating things one at a time until I found the problem. It turned out to be the proprietary graphics driver that Ubuntu had for my card (how that affects my keyboard and mouse I know not). Since installing the driver on AMD's website I have not had the problem. My problem seems to be a little different then yours but I hope that some of this information helps in the finding of a fix.

---

### Post by Altay_H on 2009-05-07
> **Falcon1002 said:**
> I had the same problem -- no keyboard and no mouse when I resumed from suspend. I eventually did a fresh install of 8.10 and the problem went away so I kept carefully updating things one at a time until I found the problem.
Thanks for posting. I don't think I have the same problem, but others who do might benefit from this post.


> **Falcon1002 said:**
> It turned out to be the proprietary graphics driver that Ubuntu had for my card (how that affects my keyboard and mouse I know not).
I don't think the graphics driver is used at all unless X is being run, but I could be wrong. Can anyone confirm this for me?


> **Altay_H said:**
> it looks like the problem only occurs when sshd is running. I'll do some more tests to ensure reliability.
It turns out this is rubbish. I tried out my theory about sshd again, and it was just a coincidence. The problem occurs with or without sshd running.



I checked my new /boot/grub/menu.lst and Jaunty Jackalope did indeed remove i8042.reset from Arch's boot option. I'll try replacing it and see if it works. If the problem goes away, that should be conclusive evidence that the i8042.reset option is what solves my problem.

---

### Post by Altay_H on 2009-05-07
I ran the previously mentioned script through 98 iterations without the problem occurring, so I'm assuming the problem is solved.

> **agave said:**
> Altay_H, could you post how you solved it?
I added the i8042.reset boot option by editing grub. It's outlined very clearly in post #58 of this thread.

> **agave said:**
> how do you use pm-suspend and rtcwake?
I use the following script.

```
#!/bin/sh

# rtcwake script
# Example:
# wakeup.sh "Nov 28, 2008 00:16:00"
# will wake up the computer from suspend or hibernate
# Note that the following format also works:
# wakeup.sh 00:16

# Convert the user's input to epoch time and store it in t
t=`date --date "$1" +%s`;

# Convert the current time to epoch time and store it in n
n=`date +%s`;

# Correct t so that it can't be before n
if [ $n -gt $t ]
	then
	# If t is in the past, add one day to t
	t=$(($t + 86400));
fi

# Prompt for super-user privileges
sudo /bin/true

# Ensure that rtcwake is not already running
sudo killall rtcwake;

# Set the rtcwake time
sudo rtcwake -l -t $t -m on &

# Give rtcwake at least 2 seconds to ensure it sets correctly
sleep 2

# Suspend the system
sudo pm-suspend

##############################################
# When it wakes up, it will pick up from here#
##############################################

# Kill the rtcwake process that should not still be running
killall rtcwake;

# If killall doesn't work, use the kill_rtcwake.sh script to kill -9 it
if ps -e | grep rtcwake
	then
	/home/altay/kill_rtcwake.sh;
	echo "Used kill -9 to kill it";
fi

# You can add more commands if you like

```

For more information regarding rtcwake and pm-suspend, see this thread: [http://ubuntuforums.org/showthread.php?t=938533&page=3](http://ubuntuforums.org/showthread.php?t=938533&page=3)



The only thing left to test is to see if the i8042.reset option works for Jaunty Jackalope as well. I'll update this post with my results, though frankly I only need Arch Linux to reliably run my script.

---

### Post by WhiteDawn on 2009-12-03
I know this a old thread, but I would also like to add some contributions to this. The issue is still in the most recent version of Ubuntu, Karmic Koala. It did not occur to me until I upgraded from 9.04 to 9.10. My problem is very similar to everyone else's here except for 2 differences. The first one is that I am not running on a ATI video card, but a intel MHD 4500. The other difference is that, after resume, not only are the keyboard and touchpad/trackpoint unresponsive, but my sleep light is blinking. This is odd as the sleep light only blinks when the computer is going into sleep mode. Another thing I noticed is that if you type really fast as soon as the screen appears you can get a few letters of your password in before becoming unresponsive. 

I could not find any pattern with this, it happens while compiz is running, it happens when metacity is running, I try closing all user tasks before suspending, there is just no pattern.

The only thing I can think of is that while opening my laptop screen the switch in the screen that triggers sleep mode might have been pressed again while the system was coming out of sleep causing it to lock up some how.

I haven't been able to prove this, I am currently trying the i8042.reset option in grub, and so far so good. I'll report back if it happens again.

Hardware: Lenovo t400
Ubuntu 9.10 x64
Intel C2D p8400 2.18ghz
4GB DDR3 ram
Intel MHD 4500

Maybe there is a pattern in the hardware that is affected other than the ATI cards...

---

### Post by Altay_H on 2009-12-03
> **WhiteDawn said:**
> I could not find any pattern with this, it happens while compiz is running, it happens when metacity is running, I try closing all user tasks before suspending, there is just no pattern.
Did you try stopping gdm and running pm-suspend from a virtual terminal? Suspend is completely broken for me in 9.10 as long as there's a GUI involved. Here's a link to the problem I have in 9.10, in case it's relevant: [http://ubuntuforums.org/showthread.php?t=1307618](http://ubuntuforums.org/showthread.php?t=1307618)

---

### Post by Altay_H on 2010-02-04
> **drs305 said:**
> To edit menu.lst, make a backup and open with a text editor:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 
gksudo gedit /boot/grub/menu.lst

```

Make the change as suggested by msserver and then save the file and run the sudo update-grub command. When you run this command, the first choice will be "install the package maintainer's version" but the second one will be highlighted. Choose the first/top option.

This is the correct way to do it for grub-legacy, but it changed in Karmic Koala with the release of grub2. In grub2, you must edit the following file: /etc/default/grub
Add " i8042.reset" to the end of whatever is in GRUB_CMDLINE_LINUX_DEFAULT. Then run update-grub as root.

Here's the original answer I found elsewhere:
```
Put additional boot options in /etc/default/grub. The first is default extra options for normal kernels, and the second is anything added for (recovery) entries:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

