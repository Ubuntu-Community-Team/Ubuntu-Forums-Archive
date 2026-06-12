---
title: "Ubuntu Eee and the 900 16gb"
date: 2008-09-27
forum: Hardware
---

### Post by michaelkahl on 2008-09-27
I've posted in a couple of threads recently so I'm sure some of you know that I'm enjoying my new toy and running Ubuntu Eee.  Here are some tips and lessons that I've learned in the last two days.  Not all inclusive so if someone can add insight please do.

Strait out-of-the-box I checked out Xandros.  It's ok, not bad and I'd seen it before on library machines.  So after abot 15 min I shutdown the Eee and hooked up my external DVD-drive.

I first did the install as I typically do, setting the / partition as ext3.  After doing some reading and searching on the net, I realized that ext2 would better fit the needs of a SSD.  Less drive traffic, extending the SSD's lifespan and battery life.

Flash 10 beta comes pre-installed and works great on hulu.com, unfortunately hulu.com doesn't host Cisco's Netacademy site.  Downgrading to Flash 9 fixed my issues there.

At some point Firefox started crashing on me.  After removing Adblock Plus and Download Helper add-ons this ended.  I'm not sure what the issue is, but I have no problems in Ubuntu 32 or 64 with this.

With Ubuntu Eee be careful with your repo's.  While the name says Ubuntu it is a custom kernel.

I disabled cache in Firefox, did not install a swap partition, and turned off log files in my fstab file.  I also set all partitions to noatime in the fstab.  From what I understand this will reduce disk activity extending the life of your SSD and saves on the battery life.

As I stated before everything seems to work out-of-the-box for me as far as hardware is concerned.  The only exception to this is the web-cam.  I haven't tried it because I never use one.  Honestly I don't think it's an issue though.
Netbook Remix is a delight to use.  I enjoy it very much and feel it's more advanced than Xandros easy mode.  All applications normally listed in the menu were available.  This is a very well designed GUI.

I hope this is helpful to someone, also if I've made any errors please feel free to correct or add to what I've posted.

---

