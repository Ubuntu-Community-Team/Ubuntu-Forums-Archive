---
title: "Built-in keyboard stops working with 686-smp kernel"
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by wolrahnaes on 2005-01-24
I have my system working with the 386 kernel, but when I reboot with the 686-smp version enabled, the built-in keyboard does not respond.

The mouse, touchpad, and even my ATI Remote Wonder still work beautifully, and I can even type in numbers and a limited set of letters using the remote's keypad, but it's not enough to log in.

System details are in my sig, I'll provide more info if needed upon request.

I'm considering moving up to Hoary, since that supposedly fixes my ATI AC'97 sound and will give me the newer Radeon drivers.  Should that also fix my issues with a SMP kernel?  I'd really like to be able to use the hyperthreading features.

---

### Post by martyr on 2005-01-25
First, I'd try using a non-SMP 686 kernel. 

Find out whether this solves the problem and if not, post again.

---

### Post by jesterfred on 2006-05-20
Stranger than fiction...

I have the exact same keyboard problem.  However, I have discovered a workaround.  While booting, continually tap the NumLock key on your keyboard.  Do this at a rate of about twice a second.   You will notice the NumLock light on your keyboard do strange things...  Start after your BIOS screen and continue until the login screen.  Works for me.  I am typing this post using the 686 SMP kernel.  There is probably an initialization problem somewhere in the driver that this keypress gets around.

---

### Post by Mikera on 2006-10-09
I had very same problem with my Ideq300 ( HT intel 3,4Mhz ) + 2xSATA drives.
I disabled ACPI from my BIOS settings and keyboard started to work.
Before changing BIOS settings keyboard only worked if I continually tapped the NumLock key in a boot.

---

