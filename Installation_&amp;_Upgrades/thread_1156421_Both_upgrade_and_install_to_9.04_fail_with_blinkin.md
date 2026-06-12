---
title: "Both upgrade and install to 9.04 fail with blinking cursor"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by fslamb on 2009-05-11
I was running 8.10 on Toshiba Satellite 1135-S1551 fine with one exception, wireless networking required re-entering the password multiple times.  Because of this problem, when the 9.04 upgrade was available, I let the system do the upgrade to 9.04.  The system then froze, leaving only a blinking cursor.  This happened twice (after reloading 8.10).

So I tried downloading 9.04 (both standard and alternate), checked the download file and the disk, booted to the cd, chose install (after setting BOOT_DEBUG=2) and the screen shows many lines of information ending with:

[  0.547470] pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11

Then there is a blinking cursor and the system is frozen.  Eventually the screen goes blank.

I've been trying the various boot parameters without any success.

Any ideas will be appreciated.

---

### Post by fslamb on 2009-05-11
Made it past that problem with the Boot Parameter:
hw-detect/start_pcmcia=false
Now I wonder if I will be able to use my Netgear Rangemax Wireless PC Card...

---

### Post by fslamb on 2009-05-11
Installation completed, now when booting the system gets to the same place described above, so I've tried editing the boot parameters as I did before installation, and the system still locks up with a flashing cursor at the same point...

---

### Post by fslamb on 2009-05-19
Gave up on 9.04.  Wish someone had an idea about solving my problem.  

8.10 is functioning again, but with continued problems logging into wireless network.

---

### Post by dabl on 2009-05-19
Sorry I didn't see your thread before.  In addition to the pcmcia issue that you fixed with a boot option, I think there was a video issue. Probably at the blinky cursor you could have done Alt-F1 and gotten a tty console login prompt.

---

### Post by fslamb on 2009-05-19
Thanks for the reply.  If I go through the install again and Alt-F1 takes me to tty console, then what will be next?  How do I overcome the pcmcia and video issues?  Why would these new issues develop with the new release of Ubuntu?  Is it worth trying to overcome 9.04 issues or should I just stick with 8.10 and work on the wireless networking problem?

---

### Post by cmkennedy on 2009-06-26
I'm having the exact same problem with the exact same laptop. I guess I'll just have to go to 8.10 instead of running the latest Xubuntu.

Any further information from any experts on here?

---

### Post by fslamb on 2009-06-27
I've given up on 9.04.  8.10 is working okay, but logging into the wireless network takes several tries.

---

### Post by cmkennedy on 2009-06-27
> **fslamb said:**
> I've given up on 9.04.  8.10 is working okay, but logging into the wireless network takes several tries.
This is what would concern me. I'd be using the laptop in bed wirelessly to write and occasionally browse the net.

And here I'd read that you don't need to scale back Ubuntu versions to use on older hardware...yet here's a perfect example of that exact problem. Windows XP works perfectly fine, if slowly.

---

