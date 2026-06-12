---
title: "OS Upgrade Grub REPLACE versus Keep?"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by gmgj on 2009-06-07
During the upgrade to Jaunty, the upgrade asked if I wanted to replace or keep GRUB menu.lst and gave me a number of options for viewing / comparing the differences between the the new file and the old one.  

If you keep the old menu.lst, will it add entries for the new version?

=========================
Can someone please suggest to the install team that, at least in GRUBS case, they keep a backup copy of menu.lst and possibly any other user edited files?

========================

---

### Post by celticbhoy on 2009-06-07
If you keep the old grub the entries for the new kernel will not be there. If you update the menu.lst a backup copy is made.

---

### Post by gmgj on 2009-06-09
Thanks for the reply, but I am still confused.  When I hit this part of the install, I went looking for an explaination.  I am not sure what I did, but I think I went forward with replace and then back, in which case, I think the backup copy turned into a copy of what I had just replaced.  An I wish I remember seeing update, but I did not.  I do remember seeing 2 way compares and 3way compares etc, but no update.

I am a newbie to linux, but I have been working with computers for over 30 years.  Yup, I know I probably shot myself in the foot, but, if I did it, I am quite sure a boatload of other people did it.  So anyway, I am at the point where I am trying to figure out how to find out where the Ubuntu firefox team is, cause I might be able to help them with testing.  For install, I am hoping that someone like you can pass this on to the install team.  A think a few subtle changes in the wording and presentation of the choices and a different scheme for backing up menu.lst might be benefical.  

Maybe its and area where the localization and translation teams needs to look at what is being done.

Writing software can be frustrating.  You get it 99.9999 right and still someone like me rights this kind of stuff.  I thought the upgrade worked really well.  I have been amazed at how well ubuntu works.  If they just saved my orginal menu.lst with either a version or date stamp, I would have not bothered with this post.  (EOR) End of Rant.  BTW, Thanks guys, Ubuntu is awwsome.  If I worked for Microsft, I'd be really embarassed.

---

