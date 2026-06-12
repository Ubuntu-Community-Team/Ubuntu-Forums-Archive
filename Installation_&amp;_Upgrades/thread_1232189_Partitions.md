---
title: "Partitions"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2009-08-05
Hello

I want to change my Ubuntu 32 bit to 64 bit version.
At the moment I have to OSs: XP (~480 GB) and Linux (~20 GB).
Recently I use second one more often so I need more space.
I'd like to remove my current Ubuntu, take it's partitions, add 100-150 GB from XP and install new 64 bit version on it.
Is it possible to take away only free space from Windows, cuz I don't wanna loose any files.

That's how my GParted looks like.
[http://img14.imageshack.us/img14/1299/screenshotoyy.png](http://img14.imageshack.us/img14/1299/screenshotoyy.png)

Here you can see Ubuntu's 64 bit CD Partitioner.
[http://img136.imageshack.us/img136/1408/99741048.jpg](http://img136.imageshack.us/img136/1408/99741048.jpg)
[http://img268.imageshack.us/img268/4194/35000082.jpg](http://img268.imageshack.us/img268/4194/35000082.jpg)
[http://img268.imageshack.us/img268/6056/91512044.jpg](http://img268.imageshack.us/img268/6056/91512044.jpg)
[http://img14.imageshack.us/img14/2795/66139686.jpg](http://img14.imageshack.us/img14/2795/66139686.jpg)
[http://img14.imageshack.us/img14/9651/12215291.jpg](http://img14.imageshack.us/img14/9651/12215291.jpg)
[http://img14.imageshack.us/img14/9291/17810399.jpg](http://img14.imageshack.us/img14/9291/17810399.jpg)

Can anyone help me with this?

Regards
Jet

---

### Post by ibuclaw on 2009-08-05
Please don't directly post images larger than 300x300 into the thread, just attach them as a thumbnail or link.

Regards
Iain

---

### Post by jet-san on 2009-08-05
Sry 'bout that.

---

### Post by ibuclaw on 2009-08-05
> **jet-san said:**
> Sry 'bout that.

No problem, it can just be a nuisance for those of us who don't have a 3000x3000 screen resolution ;)


Anyways, for your problem, I advise that you boot into Windows, and run a defragmenter on the 400GB NTFS partition.

Once complete, reboot with the Ubuntu LiveCD in your CD tray and when it loads up, go to '**System -> Administration -> Partition Manager**'

Select the 400GB NTFS filesystem and select '**Resize/Move**', then shrink it to 300GBs.

Then select the new empty space and select '**New**', and create a 'ext3' filesystem.

Once complete, press '**Apply**' to action those changes.

Close the Partition Manager and continue to Install Ubuntu.

In the step where you are asking to '**Prepare disk space**', select the option: '**Specify partitions manually (advanced)**'

From there you can set the following to the partitions:
```

**Partition    Mount         Use as    Format**
/dev/sda5    /media/disk   ntfs      NO
/dev/sda6    /             ext3      YES
/dev/sda8    /home         ext3      YES

```

It won't look exactly like that, but you should see the general jist of things there.

Regards
Iain

---

### Post by jet-san on 2009-08-06
Ok, I'll try it tomorrow.

Thanks!
Jet

---

### Post by jet-san on 2009-08-09
I've done it.

Is my SWAP big enough?
[http://img246.imageshack.us/img246/263/gparted.png](http://img246.imageshack.us/img246/263/gparted.png)

I have a question about the Mount point.
[http://img190.imageshack.us/img190/6743/preparation.png](http://img190.imageshack.us/img190/6743/preparation.png)
What should I choose and what does it mean?

Regards
Damian

---

