---
title: "No sound output"
date: 2004-11-16
forum: Hardware &amp; Laptops
---

### Post by Swad on 2004-11-16
I have Ubuntu running on an old Toshiba Tecra 8100 laptop.  The onboard sound is a YMF-744B sound card (PCI, not ISA based).  I previously had Debian unstable on this laptop and was using OSS sound (with success) because I had nothing but trouble with getting this card and ALSA to play nice with each other.  Well here I am with Ubuntu and I have no sound.  I can make audio apps *play* music... you see the progress bar churning away and the little meter (in XMMS) is moving to the music, so it's obviously reading the music fine.  I hear nothing, however, no matter how much I adjust sound.  I've used the Gnome volume controls, ALSA mixer, aumix, and I think that's it.  With everything maxed out I get nothing.  My regular user is a part of the audio group as well.  All of my sound modules (so it appears) are loaded... unless I'm overlooking one.

Anyway, is there something obvious I'm missing?  I can try to find a way to fudge OSS, but I'd rather not.

update: I thought the ALSA project page specifically listed this card, but it has no Yamaha listings.  it does, however, have listings for this chipset all over--YMF744B.  Maybe it's not really support?  :/

---

### Post by Crisp on 2004-11-16
I'm still having that exact problem, but the LiveCD works for me.  I've done everything you listed, but no luck.  It's really annoying.

-Crisp

---

### Post by absinthe on 2004-11-18
Me too :(

---

### Post by dninja on 2005-01-18
[QUOTE=][/QUOTE]
 Alsa doesn't work with the Tecra 8100. I've tried a few distros and all of them claim the same thing. OSS worked fine when I had gentoo on mine, I've just pujt ubunto on and am now going to try to get oss working now

---

### Post by gregh on 2005-01-20
I have a Toshiba A70 that worked until 2 days ago when the sound just stopped. (I am using Hoary, and upgrade every day)
The laptop *thinks* sound is playing , bit I cant hear a thing!!

EDIT: DOH, I had my sound turned down on the side of the laptop. Must have knocked it getting ot out the bag. I spent about 3 hours trying to work out what was going on.
I feel so stupid now.............

---

