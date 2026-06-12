---
title: "Problems installing"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by kane77 on 2009-04-30
To describe the situation:
Lately I have been trying to install Jaunty (I was running Hardy on that computer until now), but whatever I do it fails to install and the installation freezes at about 22-28% of copying files. Now I tried to install Hardy again, but even that now fails to install for some reason. I tried lot of things: installing Jaunty from livecd, alternate, usb-drive, installing Hardy from alternate and usb-drive and I tried all of previous with acpi=off and/or noapic. I have tried to change BIOS configuration, but no matter what I do I still get that error. I tried scanning disk using Partition Manager in Windows and using badblocks in livecd, but they all finish successfully. 

**Can anyone suggest any thing I should try to install some version of ubuntu?**

It is my dad's computer and he got used to ubuntu :)

---

### Post by dandnsmith on 2009-04-30
Sounds to me like it's possible that the CD drive is showing the first signs of failure - I once spent a couple of weeks trying to install with this sort of failure, tried a new drive and it worked instantly.

Unfortunately it isn't easy to diagnose - especially where all the hardware tests work, so you don't believe its possible. I'd try a RAM 'soak test' with memtest first - just to show if any other funnies are there.

---

### Post by kane77 on 2009-04-30
> **dandnsmith said:**
> Sounds to me like it's possible that the CD drive is showing the first signs of failure - I once spent a couple of weeks trying to install with this sort of failure, tried a new drive and it worked instantly.

Unfortunately it isn't easy to diagnose - especially where all the hardware tests work, so you don't believe its possible. I'd try a RAM 'soak test' with memtest first - just to show if any other funnies are there.

you might be right actually, because the only thing I changed since last installing ubuntu was the cd/dvd drive and I tried installing from usb drive, but only alternate cd and that needs cdrom and cd inside..

---

### Post by kane77 on 2009-04-30
> **dandnsmith said:**
> Sounds to me like it's possible that the CD drive is showing the first signs of failure - I once spent a couple of weeks trying to install with this sort of failure, tried a new drive and it worked instantly.

Unfortunately it isn't easy to diagnose - especially where all the hardware tests work, so you don't believe its possible. I'd try a RAM 'soak test' with memtest first - just to show if any other funnies are there.

Hey! You were actualy right!! What I did was created USB Startup disk, physically unplugged my DVD drive and booted and installed ubuntu from USB stick.. So THANK YOU! I spent almost week (with some pauses) trying to install ubuntu and now thanks to your advice it is done.. All is well :)

---

### Post by dandnsmith on 2009-05-02
Glad to hear of your success.

---

