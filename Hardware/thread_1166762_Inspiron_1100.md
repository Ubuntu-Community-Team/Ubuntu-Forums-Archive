---
title: "Inspiron 1100"
date: 2009-05-22
forum: Hardware
---

### Post by Narusegawa on 2009-05-22
If anyone has gotten an Inspiron 1100 to work with 9.04 can they please let me know how? I've tried adding vga=773 and nosplash to my kernel lines.

I've updated to A32 BIOS as recommend too, changed UMA from 1mb to 8mb.

I've used the latest 'intel' driver from the launchpad using some ppa repository.

Yet still I cannot get X (or login screen) to reliably come up, it's not even every other boot, it's more like a random chance to boot up X.

Also, if you have it working can you let me have a xorg.conf from a working Inpsiron 1100 setup on 9.04 as mine is always blank and whenever I see posts about adding values and changing the 'video' sections, but with a blank slate I don't know what else should be in there.

It's so unreliable I've actually kicked off a re-install of XP onto it to later today dual-boot this as it's driving me insane. I wanted to move off windows on the laptop completely but it seems I'm not allowed to do this yet.

---

### Post by Narusegawa on 2009-06-08
I'm guessing no-one else has an Inspiron 1100 with a working Ubuntu 9.04 then. Shame :(

I was really hoping to have Ubuntu on my laptop. Some days it loads X, others it won't.

---

### Post by overdrank on 2009-06-08
> **Narusegawa said:**
> I'm guessing no-one else has an Inspiron 1100 with a working Ubuntu 9.04 then. Shame :(

I was really hoping to have Ubuntu on my laptop. Some days it loads X, others it won't.

Hi and if you are having issues with intel graphics in Jaunty 9.04 you may look at the link in my signature for some help.

---

### Post by Narusegawa on 2009-06-09
I saw that page before but it's mainly all aimed at performance, and it's not performance I'm having a problem with. It's X actually... loading? I dunno

I boot up, seems to be a 30% chance I may or may not get a desktop (but I do hear the sounds). CTRL-SHIFT-F1 may (not always) bring up a console, then back to CTRL-SHIFT-F7 sometimes gives me a desktop.

Alot of people say edit the xorg.conf, but that's non-existant and I can't create one as I don't know what would be needed in there for this brand/model of laptop either. It is pretty old.

When it does load, performance isn't a problem and things run smoothly.

---

### Post by mantelo on 2009-06-19
same problem here. Sometimes it works and sometimes it doesn't

---

### Post by Narusegawa on 2009-06-22
Oddly enough, the performance fix seems to have fixed this! So far not a single boot has failed to load X. But what was you saying about xubuntu? To be honest this is an old laptop and underpowered. I like Gnome as it's easy to use, not sure how easy xfce is, last time I tried it was a nightmare to get used to/edit.

---

### Post by mantelo on 2009-06-29
Xubuntu seemed to work (for a while at least) but it started to give me the same kind of issues, so I deleted the comment. The problem seemed to start with the update to the last kernel (2.6.28.13)

Anyway, I went back to intrepid with xfce and everything works great (except the tv output)

---

### Post by captainskyhawk on 2009-07-31
Same thing happens to me.  Sometime X loads up after I log in, sometimes it doesn't.  Still on 8.04 -- this just started about a week ago.

---

### Post by cwig on 2009-08-30
I had a similar problem trying to run it from the live cd.  I got it to work by running and installing it in graphics safe mode.  After I installed it it was stuck at 800x600 with a black border around it.  Then I found this xorg.conf online and it worked perfect. good luck

---

