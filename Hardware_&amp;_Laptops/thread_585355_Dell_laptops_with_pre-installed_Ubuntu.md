---
title: "Dell laptops with pre-installed Ubuntu"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by red devil on 2007-10-21
Hi all,
I was wondering if anyone has bought one of the Dell laptops that come with Ubuntu pre-installed, and if so, what did you think of them?
I've got one on loan (a Dell 6400 - I'm in the UK) so I can do a review for my newspaper column, but it would be interesting to hear if anyone has got one and has anything positive or negative to say.
I've got mixed feelings about the one I've been using but don't want to be too critical as I believe Dell have done the world a favour by opting for Ubuntu - it's high time the other manufacturers took similar steps.
Look forward to your comments.
Cheers,
Red Devil

---

### Post by Linicks on 2007-10-21
I purchased a UK Inspiron 6400 in September, and all I can report is I am very, very pleased with it.  No issues at all, even after upgrading to Ubuntu 7.10 yesterday.

But having said that, I am a hardened GNU/Linux user of 8 years, so silly issues that took me seconds to resolve might be an issue for a newish user.

My last word is - if I had to go back and buy a laptop with pre-install GNU/Linux again, I would still buy this.

Nick

---

### Post by red devil on 2007-10-22
Hi Nick,
Thanks for the response and I´m glad you&#341;e so happy with your 6400.
Did you have to do anything to get the resolution set properly?
As I´m sure you know, the machine is capable of 1280x800 but the one I got was only working at 1024x768 - even though the xorg.conf had 1280x800 as its only option.
After some Googling I found this was a fairly common problem (I ran into the same issue on a different widescreen Dell when I installed Zenwalk a year or so back).
I had to apply the 915resolution patch to get the correct resolution which, while it isn´t a problem for those with plenty of Linux experience, would surely baffle most new users.
This is close to being a deal-breaker for me - the incorrect screen res makes the display look dreadful with stretched, fuzzy fonts - which is a shame because generally the machine works fine (I have several other issues but they&#341;e fairly minor in the great scheme of things).
Anyone else out there with any views on this issue?
Cheers,
Red Devil

---

### Post by Linicks on 2007-10-22
To be honest, it is all on the Dell wiki - what problems to expect and how to fix them up.

I did a bit of reading here first, so when I did get the issues, I knew what issues to expect and just followed the wiki - all hunky dory.

[http://linux.dell.com/wiki/index.php/Products/Client](http://linux.dell.com/wiki/index.php/Products/Client)

and the resolution issue:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues)

I also see now they have updated it to include Gutsy 7.10 too!

Nick

---

### Post by red devil on 2007-10-22
Hi Nick,
Thanks for responding, but I think maybe you understood me. I've fixed the display issue myself (and the other minor issues I had). The purpose of my original post was not to ask for help with problems; rather, I wanted to gather some opinions from fellow Ubuntu users on the Dell machines with Ubuntu pre-installed.
Thanks,
Red Devil

---

### Post by Linicks on 2007-10-22
Well, as my first post - I am extremely happy with it.

Nick

---

### Post by tschneiter on 2007-10-22
Howdy-

I did not purchase my dell with linux preinstalled, but rather installed after receiving it. With every Ubuntu release, I am seeing better compatibility out of the box. I, too had trouble with my resolution not setting itself properly in feisty. However, in Gutsy (the newest version), using the xserver-xorg-intel driver (that is now installed by default), the resolution worked perfectly out of the box. The only thing that did not work properly out of the box was my wireless card; I (stupidly) bought a lappy with the dell draft n card, which is powered by Broadcom. Sad thing is that broadcom will not release their source so the linux community has been struggling with making broadcom wifi work for ages now. The solution was just to install ndiswrapper.

So, with the new version I am seeing greatly enhanced support, out of the box. I assume that when dell starts shipping gutsy, even more problems will be resolved. Finally, when Hardy is released (in 6 months or so) I think we'll see the best stability and performance yet.

Hope this helps in some way,
-T

---

