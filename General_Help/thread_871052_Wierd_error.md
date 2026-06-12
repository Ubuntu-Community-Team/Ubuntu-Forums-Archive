---
title: "Wierd error"
date: 2008-07-26
forum: General Help
---

### Post by Safder on 2008-07-26
Hi everyone,

I've been having this problem for quite a while, I am not sure how to tackle this. I am not even sure, whether it's anything do with certain applications, 'cuz it's so random. So what happens is when i am using firefox, and I close one of the tabs, suddenly I get a black screen, with bunch of stuff displayed, like battery information etc.

I can't get out of this screen, the only thing i can do is press ctrl+alt+delete..and it restarts the system, but I dont know how to get out of that screen. I was looking at the logs and i found the following messages occuring a lot, before i restarted the sytem:

#Jul 26 09:26:17 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:37:09 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 09:37:09 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:38:07 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 09:38:07 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:51:14 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 09:51:14 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:55:55 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 09:55:55 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:57:02 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 09:57:02 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:57:11 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 09:57:11 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:59:27 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 09:59:27 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 10:01:14 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 10:01:14 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 10:04:35 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory
Jul 26 10:04:35 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 10:17:01 Shontu-moni /USR/SBIN/CRON[23510]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 26 10:18:49 Shontu-moni init: tty4 main process (4651) killed by TERM signal
Jul 26 10:18:49 Shontu-moni init: tty5 main process (4652) killed by TERM signal
Jul 26 10:18:49 Shontu-moni init: tty2 main process (4654) killed by TERM signal
Jul 26 10:18:49 Shontu-moni init: tty3 main process (4657) killed by TERM signal
Jul 26 10:18:49 Shontu-moni init: tty6 main process (4658) killed by TERM signal
Jul 26 10:18:49 Shontu-moni init: tty1 main process (5775) killed by TERM signal
Jul 26 10:18:59 Shontu-moni avahi-daemon[5094]: Got SIGTERM, quitting.
Jul 26 10:18:59 Shontu-moni avahi-daemon[5094]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.106.
Jul 26 10:19:01 Shontu-moni kernel: [ 1822.953580] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 26 10:19:02 Shontu-moni exiting on signal 15
Jul 26 10:19:47 Shontu-moni syslogd 1.5.0#1ubuntu1: restart.#

I would really appreciate some help in this area. Thanks

---

### Post by pytheas22 on 2008-07-26
That's very strange.  Does it only happen when you close a tab in Firefox--nothing else triggers it?  Does closing the whole Firefox window (if only one tab is open) trigger it?  Does it happen every time you close a tab, or only randomly?  If you press control-alt-F7 when it happens, do you get back to your normal screen?  Does pressing control-alt-backspace do anything?  Can you press control-alt-F3 and login on the command line there?  How are you closing the tab in Firefox--with the mouse, control-W, or another hotkey?

Sorry for so many questions, but if you provide answers to them it will help us get to the bottom of the problem.

---

### Post by prshah on 2008-07-26
> **Safder said:**
> 
#Jul 26 09:26:17 Shontu-moni pulseaudio[5878]: pstream.c: Failed to import memory block.
Jul 26 09:37:09 Shontu-moni pulseaudio[5878]: shm.c: shm_open() failed: No such file or directory

Clearly there is something wrong with your pulseaudio setup; I suspect clashes with flash. To confirm, open a non flash page (I think Google is one) and then close firefox to see if the black screen error appears again.

While you're at it, you may also want to take a look at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) for details on how to setup pulse properly.

---

### Post by Safder on 2008-07-26
I'll try to answer the questions you have asked.

[COLOR="Blue"]Does it only happen when you close a tab in Firefox--nothing else triggers it?[/COLOR]
I wouldn't be able to be sure, as to whether it happens only when i close a Firefox tab, but I have noticed it happening more frequently than anything else, and that's why I remember it from the top of my head. But I wouldn't be able to gurante you, that it's  the only time it happens. 

[COLOR="Blue"]Does closing the whole Firefox window (if only one tab is open) trigger it?[/COLOR]
I didn't notice anything with respect to this.

As for pressing control-alt-F7, I haven't tried that, so I will try that out if it happens again.I havne't tried ctrl+alt+backspace, so wouldn't be able to comment on that. I close the firefox tabs using my laptop touchpad. As for ctrl+alt-f3, I would have to try that too, to be able to comment.

As for questions, i am glad you are, it will help us narrow down the problem.

---

### Post by pytheas22 on 2008-07-27
> Clearly there is something wrong with your pulseaudio setup

I wouldn't necessarily attribute it to pulseaudio, since the first pulseaudio error in the log (at least, the first mention of it in the snippet posted above; possibly it starts even earlier) occurs at 09:26:17, almost an hour before the crash.  I assume that the crash occurs just before 10:18:49, when the system starts going down (presumably because control-alt-delete has been pressed).  So I'd suspect that the pulseaudio stuff is just a coincidence.

Otherwise, Safder, the next time it happens, please give those additional things that I mentioned (control-alt-backspace, control-alt-f3, et cetera) a try.  I suspect that it's only the X server that's crashing, not the whole system, and the results of those things will tell us.  If the whole system were crashing, pressing control-alt-delete probably wouldn't do anything.

You could also try looking at the X log in /var/log/Xorg.0.log the next time the crash happens to see if it mentions anything strange going on.

---

### Post by Safder on 2008-07-31
> **pytheas22 said:**
> I wouldn't necessarily attribute it to pulseaudio, since the first pulseaudio error in the log (at least, the first mention of it in the snippet posted above; possibly it starts even earlier) occurs at 09:26:17, almost an hour before the crash.  I assume that the crash occurs just before 10:18:49, when the system starts going down (presumably because control-alt-delete has been pressed).  So I'd suspect that the pulseaudio stuff is just a coincidence.

Otherwise, Safder, the next time it happens, please give those additional things that I mentioned (control-alt-backspace, control-alt-f3, et cetera) a try.  I suspect that it's only the X server that's crashing, not the whole system, and the results of those things will tell us.  If the whole system were crashing, pressing control-alt-delete probably wouldn't do anything.

You could also try looking at the X log in /var/log/Xorg.0.log the next time the crash happens to see if it mentions anything strange going on.

Hi there,

It's been a while since I came back to check this, since I did not get the error for a while, however it has happened again, and I am here. I tried to do some of the things that you suggested.
I tired ctrl+alt+(one of the function keys), and it was actually letting me log into those modes, however when I press (ctrl+alt+f7), it's just a blank screen. There is one more thing I would like to point out is that, when this happens, I see the following on my screen

```
*Starting anchron(h)tistic chron anachron
*Starting deferred execution scheduler atd
*Starting periodic command sheduler chrond
*Enabling additional executable binary formats binfmt-support
*Checking battery state...
*Running local boot scripts (etc/rc.local)
```

The aforementioned stuff, is normally displayed when I press ctrl+alt+f8 on my system, so it's almost like I get thrown into the "F8" mode, when I close the firefox tab, and when I press ctrl+alt+F7, i just see a blank screen. I haven't tried ctrl+alt+backspace yet, what's that supposed to do?

As for the pulseaudio error, you might me right about it, 'cuz this time I got something different. Here's a snippet of what I got this time before i pressed ctrl+alt+del to restart


```
Jul 31 10:18:50 Shontu-moni gdm[5987]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 31 10:18:50 Shontu-moni gdm[5987]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Jul 31 10:18:50 Shontu-moni gdm[5987]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 31 10:18:50 Shontu-moni gdm[5987]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Jul 31 10:18:51 Shontu-moni gdm[5987]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 31 10:18:51 Shontu-moni gdm[5987]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Jul 31 10:18:51 Shontu-moni gdm[5987]: WARNING: gdm_slave_send: Can't open fifo! 
Jul 31 10:18:51 Shontu-moni gdm[5987]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 31 10:18:51 Shontu-moni gdm[5987]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Jul 31 10:18:51 Shontu-moni gdm[5987]: WARNING: gdm_auth_secure_display: Cannot safely open  
Jul 31 10:18:51 Shontu-moni gdm[5987]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 31 10:18:51 Shontu-moni gdm[5987]: WARNING: Request for invalid configuration key daemon/ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh 
Jul 31 10:18:51 Shontu-moni gdm[5987]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jul 31 10:18:51 Shontu-moni gdm[5987]: WARNING: Request for invalid configuration key daemon/ConsoleNotify=true 
Jul 31 10:18:53 Shontu-moni exiting on signal 15
```

Regarding the suggestion that this happens for flash enabled websites, I do want to point out that I was on "www.indiafm.com" which is flash enabled on the home page, now I am not sure whether this is just coincidence, but just want to point out that, I was trying to close that particular tab, when this happened.However, this does not happen always.

As for checking out the Xorg.0.log file, it doesn't have any timestamps, so I am not sure what I am looking for, however I found the following "potentially valuable" msg, not sure..whether it helps you, but here it is


```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) [drm] DRM interface version 1.0
```

Hope all this information will help you out in figuring out the problem.

---

### Post by pytheas22 on 2008-08-01
> I tired ctrl+alt+(one of the function keys), and it was actually letting me log into those modes, however when I press (ctrl+alt+f7), it's just a blank screen.

From that behavior, it's clear that it's only X that's crashing, not the entire system.  Pressing control-alt-backspace when you're on the control-altF7 screen should kill and restart X and bring you back to the login screen.  Does that work?

Since we are able to narrow this down to X crashing, I found some other people who seem to be having the same problem, [here]("https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/140554") and [here]("http://ubuntuforums.org/showthread.php?t=646416").  There does seem to be justification for the suspicion that the crashes are related to flash.  Unfortunately, there's no clear solution on those pages that works for everyone, but at least you know that it's not only your particular computer that's affected.  It seems to be a bug in X, or possibly related to the video driver--which kind of card do you have (nvidia, ATI, Intel...)?  Depending on that there may be a workaround.

Beyond that, there are a few other things that may help.  First, you could try reinstalling Firefox:
```

sudo apt-get remove --purge firefox
sudo apt-get install firefox
```

Second, it may help to use a different flash player.  Under the Tools>Addons>Plugins menu in Firefox, you can switch to something else.  I think the default is called "Shockwave Flash," but there is also Adobe's player (called flashplugin-nonfree) and gnash, GNU's attempt to create an open-source, reverse-engineered flash player (it doesn't work very well yet).

Third, if you're using desktop effects, disabling them may make a difference.

You could also try looking at your gdm logs, located in /var/log/gdm/.  They may contain tracebacks for the X crashes (unfortunately, they don't have timestamps either, so you'll have to search through them all).  I'm not able to make much out of the X log you posted (although I admit that I'm hardly an expert in X; I was just hoping it might say something that we could understand).

As I said, it doesn't appear, from what I've found, that there's any concrete solution to your problem, so I can't guarantee that any of the suggestions above is going to make a difference.  But they can't hurt to try.

Also, as a workaround, you could run two X servers, and use the second one for viewing websites containing flash.  That way, if flash crashes one of the servers, at least you won't lose all of your work.  You can launch a second X server by going to the control-alt-F2 terminal, logging in, and typing:
```

startx -- :01
```

It should launch and load Gnome.  It's not an ideal solution, and it wastes resources to run two X servers, but at least you won't lose work.

Also keep in mind that whenever X crashes, pressing control-alt-backspace should reset it.

Please post on your progress if you do find anything that seems to fix the problem.

---

### Post by prshah on 2008-08-01
> **Safder said:**
> 
Regarding the suggestion that this happens for flash enabled websites, I do want to point out that I was on "www.indiafm.com" which is flash enabled on the home page, now I am not sure whether this is just coincidence, but just want to point out that, I was trying to close that particular tab, when this happened.However, this does not happen always.

As for checking out the Xorg.0.log file, it doesn't have any timestamps, so I am not sure what I am looking for,

Once again, check your pulseaudio setup. There are potential conflicts between flash and an improperly setup pulseaudio framework. Or switch everything to ALSA and check if you still run into _these_ problems. (Switching to ALSA will create new problems; audio will work in only one app at a time, eg, if you have a flash website using sound, a new music player instance will not work. That's a different kettle of fish).

The Xorg.0.log file will  contain information only till such time the X system is started; all subsequent messages will be written into the system log (dmesg or '/var/log/messages'), so it's pointless trying to look in there.

---

### Post by Safder on 2008-08-05
> From that behavior, it's clear that it's only X that's crashing, not the entire system.  Pressing control-alt-backspace when you're on the control-altF7 screen should kill and restart X and bring you back to the login screen.  Does that work?

 This does not work for me

---

### Post by Safder on 2008-08-05
> **prshah said:**
> Once again, check your pulseaudio setup. There are potential conflicts between flash and an improperly setup pulseaudio framework. Or switch everything to ALSA and check if you still run into _these_ problems. (Switching to ALSA will create new problems; audio will work in only one app at a time, eg, if you have a flash website using sound, a new music player instance will not work. That's a different kettle of fish).

Could you tell me, what would be the definition of a proper pulseaudio setup? How would I know that there are conflicts between flash and pulseaudio?

---

### Post by prshah on 2008-08-05
> **Safder said:**
> Could you tell me, what would be the definition of a proper pulseaudio setup? How would I know that there are conflicts between flash and pulseaudio?

I don't know if you have a conflict; I'm just guessing. Back in post #3, I have mentioned where you can find information on setting up pulse properly.

---

### Post by Safder on 2008-08-05
> **prshah said:**
> I don't know if you have a conflict; I'm just guessing. Back in post #3, I have mentioned where you can find information on setting up pulse properly.

This is what part A of the guide you referred to does
> This section will adjust your PulseAudio setup to allow almost every ALSA-aware application to work properly with PulseAudio. If you don't complete this step, any ALSA applications without native PulseAudio support will block access to the sound card, preventing PulseAudio from using it simultaneously.

Now when i run the test for running both alsa and pulseaudio at the same time using the following commands
```
gst-launch-0.10 audiotestsrc ! pulsesink
gst-launch-0.10 audiotestsrc ! alsasink
```

Both of the them pass for me. But I figured (from the guide), maybe some applications which do not have native Pulseaudio support may cause this, so I did part A anyways.

Now part B is for i386 systems. I have an Amd Turion 64, so am I right in assuming that Part B is not for me?

---

### Post by Safder on 2008-08-08
Ok ppl,

It happend again a few minutes back, and I would like to point out that this time, I did not have any flash site open, and it happened again. So the possibilty of flash conflicts is less likely, though there might be some obsure flash app running on one of my tabs, though I made sure that there were no flash apps running.

As for pressing ctrl+alt+backspace, it didn't do anything...so any suggestions now?

---

### Post by Safder on 2008-08-08
> which kind of card do you have (nvidia, ATI, Intel...)?

I have an ATI RADEON 1250

---

### Post by pytheas22 on 2008-08-08
I'm sorry it keeps happening.  Since you're using an ATI card, which driver are you using--the default open-source one or the proprietary version?  Maybe switching to the other driver would help (you might not get desktop effects though).

I still don't think the whole system is crashing--otherwise you wouldn't be able to log in on the other terminals by pressing control-alt-F[1-6]--so I think it's just X.  But I guess that X crashes so badly that it doesn't respond to any keyboard input, including control-alt-backspace.

Another thing to try is to see if, after a crash, you can log in on another terminal and run the command:
```

killall X
```

which should manually kill X and force it to restart.  After that, what does the control-alt-F7 screen look like?

---

