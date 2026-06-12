---
title: "ATI 8 series all in Wonder"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by Merry on 2007-07-23
I recently got hold of an ATI 8 series card with TV tuner. Am I mad for thinking of using it on my Ubuntu rig?

More to the point is there anything I need to do in order for it to work, if it will?

---

### Post by dannyboy79 on 2007-07-24
i believe that card will work with something like tvtime but definitely NOT mythtv. You can always just use the graphics portion of it IF it's better than your current graphics card.

If the installer didn't properly setup your card to use the ATI driver, then you can use this command

sudo dpkg-reconfigure --priority=high xserver-xorg

according to this bug report: 
[https://bugs.launchpad.net/ubuntu/+source/discover-data/+bug/121906](https://bugs.launchpad.net/ubuntu/+source/discover-data/+bug/121906)

Then just look into linux tv app's like tvtime or avview.

Here's a thread already devoted to the subject. [http://ubuntuforums.org/showthread.php?t=46496&highlight=ATI+AIW&page=2](http://ubuntuforums.org/showthread.php?t=46496&highlight=ATI+AIW&page=2)

---

