---
title: "can't set external monitor to correct resolution"
date: 2011-08-04
forum: Hardware
---

### Post by kedmond on 2011-08-04
I am running Ubuntu 11.04 on a Dell Latitude E6400 that uses a Quadro NVS 160M video card.

The native resolution of the laptop's display is 1440X900, and that works just fine.  I installed the Nvidia drivers using the "Additional Drivers" utility in the "System->Admin" menu.  I'm pretty sure video acceleration is working correctly.

I have used a 19" 1280X1024 Dell LCD display for a number of years since Ubuntu 9.  I did a completely clean install of 11.04 and now the monitor cannot display 1280 X 1024.  The max. resolution the external display will show is 1024 X 768. 

I have tried a number of things and nothing has worked.  I'm desperate for help.

Under the Nvidia X Server Settings the monitor is listed as a "CRT-0" and it is connected via VGA.  I'm successfully using TwinView, but not at the correct resolution.  I have tried editing my xorg.conf file myself, but it has no effect.

Please let me know what additional information you all may need if you can help.  Thanks.

---

### Post by Neutrosider on 2011-08-05
i had quite the same problem. reading through this thread might help you:
[http://ubuntuforums.org/showthread.php?t=1812872](http://ubuntuforums.org/showthread.php?t=1812872)

thats where my problem got solved :)

---

### Post by realzippy on 2011-08-05
*I have tried editing my xorg.conf file myself, but it has no effect.*

please show/attach the file and your
/var/log/Xorg.0.log ...


@Neutrosider

hi there !

---

### Post by kedmond on 2011-08-05
> **Neutrosider said:**
> i had quite the same problem. reading through this thread might help you:
[http://ubuntuforums.org/showthread.php?t=1812872](http://ubuntuforums.org/showthread.php?t=1812872)

thats where my problem got solved :)

Thanks!  I'll work through this thread.

In the mean time...

> **realzippy said:**
> *I have tried editing my xorg.conf file myself, but it has no effect.*

please show/attach the file and your
/var/log/Xorg.0.log ...


...I've attached my log file.  Thanks again!

---

### Post by realzippy on 2011-08-05
..and xorg.conf ? (btw,common no-edid-issue)

---

### Post by kedmond on 2011-08-05
> **realzippy said:**
> ..and xorg.conf ? (btw,common no-edid-issue)

To be specific, I turned off my laptop's monitor.  So this ONLY my external monitor.  If you press the configuration button on the front of the monitor, the onscreen menu that pops up says it's displaying at 1024 X 768 while it's optimal resolution is 1280 X 1024.  Information about the monitor is here: [http://support.dell.com/support/edocs/monitors/1908fp/en/ug/about.htm](http://support.dell.com/support/edocs/monitors/1908fp/en/ug/about.htm)

I just followed the steps on this website ([http://www.arunviswanathan.com/node/53](http://www.arunviswanathan.com/node/53)) but ran into an error when I attempted to add a new mode with xrandr.

Thanks again.

---

### Post by realzippy on 2011-08-05
can you run 
```
sudo nvidia-xconfig
```
and post the file again ?
Or is it fresh,means you have not edited anything?

Edit.
Just see you have not edited Hsync/Vrefresh values:
which should be according to your [link]("http://support.dell.com/support/edocs/monitors/1908fp/en/ug/about.htm#Specifications")
H 30-81
V 56-76

---

### Post by kedmond on 2011-08-05
I JUST FIXED IT!!!!


realzippy, I did what you said in this post: [http://ubuntuforums.org/showthread.php?t=1812872&page=2](http://ubuntuforums.org/showthread.php?t=1812872&page=2)

I went into the xorg.conf and changed the frequency ranges from their default values to the range specified in Dell's table: [http://support.dell.com/support/edocs/monitors/1908fp/en/ug/about.htm](http://support.dell.com/support/edocs/monitors/1908fp/en/ug/about.htm)

I rebooted, and the Nvidia X Server Settings let me choose any approved resolution.  It works really well now.

I'm so relieved.

---

