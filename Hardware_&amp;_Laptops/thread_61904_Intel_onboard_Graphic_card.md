---
title: "Intel onboard Graphic card"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by masteryoda on 2005-09-02
I am having intel 810 .. onboard graphics card.
When in grub menu.list vga=792/791/ etc... is used I get 

> You passed an undefined mode number.
Press <RETURN> to see video modes available, <SPACE> to continue or wait 30 secs.'

At this point, I hit the Enter key, and it gives me:

'Video Adapter: VESA VGA
Mode:
0 0F00 80X25
1 0F01 80X50
2 0F02 80X43
3 0F03 80X28
4 0F05 80X30
5 0F06 80X34
6 0F07 80X60
Enter mode number or 'scan''

Due to this I am not able to get bootsplash  of any type (splashy/upower) 
I have also searched the web and have realised that not even Suse's Bootsplash (kernel based) is able to do it... 
So in short the linux kernel itself is not supporting intel onboard graphics.
I know the chipset graphics is not that efficient... but if M$ can do it why not linux kernel?

Is there any solution for this?
Plz help us ... all those who r using chipset.

---

### Post by masteryoda on 2005-09-03
I have done some more searches on the web and have found this on intel website..............

Does the vesafb frame-buffer module work on the Intel® 810 and Intel® 815 Chipset Families?
No. The vesafb module can only make use of linear VESA modes. The Intel® 810 and Intel 815 chipset families use banked modes and therefore, cannot boot into a frame-buffer. It would be possible to add banked mode support to the vesafb driver, but as of yet there are no plans to do so. The vga 16 color frame-buffer available in recent Linux* kernels does function properly and can be used in place of the vesafb frame-buffer.

Thus 810 and 815 boards require new driver with vesafb drivers with banked mode support. So Can anyone plz tell me where I would get these??? 
Some developers have patched kernel to solve this .. refer:
[http://developer.momonga-linux.org/viewcvs/trunk/pkgs/kernel24/linux-2.4.25-i810fb-0.0.35.patch?rev=2881](http://developer.momonga-linux.org/viewcvs/trunk/pkgs/kernel24/linux-2.4.25-i810fb-0.0.35.patch?rev=2881)
Can Ubuntu devlopers do something for 810/815 board guys??? or some driver to support it???
Plz help us!!!

---

