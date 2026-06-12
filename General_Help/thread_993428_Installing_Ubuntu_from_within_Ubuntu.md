---
title: "Installing Ubuntu from within Ubuntu"
date: 2008-11-25
forum: General Help
---

### Post by ItsJweed on 2008-11-25
I will soon be getting a 16gb flash drive and I'm going to be installing Ubuntu on it. I would like to be able to use it to install Ubuntu on whatever computer I've booted it from. Is this possible?

---

### Post by john183 on 2008-11-25
yes it is very possible. search the forums for live usb. on second thought you could just search for posts by me, i think there are about five different threads regarding this subject that i have posted on.

---

### Post by ItsJweed on 2008-11-25
> **john183 said:**
> yes it is very possible. search the forums for live usb. on second thought you could just search for posts by me, i think there are about five different threads regarding this subject that i have posted on.

I searched through your posts but didn't find anything relevant to this. I don't plan on putting the "Persistent Live CD" version of Ubuntu on the flash drive; I would like to actually install Ubuntu on it and then use that normal installation to install again on other drives.

For example, I'm currently running Ubuntu on my PC. Lets say I wanted to install Ubuntu on my external hard drive so that I could boot from it. How would I go about doing this?

(If you did talk about this in one of your threads, please point me in the right direction.) Thanks,

Jon

---

### Post by decard_pain on 2008-11-25
theres a program called unetbootin that can make the live usb's
in ubuntu 8.10 i think theres a live usb creator either in the repo or on the live cd itself.
but I've found unetbootin to work best as it can be done from windows or linux.
if you do it in linux remember to mount the usb before running unetbootin

hope this helps

---

### Post by ItsJweed on 2008-11-25
> **decard_pain said:**
> theres a program called unetbootin that can make the live usb's
in ubuntu 8.10 i think theres a live usb creator either in the repo or on the live cd itself.
but I've found unetbootin to work best as it can be done from windows or linux.
if you do it in linux remember to mount the usb before running unetbootin

hope this helps

I looked into UNetBootin (I've actually used it before) and I see I can use it to install Ubuntu on a computer without using the CD drive. It requires a reboot though, and that was what I was trying to avoid. Specifically here is what I would like to do:

Boot from my flash drive which contains Ubuntu (the actual operating system - not the "Persistent LiveCD" version) and then install Ubuntu on another drive or partition. You know how in the LiveCD there is the link on the desktop to run the installer? Is it possible to get the same installer on an actual Ubuntu system?

---

### Post by john183 on 2008-11-26
When you setup a thumb drive with a persistant live version of ubuntu, it is just like installing to actual os on the thumbdrive. Granted there are a few things you can't do such as kernel upgrades, but other than that you can install/remove whatever software you need. then you also get the option to install ubuntu just as you can from a liveCD. I guess, in theory you can actually install ubuntu to a thumbdrive, but i believe that you will have issues booting it do to GRUB not being on the computer.

---

### Post by ItsJweed on 2008-11-27
> **john183 said:**
> When you setup a thumb drive with a persistant live version of ubuntu, it is just like installing to actual os on the thumbdrive. Granted there are a few things you can't do such as kernel upgrades, but other than that you can install/remove whatever software you need. then you also get the option to install ubuntu just as you can from a liveCD. I guess, in theory you can actually install ubuntu to a thumbdrive, but i believe that you will have issues booting it do to GRUB not being on the computer.

I got the drive today today, and it boots just fine with Ubuntu installed on it. I installed GRUB on the drive. I've had the live version on a flash drive before but I'm bothered by not being able to do kernel updates. In addition, it seems like it uses a persistence file to keep track of changes rather then actually writing them to the filesystem. This means a significant performance hit. I'm writing from the flash drive right now and it boots and runs much faster then LiveCD versions have in the past. In addition I noticed that removing software on the persistent LiveCD version doesn't free up any drive space - which is frustrating.

Moral of the story is that I'm very happy with my new flash drive and portable Ubuntu but I'm still hoping to be able to figure out if it's possible to install from it. Thanks for you responses so far though.

---

