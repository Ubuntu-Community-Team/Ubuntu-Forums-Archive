---
title: "Can't Change Screen Resolution - Can only get 640x480 NOT NIVIDIA OR ATI"
date: 2008-05-22
forum: Hardware
---

### Post by seismicmike on 2008-05-22
I have an on board video card that I had working with full 1200 x 1024 resolution until I just reinstalled everything and now I can only get 640 x 480 resolution. I go to System > Preferences > Screen Resolution and 640 x 480 is the only option I'm given.

I KNOW this monitor can do higher resolution because I just had it working. I KNOW its not a malfunction of the card b/c I can boot into Windows and it works fine. I KNOW it's not a proprietary driver b/c I never needed it before.

Please help.

PS. I'm running Gutsy (7.10)

---

### Post by housam on 2008-05-22
open your xserver-xorg
```
sudo dpkg-reconfigure xserver-xorg
```

and press enter for every thing ( leave every thing as it is ) till you get the sitting page as in the [[COLOR="Red"]_Image_[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=70453&d=1211042863") and select 1280x1024 or whatever you want ( by pressing space ) and continue to go out.

---

### Post by Steve Lyne on 2008-05-22
Hi, I am having the same problem. I have just installed Ubuntu on a clean hard drive. The computer and screen run perfectly ok if I install a hard drive with Windows on, so I know all my hardware works.
I have tried to find a cure on the various postings but being an absolute Ubuntu beginner the suggested solutions make no sense. I have tried going into terminal but come unstuck with the commands.
I have an MSI motherboard and a Nvidia Geforce Fx 5200.
Regards
Steve

---

### Post by Spikehead on 2008-05-22
That advice about dpkg-configure is good, if you get the option as shown in the image. I only get keyboard coniguration qestiosn. :mad:

---

