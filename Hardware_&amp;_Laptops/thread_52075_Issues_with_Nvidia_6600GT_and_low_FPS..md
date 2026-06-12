---
title: "Issues with Nvidia 6600GT and low FPS."
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by DeezElbowz on 2005-07-26
Morning everyone,

First off, let me give you my system setup:

MSI K8N Neo 4 Mobo
Athlon 64 3000+
Chaintech 6600 GT OC'd to 600/1200 (around 9K in glxgears, PCIe)
1 gig of PC3500 Corsair RAM
Ubuntu 5.04 running the K7 kernel
Most recent stable Nvidia driver install 7664

All of the equipment but the ram is new.  Because of this, I decided to do a completely new install of Ubuntu (well, I was also having major issues with the newest nvidia drivers).  Upon booting into Ubuntu, I get a PCIe error about not being able to allocate to a region in 0000:5.yadda yadda.  Much like I have found out by tooling around on forums (nvnews, here, gentoo, etc), many people have had issues with 7667 and their NVidia cards (specifically 6600GTs).   No clue what to do about this issue, though someone on the Gentoo forums claims to have fixed his problems (but then further no one else has had luck with his steps).

But from here, I only get *max* 30 fps in SWG:TTE (through Cedega).  I get no shadows (even when they're set to max), and it's really chunky (if you know what I mean).  Also, to note, I do not have any artifacts either--outside of the shadows issue and being insanely slow, it looks nice.  Last evening I noticed something while messing with the terrain graphics settings--I couldn't max them out *at all*.  The bars were literally blocked from a certain point on within the game.  Yet, after messing around with it some (I believe I installed another version of the Nvidia driver) I got them to open up, but I still had poor performance issues.

Apologies about how this post is setup; I'm racking my brain trying to think of anything to say that might help.  I'm currently not on my computer, I'm at a friend's, so I cannot throw up my xorg.conf file and such--but I can say that there isn't a GLcore and DRI is most definitely commented out.  I do have it set to nvidia for the driver, I even have the VideoRam set as an option too.  What else should prob'ly be there?  I also have questions about some of the AGP options--I remember on my old 5950 I could do a cat of the ***/agp/card and get info--yet, of course, with my PCIe that doesn't really work anymore.  Are there somethings I should prob'ly be setting wtihin Ubuntu (and elsewhere, say Cedega) to be optomizing this?  What if I'm just forgetting something in my BIOS to set?  (I didn't notice anything while tooling around there.)  

I'm just a little frustrated with the performance, even at low resolution and low settings--especially when I know I was getting better not too long ago.  (Shadows, etc!)  In some ways I'm just a complete newbie about linux and I have no earthly idea what to do.  Any help would be greatly appreciated--especially from people who might have a PCIe card, of course those with my exact card.

Apologies again about the meandering of the post, and Many Thanks.

---

### Post by DeezElbowz on 2005-07-26
Uh.. you should go code some unix and shut yer cockwasher.  l@m3r   lololol

---

### Post by rwabel on 2005-07-27
[QUOTE=DeezElbowz]Morning everyone,

First off, let me give you my system setup:

MSI K8N Neo 4 Mobo
Athlon 64 3000+
Chaintech 6600 GT OC'd to 600/1200 (around 9K in glxgears, PCIe)
1 gig of PC3500 Corsair RAM
Ubuntu 5.04 running the K7 kernel
Most recent stable Nvidia driver install 7664

All of the equipment but the ram is new.  Because of this, I decided to do a completely new install of Ubuntu (well, I was also having major issues with the newest nvidia drivers).  Upon booting into Ubuntu, I get a PCIe error about not being able to allocate to a region in 0000:5.yadda yadda.  Much like I have found out by tooling around on forums (nvnews, here, gentoo, etc), many people have had issues with 7667 and their NVidia cards (specifically 6600GTs).   No clue what to do about this issue, though someone on the Gentoo forums claims to have fixed his problems (but then further no one else has had luck with his steps).

But from here, I only get *max* 30 fps in SWG:TTE (through Cedega).  I get no shadows (even when they're set to max), and it's really chunky (if you know what I mean).  Also, to note, I do not have any artifacts either--outside of the shadows issue and being insanely slow, it looks nice.  Last evening I noticed something while messing with the terrain graphics settings--I couldn't max them out *at all*.  The bars were literally blocked from a certain point on within the game.  Yet, after messing around with it some (I believe I installed another version of the Nvidia driver) I got them to open up, but I still had poor performance issues.

Apologies about how this post is setup; I'm racking my brain trying to think of anything to say that might help.  I'm currently not on my computer, I'm at a friend's, so I cannot throw up my xorg.conf file and such--but I can say that there isn't a GLcore and DRI is most definitely commented out.  I do have it set to nvidia for the driver, I even have the VideoRam set as an option too.  What else should prob'ly be there?  I also have questions about some of the AGP options--I remember on my old 5950 I could do a cat of the ***/agp/card and get info--yet, of course, with my PCIe that doesn't really work anymore.  Are there somethings I should prob'ly be setting wtihin Ubuntu (and elsewhere, say Cedega) to be optomizing this?  What if I'm just forgetting something in my BIOS to set?  (I didn't notice anything while tooling around there.)  

I'm just a little frustrated with the performance, even at low resolution and low settings--especially when I know I was getting better not too long ago.  (Shadows, etc!)  In some ways I'm just a complete newbie about linux and I have no earthly idea what to do.  Any help would be greatly appreciated--especially from people who might have a PCIe card, of course those with my exact card.

Apologies again about the meandering of the post, and Many Thanks.[/QUOTE]
 the performance on my gt6600 with the ubuntu nvidida driver is also poor. I was suggested to try with 16bit instead of 24bit.That doubles almost my fps in glxgears. It's kinda pity, because it looks terribly in most games!
Also try to quit programs like amule and other which might take on your performance

---

### Post by g-joey on 2005-07-27
> the performance on my gt6600 with the ubuntu nvidida driver is also poor. I was suggested to try with 16bit instead of 24bit.That doubles almost my fps in glxgears.I also have this card, and I'm curious to know which frame rates you get in glxgears.

I tested it and got everything from 7000 to 10500 fps. Is that slow?

//Joe

---

### Post by rwabel on 2005-07-27
[QUOTE=g-joey]I also have this card, and I'm curious to know which frame rates you get in glxgears.

I tested it and got everything from 7000 to 10500 fps. Is that slow?

//Joe[/QUOTE]
 in 16bit around 9000 without amule running. You shouldn't move windows or do anything while glxgears is running.
in 24bit it's around 5000

I guess around 9000 should be fine. just do the test without moving around or starting applications

---

### Post by DeezElbowz on 2005-07-27
[QUOTE=rwabel]in 16bit around 9000 without amule running. You shouldn't move windows or do anything while glxgears is running.
in 24bit it's around 5000

I guess around 9000 should be fine. just do the test without moving around or starting applications[/QUOTE]
 I get around 7K now, since I reverted completely back to 7174 so I wouldn't crash.  :-(

---

### Post by rwabel on 2005-07-27
[QUOTE=DeezElbowz]I get around 7K now, since I reverted completely back to 7174 so I wouldn't crash.  :-([/QUOTE]
 question remains, with 16 or 24bit?

---

### Post by g-joey on 2005-07-27
>  question remains, with 16 or 24bit? As far as I'm concerned, the 7000-10500 fps are for 24 bit colors. So I guess that's not too bad :)

BTW: Without working at the same time, the fps rate is always over 10000. But it drops after 4 minutes, when my screen saver starts... :-\"

BTW2: My CPU is an Athlon XP64 3000+

// Joe

---

### Post by rwabel on 2005-07-27
[QUOTE=g-joey]As far as I'm concerned, the 7000-10500 fps are for 24 bit colors. So I guess that's not too bad :)

BTW: Without working at the same time, the fps rate is always over 10000. But it drops after 4 minutes, when my screen saver starts... :-\"

BTW2: My CPU is an Athlon XP64 3000+

// Joe[/QUOTE]
 your values seems to be good, well the CPU is much better than my Athlon 2200+
The strange thing is that I only get acceptable values with 16bit, 24bit is inacceptable...damn

---

### Post by DeezElbowz on 2005-07-28
[QUOTE=rwabel]your values seems to be good, well the CPU is much better than my Athlon 2200+
The strange thing is that I only get acceptable values with 16bit, 24bit is inacceptable...damn[/QUOTE]
 Really another question of mine is this:  Has anyone had luck with either the 7664 or 7667 drivers?

---

