---
title: "Lucid - Sound stutters on Thinkpad X21"
date: 2010-04-30
forum: Hardware
---

### Post by Wheel_nut on 2010-04-30
Took the upgrade to Lucid 10.04 last night and now neither the Rhythmbox nor Movie Player will play Sound correctly. The sound stutters and jumps passages.

Anybody else seeing this? :(

As an aside, I had two other problems:

1) The 3Com 3CRWE154G72 Wireless PC Card which worked perfectly up to 9.10 no longer works. However, the MSI Ralink Card which wouldn't work before now works perfectly! :)

2) The Trackpoint Scroll functions which I configured in UDEV under 9.10 no longer work. I have recovered this by installin the GPointing Device Setting Tool from Synaptics. :)

---

### Post by Redsunz on 2010-05-01
Yes also stuttering on my pc music and movies sound skips delay in games between graphics and sounds.:(

---

### Post by Redsunz on 2010-05-01
> **Wheel_nut said:**
> Took the upgrade to Lucid 10.04 last night and now neither the Rhythmbox nor Movie Player will play Sound correctly. The sound stutters and jumps passages.

Anybody else seeing this? :(

As an aside, I had two other problems:

1) The 3Com 3CRWE154G72 Wireless PC Card which worked perfectly up to 9.10 no longer works. However, the MSI Ralink Card which wouldn't work before now works perfectly! :)

2) The Trackpoint Scroll functions which I configured in UDEV under 9.10 no longer work. I have recovered this by installin the GPointing Device Setting Tool from Synaptics. :)

I got it working a little better by clicking system/preferences/startup application and un checking Pulse Audio sound system.  Then re-booting.
Looks like this version of Ubuntu has more Pulse audio sound problems.

---

### Post by Wheel_nut on 2010-05-03
:( I just tried un checking Pulse Audio sound system. Then re-booting. It is still skipping though (perhaps optimistically), I thought it was less severe.

Is this a known problem? If not, how do we get it registered on the bug list?

---

### Post by Redsunz on 2010-05-04
> **Wheel_nut said:**
> :( I just tried un checking Pulse Audio sound system. Then re-booting. It is still skipping though (perhaps optimistically), I thought it was less severe.

Is this a known problem? If not, how do we get it registered on the bug list?

Try this as well click System/Preferences/Main Menu
Scroll down to System/Preferences then on the right click on show Multimedia Systems Selector.
 
Now in your system/Preferences you have Multimedia System Selector.
Click that and set Default Audio output to another selection.
Alsa is currently working pretty well for me.
I don't know why Ubuntu defaults to Pulse it seems to be a huge problem.
I think this is the same bug as this?
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849")

Sign up for a launchpad account and report this.
Welcome to the club.

---

### Post by Orbiter on 2010-05-04
I also have the same problem with my 3com 3CRWE154G72 card.

Worked perfectly in 9.10 but now upgraded to 10.04 it has stopped.

I've now reverted to cable.

any help would be gratefully received.

Orbiter.

BTW - love Lucid, its now on a net-book, desktop & my laptop.

---

### Post by Wheel_nut on 2010-05-04
Redsunz, I have just tried your suggestion to switch to ALSA but the sound is still skipping. It doesn't seem to stutter as much but it is still skipping passages.

I will raise a bug report on Launchpad once I work out how ... :confused:

Orbiter, I have replied to your other thread. I suggest we continue the dialogue about the Wireless Card issues there.

---

### Post by Wheel_nut on 2010-05-05
OK, I have raised Bug# 575538 on Launchpad and have received an acknowledgment email confirming it with "New" status. 

Here's hoping.....

---

### Post by lidex on 2010-05-05
First thing do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Now do 'Part 1/5' here (only the preparation and installation for 8.10 and higher):
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Report your results.

---

### Post by mbuller10 on 2010-05-05
You wanna know my results, I got tons of errors and my sound stopped working on a whole bunch of applications I had to do
sudo apt-get install libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol

to get my sound working right again, still skips once and a while too
isn't there a way to fix pulse audio without switching to alsa

---

### Post by Pikhouweel on 2010-05-08
I've been experiencing the same problem since updating to Lucid. The following solved the problem for me:

Open a terminal and type:

sudo gedit /etc/pulse/daemon.conf

This will open a configuration file and near the end you will find the following line:

default-sample-rate=44100

I changed 44100 to 48000 and saved the file. I'm not sure if you have to restart for the changes to take effect, but I did just to be sure.

Since then the stuttering stopped. I hope this will help you as well!

---

### Post by Wheel_nut on 2010-05-08
Hi Pikhouweel,

I have just tried your suggestion and even after re-booting, the stuttering is still there.:(

That really gave me hope ...... Oh well! .... Any other suggestion welcome.

---

### Post by lidex on 2010-05-08
Have a look here:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html]("http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html")

BTW- you'll want to change your default sample rate back to original value.

---

### Post by Wheel_nut on 2010-05-08
Hi Lidex, That looks promising but it is too complicated to be trying at this time of night (it is after midnight here!). I will give it a go tomorrow and report back here.

---

### Post by Pikhouweel on 2010-05-16
When you tried the suggestion I gave earlier, did you remove the ";" which is placed in front of "default-sample-rate" in daemon.conf ?  If you haven't, you might want to try it again with the ";" deleted. If the ";" is still there PulseAudio will use the default setting (which is 44100) and not the 48000 you filled in yourself.

> **Pikhouweel said:**
> 
sudo gedit /etc/pulse/daemon.conf

This will open a configuration file and near the end you will find the following line:

default-sample-rate=44100

I changed 44100 to 48000 and saved the file. I'm not sure if you have to restart for the changes to take effect, but I did just to be sure.



---

### Post by Wheel_nut on 2010-05-20
Hi Pikhouweel, I hadn't removed the semicolon. I tried it again with the semicolon deleted but it still stutters. :(

---

### Post by scprotz on 2010-05-25
I tried the site provided by lidex.  Worked like a charm (though my volume control seems to be disabled on the menubar).  But other than that, no more stuttering.

One comment: on Lucid 10.04, there is no pulse-rt group, so the commands on the site that suggest making those changes weren't applicable for me (so I just didn't do them).  

I'll revisit at some later date (this was for a media server anyway..so it seems to be 'good enough' for now)


Thanks for the pointer

---

### Post by Wheel_nut on 2010-05-25
Hi Scprotz,

Please could you post a step by step instruction of what you did. I haven't tried this because I couldn't understand the procedure and I don't understand the structure of the Linux operating system. :confused:

---

