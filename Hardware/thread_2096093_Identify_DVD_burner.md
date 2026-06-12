---
title: "Identify DVD burner"
date: 2012-12-19
forum: Hardware
---

### Post by Acharn on 2012-12-19
I can't figure out who the manufacturer of my DVD burner was, and I was hoping to learn how to update its firmware. I have a desktop Acer Aspire M-1610. When I run lshw I get:
```
*-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

```
My basic problem is that since I installed Ubuntu it has not recognized the DVDs I burned on it when I was running Windows XP nor the blank DVDs I have. Strangely, it recognized and reads some commercial DVDs I have of The Sopranos TV show. The old DVDs work fine in my TV's DVD player, and I haven't been able to take them to try on another computer. It recognizes and reads CDs, which is nice because that's what I prefer to use if the data isn't too large. One site I found claimed that this brand (Princo) is inferior and has lots of problems, but I used it for years on many computers and never had a problem until now.

---

### Post by Acharn on 2012-12-22
Found it. Turns out it's a Lite-On drive, which, now that I think of it, is the only brand I have ever seen here in Thailand. Model number is DH16A1S (HA11), which of course is no longer in production. Their firmware updater is a Windows program, the whole site is Windows oriented, and their blog doesn't seem to have been touched since Feburary 2011. Guess I need to bite the bullet and buy a new drive.

---

