---
title: "Need help with gparted &amp; my drives"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by davewickett on 2009-08-01
[attach]123224[/attach]     " GPARTED IMG "

need help i have ubuntu & vista on my c drive i gave ubuntu something like 13 gb & i want to add some more space to it from vista but dont know witch 1 is witch & i have my d drive witch is hp recovery & want to add that 1.66 gb to ubuntu that is not being used i have a hp dv5 with 3 gb ram & 250 gb hd ubuntu is quick now & vista is starting to get slow how much more space can i give to ubuntu all i want vista for is so if something went wrong with ubuntu ill have vista to get on the net & try to fix it i have downloaded gparted live iso ready if anyone could help me with this please thanks
dave:ks:ks:ks

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e8499e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27154   218114473+   7  HPFS/NTFS
/dev/sda2           29182       30401     9797632    7  HPFS/NTFS
/dev/sda3           27155       29181    16281877+   5  Extended
/dev/sda5           28856       29159     2441848+  83  Linux
/dev/sda6           29160       29181      176683+  82  Linux swap / Solaris
/dev/sda7           27155       28777    13036684+  83  Linux
/dev/sda8           28778       28855      626503+  82  Linux swap / Solaris
[ATTACH]123224[/ATTACH]

---

### Post by merlinus on 2009-08-01
You might find some useful info here:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by davewickett on 2009-08-01
Ok thanks alot mate really helped me out thanks ill have a good read over it in a bit this will help so many other people out aswell ""good job"":D:D:D

---

### Post by davewickett on 2009-08-01
> **merlinus said:**
> you might find some useful info here:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
ok the only thing i dont understand is why do i have 2 swap & 2 ubuntu partitions

---

### Post by merlinus on 2009-08-01
Dunno, but looks like you can delete sda5 and sda6 and add the space to sda7.  IIRC the step-by-step guide will help you to do this.

If not, post back.

---

### Post by raymondh on 2009-08-01
> **davewickett said:**
> ok the only thing i dont understand is why do i have 2 swap & 2 ubuntu partitions

Did you install Ubuntu twice?  As merlin says, you look at removing 5 and 6.

---

### Post by davewickett on 2009-08-01
I installed ubuntu from a ubuntu cd where it goes through it with you & i just done side by side & gave ubuntu 13gb
WITH WHAT I HAVE PUT UP CAN YOU NOT TELL ME WHAT I HAVE TO DO WITH WITCH ONES PLEASE I THINK I MIGHT FIND IT A BIT HARD AS I HAVE TO BOOT FROM ISO ASWELL

---

### Post by merlinus on 2009-08-01
What about using gparted live:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You can burn it to a cd or usb flashdrive.  It is a very small download.

---

### Post by davewickett on 2009-08-01
yes i do have it but just dont want to mess anything up thats all

---

### Post by merlinus on 2009-08-01
It is a bit complicated, but here are the steps.

Boot from gparted.  Delete sda5 and sda6.  Click on sda8 and select swapoff.

Then you can grow sda7 into the freed-up space, leaving room for a swap partition of about 1.5G.

There are screenshots at the gparted website to help, as well as at the link I gave in an earlier post.

As always, back up important data first.

---

### Post by davewickett on 2009-08-01
Thanks alot mate thats wicked anyway ill be ok with that i think ill give it a go & post what happend anyway  so thanks for all your help 
dave

---

### Post by merlinus on 2009-08-01
Best of luck, and let us know how it turns out.

---

### Post by davewickett on 2009-08-01
Thanks there is one thing on sda5 there is 2.33gb and 2.33gb used so if i delete that one is there something important on that,that i will need.you said to delete sda5 and 6 and then add them 2 sda7 but how do i add them plz? Mate thanks for all the help you have given me and i will let you no how i get on thanks again mate.

---

### Post by merlinus on 2009-08-01
Before deleting anything, make sure you have backed up important data.

As for resizing, there are menus, and arrows that you can move to grow a partition, but the freed-up space has to be touching it.

If you follow my steps, this will work.

---

### Post by davewickett on 2009-08-01
Ok ill write all your steps out & have a go mate thanks post results 2morrow

---

### Post by merlinus on 2009-08-01
Sounds good.  If at any time in the process you are uncertain, and unwilling to risk creating problems, post back before doing anything further.

And once again, be sure to back up important data first!

---

