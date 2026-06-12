---
title: "nVidia video flicker on Karmic"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Frantic_Earthling on 2009-11-01
I just did a clean install of 9.10 on an Asus M70VN portable with a GeForce 9650M GT video.

Everything works fine :D with the exception of a small annoying problem.
The bottom half of the screen flickers randomly from time to time :( (several times per hour), apparently without any specific reason.

I installed the recommended nVidia driver Version 185.

I was wondering whether I could/should try the following recent update, though not available from the Ubuntu repos, but from the nVidia site:

    Linux Display Driver - x86

    Version:
    190.42 Certified

    Release Date:
    2009.10.27

    Operating System:
    Linux

    Language:
    English (U.S.)

    File Size:
    22.8 MB 

Do you think that this could solve my problem, or could generate more problems?

Incidentally, before 9.10, I was running 8.04 without any such problem.

---

### Post by Frantic_Earthling on 2009-11-01
Finally what I did was to roll back to the previous version (173) and I uninstalled version 185.

So far so good.

No more flicker.

Touch wood.

Will report back should the problem return.

---

### Post by Frantic_Earthling on 2009-11-05
After several days with the 173 nVidia driver, I can safely say that the bottom half of my Asus M70VN screen does not flicker any longer.:D

However, I have to put up with two small issues:confused::

When booting the system, there is a 25-second freeze just before the login windows appears. I always have this freeze and the login windows eventually always appear.

When changing the desktop backgroung (which obviously you do not do so often), the system experiences the same 25-second freeze after which the newly selected backgroung appears.

Weird.

I am interested in any suggestions as to why this happens.

(If I re-install the 185 driver, this freeze disappears, but my screen starts again flickering randomly.)

---

### Post by drbenway2 on 2009-11-05
Just curious.  Have you tried the 190 driver to see if you still experience either or both of these problems?

---

### Post by Frantic_Earthling on 2009-11-05
> **drbenway2 said:**
> Just curious.  Have you tried the 190 driver to see if you still experience either or both of these problems?

I did.

It worked exactly like the driver version 185 :  flicker happening on a random basis for half a second in the bottom half of the screen (sigh!).

However, just like with the 185, I did not experience any freeze.

I decided that I could put up with the freeze, not with the flicker, so I rolled back to 173.

---

### Post by Frantic_Earthling on 2009-11-11
Well, I did a clean reinstall of Jaunty and gave up on Karmic.
Will give Lucid a try next year.
For the time being, I am staying with a system that I know is stable.


> **Frantic_Earthling said:**
> After several days with the 173 nVidia driver, I can safely say that the bottom half of my Asus M70VN screen does not flicker any longer.:D

However, I have to put up with two small issues:confused::

When booting the system, there is a 25-second freeze just before the login windows appears. I always have this freeze and the login windows eventually always appear.

When changing the desktop backgroung (which obviously you do not do so often), the system experiences the same 25-second freeze after which the newly selected backgroung appears.

Weird.

I am interested in any suggestions as to why this happens.

(If I re-install the 185 driver, this freeze disappears, but my screen starts again flickering randomly.)

---

### Post by RemyLeBeau on 2010-01-04
Hi!

I'm having similar trouble with a clean install of karmic and nvidia drivers 185, 190 & 195.

Screen freezes (and flickers every 5 seconds or so) and there's no way of coming back except rebooting with REISUB.

Graphics card is a EVGA Geforce 8400 GS two months old, tops.

I've never had trouble here in karmic (been using it for a couple of months) and two days ago I decided to install the propietary drivers by nvidia and things got nasty!

There's no time pattern for this: it might ocurr 2 mins after boot or 6 hr later after watching two movies. There's no specific event that triggers this except maybe that it happens while surfing the net. Maybe a flash-related bug that's freezing X? It's the only thing I noticed during these events. 

Here's the last syslog entry related to the episode I think. Couldn't find the first ones but they're very similar.

```
Jan  4 10:18:05 SkyNet kernel: [  530.862575] NVRM: Xid (0002:00): 8, Channel 00000001
Jan  4 10:18:08 SkyNet kernel: [  533.877440] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 00000860 00000000 00000040
Jan  4 10:18:13 SkyNet kernel: [  538.861563] NVRM: Xid (0002:00): 8, Channel 00000001
```


Any ideas?

Thanks in advance!

PS: Graphics card is a 8400 GS - Ubuntu Karmic 9.10 (64-bit) - nVidia drivers tested: 185, 190, 195 - Using google chrome as my default browser. nVidia driver currently in use is: 190.53

---

### Post by RemyLeBeau on 2010-01-21
bump! :D

PS: Don't know how to edit the repositories in order to add older versions of the drivers (eg. 180) which are not available in Karmic. Any ideas? thx!

---

### Post by ephman on 2010-01-21
i'm also using a m70vn.  but what i did to fix the issue after a TON of research was i installed the latest driver right from nvidia.  then on startup i run the nvidia x server settings program and select maximum performance from the powermizer option.  a pain, but i hardly reboot.  for some reason and like i said after a TON of trial error and research, this is my solution.  and it seems to have worked for a few others i've told it to as well.  

good luck,

ephman

---

### Post by RemyLeBeau on 2010-01-22
> **ephman said:**
> i'm also using a m70vn.  but what i did to fix the issue after a TON of research was i installed the latest driver right from nvidia.  then on startup i run the nvidia x server settings program and select maximum performance from the powermizer option.  a pain, but i hardly reboot.  for some reason and like i said after a TON of trial error and research, this is my solution.  and it seems to have worked for a few others i've told it to as well.  

good luck,

ephman

I've already did that: downloaded nvidia's 195 from their webpage (or via repositories, don't remember now) and set just by chance, the maximum performance option but it only worked a few hours then it seems that X died and the only way to make it work again was rebooting via R-E-I-S-U-B. In addition to this, I couldn't find any other descriptive messages or logs that could shed some light to this problem. 

I will test the vga card under window$ in case it is a hardware problem but I'm convinced it has something to do with ubuntu and the drivers because the card is brand new.

---

### Post by FreddyAV on 2010-01-24
For people with laptops such as the M70Vn the solution seems to be to upgrade the BIOS. (Laptop BIOS includes fixes for the inbuilt NViDIA card, even if it is attached via MXM I think)

I'm on an ASUS x57Vn and it seems to have solved it for me (flickering and system hang / freeze). I'm hoping the issue is also related to Xorg using 100% CPU time and thus freezing the system (I had two different kinds of freezes) and that it also solves my issue with videos only producing a black area after running a few videos.

See also [http://bbs.archlinux.org/viewtopic.php?id=83575](http://bbs.archlinux.org/viewtopic.php?id=83575) for more info (the link to info on PowerMizer needs the last ; removed from the link).

Hope this helps! 

Cheers
Freddy

---

### Post by RemyLeBeau on 2010-01-24
> **FreddyAV said:**
> For people with laptops such as the M70Vn the solution seems to be to upgrade the BIOS. (Laptop BIOS includes fixes for the inbuilt NViDIA card, even if it is attached via MXM I think)

I'm on an ASUS x57Vn and it seems to have solved it for me (flickering and system hang / freeze). I'm hoping the issue is also related to Xorg using 100% CPU time and thus freezing the system (I had two different kinds of freezes) and that it also solves my issue with videos only producing a black area after running a few videos.

See also [http://bbs.archlinux.org/viewtopic.php?id=83575](http://bbs.archlinux.org/viewtopic.php?id=83575) for more info (the link to info on PowerMizer needs the last ; removed from the link).

Hope this helps! 

Cheers
Freddy

Thanks for the info. It says in that post that someone had a similar problem with an asus board with a nvidia card.

I've replaced my 7300 LE with a 8400 GS recently and I did an upgrade in my ubuntu before this problem. I had no issues with (Ubuntu9.04+7300+180 drivers) but the thing is I can't test the vga because the old one died and I don't know how drivers 180 can be installed here in karmic. 

Tried downloading them from nvidia.com but throws some error during compilation (I guess something related with another library that is newer in the system and the installer doesn't know how to proceed) but I don't remember exactly.

---

### Post by RemyLeBeau on 2010-02-12
I'm still having the same problem but I tried more stuff:

I've restored ubuntu 9.10 from an old image and reinstalled 190 drivers from ubuntu repos.

Tried tweaking the powermizer a bit. Seems that many users had trouble there because of some nvidia feature called adaptive clocking which adjusts clock frecuencies acording to the demands of the system. One solution to the flickers, was to override that. Ppl say that the flickers/crash was due to the changes in frecuencies. The thing is that my vga card doesn't have profiles like mobile cards have so forcing the vga to one won't work for obvious reasons.

Also tried underclocking the card in case that it was related (done that by adding the "Coolbits" "1" in the xorg.conf) but it didn't work either.

The only pattern I've found is that crashes ocurr when surfing the web and I recall hanging more than once in two news-sites which have several flash apps. In addition to this, for those blessed with 32bit installations, it's of public knowledge that 64bit flash clients are pathetic. Could it be related to this?

Thanks!

---

