---
title: "Asus A6jc Q003, bisoncam, ricoh CR, TP button don`t work"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by XomboX on 2006-08-27
Hi guyz! 
I have bought a new notebook Asus A6jc Q003 recently. It is cool! And it did not cost a fortune :)
However I have got some problems with hardware in Ubuntu:

[color=#000099]Webcam BisonCam 1.3mgpx[/color]
I think it is based on m5603c chip, it is said it worked with the m560x drivers ([http://www.actiongames.co.uk/m560x/forum/viewtopic.php?t=63](http://www.actiongames.co.uk/m560x/forum/viewtopic.php?t=63)), but I was not able make it work :-(


[color=#000099]RICOH Media card reader[/color]
I have tried only memory stick card. It could not read it :-(

[color=#000099]"TouchPad off" button[/color]
It has got a synaptic touchpad. I have tried few drivers but the buttons still does not work. It is really annoying when you use a mouse and you touch the TP during writing on keyboard :frown: 
And the touchpad scrolling does not work too :mad: 

Everything else works well for me.The graphic card geforce 7300 is great! :D  and I love the LCD Crystal View display!!

I have installed linux-686-smp.
The temperature is about 55&#730;C, stressed: comes up to 60-70&#730;C.

If anyone knows how to fiw the hardware issues, please post it here. I would be greatful! 

Thanks!!

---

### Post by chiefofthejojos on 2006-09-04
I have had an Asus A6U for a year now and have had exactly the same issues.  

Touchpad:
A lot of people have the same issue.  It's listed as a bug at launchpad.net: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/37234](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/37234)
I didn't bother to read through the whole thing so I don't know if there's a workaround or not.

Card reader:
I don't know about this.  I just came to the forums to look for this when I found your thread.  But I thought I heard of a way to get it working that requires a recompilation of the kernel.

Webcam:
I have been following the development of this driver for a while.  I believe that the current "working" driver only works with the test application that willem has written.

---

### Post by teh_howch on 2007-01-23
[FONT="Arial"]My buddy helped me fix the same touchpad problem (no vertical scroll, no double-tap drag) with an addition to the /etc/X11/xorg.conf text file

My system, btw, is an Asus Z96Js, and said buddy is using an Asus W3J.

To fix:
$ sudo gedit /etc/X11/xorg.conf

In the text file:
-Under 'Section "ServerLayout" ' add 'InputDevice    "Synaptics Touchpad" '
-Create in xorg.conf:
```
Section "InputDevice"
       Identifier   "Synaptics Touchpad"
       Driver         "synaptics"
       Option        "SendCoreEvents" "true"
       Option        "Device" "/dev/psaux"
       Option        "Protocol" "auto-dev"
       Option        "HorizScrollDelta" "0"
EndSection
```
-Once that section is added to xorg.conf, reload X fix the bug.
Note:  make sure you have /dev/psaux before saving....


As for the card reader, I tried a standard SD card from a digital camera and it worked fine.  My buddy tried a Memory Stick, and it didn't work on his computer.  In other words, no clue.

Any news on the BisonCam driver?  I would really like to use the camera.[/FONT]

---

### Post by cmavr8 on 2007-02-08
I have a Lenovo 3000 V100 which has Bisoncam NB. 
Hasn’t anyone tried the windows driver in linux?

---

### Post by dangerboy_ds on 2008-03-04
This worked for me, although i have to build and load it everytime i reboot the system...


But hey... it works...

My lap-top is Asus A6Jc,

```

$ make -f Makefile.standalone clean
$ make -f Makefile.standalone
$ modprobe videodev
$ insmod stk11xx.ko
```

These are the commands... for more info read the README.txt in the tar.gz file ;)

[http://rapidshare.com/files/97076983/stk11xx-1.2.3.tar.gz](http://rapidshare.com/files/97076983/stk11xx-1.2.3.tar.gz)

this is the archive with the driver ;)

Hope it helps

---

### Post by cmavr8 on 2008-03-06
Thanks for the info, but doesn't work on my V100.

Did compilation, but camorama still says "Could not connect to video device (/dev/video0). Please check connection."

---

