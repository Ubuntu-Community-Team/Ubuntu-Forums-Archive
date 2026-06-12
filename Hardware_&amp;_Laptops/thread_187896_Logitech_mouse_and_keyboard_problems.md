---
title: "Logitech mouse and keyboard problems"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by mikaPELL on 2006-06-03
Hi, I just upgraded from Breezy to Dapper, and my Logitech mouse and keyboard stopped working... Other USB devices work fine, and I got a keyboard running on PS/2. Any suggestions?

---

### Post by ketekojo on 2006-06-03
¿what is your kernel, i386 or i686? I have a keyboard PS/2 and it stop working under the i686 kernel.

---

### Post by nickle on 2006-06-03
I am having the same problem. I could not get the install going with the Logitech USB keyboard, but it worked with another Logitech PS2 keyboard...????

The USB keyboard works perfectly on my other installed system, but heck not for the install. I don't know what i would do if I did not have an alternative...

---

### Post by mikaPELL on 2006-06-03
I have 386 kernel, though I am really not sure about the difference between the two (I found out by running uname -a). It's the USB keyboard, not the PS/2 that is not working, and I find this really strange.

---

### Post by xENObRAIN on 2006-06-03
I have a Logitech MX1000 on usb and a Saitek Eclipse keyboard also on usb.

Both of these are not detected when booting Kubuntu 6.06 amd64, leaving me... well.... absolutely helpless.

The mouse I can plug into ps/2 and it works, the keyboard I cannot, and I do not have a spare ps/2 keyboard either.

This is absolutely ridiculous and completely unacceptable. What went wrong here?

---

### Post by ketekojo on 2006-06-03
¿Are the USB keyboard support activated in the Motherboard BIOS?

---

### Post by mikaPELL on 2006-06-03
[QUOTE=ketekojo]¿Are the USB keyboard support activated in the Motherboard BIOS?[/QUOTE]
It might not be, but that shouldn't stop the mouse from working, and does that explain why it worked like 10 minutes ago in Breezy? Thanks for the replies :)

---

### Post by xENObRAIN on 2006-06-03
[QUOTE=ketekojo]¿Are the USB keyboard support activated in the Motherboard BIOS?[/QUOTE]

Yes both usb keyboard and mouse support are activated in BIOS. The keyboard is active on bootup, allowing me to make menu selections, etc.

The problem being that it gets turned off and never gets turned back on when ubuntu starts, this happens when I select console mode as well.

Normally the keyboard will go off for a half-second when my Arch install is booting up, then come back on quickly. Ubuntu turns off my keyboard and never turns it back on.

My KUbuntu Breezy cd boots up just fine, keyboard/mouse support and all. This has got to be a problem with Dapper.

It sounds to me like others are experiencing the exact same problem.

As for possible solutions, I suppose I could borrow a friends keyboard and install DD with that, then maybe replace hotplug with udev and fiddle with modprobe.conf a bit.....

But seriously not worth it.

I was a fan of Ubuntu for the time I used it, 5.04-5.10 and was looking forward to trying it out again, but this is a bit disheartening.

Looks like I'll be loading Ubuntu on my dad's laptop and sticking with Arch on my desktop for the time being.

---

### Post by ketekojo on 2006-06-04
Well, finally i find the solution: enter in the BIOS and desactive the HyperThreading. The keyboard run fine... i supuse that is a kernel error.

---

### Post by mikaPELL on 2006-06-04
Well, I didn't find any hyperthreading, but all of a sudden after the PC being on for like 15 mins, my PC Speaker went berserk, and I could use the keyboard and mouse again. I don't have a *clue* what's going on here :confused:

---

### Post by trmentry on 2006-07-30
> **xENObRAIN said:**
> I have a Logitech MX1000 on usb and a Saitek Eclipse keyboard also on usb.

Both of these are not detected when booting Kubuntu 6.06 amd64, leaving me... well.... absolutely helpless.

The mouse I can plug into ps/2 and it works, the keyboard I cannot, and I do not have a spare ps/2 keyboard either.

This is absolutely ridiculous and completely unacceptable. What went wrong here?


I'm having the same issue as well.  I'm wanting to get Ubuntu installed but well... I can't as I have no keyboard or mouse to use to get this done.  

Has this issue been solved and I missed it in my search? 

My hardware:
```

o Asus A8N-SLI Premium
o AMD64 x2 4400+
o 3 gig DDR400 Memory
o BFG 7900GT
o 2x 160g SATA drives.  (1 with winders, the other waiting for Ubuntu)
o DVD-ROM drive
o DVD Burner (Dual Layer)

```

---

### Post by esan on 2006-10-02
Hi! I've got same problem. I have solved it temporarily by unplugging Logitech Cordless Desktop (both mouse and keyboard) and then re-plugging them. Then they are both working! Thus I was able to install Dapper. I'm looking for permanent solution.

---

