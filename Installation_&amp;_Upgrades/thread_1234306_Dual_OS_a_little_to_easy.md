---
title: "Dual OS a little to easy ?"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Sticks_uk on 2009-08-07
Ok so after reading up to see if my system hardware was on the HCL I decided to try a linux distro and opted for Ubuntu.

I'm a very concerned to how easy to install it was.

I installed inside windows and assume some how it compiles your drivers and such to enable you to run ubuntu straight away ?

I was thinking of getting rid of xp completely but I am very doubt full it would be as easy on a fresh install. Am I right ? 

My main concern is not being able to get on the internet if I do a clean install

Sorry for my waffling I am sure there is a question in there somewhere :)

---

### Post by Soley on 2009-08-07
If you're leary of Ubuntu not working with your computer, I would try the 9.04 live disc & see how that goes. I haven't run into any issues with 9.04 as of yet. It's worked perfectly on my wife's laptop when her windows install went haywire & it works perfectly on my computer. I also tested an old wireless dongle I had lying around today & it recognized it right off the bat.

---

### Post by _Slike_ on 2009-08-07
> **Sticks_uk said:**
> Ok so after reading up to see if my system hardware was on the HCL I decided to try a linux distro and opted for Ubuntu.

I'm a very concerned to how easy to install it was.

I installed inside windows and assume some how it compiles your drivers and such to enable you to run ubuntu straight away ?
Most modern day "easy to use" Linux versions like Ubuntu come with built in support for tons of devices.
If you're able to run Ubuntu successfully from the live cd, you shouldn't worry about anything concerning your hardware. 

Personally I haven't had any pc yet that wasn't able to run Ubuntu properly ;)


> **Sticks_uk said:**
> I was thinking of getting rid of xp completely but I am very doubt full it would be as easy on a fresh install. Am I right ?
You can always install both operating systems next to each other. You don't *have to* ditch Windows in order to have/use Ubuntu.

As always, make sure you've made a backup of all the important data you don't want to lose before making any changes to your hard drive!

If you're very unsure, and you wish to simulate an Ubuntu install, you can always use a spare pc, or Sun's free [VirtualBox]("http://www.virtualbox.org/") to try it out in advance, without any risk.

> **Sticks_uk said:**
> My main concern is not being able to get on the internet if I do a clean install
If you install Ubuntu (on to your harddisk) while using the live cd environment, you'll even be able to go online while installing!

Good luck!

---

### Post by tgalati4 on 2009-08-07
Your concerns are valid.  It's easy to screw up.  Some people accidently delete windows with all their music and photos on it (no backup of course).  Keep a valid backup of your data, proceed carefully, read the instructions, and keep a 2nd machine handy with net access when you get stuck.

My quickest installation was 14 minutes.  Yours will be longer, but yes it is easy.

---

### Post by Sticks_uk on 2009-08-08
thanks all for the replies, just wondering if there is a way to make my PC boot in to ubuntu by default(by having it at the top of the boot up list) as at the moment I have to select ubuntu from the boot up list as it is on the bottom.

hope this makes sense

---

### Post by tgalati4 on 2009-08-08
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
sudo nano /boot/grub/menu.lst

Change the value of:

default  0

default 0 is the first operating system,  default 1 is the second etc.

timeout 7 can be changed to timeout 10 to give you more time to watch the grub screen.

Yes, you can change the order as well, just be careful that you cut and paste all of the entries for a given OS.  Mistakes here mean that you won't boot.

---

### Post by harry2006 on 2009-08-08
the best bet to learn/try a linux distro is to try the liveCD version of that flavor, now almost all popular linux flavors have their liveCD versions. first try that out and go for a full installation if everything works fine in the live version, and yes have a backup of your data, b'coz if thats gets lost no one can help you get that back.

---

