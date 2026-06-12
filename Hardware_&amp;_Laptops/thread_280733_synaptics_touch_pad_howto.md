---
title: "synaptics touch pad howto?"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by chefjames on 2006-10-19
Can anyone point me to a howto for this?  Searching the forums has not helped me any.  I have and old Micron Trek2 that I bought used.  I brought it back from the dead by installing Dapper.  It has both a little eraser mouse in the middle of the keyboard and a touch-pad.  The little eraser mouse works fine and so do the buttons for the touch-pad.  If I plug in a usb mouse that works too.  The touch-pad itself does nothing.  I would be happy to try any suggestions or provide more info if needed.  I am however pretty new to linux so please bear with me.  Your help will be much appreciated.

---

### Post by SendDerek on 2006-10-19
It might not be much, but I'm trying to be as helpful as I can on these forums tonight:

[http://ubuntuforums.org/archive/index.php/t-27851.html](http://ubuntuforums.org/archive/index.php/t-27851.html)
(It looks like this fellow might be having some of the same problems as you?)

> 
Untested commands follow:


% sudo aptitude install linux-source-2.6.10 kernel-package
% cd /usr/src
% sudo tar -x -j -f linux-source-2.6.10.tar.bz2
% cd linux-source-2.6.10
% sudo gunzip -c /usr/share/doc/xorg-driver-synaptics/alps.patch.gz | sudo patch -p1
% sudo cp /boot/config-2.6.10-5-386 ./.config ## or whatever you are currently running--note that there are two dots there, since the file is <dot>config
% sudo make-kpkg --us --uc --initrd --append_to_version "-5-386-alps" kernel_image kernel_headers kernel_source
% cd ..
% sudo dpkg -i kernel*alps*deb


I haven't tested these commands, but they look approximately correct. If anything fails, it will happen before the sudo dpkg line, which means you won't have screwed anything up.

Then just copy the InputDevice section from /usr/share/doc/xorg-driver-synaptics/README.alps and tweak to suit yourself, such as setting MaxTapTime to 0 to disable click-on-tap behavior, and reboot.


---

### Post by chefjames on 2006-10-20
Thanks,  

I havn't tried yet, but should I be concerned that this is kernel 2.6.10 and I have kernel 2.6.15-27?  Also being new to linux I am not sure I understand some of the syntax in the commands. I assume I can't type things in exactly as they appear, but I am not sure what to type instead.

---

