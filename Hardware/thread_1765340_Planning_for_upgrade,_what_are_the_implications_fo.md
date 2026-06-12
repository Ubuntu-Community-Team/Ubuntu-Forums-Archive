---
title: "Planning for upgrade, what are the implications for an existing Ubuntu install?"
date: 2011-05-23
forum: Hardware
---

### Post by jamesjenner on 2011-05-23
G'day all,

I currently have 11.04 (64) running very nicely on my main desktop, however the hardware is now quite aged and I was thinking of upgrading to a new CPU, which means a new mobo and most prob new memory as well.

Now I've done this numerous times in windows and know what to expect but I have never done this with a Linux distribution. So I have the following questions:

[LIST=1]
[*]Can I just throw the new hardware in, boot up Ubuntu and expect Ubuntu to sort itself out with the new motherboard?
[*]I'm looking at a low end i7 and possibly a Asus or Gigabyte Mobo, any preference for brand of mobo's to reduce issues with Ubuntu?
[*]Should I just ditch my xFi card and use a mobo embedded sound card (that is what I currently use after getting so frustrated with xFi and how I get sound output included with the mic input)?
[*]I will be doing a backup of my system before I install the new hardware (I use Déjà so will be incremental, not sure if its the best). Do I need to backup anything else to make sure I have a correct snapshot of what is installed from a software point of view? I'm presuming that the backup is only focused on data and will not help me determine what I had installed.
[/LIST]
I'm really interested in 1 and 2, the other questions are just bonus ones :) 

I should also note that network will be available after installation but can also have a livecd handy if required (I'm not really sure what I will need, hence my post). I will have access, via several other computers, to the internet while doing the upgrade.

---

### Post by DanneStrat on 2011-05-23
Hello.

I will see if I can answer some of your questions.

> Can I just throw the new hardware in, boot up Ubuntu and expect Ubuntu to sort itself out with the new motherboard?

Yes. I don't think you will have any problems with that.

If you think of buying a new video card with different brand, you 

may have to manually install the appropriate graphics driver 

module.

> I'm looking at a low end i7 and possibly a Asus or Gigabyte Mobo, any preference for brand of mobo's to reduce issues with Ubuntu?

Both Gigabyte and Asus motherboards is known to work well with 

linux, so I think you will be good with either one of them.

> Should I just ditch my xFi card and use a mobo embedded sound card (that is what I currently use after getting so frustrated with xFi and how I get sound output included with the mic input)?

There seems to be a couple of problems with xFi cards under 

linux.

From my experience, the integrated soundcard on the motherboard

works very well. I use it right know and everything works as 

expected. So if you feel that your xFi gives you problems, try

the motherboard sound and see if it works better. If not, you can 

always pop the old card back in again.

> I will be doing a backup of my system before I install the new hardware (I use Déjà so will be incremental, not sure if its the best). Do I need to backup anything else to make sure I have a correct snapshot of what is installed from a software point of view? I'm presuming that the backup is only focused on data and will not help me determine what I had installed.

If you want to be absolutely sure everything on your drive is 

backed up, use clonezilla to make an image of your drive.

Clonezilla live cd:

[http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/1.2.8-42/clonezilla-live-1.2.8-42-i486.iso/download](http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/1.2.8-42/clonezilla-live-1.2.8-42-i486.iso/download)

Just burn it to a cd or dvd and boot from it.

Usage instructions:

[http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla](http://linuxgravity.com/creating-and-restoring-an-image-of-hard-disk-with-clonzilla)

I hope this answered some of your questions.

Good luck.

---

### Post by jamesjenner on 2011-05-24
Thanks for the reply. Hmm I was looking at Clonezilla and was turned off you need to boot from a cd to do it, but then when I think about it, that kinda makes sense (cause how else could you take a snapshot of a running system).

Reckon that's soothed my nerves a bit, I had a feeling it would be that simple.

Cheers,

James.

---

### Post by DanneStrat on 2011-05-24
> **jamesjenner said:**
> Thanks for the reply. Hmm I was looking at Clonezilla and was turned off you need to boot from a cd to do it, but then when I think about it, that kinda makes sense (cause how else could you take a snapshot of a running system).

You're welcome.

Exactly. The best way of making an image of an operating system 

is when it's not in use, simply because you won't have to deal 

with locked files and permission problems.

Let me know how it goes.

---

### Post by jamesjenner on 2011-05-24
> **DanneStrat said:**
> Let me know how it goes.

No worries, will do. I'm planning to upgrade within the next month so may not be for a few weeks before I post a reply.

Btw, our company just got brought out by a very big Swiss/Swedish company, ABB :)

---

