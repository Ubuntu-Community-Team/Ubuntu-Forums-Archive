---
title: "Accidentally clicked &quot;entire disk&quot; in installation enviroment"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by zepita on 2009-05-07
Hello great community,

I was trying to install Ubuntu 9.04 in my laptop and when I got to the partitioning step the installation environment was not able to "see" my windows partitions, it just said in the upper bar "No OS detected"

So I went to manual partitioning, (as I always do ) but I found out that any of my 2 ntfs partitions were detected.
I went back and accidentally selected "entire disk" and pressed forward.

I went back one screen and the disks looks like this (I think I lost my partitions)

[[IMG]http://img216.imageshack.us/img216/373/screenshotpbl.th.png[/IMG]](http://img216.imageshack.us/my.php?image=screenshotpbl.png)

[[IMG]http://img218.imageshack.us/img218/737/screenshot1h.th.png[/IMG]](http://img218.imageshack.us/my.php?image=screenshot1h.png)


I managed to open firefox and I'm still inside the installation environment.

Your help will be very appreciated

---

### Post by abn91c on 2009-05-07
if you haven't gone forward from this step to format the drive, cancel this step and see if you can mount the drives first then run the setup again,

---

### Post by zepita on 2009-05-07
> **abn91c said:**
> if you haven't gone forward from this step to format the drive, cancel this step and see if you can mount the drives first then run the setup again,

Thanks abn91c, when I made my mistake I did press forward and went back to see ubuntu 9.04 showing in the lower bar.. 
Do you think I have any chances to get my partitions back?

---

### Post by HyRax on 2009-05-07
The changes you make are not committed to disk until it warns you and you click YES, so until then you should be able to click that "Undo" button in the second pic and it should re-read your current drive configuration.

---

### Post by benj1 on 2009-05-07
have you actually finished the installation?
i can't remember if formatting is done end the end or part way through, if it is part way through it would take a good amount of time so you would know.

anyway if the installation isn't done you should just be able to cancel it without any harm. try rebooting to find out.

if it is reformatted you could try and recover the files, im not sure what program to use but some body will know, just don't install ubuntu until you've tried that.

---

### Post by zepita on 2009-05-07
I tried first one of the recommendations to "undo" the changes but it did not work, so I cancelled the installation and got back to ubuntu live cd.
I was pleased to see my patitions and mount them normally :) I'm backing up everything to dvd just in case..
Hopefully it was a false alarm and I'm almost sure when I restart it will boot the other OS.
For now I will keep using the live-cd until I findout how to use some work-related stuff in linux so I can "upgrade" to this wonderful OS

Thanks for all the replies guys!

---

### Post by gamblor01 on 2009-05-07
Just FYI, if you ever want to see what partitions are on your hard drive(s) just run the following command:

```

sudo fdisk -l

```

That's a lowercase 'L' by the way.

---

