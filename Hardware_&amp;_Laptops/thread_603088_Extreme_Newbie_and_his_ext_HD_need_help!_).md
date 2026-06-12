---
title: "Extreme Newbie and his ext HD need help! :)"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by Revfisk on 2007-11-04
Newbie here,

I am trying to mount a Rock HD1-Series-RB external hard drive to my laptop running Gutsy. Most the other posts seem able to run a "fdisk -l" command and see their ext. hard drive, but I've not been able to get that far. (The command runs a blank line.)

A step by step command prompt tutorial running me  from getting this thing working to begin with, to, if possible, auto-mounting to the desktop at USB plugin, would be** great**. (I do have USB hot pluggins enabled and my flash drive works fine.)

I have not run any formating programs on the HD, but my Windows desktop does access it, and I have put back up files on it.  

Any help would be appreciated.

---

### Post by ROBarber on 2007-11-05
Hi.
maybe this will help you
[http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/]("http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/")
(thx to Harpoon)

it's strange that fdisk -l doesn't show anything to you

---

### Post by Revfisk on 2007-11-05
Thanks, but that link is WAY over my head.   

And yes...I apparently have no f-disk at all.  I'm not sure what that means, but the response to 

sudo f-disk -1 

comes back

command not found

---

### Post by bingoUV on 2007-11-05
> **Revfisk said:**
> Thanks, but that link is WAY over my head.   

And yes...I apparently have no f-disk at all.  I'm not sure what that means, but the response to 

sudo f-disk -1 

comes back

command not found

```

sudo /sbin/fdisk -l

```

---

### Post by Revfisk on 2007-11-05
Thanks!.  That's a start! :D

---

### Post by ROBarber on 2007-11-06
post the result here ;)

---

### Post by Revfisk on 2007-11-06
Well...it works now, though not because of the advice.  Essentially, the trouble lay with the fact that the usb cable had TWO male ends, one primary, the other secondary.  I was plugging in the secondary, which, a discovered, does not work in windows either.  The primary auto-mounts to the Ubuntu desktop.  So...at least we now know this device is a solid goal ext HDD for Gutsy.  

I recommend it.  Not too expensive, VERY portable and powered through the USB.  For anyone working with an Ubuntu laptop and a Windows desktop/network, it is a an excellent way to keep all your files in one place, accessible from all of your computers/OS's.

Thanks for you paying attention!

---

