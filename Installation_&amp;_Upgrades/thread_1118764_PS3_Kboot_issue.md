---
title: "PS3 Kboot issue"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by cherry.ghost41 on 2009-04-07
Got everything install but when i get to Kboot it says “no default rootfs was found, or one was found and it didnt contains a message= config file.
if no rootfs was found, you can enter the shell with “sh” exiting wil return you to this prompt. in the shel you can mount your rootfs as /mnt/root/.

then gives me the three reasons why it could of happened. have tried everything, cannot get past this. any ideas?

---

### Post by ditsch on 2009-04-07
Which version are you using now and did you have a prior installation of another Linux/Ubuntu?

---

### Post by cherry.ghost41 on 2009-04-07
I am using 8.10 and I had no prior installations.  I was told i need to reformat everything completely and try it again but i'm trying to avoid that if i can.

---

### Post by ditsch on 2009-04-07
Can you boot when you start the following line at the kboot: prompt?

```
mnt/root/boot/vmlinux initrd=mnt/root/boot/initrd.img root=/dev/ps3da1
```

---

### Post by cherry.ghost41 on 2009-04-07
I am at work right now.  i will try when i get home later.  Will i have to enter that every time?

---

### Post by cherry.ghost41 on 2009-04-07
I would enter all of that in from the shell correct?  as one line?

---

### Post by ditsch on 2009-04-07
> **cherry.ghost41 said:**
> I am at work right now.  i will try when i get home later.  Will i have to enter that every time?

No, you can fix your kboot.conf (if this is the issue you are facing) once you have booted successfully. Please enter that line at the first prompt you get (This should be kboot:_ ).

---

### Post by cherry.ghost41 on 2009-04-07
What do i need to do to fix this once i have booted successfully?

---

### Post by ditsch on 2009-04-07
That depends on what is wrong ;) If you are unsure, you could post your kboot.conf here.

---

### Post by cherry.ghost41 on 2009-04-07
to be completely honest i wouldn't even pretend to know how to do that.  i'm a noob to all this.  i have never used a linux system before.  the code you gave me didn't work.  I guess i am just going to reformat and try again with the alternative ps3 .iso.

---

### Post by cherry.ghost41 on 2009-04-07
Thank you very much for all your help.  i have about 4 different posts about this on a couple different forums and you are the only one that has tried to help.  i appreciate it.

---

