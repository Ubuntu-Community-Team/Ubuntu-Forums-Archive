---
title: "X Server Failed..."
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by Enzo on 2006-01-28
I've just installed ubuntu on my new dell e510.
I've never used linux before and hear good things about ubuntu so i wanted to try it out. I ordered the dell ready for open source so nothing was done to hard drive. I installed ubuntu and everything seemed to go fine but then right before it would boot up it pops up with the following error...

Failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Has anyone seen this before? IS the problem due to my video card? 

Any help would gladly be appreicated...

---

### Post by Ocxic on 2006-01-28
can you login. if you can try this at the terminal
```
 sudo dpkg-reconfigure xserver-xorg 
```
that will reconfigure all of th Xserver setting and allow you to pick and choose the settings, make sure you pick the proper driver
ati/radeon/fglrx for ATI cards try ati as the first driver, vesa and vga drivers are mor compatable with most systems kind of like a failsafe, so try thos if others don;t work.

---

### Post by guytrinn on 2006-01-28
hey i am having the same problem, and i did what you said, but when i go to select the bit depth, no matter which one i select, it fails and said i was attempting to change something that was customized or something

---

### Post by findik1 on 2006-04-05
sorry to bother but I have the same system, could not install , it gave errors in from the beginning. Can you explain how did you install?
Thanks 

[QUOTE=Enzo]I've just installed ubuntu on my new dell e510.
I've never used linux before and hear good things about ubuntu so i wanted to try it out. I ordered the dell ready for open source so nothing was done to hard drive. I installed ubuntu and everything seemed to go fine but then right before it would boot up it pops up with the following error...

Failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Has anyone seen this before? IS the problem due to my video card? 

Any help would gladly be appreicated...[/QUOTE]

---

### Post by kaif on 2006-04-06
I have the same problem too! (On my desktop PC, works fine on my laptop).

Very fustrating, I'll give what Ocxic suggested a try when I get back home today.

I think this could be related to ATI cards, I'm using a 9800.

---

### Post by kaif on 2006-04-07
Is anyone able to shed some light on this? Seems like a few people are having this problem.

---

### Post by warrentuck on 2006-04-10
[QUOTE=kaif]Is anyone able to shed some light on this? Seems like a few people are having this problem.[/QUOTE]
ive got same prob on my instal.  Any one above resolve their issue?

---

### Post by warrentuck on 2006-04-10
tried sudo dpkg-reconfigure xserver-xorg   went thru set up selected 'ati',  and on rebot still same, redid and selected 'nv', rebooted, and still same, pulled out the unknown video card, plug monitor onto mobo, rebooted and still getting x server failed.  Think i will go back to windows, this is all too hard.

---

### Post by alamba on 2006-04-10
Here's a generic solution that should help most of you. This is just a bandaid job to get you up and running, though the basic issue still needs to be fixed. First a little background, 2 main reasons for X-server failing (that I have come accross) are driver not available or basic misconfiguration of bit depth, resolution, refresh rates, etc. Incase it is a basic misconfiguration the only thing I can suggest is  sudo dpkg-reconfigure xserver-xorg and read your hardware manual.

Incase of a driver issue, the following should get you up soon:
1. Boot into the rescue mode (press esc during grub and then select rescue mode)
2. sudo vi /etc/X11/xorg.conf
3. Scroll to "Section Devices"
4. For the tab Driver "XXXXX" change to Driver "vesa"
5. Save and reboot (press esc and :wq)

This should get your GUI going. Do keep in mind that u're now using a generic diplay card driver. Once you have the GUI going you would still need to figure our your card manufacturer and install the neccessary linux drivers for it.

Good luck.

A

---

### Post by boyced on 2006-04-10
when I type the sudo command I get an error "unable to lookup ubuntu via gethostbyname()"

---

### Post by alamba on 2006-04-11
Can you go to the directory /etc/X11/ and ls for a file called xorg.conf

A

---

### Post by Bishop Hill on 2006-04-11
I used to have the exact same problem, and I solved it by doing almost as alamba wrote, only that I did not use recovery mode. When my screen got blue and all that stuff happend, my system automaticly went into a non-graphical state, and I could just type the code.

---

### Post by alamba on 2006-04-12
Bishop: You're absolutely right. I should have said that if you get console mode then those commands can be used straight off. You only need recovery mode if you're stuck in a non-gui & non-console area (like I got a black screen - period).

A

---

### Post by l.tambiah on 2006-04-12
Hmmm,

When it comes to Linux NVIDIA is the best card to get ATI cause's a lot of problems. I've never had any issues with NVIDIA though. Also onboard graphic cards can cause problems from what I have found.

---

### Post by RoshanDawrani on 2006-04-18
If you are trying out Ubuntu 5.10 with a live CD, then instead of trying to modify the /etc/X11/xorg.conf to change the driver from default to 'vesa', you may enter the boot process in expert mode by entering 'live-expert' at the prompt at the start of boot process [don't press Enter to enter into the default mode]. It then asks you questions relevant to various steps of booting process. At the video hardware detection step, chose not to autodetect. It then shows you the list of drivers. Chose 'vesa' in this list and proceed with defaults with rest of the steps. For me, changing the default video driver to 'vesa' this way helped and Ubuntu 5.10 came up nicely and identified my USB disk, on-board sound-card, etc quite neatly.

Hope it'll help you too.

Regards,
Roshan Dawrani

---

