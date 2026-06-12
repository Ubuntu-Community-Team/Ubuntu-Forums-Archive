---
title: "sound problems on thinkpad 600"
date: 2008-07-27
forum: General Help
---

### Post by sledge73 on 2008-07-27
I'm extremely new to linux & just installed xubuntu on a thinkpad 600 not the 600e or 600x but 600 & I cant seem to get the sound going if someone has any ideas or can hook me up with specific instructions I wound greatly appreciate it, thanks.

---

### Post by alfu on 2009-09-10
Here is a resource for [ installing on a Thinkpad 600]("http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_600").
Here is some software doodling [from this forum]("http://ubuntuforums.org/showthread.php?t=31226") you can do, but I'm not sure how permanent the results would be (your hard work overwritten by the Update Manager?) unless you wrote an executable to refresh the changes you made.

The problem is that the CS4239 Crystal Audio chip in this Thinkpad is a legacy device not supported in Ubuntu by default.  

So I took a hardware approach since I was donating a Thinkpad 600 to a disabled person for use as a recording studio.  I ordered a [Behringer UCA 202]("http://www.amazon.com/gp/product/B000KW2YEI") USB sound card.  You set it up in the System/Preferences/Sound menu (use the USB OSS Audio CODEC), and, aside from the dog-slow 400MHz performance of the Thinkpad, you should be good to go.

I recommend the Audacity music editor, it works well on the Thinkpad with this setup.  And although the VLC Media Player is a super program, it does not seem to go through the Gnome sound protocol, and does not play through an external USB sound device on this Thinkpad.

091006: Per sledge73's advice, I burned the Puppy Linux 4.3 install CD.  Booting on the 600, it jammed with a **[COLOR="Red"]pup-430.sfs not found. Dropping out to initial-ramdisk console ...[/COLOR]** error.  For now I will just have to accept it as one of those Linux distros that either don't work or are too doggone wierd (Gentoo) to bother dealing with.

---

### Post by sledge73 on 2009-09-10
Thank you very much!!!! I finally solved the problem by installing puppy on this machine & everything works perfectly. I would recommend puppy for anyone with this computer. Again thank you!

---

