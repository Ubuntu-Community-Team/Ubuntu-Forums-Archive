---
title: "Upgrade from Jaunty to Karmic was not a happy one!  Will clean install be better?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by mrpeachy on 2009-10-29
I just upgraded to 9.10 from 9.04.
I now have no sound and I can't enable desktop effects.  These are the problems i have encountered so far!

If these problems exists with the upgrade will they still be there if i do a clean install of 9.10?  Or is there a chance the clean install will work properly?

I could always try, but i thought i would ask to hopefully save time!

Thanks

---

### Post by w00ly on 2009-10-29
No desktop effects probably means your video card drivers arent installed

---

### Post by jsimerly on 2009-10-29
My upgrade from Jaunty to Karmic bombed, giving me a completely unusable platform, so had to do a clean install.  Here are issues I'm fighting so far:

1.  nvidia-settings video texture adaptor settings screwed up local video playing.  Have to reset with every file played.

2.  External USB drive used for backups has to be powered down and back up every time PC is rebooted.  Jaunty had no problems rebooting and recognizing drive.

Minor problems after the clean install, but very perplexing.  Bigger issue is why the upgrade from Jaunty bombed in the first place.

So, yes, I think a clean install will be better, but not issue-free.  Hope it works well for you.

---

### Post by mrpeachy on 2009-10-29
I have Device Manager installed and when i look at my graphics card it says this: 
VGA Controller
Model: Radeon R350 [Radeon 9800 Pro]
Vendor: ATI Technologies Inc
Connection: PCI (Peripheral Component Interconnect)

same for display controller

which is all correct.  is there a better way to check?

---

### Post by mrpeachy on 2009-10-29
> **jsimerly said:**
> My upgrade from Jaunty to Karmic bombed, giving me a completely unusable platform, so had to do a clean install.  Here are issues I'm fighting so far:

1.  nvidia-settings video texture adaptor settings screwed up local video playing.  Have to reset with every file played.

2.  External USB drive used for backups has to be powered down and back up every time PC is rebooted.  Jaunty had no problems rebooting and recognizing drive.

Minor problems after the clean install, but very perplexing.  Bigger issue is why the upgrade from Jaunty bombed in the first place.

So, yes, I think a clean install will be better, but not issue-free.  Hope it works well for you.

Reading that I think I might just reinstall 9.04 and wait a while for 9.10 to improve.  Might give 9.10 a go just for the hell of it though!

---

### Post by appier on 2009-10-30
> **mrpeachy said:**
> I just upgraded to 9.10 from 9.04.
I now have no sound and I can't enable desktop effects.  

Exactly the same problem here.

---

### Post by mrpeachy on 2009-10-30
Well, I just finished a clean install of 9.10 and so far so good.  My sound is working fine, I have desktop visual effects back.  So it seems I'm going to be ok!

Luckily I didnt have alot to lose, had only been working with 9.04 (first ubuntu install) for a couple of weeks.  Got to reinstall all the programs i use and i have a few things to set up again.

BIG let down that the upgrade didn't work however.

---

### Post by note32 on 2009-10-30
theres nothing like a fresh install;)

---

### Post by Stosskraft on 2009-10-30
Hey sorry to piggy back on this tread but can some who has done the UPGRADE tell me how it went? I started it before I left for work so I am not sure what to expect when I get home.

I mean if I update through the manager will all my stuff be there, video and files? How about the themes and how my cairo-dock and compiz is set up? The restricted codecs, will the still be there?

I am not so worried about losing everything as it is backed up, I am just wondering what to expect. Through I have just burned a 9.10 disk at work and might to a clean install if I have any bugs.

Do you suggest I do a clean install if the upgrade is successful? I will have the disk and the back up is pretty much done.... suggestions?

---

### Post by appier on 2009-10-30
> **Stosskraft said:**
> UPGRADE tell me how it went?

Not very good--sound was gone and video drivers not able to load desktop effects.  The KDE desktop crashed upon loading.

> I mean if I update through the manager will all my stuff be there, video and files?

Yes

> How about the themes and how my cairo-dock and compiz is set up? 

In my case--no.

> The restricted codecs, will the still be there?

Don't know--I never got that far.

> I am not so worried about losing everything as it is backed up, I am just wondering what to expect. Through I have just burned a 9.10 disk at work and might to a clean install if I have any bugs.

I just did a clean install, and none of the bugs showed up for the party.

> Do you suggest I do a clean install if the upgrade is successful?

I hope your upgrade went better than mine--it was not usable.  On the ohter hand, if the upgrade is successful and you like the ext3 file system, then I would stay with the upgrade.

> I will have the disk and the back up is pretty much done.... suggestions?

Double check the back-up so you can restore your home folder.

Good Luck!

Mark

---

### Post by appier on 2009-10-31
Using a clean install, so far there have been none of the problems associated with the upgrade process.  It has worked well.

---

