---
title: "Wacom stylus not working on Thinkpad x201 Tablet under Xubuntu 15.04 beta"
date: 2015-04-22
forum: Hardware
---

### Post by mrbigmouth502 on 2015-04-22
I recently purchased a used Thinkpad X201 Tablet from Ebay, and while the inbuilt touchscreen (single touch w/ stylus only as far as I can tell) and stylus work just fine on Windows 7, I have been unable to get them working on the Xubuntu 15.04 beta. I've heard that earlier versions of Ubuntu supported this laptop and its touchscreen, so I'm wondering where the regressions have been introduced, and how I can fix them. I know that 15.04 is only a beta and that I should probably be sticking with 14.04 until its official release, but I don't want to risk having the Shellshock vulnerability, even just temporarily.

From the resarch I've done, I've found that the touchscreen this laptop uses is actually a Wacom serial tablet, which I find to be unusual for a machine of its age. There is evidence that this tablet is receiving input, as I get output in the terminal whenever I run ```
sudo inputattach --dump /dev/ttyS0
``` and move the stylus in front of the screen, though when I run it without sudo I get "permission denied". If I try to run ```
inputattach --w8001 /dev/ttyS0
``` without sudo I get "permission denied", and with sudo I get "inputattach: can't set line discipline".

These are some of the pages I have consulted thus far on the issue:
[http://ubuntuforums.org/showthread.php?t=1780154&page=23](http://ubuntuforums.org/showthread.php?t=1780154&page=23)
[https://groups.google.com/forum/#!topic/android-x86/U3EdLn5eK0U](https://groups.google.com/forum/#!topic/android-x86/U3EdLn5eK0U)
[http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus#systemd](http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus#systemd)


If it makes a difference, I'm currently running the latest x86-64 Zen Liquorix kernel, 3.19-5 to be exact. The stylus didn't work with the generic kernel either, however. I even tried compiling a custom Liquorix kernel and messing with the driver options, but this only compounded my problems, so I went back to using the official Liquorix kernel.

This isn't mission critical, but I am running out of patience here. Should I just take the plunge and downgrade to 14.04, or even 13.04? Or is there a way that I can fix this?

Thanks. :)

---

### Post by mrbigmouth502 on 2015-04-23
Anybody? I'm kinda lost here.

---

### Post by philipptrenz on 2015-04-24
Hey,

same problem here. In 14.04 as well as 14.10 the wacom and touch worked out of the box. Since upgrading to Vivid yesterday it doesn't work anymore ...

Thanks for help!

---

### Post by mrbigmouth502 on 2015-04-24
I decided to load up Manjaro just to see if my stylus would work, and miraculously, it does. It's even more accurate than it is on Windows too. I wonder what it's doing differently that's allowing it to work. I also tried it out with Android x86, the 4.0-r1 Thinkpad build to be exact, just for the heck of it, and while my stylus worked, it wasn't precise at all.

Anyway, when I was looking through the mouse options in Manjaro, I noticed that my tablet screen was detected as a "Wacom Penabled Serial Tablet". It was also running on an older kernel, based on 3.16. Now I wonder if regressions in the kernel have something to do with this. I might boot back into Manjaro and upgrade the kernel to 3.19 or 4.0 to see what happens.

---

### Post by lesilvestre on 2015-04-25
I'm having the same problem. The touchscreen and stylus are dead after upgrading to 15.04. They used to work out of the box in all previous versions since I bought the laptop a few years ago.

When I try xinput, it does not list either the touchscreen or stylus. It used to.

If anyone figures out what's going on, please share.

---

### Post by wn_bluebird on 2015-05-05
Same for me. I don't think it's kernel related, since "sudo inputattach --dump /dev/ttySN" (n=4 for me) works, regardless of the kernel (I tested 4.1 and 3.16 stock as well).

Any news, ideas?

---

### Post by blakkat on 2015-05-08
I had the same problem on my X201 tablet, upgraded to vivid, stylus wouldn't work anymore. 

I think the problem is that in the xserver-xorg-input-wacom package serial support was depreciated.
In particular, the wacom_w8001 module is not available. 
I followed the instructions from the wacom-linux project 
([http://linuxwacom.sourceforge.net/wiki/index.php/Input-wacom](http://linuxwacom.sourceforge.net/wiki/index.php/Input-wacom)) to compile and install the wacom and wacom_x8001 modules.

It turned out that the inputattach coming with viwid did not work for me. So, I needed to compile also the the inputattach command provided in the same tarball. 

So the steps were:

1) Download, compile and install wacom drivers from [http://linuxwacom.sourceforge.net/wiki/index.php/Input-wacom](http://linuxwacom.sourceforge.net/wiki/index.php/Input-wacom).
load both modules: 
```
sudo modprobe wacom
sudo modprobe wacom_x8001
```

cd into the inputattach tree and follow instructions in README file. Compile and start inputattach with
```
./inputattach --wacom /dev/ttyS<#>
```
, where you need to make a guess where your wacom device is registered. Mine was on ttyS4 and not on ttyS0 as frequently suggested. I hope it works for you guys, too. [FONT=monospace]

[/FONT]

---

### Post by wn_bluebird on 2015-05-11
Awesome! After falling back to windows for one week because of that, I was finally able to switch back due to your help.
Thanks a lot!

For finding out ttyS#, you can get hints from

```
dmesg | grep wacom
```

For the record, hardware was a Fujitsu Siemens T5010, and I found the Wacom device at ttyS4 as well.

---

