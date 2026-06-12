---
title: "&quot;Mode not supported&quot; after start-up"
date: 2010-09-17
forum: Hardware
---

### Post by Kono on 2010-09-17
After I upgraded from 9.04 (?) to 10.04.1 LTS I have a very weird problem, which also happens after a fresh install.

My configuration: Intel 64 bit processor, Nvidia GT 220 graphics card, 8 GB of RAM, Ubuntu 10.04.1 LTS (64 bit, alternate, installed with full disk encryption).

I'm pretty sure I have done nothing wrong during the installation process; it's not the first time I installed Ubuntu with full disk encryption.

The problem surfaces right after grub loads the kernel. My monitor just goes blank and says "Mode not supported" while displaying the horizontal and vertical refresh rates (which may indicate it's a problem with the refresh rate). I also tried two other monitors, same problem. This led me to believe it's not a problem with the monitor per se. Also, the problem did not show up on the same configuration in versions 9.04 or before.

The problem appears BEFORE I can even enter the passphrase to unlock the root partition / (/boot is the only available, unencrypted partition at this point), so IMHO it CANNOT be be a problem with X. It also happens if I choose 'recovery mode' from the grub menu. I see text for about 1 second, then right before where I'd usually be asked for the password, the monitor goes blank. Same problem. Which is weird, because recovery mode is supposed to be text only, right?

Now, I can type in the password blindly and I can see that my hard disk starts working, but no matter what I do, I can't get rid of the problem. I even tried to go to command prompt in recovery mode and type in "fix-vesa" and reboot, but the problem remains.

I also tried to manually set the resolution, bit depth, and refresh rate in the grub menu (by pressing e), but it doesn't work either (and I don't know which resolution, depth, and especially which refresh rate to use and I'm not even sure it's a problem with the refresh rate).

After hours of googleing and testing, I'm exhausted and glad if someone could help me.

Any help is appreciated. :)

---

### Post by wilee-nilee on 2010-09-17
Did you try adding nomodset in that kernel e=edit section?
You would just add nomodset at the end of the first kernels stanzas.

Sounds like a graphic driver problem, I am assuming this is now the fresh install we are talking about. 

When and if you get in check the additional drivers in the menu-system-admin.

---

### Post by Kono on 2010-09-18
> **wilee-nilee said:**
> Did you try adding nomodset in that kernel e=edit section?
You would just add nomodset at the end of the first kernels stanzas.

Sounds like a graphic driver problem, I am assuming this is now the fresh install we are talking about. 

When and if you get in check the additional drivers in the menu-system-admin.

Yes, it's a fresh installation.

The **nomodeset** parameter fixed the problem (note that it's **nomodeset**, not **nomodset**, for those reading this thread having the same problem).

After I got into Ubuntu in graphics mode, I installed the official Nvidia drivers and now it works flawlessly, but I had to configure grub to include **nomodeset** at every boot.

Should I file this as a bug? It sure sounds like one given that it messes up after a fresh install and the way I had to fix it.

---

### Post by wilee-nilee on 2010-09-18
> **Kono said:**
> Yes, it's a fresh installation.

The **nomodeset** parameter fixed the problem (note that it's **nomodeset**, not **nomodset**, for those reading this thread having the same problem).

After I got into Ubuntu in graphics mode, I installed the official Nvidia drivers and now it works flawlessly, but I had to configure grub to include **nomodeset** at every boot.

Should I file this as a bug? It sure sounds like one given that it messes up after a fresh install and the way I had to fix it.

Funy thing about the spelling I have seen it

---

### Post by Nomkaz on 2010-12-26
I'm having the same problem but I can't access "safe mode" in Grub. This isn't a new install either, it's a problem that just randomly popped up when I tried to boot up the computer this morning. My Grub is set to automatically boot Ubuntu since I have no other OS. I am currently running from an live cd. I can't do anything in grub.

---

