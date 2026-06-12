---
title: "Some problems with acer aspire"
date: 2010-07-12
forum: Hardware
---

### Post by MartinoM on 2010-07-12
Hi! I have some problems for configure my notebook. I just try some way that i founded on the web, but nothing. These is a list of errors: it appears when i turn on my pc.

**EDIT: I solved lines 4 and 5.**

[IMG]http://img338.imageshack.us/img338/6168/foto0030z.jpg[/IMG]

Thank you!



Ubuntu 10.04 64 bit. Intel core 2 duo processor T8100, nVidia GeForce 8m series, 4GB RAM

---

### Post by AltomineUK on 2010-07-12
Update BIOS.....

---

### Post by MartinoM on 2010-07-12
I just update BIOS, but nothing:(

---

### Post by AltomineUK on 2010-07-12
Hmmmm.... i thought the firmware bug would have been sorted out with a firmware update of the BIOS. However, it seems that your BIOS cannot successfully link to MBR for Grub to load and start booting linux..... i'm confused :S

---

### Post by Yellow Pasque on 2010-07-12
Either the BIOS is buggy or you have something set wrong. Try resetting it to factory defaults.

---

### Post by MartinoM on 2010-07-13
> **Temüjin said:**
> Either the BIOS is buggy or you have something set wrong. Try resetting it to factory defaults.

I try and no news! I have always the sames problemes

---

### Post by AltomineUK on 2010-07-13
> **MartinoM said:**
> I try and no news! I have always the sames problemes

Run a LiveCD of any Linux distro (Puppy or Ubuntu itself would be best) and see if your notebook can load the kernel and boot linux from the liveCD.

---

### Post by MartinoM on 2010-07-13
> **AltomineUK said:**
> Run a LiveCD of any Linux distro (Puppy or Ubuntu itself would be best) and see if your notebook can load the kernel and boot linux from the liveCD.

If i create the usb live with Ubuntu's default program, after boot appear this error message: error boot and i can't use the LiveCd.
I try to create the live usb with Linux Usb Live Creator and Live Ubuntu works!

---

### Post by MartinoM on 2010-07-13
I try to run opensuse gnome from live cd and appear this message: "kernel image not found"

---

### Post by AltomineUK on 2010-07-13
> **MartinoM said:**
> If i create the usb live with Ubuntu's default program, after boot appear this error message: error boot and i can't use the LiveCd.
I try to create the live usb with Linux Usb Live Creator and Live Ubuntu works!

Hmmmm....ok, sounds like progress. If your LiveCD is booting then the cause of your error may not be system-wide. What processor are you using, by the way? And have you got any important data in your HDD? Using the liveCD you can try and repair your OS. I think the options to repair can be found at the main menu when you boot from your LiveCD....then there is the option to re-install the whole thing but we'll save it for the end.

---

### Post by MartinoM on 2010-07-13
I have some news. I solved the errors that appears at lines 4 and 5!
For line 4 i updated the kernel and i installed 2.6.34 lucid
For line 5 i follow this guide (i found it in italian): [http://www.linuxqualityhelp.it/supporto/viewtopic.php?f=25&t=5950]("http://www.linuxqualityhelp.it/supporto/viewtopic.php?f=25&t=5950")

For other nothing for now!

---

### Post by MartinoM on 2010-07-13
I have this processor: Intel core 2 duo processor T8100 (2.1GHz, 800MHz FSB, 3MB L2 chache)

---

