---
title: "Should my Ubuntu be this slow??"
date: 2008-11-20
forum: General Help
---

### Post by pavsid on 2008-11-20
Hi all,

I'm new to Linux and wanted to give it a go for all its benefits and get used to it with the intention of moving over permanently.

My PC is set up for dual boot alongside Vista, 2GB RAM, 2.6Ghz AMD Dual-Core X2 Processor, nVidia 8600GT Graphics Card, Vista is running off an internal 80GB IDE Hard Drive and Ubuntu is running off an internal 300GB SATA II Hard Drive.  I have a swap partition of 8GB (want to upgrade RAM to 4GB soon), a root directory of about 70GB and home directory of about 200GB.  I also have an external NTFS 500GB hard drive which i share between Windows and Linux.

I hate to say it but Vista runs like a dream - it's fast, responsive and smooth, even when there are multiple programs running. However, i'm just not getting the same feeling from Ubuntu. It's most noticeable browsing the internet - firefox just isn't as responsive as it is on Vista.  Changing tabs isn't instant and pages don't seem to load as quickly. It's also apparent when browsing through the filesystem - when you open a directory (whether it be on the internal HD or the external one) then it isn't an instant response like it is in Vista, don't get me wrong, it's not really slow, it just opens up more like a web page rather than a local folder!

Another thing is Apache/PHP/MySQL. I have them installed on Vista as well and when i request a web page held locally the response is instant, however in Ubuntu it doesn't seem to load much quicker than it would if it was live on the net! Surely there must be something wrong here - Apache is made for Linux!

I originally installed 8.04 and then upgraded to 8.10 hoping the speed might improve.

Any help or pointers would be massively appreciated folks, many thanks!

---

### Post by philinux on 2008-11-20
System>admin>hardware drivers.

Is the graphics driver enabled ok.

I have same card and everything fine here.

---

### Post by pavsid on 2008-11-20
> **philinux said:**
> System>admin>hardware drivers.

Is the graphics driver enabled ok.

I have same card and everything fine here.

Yep, using the latest recommended driver!?

Any other ideas? Thanks for your reply

---

### Post by philinux on 2008-11-20
Well, I've got compiz on and when i have say 6 tabs open clicking any renders the page straight away. Hardly any lag at all.

Maybe try turning compiz off for a spell.

---

### Post by pavsid on 2008-11-20
Hi Phil, tried that before as well, no real noticeable difference.

So you don't think it could be the way it's set up then - partitions, dual boot etc..?

I was thinking about trying a reinstall but i've done that before, for a different reason, and can't remember the first install being any faster.

---

### Post by philinux on 2008-11-20
I would have a look in /var/log/messages logfile to see if anything filling up the log.

Have a look at the ```
top
``` command and see if anything hogging resources.

Also look at ```
dmesg
``` for any clues.

I've had problems upgrading in the past but not with firefox's performance.

---

### Post by pavsid on 2008-11-20
Hi Phil,

Had a look, can't see anything that stands out in the log files, there seems to be a lot of processes running though, but to be honest i don't really know what i'm looking for! Would you mind taking a quick look?

log files are too big to upload - 38KB and 324KB! Processes attached

Thanks again

One last thing, things seem to be worst with visual effects turned off - now everything is blocky and stuttering (if you know what i mean)!

---

### Post by philinux on 2008-11-20
Looks fairly normal. i dont run apache or mysql so cant comment on those entries.

---

### Post by pavsid on 2008-11-20
> **philinux said:**
> Looks fairly normal. i dont run apache or mysql so cant comment on those entries.

Damn, was kind of hoping it didn't and at least then i'd be a step in the right direction!

Thanks for all your help anyway Phil, will wait and see if anyone else comes up with anything else, and will search the forums in the meantime

---

### Post by philinux on 2008-11-20
It could be down to the router or the network manager. No my area that. If it works I leave it alone.

Might be worth a specific post in that forum.
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

It will take a while to get replies as it's not as busy as here.
Dont forget to include your full pc and network spec if you do post there.

---

### Post by sedawk on 2008-11-20
Here is something you can try:

* Install avidemux on Ubuntu and on Vista

* Open some video file (350 MB or bigger) 
  and use copy-modus for video and audio to simply create a copy of the
  file.During copying avidemux tells you how many frames it writes
  per second. Is there a big difference between Ubuntu and Vista?

* You can repeat the last step, but do some real action, like
  recoding the video, so your CPU has to do lots of work.
  Check again the speed of recoding on Ubuntu and Vista.

I have an older PC here that works fine on Ubuntu (2000 F/s), but sucks
on XP (200 F/s) - both writing to the same NTFS partition!
(Videos are TV recordings in 320x200,  With a newer PCs I get 
 more than 4000 F/s).

---

