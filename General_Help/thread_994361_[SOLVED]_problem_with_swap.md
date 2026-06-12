---
title: "[SOLVED] problem with swap"
date: 2008-11-26
forum: General Help
---

### Post by TheMyself on 2008-11-26
I turned swap off by mistake and now it's "unknown".  When I use gparted to format it as swap and swapon, it doesn't stay so. I mean when I hibernate and then restart, it restarts from beginning (my session is gone) and now swap partition is again "unknown". Any help? I know that I should update some file in ./etc but don't now exactly.

---

### Post by Waappu on 2008-11-26
Hi

When you "re-created" swap it have now new UUID.
You need change /etc/fstab file to point right place.

Look line like this
```
UUID=8f99c8f6-0cc6-4704-a645-87920c46178c none            swap    sw              0       0
```

---

### Post by jenkinbr on 2008-11-26
I am willing to bet that when you turned swap off, you also removed the record of it form /etc/fstab.

Run the command ```
cat /etc/fstab
``` and post it's output here.

EDIT: or just do what Waapu said...

---

### Post by TheMyself on 2008-11-26
Hi

No, I hadn't  done such a thing.  Now I used vol_id to get the UUID and edited fstab accordingly. Now swap is on and system recognizes it. When I hibernate, HDD led is on for a while which means (I think) Ubuntu saves my session. But when I turn on the computer, I'm back in the first square.

---

### Post by kerry_s on 2008-11-26
> **TheMyself said:**
> Hi

No, I hadn't  done such a thing.  Now I used vol_id to get the UUID and edited fstab accordingly. Now swap is on and system recognizes it. When I hibernate, HDD led is on for a while which means (I think) Ubuntu saves my session. But when I turn on the computer, I'm back in the first square.

now you need to tell it where to resume from, you can add the kernel line "resume=/dev/?" (i think) or there might be a setting for the program used to hibernate, for example: i uses s2disk the settings in /etc/uswsusp.conf

---

### Post by TheMyself on 2008-11-27
I think I now know what the problem is. When I installed Linux, my laptop's RAM was 500MB and Ubuntu set swap to 1.4 GB but later I upgraded RAM to 2GB. I guess Ubuntu can't save all the RAM although I normally use less than 1GB of RAM. Do you think this is correct? Thanks.

---

### Post by Bucky Ball on 2008-11-27
Adding the RAM should make any difference. In fact, with more RAM you are less likely to need a swap at all.

---

### Post by TheMyself on 2008-11-27
Hello Bucky Ball. My problem is that I can't hibernate Ubuntu and it uses swap to save the session when hibernating. My swap is now on, just I can't hibernate.

---

### Post by Bucky Ball on 2008-11-27
You may want to start a new thread with this new problem as it doesn't pertain to the title of this one. You will have more luck getting help. :)

---

### Post by CatKiller on 2008-11-27
> **TheMyself said:**
> I think I now know what the problem is. When I installed Linux, my laptop's RAM was 500MB and Ubuntu set swap to 1.4 GB but later I upgraded RAM to 2GB. I guess Ubuntu can't save all the RAM although I normally use less than 1GB of RAM. Do you think this is correct? Thanks.

That seems like a reasonable assumption.

---

### Post by skymera on 2008-11-27
Depending on how much RAM you have you might never touch the swap.

Over 2 years of *Buntu-ing and never used the swap.

---

### Post by Elfy on 2008-11-27
+1 - check the swap size - make it a little bigger than ram - make sure /etc/fstab has correct UUID

Then also check /etc/initramfs-tools/conf.d/resume
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
that also has to be the same UUID, if you've had to change it you also need to run this command

```
sudo update-initramfs -u
```

edit - @skymera - to hibernate I believe swap must be equal or greater than RAM

---

### Post by TheMyself on 2008-11-29
Hi. I did what forestpixie said and it works now. Thank you!

---

