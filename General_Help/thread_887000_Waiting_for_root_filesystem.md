---
title: "Waiting for root filesystem"
date: 2008-08-11
forum: General Help
---

### Post by jmacdallas on 2008-08-11
Hi, I'm pretty new to this and I've spent days on this one problem. 

My Ubuntu 6.06 install runs as a server, without a screen. So the other day I turned it off without shutting down because I was to lazy to press the KVM button (arg!). Then when I turned it back on - it hangs at the 
Waiting for root filesystem line.

Then it drops me to a Busybox prompt. 

I don't know what to do from there. I can boot from the liveCD and I played around with fstab and menu.list (the device names didn't line up at all) but it's had no effect. 

Please tell me there's something terribly simple that I'm missing? 

Thanks.

---

### Post by oldos2er on 2008-08-11
Boot from the live CD and run fsck on your hard disk.

---

### Post by jmacdallas on 2008-08-12
Hi oldos2er, thanks for the help. 

But I don't know if I'm doing something wrong. I am using the Hardy Heron live CD because I can't find my 6.06 CD. 

I select the Try Ubuntu Without Making Changes... option from the boot menu and then boot into a desktop. I open a console and type *fsck* and the ouput only looks like a version number and a date. (I can't remember what it said, I'll check tonight after work.)

Surely I need to log into my problematic drive or something? 

Thanks for the help so far.

---

### Post by nazish on 2008-08-12
in the grub menu you have an entry called as Ubuntu (Recovery Mode) log into that and run the fsck command .
It ll solve ur problem.

---

### Post by oldos2er on 2008-08-12
You would want to run something similar to "fsck /dev/sda" or whatever the partition is named.

---

### Post by jmacdallas on 2008-08-12
> **nazish said:**
> in the grub menu you have an entry called as Ubuntu (Recovery Mode) log into that and run the fsck command .
It ll solve ur problem.

Yeah, I tried that - but I can't even log into the recovery console! It gives the same error, waiting for root filesystem. :s

---

### Post by jmacdallas on 2008-08-12
> **oldos2er said:**
> You would want to run something similar to "fsck /dev/sda" or whatever the partition is named.

The fsck command worked. It said something about cleaning the disk. But when I rebooted, I still got the same error! :s

I'm getting pretty desperate. Short of reinstalling from sratch, I'm willing to try anything! 

Is there some way that I can reinstall or something without losing my config and current filesystem. Took me ages to set this up the way it was.

---

### Post by jmacdallas on 2008-08-13
Bump.

Any ideas?

---

### Post by oldos2er on 2008-08-13
Try it again. "fsck -a /dev/sda"

---

### Post by bodhi.zazen on 2008-08-13
> **nazish said:**
> in the grub menu you have an entry called as Ubuntu (Recovery Mode) log into that and run the fsck command .
It ll solve ur problem.

NOOOOO !!!

Do NOT run fdisk on mounted partition. You need to run it from a live CD.

You need to know your Ubuntu partition, sda1 ??

```
sudo e2fsck -C0 -p -f -v /dev/sdxy
```

        if that fails

```
sudo fsck -fvy /dev/sdxy
```

 Where sdxy is your Ubuntu root partition , sda1 for example.

---

### Post by jmacdallas on 2008-08-13
Thanks for the help so far guys - it's **really** appreciated.

> sudo e2fsck -C0 -p -f -v /dev/sdxy

The above command ran something like a filesystem check and reported that everythinh was ok, but when I booted, I got the same problem. It says that it can't find dev/sda1/ 

I loaded gparted and made sure that the name of the FS was dev/sda1/ and then I checked that fstab and boot/grub/menu.list agreed (they didn't, so I changed them - and now everything **looks** right but it's still not working.

Am I missing something?

---

### Post by bodhi.zazen on 2008-08-13
From what you have posted, could it be a few simple typos ?

You need a leading /

/dev/sda1 (not dev/sda1)

/boot/grub/menu.list (not boot/grub/menu.list)

---

### Post by aleks_ja on 2008-08-14
I had the same problem after updated Breezy->Dapper->Hardy.

Tried fsck - but the problem was totally different. During my upgrade from Dapper to Hardy I had some errors and it stopped several times, then I removed some packages, forced install etc.

So... I ran dpkg-reconfigure -a from older kernel and it worked for me. Though after that gnome didn't want to load, and it used gnome-desktop-enviroment that was missing in Hardy, I installed ubuntu-desktop instead. And that's it, right now only network-admin doesn't want to switch to administration mode and some minor error appears saying something about USB.

dpkg-reconfigure -a

---

### Post by jmacdallas on 2008-08-17
Hey guys,

I've tried everything suggested here and a few more tricks - but nothing. 

Thanks for the help but I guess I'm going to have to reinstall. :(

---

