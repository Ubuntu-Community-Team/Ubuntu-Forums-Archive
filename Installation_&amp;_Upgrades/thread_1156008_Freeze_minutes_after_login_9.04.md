---
title: "Freeze minutes after login 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by quantum64 on 2009-05-11
Like many I'm _very_ new to Ubuntu and linux in general, and I'm only posting because I've exhausted all other solutions I have been able to find within the Ubuntu support forum.

**The problem:**
Clean install of Ubuntu 64bit 9.04 on a empty 320GB drive ext3. About 1 minute after I login, my mouse and keyboard freeze. No key combinations work either. It requires a hard reset. Before 'the freeze', I am able to do anything on the system, no particular function seems to lock it up. It freezes almost exactly the same time after each login.

**Computer:**
GA-K8NSNXP socket 754
AMD64 3200+
1.5GB Memory
GeForce 6800GT
Audigy 2 sound card
320GB hard drive
[B]
Solutions attempted:[/B]
1. Removed compiz because I heard the special effect features can freeze some video cards. I followed the following steps to do this.

[LIST]
[*]From the Grub boot menu slect the “recovery mode” option.
[*]Select “root   Drop to root shell prompt”
[*]sudo apt-get remove compiz
[*]sudo apt-get remove compiz-core
[*]exit
[*]Still freezes
[/LIST]
     
2. Updated video card drivers by using envy.

[LIST]
[*]Start recovery mode and enter root with networking.
[*][Followed steps in: http://albertomilone.com/envyngfaq.html#A]("http://albertomilone.com/envyngfaq.html#A")
[*]Confirmed new drivers in use. sudo nano /etc/X11xorg.conf
[*]Still freezes
[/LIST]

3. Updated Ubuntu by following these steps.

[LIST]
[*]apt-get update
[*]apt-get upgrade
[*]Still freezes
[/LIST]
4. I then tried the 32bit version of Ubuntu and encountered the same problems.

I've read some things about sound card issues but I'm not sure where to start with that. I suppose I could stry by pulling the sound card and seeing if that works. (Will try later tonight)

For now, can anyone point me in the right direction?

---

### Post by drs305 on 2009-05-11
Regarding your *envy* entry: 
I run a 7600GS card on Jaunty 64-bit. I checked and your card is supported by the standard nvidia drivers available from within Jaunty (180.51). System, Administration, Hardware Drivers. I would use these drivers and let Jaunty install it rather than envy. Envy was a valuable tool in previous versions but I find it unnecessary now.

Anything you can allow Jaunty to do for you is usually a better option than trying to bypass the system. Of course, if you have already tried this then you will have to wait for more inputs.

---

### Post by quantum64 on 2009-05-11
Thanks for your input. I've not used Jaunty before. I'll be sure to look up how to use it when I get home tonight. For some reason, I'm leaning away from a video card problem since it seems to work for at-least a minute after login, but I certainly have not ruled it out.

---

### Post by quantum64 on 2009-05-11
I've also had XP on this computer and did not have this issue. So I have no reason to believe its hardware related.

---

### Post by a fenderson on 2009-05-11
I've had this same problem.  I have onboard intel video, and it doesn't happen after every login, but it's definitely often enough to be noticeable.  What kind of sound card do you have? (Mine is built in and uses the snd_hda_intel driver.)

---

### Post by quantum64 on 2009-05-11
I have an Audigy 2 soundcard. I'm going to try pulling it when I get home to see if it still freezes.

---

### Post by quantum64 on 2009-05-11
Removed Audio card and still have no luck. Anyone have any other suggestions?

---

### Post by quantum64 on 2009-05-12
Still need help if anyone is willing to offer... :)

---

### Post by quantum64 on 2009-06-03
I ended up replacing the motherboard, cpu, and ram. All seems to be working with the new hardware.

---

