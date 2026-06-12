---
title: "Serial Wacom tablets on Maverick"
date: 2011-03-28
forum: Hardware
---

### Post by LostKahuna on 2011-03-28
[FONT=Times New Roman][SIZE=3]I am very new to Ubuntu.  In fact, it was only yesterday when I reformatted one of my USB sticks and ran Maverick from there.  The browser worked without any intervention and in general, I am impressed with the other stuff I found in Ubuntu.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]However, my old Wacom Graphire tablet (serial) did not work on Maverick.  I use this tablet on Windows as a pen mouse to avoid RSI related issues I had in the past.  To win me over, the support for a serial tablet is absolutely essential!  Unfortunately, from a few web searches, I have gathered that the support for old serial tablets has been dropped.  Some people tried to work around this restriction by compiling the code with different patches.  Is there any success on Maverick?  Is there anyone out there running a serial Graphire on Maverick?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I am interested to recompile xf86-input-wacom if that’s what I have to tinker!  Please could someone explain the steps?  I have seen quite a few discussions on this topic but it is not clear to me whether a serial Wacom tablet would work on Maverick or not.  The selection of codebases and patches is also not clear.[/SIZE][/FONT]

---

### Post by Favux on 2011-03-28
Hi LostKahuna,

Welcome to Ubuntu forums!

> the support for old serial tablets has been dropped.
Correct, but due to lack of developer resources rather than by design.  If someone whips the serial patch set into good enough shape it would be included in xf86-input-wacom.

Yes folks have gotten the serial patch set working on Maverick.  Because the patch set only applies to xf86-input-wacom-0.10.6 (& 0.10.5) and 0.10.6 won't build on Maverick's X server 1.9 you have to use another patch.  So in addition to applying the second patch set on the linuxwacom-discuss link to xf86-input-wacom-0.10.6 you have to use a patch to get it to compile on X server 1.9.

See the links and explanation not far down from the top in the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").

---

### Post by LostKahuna on 2011-03-29
Hi Favux
 

 Thank you very much for your reply. I tried to follow your notes in applying the patches to xf86-input-wacom-0.10.6.  Your notes have suggested that I should use &#8220;./autogen.sh &#8211;prefix=/usr&#8221; to build the driver.  I couldn't find any autogen shell file and then realised that the build command would be different for the tarball.
 

 With &#8220;./configure && make&#8221;, I finally managed to build wacom_drv.so.  Not sure what &#8220;sudo make install&#8221; did but the newly built driver didn't appear in /usr/lib/xorg/modules/input.  Hence, I manually copied it from /home/ubuntu/Desktop/xf86-input-wacom-0.10.6/src/.libs.
 

 After restarting the X server, I was expecting some interaction with my serial Graphire but there was nothing in /var/log/Xorg.0.log.
 

 Obviously, I have to check/add a few things before it works.  Any tips from anyone?
 

 Thanks.

---

### Post by Favux on 2011-03-29
A fair number of folks report having to run wacdump to initialize their serial tablet.  Wacdump should only be run briefly otherwise it will segfault.

---

### Post by Favux on 2011-06-19
Hi LostKahuna,

I made a how to for serial tablets:  [http://ubuntuforums.org/showthread.php?t=1780154](http://ubuntuforums.org/showthread.php?t=1780154)  Maybe that'll help some.

My current guess is you didn't use the "ForceDevice" "SERIAL" option in the xorg.conf to tell the Wacom X driver it is dealing with a serial tablet.

---

