---
title: "Partition problem need to reallocate memory..."
date: 2008-07-17
forum: General Help
---

### Post by wbutchart on 2008-07-17
Hi i run ubuntu.  I installed xubuntu earlier to test it as i was thinking of installing it on a old computer.  The problem is that even through i said to use only 8GB xubuntu took every spare GB my hard drive has.  I have removed xubuntu now via the partition editor that i downloaded.  The problem is i cannot reallocate the memory back to my ubuntu installation.....it doesnt have the option to do that.  Anyone know how i can transter the memory back?  Thanks.

---

### Post by pmlxuser on 2008-07-17
can you be specific what you did and what you mean realocate memory.
I know that xface can be installed on an already exising ubuntu installation. so what did you actually do.

---

### Post by wbutchart on 2008-07-17
I installed xubuntu by partitioning my hard drive via the install cd.  It was meant to take 8GB (of my 40 GB) but it took every spare GB.  I have now removed the xubuntu installation by the spare Gb (29GB) is sitting unallocated and i cannot use it for my ubuntu.  I need to reallocate it to the root ubuntu installation but it wont let me do that.

---

### Post by Elfy on 2008-07-17
You can do 2 things here - either add it to the existing partition or make a standalone partition to use for data or something.

If you want to add it to your existing installation then you have to do it with a livecd in order that your installation isn't mounted.

Incidentally the second option will be a few minutes at most :)

---

### Post by evets25 on 2008-07-17
You want the gparted live CD - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) .

Download that, burn it to a CD, boot from it, and then you can use Gparted to resize your partition to take up the rest of the free space. Gparted might also be on the ubuntu live CD, I'm not sure. At any rate, the gparted live CD is a small download, and it boots faster than the ubuntu live CD. It's one of those things that everyone should have a copy of! :)

---

### Post by snowpine on 2008-07-17
> **evets25 said:**
> You want the gparted live CD - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) .

Download that, burn it to a CD, boot from it, and then you can use Gparted to resize your partition to take up the rest of the free space. Gparted might also be on the ubuntu live CD, I'm not sure. At any rate, the gparted live CD is a small download, and it boots faster than the ubuntu live CD. It's one of those things that everyone should have a copy of! :)

GParted Live CD is a great suggestion. GParted is also, indeed, on the Ubuntu Live CD, if you already have one of those lying around. As was already mentioned, you can't resize a partition if it's in use, which is why you need to use the LiveCD. Good luck!

---

### Post by Elfy on 2008-07-17
Another option is partedmagic which has testdisk, photrec and a few others as well in addition get supergrub and you have a good tool set.

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by wbutchart on 2008-07-17
Hi i tried the gparted by using puppy linux via ram.  I was able to change the size of the disk on the sda 2 area however the sda1 section is the one i want to add memory too and it wont let me.  The memory seems to be trapped in the sda2 area and i have no idea how to get it accross.  I tried deleting it, copying and pasting it, tried anything and everything but it wont goto the sda1 section.  Anyone any ideas how to get it to move?.  Thanks.

---

### Post by Elfy on 2008-07-17
If it happens to be inside an extended partition you have to resize the extended partition as well in order that the disk psace is outside.

It's not memory either :)

---

### Post by wbutchart on 2008-07-17
Hi ill try that, not too sure what im doing like lol but ill give it another go.  I really want to avoid reinstalling ubuntu i like how ive got it set up.

---

### Post by Elfy on 2008-07-17
YEa - go for it - once you're in the livecd get the list of menu.lst and possible backups - we can go from there

AS long as you make backups of anything you chnage the situation shouldn't get worse :)

---

### Post by wbutchart on 2008-07-17
Hi i tried that, it didnt work.

My partition layout is - 
/dev/hda1
/dev/hda2
---/dev/hda7
---unallocated
---/dev/hda8
---/dev/hda6
---/dev/hda5
What i need to do is get the unallocated into hda1.  However i cannot resize hda2 it gives me maxamium and minumum as 30 GB (when its using only 8) it wont let me rezise.  I can resize hda7 no problem with the spare gb but not hda1 which is where my ubuntu install is.

Any ideas? gpartition doesnt seem able to do this.

---

### Post by Elfy on 2008-07-17
Open a terminal and do

```
sudo swapoff -a
```

then try again - if you still can't do it - please screenshot gparted and post it (accessories - take screenshot)

Please use the manage attachment tool - make sure you use New Reply button not quick reply

---

