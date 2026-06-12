---
title: "Performing SSD optimization, FSTAB question"
date: 2015-05-14
forum: Hardware
---

### Post by mr.rhtuner on 2015-05-14
Hey everyone, I have a thinkpad X220 with Samsung 850 Pro SSD installed

I want to optimize the SSD as much as I can to prevent unwanted writes to the drive.

As I was following some articles, it seems my FSTAB looks a bit different then what others have.

Example:
Here’s what fstab looks like on an online blog:

/dev/sda1        /              ext4    discard,noatime,errors=remount-ro   0       1


Mine, while showing ext4 looks a bit different. I don't have the drive listing /dev/SDA# but instead I have a UUID listed. I am guessing this is correct?

[url=http://i.imgur.com/z9TnCGo.png]
  [img]http://imgur.com/z9TnCGol.png[/img]
[/url]



Also, do I need **noatime** at the end of the fstab file where it shows *tmpfs*?

---

### Post by oldfred on 2015-05-14
UUID is preferred over device paths.

This is my fstab entry:
```
# / was on /dev/sda3 during installation
UUID=45de38c8-6748-4634-b207-628d9aa8b42b /               ext4    noatime,errors=remount-ro 0       1
```

I do not think they recommend discard any more, but use a cron task for trim. I turned off the version Ubuntu has as I was not sure my model SSD worked. And I preferred a log to know it is working.
       SSD tips for both 14.04 & 12.04
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
TRIM in 14.04
[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)
HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)
Ubuntu Aims To TRIM SSDs By Default
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY)
TRIM as cron job, also must be ext4
[http://www.howtogeek.com/176978/](http://www.howtogeek.com/176978/)

I think this was the version I followed.
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

### Post by kerry_s on 2015-05-14
there's no need to mess with it, ubuntu auto adjusts for ssd.

if you read more "discard" makes things slow, so a weekly job of /etc/cron.weekly/fstrim is used instead. ubuntu also changes from cfq to deadline, etc...

chances are any changes you make are going to get in the way or just not boot.

ps: the 1 thing i would do is check if it is supported, run-> sudo fstrim -v /
also i would recommend you install zram-config to compress swap in ram.

---

### Post by efflandt on 2015-05-15
This gives some helpful hints for optimizing SSD which I used when installing 14.04 to mSATA SSD card in my laptop. Although, with a larger drive (or maybe newer SSDs account for that) you may not need as much space for step 5. The drive in the example was probably 128 GB and my mSATA SSD is 512 GB (gaming laptop with room for Linux Steam games).

[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

