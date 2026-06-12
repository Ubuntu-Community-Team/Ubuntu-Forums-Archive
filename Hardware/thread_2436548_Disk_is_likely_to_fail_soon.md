---
title: "Disk is likely to fail soon"
date: 2020-02-08
forum: Hardware
---

### Post by ts1971 on 2020-02-08
Hi,

I've been a very casual user of UBUNTU for a couple of years and last night I was prompted to upgrade to 18.04 from 16.whateverIwason and I kicked off the process and went to bed.  When I woke up this morning, the process had completed and there was a login screen.  I logged in and the first thing that popped up was an application with the message in the title.  Here is the whole screen:



I really have no idea how seriously I should take this.  Can someone tell me what program is generating this message and what I can do to get further information?

Thanks!

---

### Post by ts1971 on 2020-02-08
It appears as though I can't get the image to display.  I'm not sure why; I've tried with both dropbox and flickr.  I've tried a couple of free image hosting sites,but this doesn't seem to be as easy as it used to.  Can anyone suggest a good free site for hosting images destined for message boards?

Thanks (again)!

---

### Post by deadflowr on 2020-02-08
Use the forum attachment feature to upload images
[https://ubuntuforums.org/showthread.php?t=1626753]("https://ubuntuforums.org/showthread.php?t=1626753")

---

### Post by CatKiller on 2020-02-08
> **ts1971 said:**
> I really have no idea how seriously I should take this.  Can someone tell me what program is generating this message and what I can do to get further information?

You should take it seriously. Modern hard drives test themselves periodically through a mechanism called SMART so that you can get an early warning before (some) failures and have a chance to switch to a replacement on your own schedule rather than when the drive is already dead. You can use the *smartmontools* package to read all the information that the drive gives from its tests. Replacement drives are pretty cheap as computer components go.

---

### Post by TheFu on 2020-02-08
Disks have a built-in health check system, called SMART.  There are a few tools which look at SMART data, gnome-disks is one. I prefer **smartctl**, which is used on servers that don't have any GUI and provides the raw data. The raw data provides incite that gnome-disks doesn't.

However, you should take any warning like that very seriously.  Backup anything you don't want lost and plan to replace the disk ASAP.  Chances are there is already significant data lose.  Then I'd use smartctl to see how bad things are.  Lots of examples in these forums.

---

### Post by ts1971 on 2020-02-08
Thank you!

---

### Post by ts1971 on 2020-02-08
> **deadflowr said:**
> Use the forum attachment feature to upload images
[https://ubuntuforums.org/showthread.php?t=1626753](https://ubuntuforums.org/showthread.php?t=1626753)

Thank you!  I feel silly for not seeing that earlier.  Or rather for seeing it, but dismissing it for some reason.  I could have saved myself an hour spent creating free accounts in image hosting sites, none of which seem to provide the basic service of allowing me to share publicly share an image.  Anyway, thanks again!

---

