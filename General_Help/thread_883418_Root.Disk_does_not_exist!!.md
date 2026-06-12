---
title: "Root.Disk does not exist!?!"
date: 2008-08-07
forum: General Help
---

### Post by mistersam on 2008-08-07
My computer froze so I had to do a hard reboot (hold power button for 5 secs).

When it was booting back up, it stopped and gave me the "BusyBox"
So I tried to boot with another initrd.img. What's when I see the message

"root.disk does not exist"

This is a wubi installation so I log into windows and look in the ubuntu folder and root.disk is right here.

Any ideas?

---

### Post by mistersam on 2008-08-08
Okay, I fixed it, and here's how (this will not work for most of you):

A while back I had run out of space on my Wubi installation, so I created a copy of root.disk increased the virtual size usinh the following method:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Today, I ran into my problem described above. To fix it, I booted into windows and backed up my current root.disk file to root.8-7-08.disk and replaced it with my old backup root.5-30-08.disk. I rebooted into Ubuntu and everything worked as before. I rebooted into Windows and swapped the files again:

root.disk ----> root.5-30-08.disk
root.8-7-08.disk ---> root.disk

Rebooted and now it works again.

:popcorn:

---

### Post by Seed44 on 2009-03-03
I´m having the same error that you had....it´s exacly the same....
can you send me a copy of your root.disk backup, please?

and if it works then I must figure why my ubuntu freezes somethimes (to not press power again :( )

you´ve solved your primary problem? (the freezing?)

---

### Post by mistersam on 2009-03-03
Hi Seed,

I can try to help. Why don't you send me a PM with your contact info and I'll figure out a way to send that file your way (it's a BIG file).

I can't remember what I did to stop the freezing :(

---

