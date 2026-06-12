---
title: "Wacom Cintiq 21ux"
date: 2009-10-17
forum: Hardware
---

### Post by ddeo on 2009-10-17
Hi All, I have a Cintiq 21ux that I have connected to my laptop running ubuntu 9.04

When I first hooked it up the stylus worked right away with no software changes but the cursor is not anywhere near the stylus point.  I figured that i had to calibrate it much like you would on windows or mac but there was no utility that I could find easily.

I have spent a fair amount searching these forums and the linuxwacomproject page and at least figured that the tool that I think I need to run is wacom-tools.  When I try to run it it says that the program is not found.

I then installed the latest driver using this method:
[https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver)

No I am up to date with 0.8.4-3 (i think)

Now the stylus will not move the cursor at all.

If anyone has any experience and would like to help me out it is greatly appreciated.  Thanks, Ddeo

---

### Post by Favux on 2009-10-17
Hi ddeo,

You need to check if you still have a 10-wacom.fdi installed.  Jaunty uses the HAL/.fdi method.  You could probably configure through xorg.conf if the 0.8.4-3 install was succesful.  You lose hot plugging using xorg.conf.

You may want to uninstall linuxwacom 0.8.4-3 and go back to the default Jaunty packages.  To uninstall see Appendix 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Then to set things up with the default Jaunty packages and get a little more explanation see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  Also see this Cintiq thread starting at post #61 here:  [http://ubuntuforums.org/showthread.php?p=7247502](http://ubuntuforums.org/showthread.php?p=7247502)

So look things over before deciding what to do.

---

