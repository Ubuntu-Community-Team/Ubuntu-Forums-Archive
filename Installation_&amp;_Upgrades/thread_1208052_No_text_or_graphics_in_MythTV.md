---
title: "No text or graphics in MythTV"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by paal on 2009-07-08
I'm trying to install MythTV on my Ubuntu 9.04. When I start mythtv-setup (or any other part of MythTV) it just gives me a coloured screen with some squares. There's no text or graphics. It appears that MythTV is complaining about that it "*Couldn't find theme /home/<user>/.mythtv/themes/Mythbuntu-8.04*". Probably it's with good reason because the folder themes in .mythtv does indeed not exist.
Any suggestion on how to fix this?

---

### Post by earthpigg on 2009-07-08
folders starting with a period are hidden, make sure you enable viewing hidden files/folders when you are looking for them.

if you are trying to install 9.04, why would it be looking for 8.04 themes, though?

this is running from a mythbuntu live cd?

---

### Post by lawhorne on 2009-07-08
I am having the same problem.  this is happening on a fresh install of 9.04, and it was happening with an upgrade to 9.04.  This was not a problem for me with previous versions.  any suggestions?

---

### Post by paal on 2009-07-09
> **earthpigg said:**
> folders starting with a period are hidden, make sure you enable viewing hidden files/folders when you are looking for them.

if you are trying to install 9.04, why would it be looking for 8.04 themes, though?

this is running from a mythbuntu live cd?
The .mythtv folder exist, but there's no theme folder in it. It's not running from a Mythbuntu live CD. I tried that too by the way and just the same happend.

---

### Post by Subaru4WD on 2009-07-09
I installed MythTV and am getting this exact same problem.  This is on two seperate machines, two different distro's.

First install was on my notebook, with Ubuntu 9 (downloaded yesterday).  Then i followed some guides and installed MythTV, but when I ran setup all I got were boxes, no text.  And a cursor that would change to a text input on hover.

So then I went and downloaded the ISO for Mythbuntu and installed that.  Install went fine, but when it came to setup MythTV, same thing as before.


-so-

I took the Mythbuntu CD over to my other PC, which is a desktop PC and just ran the Live CD portion of MythBuntu, but when it came time to run the MythTV Front end, i got a better looking screen... still boxes, no text.  Pretty blue colors though.

The laptop in the first install is a Dell D610 with a ATi X300 Mobile GPU
The Desktop is a homebuilt PC, with a nVidia Geforce 8600GT GPU

Anyone find a solution to this yet?

---

