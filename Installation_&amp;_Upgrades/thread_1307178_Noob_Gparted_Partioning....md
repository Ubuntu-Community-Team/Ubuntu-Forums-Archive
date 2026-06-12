---
title: "Noob Gparted Partioning..."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by fedexfrt357 on 2009-10-30
Hey all,
I'm very new to Ubuntu, but fairly familiar with Windows...(enough to know I'm tired of it...) and I am trying to set up a dual boot system on my XP Laptop with Ubuntu 9.04.
I have read many posts here, and think I may have a 'slight' grasp on some of it...:lolflag:

If someone could give me some insight, I would really appreciate it...
I'm attempting to get a system for primarily Ubuntu use, with just enough space for Windows to have a few apps I can run...

Is  this anything close to being something workable with the configuration below...?

[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s86.photobucket.com/albums/k90/killmypc/?action=view&current=Screenshot--dev-sda-GParted.png%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i86.photobucket.com/albums/k90/killmypc/Screenshot--dev-sda-GParted.png%22%20border=%220%22%20alt=%22Photobucket%22%3E%3C/a%3E[/IMG][IMG]http://i86.photobucket.com/albums/k90/killmypc/Screenshot--dev-sda-GParted.png[/IMG]

[IMG]http://ubuntuforums.org/%5BIMG%5Dhttp://i86.photobucket.com/albums/k90/killmypc/Screenshot--dev-sda-GParted.png%5B/IMG%5D[/IMG]
I realize the answer to this is already out there somewhere... but still confused..
Thanks

---

### Post by howefield on 2009-10-30
Looks fine, 10 gig for swap is excessive though, but won't do any harm. You probably only the size of the swap partition to be about 1 times your ram. (2 x your ram max)

---

### Post by fedexfrt357 on 2009-10-30
Thanks for the quick reply...:D
I'll shrink it to 5G...

---

### Post by fedexfrt357 on 2009-10-30
Well.... I went to install and a "Ubuntu 9.04" at 2.5G was added... is this going to be as issue...? Should I increase this size..? Guess I should have set that up in Gparted huh?

Can I just go back into Gparted and give a label of Ubuntu 9.04 to a partition, and size it myself.... and it work...lol ?

---

### Post by howefield on 2009-10-30
I would try an answer if I could work out what you just said ;)

You have already set up your partitions for your install, you shouldn't need to add more.

Have a look at this 10 minute Ubuntu Partitioning video, it is about the 4th video down the page.

[http://screencasts.ubuntu.com](http://screencasts.ubuntu.com)

The second half of the video deals with your scenerio, I think.

---

### Post by macogw on 2009-10-30
The installer has a partitioner built in...

---

### Post by fedexfrt357 on 2009-10-31
lol...confused myself too...

Maybe I can explain better... I went into the installer, and that's when i saw a 2.5G partition had been added, labeled Ubuntu 9.04... I'm assuming this is where my system files will go, and I had intended for them to go into the 20G partition I made...

I'll try to get a screen shot... :)

I'll check out the video...Thanks

>edit<  These videos are awesome...=D>

---

### Post by morphodone on 2009-10-31
That's weird.  Are you installing from live-cd?  You may be looking at the wrong disc.

---

### Post by macogw on 2009-10-31
Ah, ok it was showing "hypothetically, if you choose this side-by-side option"... Choose the Manual partitioning option, and then you'll be able to tell it to use the partitions you created in GParted.

---

### Post by howefield on 2009-10-31
> **fedexfrt357 said:**
> i saw a 2.5G partition had been added, labeled Ubuntu 9.04... I'm assuming this is where my system files will go, and I had intended for them to go into the 20G partition I made...

That's right, you need to tell the installer at the partitioning stage where your / and your /home partitions are.

Selecting manual partitioning during the install should allow you to mount the partitions you want to use for / and /home and specify which file system, whether or not to format them ect.

---

### Post by fedexfrt357 on 2009-10-31
[quote=morphodone]That's weird.  Are you installing from live-cd?  You may be looking at the wrong disc.[/quote]

Yes, live-cd.... Only one disk (hdd) tho...


[quote=macogw]Choose the Manual partitioning option, and then you'll be able to tell it to use the partitions you created in GParted.[/quote]

I'll try that... 

[quote=howefield]Selecting manual partitioning during the install should allow you to mount the partitions you want to use for / and /home and specify which file system, whether or not to format them ect.[/quote]

Thanks a lot folks, I sure appreciate the help...:) (fingers crossed)

---

### Post by ikacer on 2009-10-31
this is kind of off topic, but is there a reason you are installing Jaunty (9.04)? Karmic (9.10) was just released and is IMHO a nice improvement over Jaunty.

---

### Post by fedexfrt357 on 2009-10-31
...Karmic was still in beta when I started playing around with Ubuntu, and I figured I would stick with Jaunty for a bit, kinda get a better grasp on this one before I switch, but I undoubtedly, will try it out...  :)

...But other than that....no...

---

### Post by fedexfrt357 on 2009-10-31
Thank you greatly for your help and advice... Worked nicely...

\\:D/

---

