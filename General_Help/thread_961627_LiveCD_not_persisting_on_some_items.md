---
title: "LiveCD not persisting on some items"
date: 2008-10-28
forum: General Help
---

### Post by greatwolf on 2008-10-28
Hi guys,

Really quick question: how do you make the hostname and nvidia drivers persist across reboots?

I'm currently using a 4gb flash drive for saving the persisting settings and using F6 + persistent during the boot menu. Most of the items are getting saved liked the ndiswrapper wireless driver, menu settings, preferences etc. But for some reason I can't get the hostname nor the nvidia drivers to persist across reboots. After the reboot I always have to open a terminal and type in nvidia-xconfig followed by ctrl-alt-backspace to restart the Xserver. I've used envyNG btw to install the nvidia drivers.

Thanks

---

### Post by C.S.Cameron on 2008-10-28
For persistence with Live CD I am using partitions named casper-rw and home-rw on my flash drive.
I notice that when caser-rw icon shows up on my desktop my downloaded programs don't work.
When it doesn't show up they do work.
Not sure how to keep it from being mounted when I boot the CD though. 
Home-rw always seems to work.

---

### Post by greatwolf on 2008-10-28
It's a silly question but what is casper-rw? I understand that that is the default name of the partition ubuntu looks for when it attempts a persistent boot. In which case, what is home-rw and how does it work with ubuntu's persistent?

Oh, and any help on making the hostname persistent for ubuntu?

Thanks

---

### Post by C.S.Cameron on 2008-10-28
Casper-rw seems to be the place where downloaded programs are saved.
Home-rw seems to be where settings like desktop background and Firefox bookmarks are saved.

I have used System, Administration, Users and Groups to add my name and password as a user, I now get a screen asking for user name and password at login. I then leave blank and hit enter if I want to login as default Live Session User.

Most of what I know about making the Live CD persistent can be found here:
[http://ubuntuforums.org/showthread.php?t=953008](http://ubuntuforums.org/showthread.php?t=953008)

---

### Post by greatwolf on 2008-11-02
Ok, I did some more digging around and it seems to me I have to some how make the xorg.conf persistent between reboots. I've wasted a lot of time searching for the answer on how to do this but have come up with nothing. I can't be the first one to want to do something like this.

Does anyone know how to do this please help me out; direct me to a link or a thread about this issue would be greatly appreciated. I'm using intrepid 8.10 btw with nvidia drivers 177.80.

Also btw, I checked out the thread cameron linked. So what I did was repartitioned and reformated my usb flash drive. So now I have one partition labeled casper-rw and a second part labeled as home-rw. Needless to say, it didn't help make the nvidia drivers persistent on reboot.

Thanks

---

### Post by greatwolf on 2008-11-03
Bump,

ok guys, all I'm really looking to do here is I want ubuntu to load the nvidia drivers at startup and actually **USE** those drivers instead of the default open-source ones. And I want to do this on a livecd with persistence via usb flash drive.

Now, are the lack of replies here simply because no one has attempted to actually do this so no one knows how or what's the deal?

Btw Cameron, thanks for the reply. I've since checked that thread out and repartitioned/reformatted my flash as such. It still isn't doing what I need though. :(

Thanks

---

### Post by jisare on 2009-01-27
[http://209.85.173.132/search?q=cache:GGqNrpxZSuwJ:ubuntuforums.org/archive/index.php/t-211515.html+livecd+persist*+xorg.conf&hl=zh-CN&ct=clnk&cd=3&gl=sg&client=firefox-a](http://209.85.173.132/search?q=cache:GGqNrpxZSuwJ:ubuntuforums.org/archive/index.php/t-211515.html+livecd+persist*+xorg.conf&hl=zh-CN&ct=clnk&cd=3&gl=sg&client=firefox-a)

this link should help...;)

---

### Post by greatwolf on 2009-02-04
Thank you, I will give this another go later.

---

