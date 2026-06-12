---
title: "ACPI=OFF=double edged sword"
date: 2008-12-01
forum: Hardware
---

### Post by thomasboleyn on 2008-12-01
Hi there, I currently run Ubuntu Feisty on my Sony Vaio PCG-K215Z notebook (specs here [http://www.laptopsdirect.co.uk/Sony-Vaio-K215Z-PCG-K215Z/version.asp](http://www.laptopsdirect.co.uk/Sony-Vaio-K215Z-PCG-K215Z/version.asp)). Everything runs flawlessly, and I have compiz enabled through a guide I found online, as it is not included by default in feisty. Most of the programs I use I have managed to compile to their most recent versions (Pidgin, transmission, AWN) after a lot of dep satisfying etc. 

Anyway to cut to the point, My laptop won't boot properly with any distro newer than Feisty (anything using a newer kernel) UNLESS I use the boot option 'ACPI=OFF'. If I use this I am able to boot from live cd and install anything including Intrepid. The only problem this leaves me is that my wireless card does not work when I use this boot option. From everything I've gathered from months of googling/asking around, it is to do with the laptop's ACPI being incompatiable with these newer kernels. Another user on here messaged me and advised he had got Xubuntu Hardy working with wireless on the same model laptop, but only with 'nohz=off' and 'highres=off' enabled. I tried this and still had no luck however.

I'm just wondering if there are any further boot options available or anything else generally which I can try.

Any help would be greatly apprecited, thanks.

---

### Post by thomasboleyn on 2008-12-02
Bump :KS

---

### Post by thomasboleyn on 2008-12-04
anyone..?

---

### Post by thomasboleyn on 2008-12-05
Looks like I'm sticking with trusty Feisty..you never really failed me:KS

---

### Post by Rhubarb on 2008-12-05
If you're prepared to do some research, you may be able to compile your own kernel for a more recent version of ubuntu (like Intrepid for example).
There's a good howto detailing how to compile your own custom kernel for ubuntu.

While I haven't had the need to do this myself, I know of others that have, and has worked very well for them.

My wild guess is that it may have something to do with a tickless kernel (in the newer Ubuntu versions).

At the very least, it's good to know that Linux is flexible, and can pretty much be customised to work for you if you're willing to put in a little time yourself.

Hope you get it sorted soon enough as I can't be of that much help in this case.
- Rhubarb

---

### Post by thomasboleyn on 2008-12-05
> **Rhubarb said:**
> If you're prepared to do some research, you may be able to compile your own kernel for a more recent version of ubuntu (like Intrepid for example).
There's a good howto detailing how to compile your own custom kernel for ubuntu.

While I haven't had the need to do this myself, I know of others that have, and has worked very well for them.

My wild guess is that it may have something to do with a tickless kernel (in the newer Ubuntu versions).

At the very least, it's good to know that Linux is flexible, and can pretty much be customised to work for you if you're willing to put in a little time yourself.

Hope you get it sorted soon enough as I can't be of that much help in this case.
- Rhubarb

I've never tried anything this advanced, but i'll certainly give it a go, which guide would you suggest is the best? I've had a look at a couple and they both seem a bit too finely tuned for the machines the author was using.

---

### Post by Rhubarb on 2008-12-05
I've never actually compiled a kernel myself, so I can't help you / point you in the right direction there.

I do want to compile a kernel myself, because I have to turn ACPI off for my desktop computer to run Ubuntu.  I know it's a little setting in the kernel that can be changed to make it work - but it's low-priority for me, so I haven't got around to compiling it.

---

### Post by thomasboleyn on 2008-12-05
> **Rhubarb said:**
> I've never actually compiled a kernel myself, so I can't help you / point you in the right direction there.

I do want to compile a kernel myself, because I have to turn ACPI off for my desktop computer to run Ubuntu.  I know it's a little setting in the kernel that can be changed to make it work - but it's low-priority for me, so I haven't got around to compiling it.

Does having ACPI off have any consequences for you? I tried to install the apps needed to start compiling the kernel using this guide [http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/](http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/) but there's something up with the feisty servers at the moment so I'll try again later.

Thanks for getting back to me.

---

### Post by Rhubarb on 2008-12-06
The only consequences I have when ACPI is off, is that my computer is unable to turn itself off.
When I shutdown the computer, it does all the shutting down business, but is unable to do the actual turn off bit - as if it tries to turn off, but can't.
Just like an old 286 computer, you have to press the power button for it to turn off.

I'm sure it'd have other power related problems, like not being able to suspend / hibernate.

Apart from those small issues, it runs fine, and has been running fine for the past 1+ years.

---

