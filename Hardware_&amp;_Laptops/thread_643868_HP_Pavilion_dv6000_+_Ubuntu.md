---
title: "HP Pavilion dv6000 + Ubuntu"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by Dawa on 2007-12-18
i guess this won't be a guide so much as a collection of links...  but hopefully it'll save someone some time.

Display settings:

my laptop came with an nVidia GeForce GO something or other.  To get it working right, I enabled the nvidia drivers from the Restricted Drivers Manager.  Then (here's where i was lost for a while) I went into the nvidia settings.  I'd like to say that the existence of this should be made a little more obvious.  I spent a lot of time swearing at System>Administration>Screens and Graphics before I found out you could go into a terminal and do a "sudo nvidia-settings".  Anyways....  go into a terminal and enter "sudo nvidia-settings".  Any settings you apply in the window that pops up should stick  (i.e. the resloution will stay the same as it was when you logged out).



To get the wireless working:

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

This guide worked wonders for me.



To get the speakers to mute if you plug in headphones or external speakers:

[http://ubuntuforums.org/showthread.php?p=3501600#post3501600](http://ubuntuforums.org/showthread.php?p=3501600#post3501600)

again, fixed the problem completely.



To get the lightscribe drive working:

[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

Download the .deb package for "LightScribe system software" and install it first.  Then get the .deb package for the lightscribe simple labeler program.  Be warned, this is a very good example of "simple".  It will only do extremely basic text labels.  I haven't tried any other label burning software, but the lightscribe site suggests LaCie and such, I believe.



and, as a bonus:

Getting Bluetooth stuff to work:

[http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

I ordered a Targus BT Notebook Laser Mouse with my laptop, and when i tried to use it i got "OBEX" errors galore.  I followed that guide (omitting the instructions to install the keyboard), and now my mouse works great.


Well, here's hoping this saves someone some time and stress.  Good luck!

edit: almost forgot.   THANK YOU to the people who posted the guides i linked to.  THANK YOU!!!!!!

---

