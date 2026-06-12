---
title: "DELL Latitude C800"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by psychoshooter on 2009-11-12
Hello guys I have a problem which i found was more common.

Like here:
[http://www.baltimoremick.com/blog/2008/08/25/dell-latitude-c800-display-problems-with-ubuntu/](http://www.baltimoremick.com/blog/2008/08/25/dell-latitude-c800-display-problems-with-ubuntu/)
My screen has the exact same problem...

They say that, that is the fix, I tried to look for the menu.lst not there. I look for the xorg.conf not there.

What do I have to do? my screen looks exactly the same as on that website

Please help!

Kind regards,

Martijn

---

### Post by psychoshooter on 2009-11-13
*bump* sorry for the bump but i need to finish this laptop today

EDIT

got it solved :)
Since ubuntu 9.10 doesn't seem to create the xorg.conf it self you have to let it create.


```
# X -configure
~~ If successful ~~
# cp /root/xorg.conf.new /etc/X11/xorg.conf
# /etc/init.d/gdm restart (assuming gnome is your DE.  Could also be xdm, kdm, whatever)
```
Thanks to .walls from [www.overclockers.co.uk](www.overclockers.co.uk)
Refrence:  [http://forums.overclockers.co.uk/showpost.php?p=15245992&postcount=2](http://forums.overclockers.co.uk/showpost.php?p=15245992&postcount=2)

After this i opened it up and followed this post:
[http://ubuntuforums.org/showpost.php?p=977236&postcount=5](http://ubuntuforums.org/showpost.php?p=977236&postcount=5)

Quote:

> 
Edit /etc/X11/xorg.conf and add the following lines to 'Section "Monitor"':
 	Code:
 		HorizSync	31-82
	VertRefresh	40-110 
Do you have an ATI Mobility M4? If you do, you'll experience crashes when switching to a terminal or starting/stopping X. The problem is related to the Fn-F7 key. In the past the only way I could get it not to crash was to keep the screen unscaled, but this can be fixed by changing some settings:

Edit /etc/X11/xorg.conf again, and add these lines to 'Section "Device"':*
 	Code:
 	        Option          "AGPMode"               "4"
	Option		"AGPSize"		"32"
	Option          "EnablePageFlip"        "true"
        Option          "Display"               "BIOS"
	Option		"SWCursor"		"true"
        Option     	"CCEusecTimeout" 	"20000" 
Edit your grub config at /boot/grub/menu.lst, find the defoptions line, and add this part in red:
(because I didn't had the menu.lst i just created it.)
 	Code:
 	# defoptions=quiet splash [COLOR=Red]vga=0x311[/COLOR] scheduler=cfq 
Changing the scheduler to CFQ worked wonders on this laptop, you may want to change that setting too. Now, update grub's config: 	Code:
 	sudo update-grub 
Changes should take effect when you reboot your system. Hope that helps.

*Note that some of these tweaks are performance enhancements. Page flipping, for example, increases my glxgears score to ~714fps, and the CCEusecTimeout is a workaround to a nasty CCE idle bug in the r128 driver that can cause some games to crash badly. It's solved problems for several apps, but not for others (increasing the timeout may help). Changing AGPSize to 32 enables me to play some games where textures would be missing otherwise; in neverball, for example.


Thanks to: [psyke83]("http://ubuntuforums.org/member.php?u=50843") from [www.ubunuteforums.org](www.ubunuteforums.org)
Reference: [http://ubuntuforums.org/showpost.php?p=977236&postcount=5](http://ubuntuforums.org/showpost.php?p=977236&postcount=5)

Then I rebooted as he said but for me it didn't fixed it instantly, i had to change my resolution too 1400x1050(4:3)
Pressed apply and it was good :)

I hope this helps anyone else out in ubuntu 9.10 cause I had some search to do.

Thanks for all people that wrote posts on whatever forum which helped me to fix this error.

Kind regards,

Martijn

---

