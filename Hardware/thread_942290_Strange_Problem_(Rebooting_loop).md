---
title: "Strange Problem (Rebooting loop)"
date: 2008-10-09
forum: Hardware
---

### Post by Fraktured on 2008-10-09
So I was really excited I had tried ubuntu at version 6 on another laptop and it worked and recently wanted to take full advantage of 64 bit processing on my HP dv6125se

Got the Broadcom wireless working..

Got Nvidia drivers loaded...

Ready to start working!

But, then I had to go to do something and set the machine to Hibernate, when I attempted to reboot the machine booted (not even past the Bios screen) and then rebooted several times (not getting past the bios load). Finally I manually held the powerswitch down and got it to actually shutdown. 

After this boot it seemed to be working but my WIFI card was not working, I could see it, my light was lit, but it was saying that it could not connect in the network manager. 

I am currently afraid to boot into Ubuntu for fear of doing irreparable damage to my laptop due to the reboot loop problem. Should I reinstall Ubuntu or run recovery mode?

If I get there what should I do?

I had the nvidia settings to run dual monitors with seperate x-sessions could this have anything to do with it?

I really hope to get this working as I feel that I could move most of my audio/video work over to linux now except for this hang up.

---

### Post by andrewc6l on 2008-10-09
If you're really not getting past the BIOS screen, then the problem is more likely with the hardware than with the OS.

You might try booting from CD - if you can get into the BIOS setup and set it to boot from CD. If you can, that would indicate it's not the BIOS, and also that it probably *is* the HD (probably the boot record or something like that).

I'd recommend reinstall - you could try recovery mode, but without knowing what's gone wrong, it's a lot harder to diagnose.

---

### Post by Fraktured on 2008-10-10
Well, during this rebooting 'loop' if I hold the power button down it will boot as normal. I tried noacpi in grub, but today it exhibited the same problem, I shut the machine down last night, and then when I went to boot today, it started 'rebooting'

Any ideas on things to check in the bootloader? I'm up and running now, going to try sort alsa and stuff.

---

### Post by andrewc6l on 2008-10-10
This sounds like it could be a hardware fault that happened to occur at the same time. Here's a URL that might help:

[http://www.houseofhelp.com/forums/showthread.php?t=72786](http://www.houseofhelp.com/forums/showthread.php?t=72786)

---

### Post by Fraktured on 2008-10-10
Thanks, this doesn't appear to be the problem..

I'm thinking that there's a possibility that the processor is too hot, now I just shutdown (halt) instead of restart, then let the machine sit for about 10 or more seconds and it boots ok.

def a hardware issue.

What makes it annoying is i'm trying to get jack to work and everytime I shutdown jackd the machine stops recognizing any usb devices so I have to restart to continue trouble shooting.

---

