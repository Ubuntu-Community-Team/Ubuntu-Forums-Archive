---
title: "Dual monitor (fireglcontrol not working)"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by lozzd on 2005-04-16
Hey there
Newbie question here.

I've sucsesfully broken X, fixed it, and followed the excellent guide at [http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557) to install the ATi drivers, which are now working fine. 

I have a Radeon 9800 Pro which I want to get dual monitors working with, at the moment they're just cloning. I run the **firefglcontrol** (tried it with sudo too) and click the DualScreen tab, select Extend desktop horizontal, click ok, it says the changes have been made and to restart. So i do, and its back to before again. What could be the problem here? On the Adjustment tab I can change the gamma values of each monitor so it definately knows there are two, its just it refuses to "remember" the "Extended desktop horizontal" option.
Can't live without dual monitors! please help!

Thanks
Laurie

---

### Post by bobmitch on 2005-04-16
Hey Laurie,

Unfortunately, the ati control panel program is useless for config changes.  You`re gonna have to get your hands dirty making a dual display config file.

You can see both my **fglrxconfig** generated hardware 3d accel config, and my hand-crafted xinerama software open gl config [HERE](http://www.ubuntuforums.org/showthread.php?p=111644#post111644) .

Hopefully you can make use of either of these to get things going.

If you have a hand-made fglrx driver based config file based on the fine HOWTO you followed, adding the following options to the device setting might work (but I can`t be sure, as I used a different method of making my configs).

```
Option "DesktopSetup"               "0x00000201"
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "ScreenOverlap"              "0"
``` 

Certainly, the DesktopSetup using that hexcode is necessary to tell fglrx driver to use large-desktop mode, as xinerama doesn`t work.

---

### Post by lozzd on 2005-04-16
Thanks for the quick reply.

I simply added that line of code you gave at the end of your post and I now vaguely have some dual monitors.. well... First of all my right hand monitor should be my left hand one, i.e. the displays are the wrong way round. Secondly, the second display (currently the left one, should be the right) is running at 640x480@60hz... any quick and easy way to fix these two? I dont mind getting my hands dirty as you say but only if I know exactly what to type where! ;) 

Thanks very much
Laurie

---

### Post by bobmitch on 2005-04-16
Ok, to swap the screens, change the desktopsetup option to "0x000000200"

You will need 2 Monitor sections, with the appropriate modelines and the appropriate settings for your 2 monitors. The driver will use the same modeline for both screens and it will select it according to the lower spec monitor. So if you have a 640x480 capable monitor and a 1600x1200 one, big desktop will use a 2x(640)x480.

Without seeing your config file, I can`t tell you what to type or where.  Even then, I`m pretty new to this myself, so take what I say as friendly advice, rather than gospel truth. :)

To make things easier (for me as well ;) ) , I`d back up your existing xorg.conf file, then replace it with the fglrx one I pasted a couple of msg's back, making sure to change the desktopsetupoption from 201 to 200, and also making sure the BusId in the ATI device section matches yours.

ie.  Mine is:   BusID "PCI:2:0:0"

To find out what yours should be, run:

```
lspci | grep -i "ati tech" | grep -v -i "secondary"
``` 

Which returns the following for me:

```
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
```

---

### Post by lozzd on 2005-04-16
Thanks so much for yourhelp!
I added the "modelines" line from your file, since i was slightly wary about copying the whole thing (have already killed the X server twice today didnt fancy it again ;) ) and swapped the value to make the screens the right way round and its working great now, so thanks very much! its much more at home now. Just gotta install VMWare (fingers crossed) and hopefully everything will be sorted...
Anywho, one last thing, all the dialog boxes, and the logon screen all go beautifully smack bang in the middle of both my monitors.. not really too convenient (btw for your reference my two TFTs are identical) i was just wondering if its possible to make all the boxes appear centered (or at least somewhere else) of either screen.
Thanks soo much for your time

Laurie

---

### Post by bobmitch on 2005-04-16
[QUOTE=lozzd]Thanks so much for yourhelp!
I added the "modelines" line from your file, since i was slightly wary about copying the whole thing (have already killed the X server twice today didnt fancy it again ;) ) and swapped the value to make the screens the right way round and its working great now, so thanks very much! its much more at home now. Just gotta install VMWare (fingers crossed) and hopefully everything will be sorted...
Anywho, one last thing, all the dialog boxes, and the logon screen all go beautifully smack bang in the middle of both my monitors.. not really too convenient (btw for your reference my two TFTs are identical) i was just wondering if its possible to make all the boxes appear centered (or at least somewhere else) of either screen.
Thanks soo much for your time

Laurie[/QUOTE]

You're very welcome.

Unfortunately, the only way to make logons / dialogs appear central in a monitor as opposed to the screen is to use the Xinerama extension, and hope that the application has been coded to take it into account.  As you know, the fglrx driver doesn`t support Xinerama, so the answer is no, you are stuck with that behaviour.

You could always run an x server in each monitor, but then you won`t be able to drag windows / application between monitors.  Not a good compromise imho.

Good luck with VMWare. :)

---

### Post by lozzd on 2005-04-16
Hehe ok thanks, i'm sure i'll get over it! :)

VMWare excellently btw :P 
I've been using Windows for years and years and i've finally installed Ubuntu on my main PC after trialling it on another PC. Its so powerful! I have Windows XP Pro running in a window on my second monitor now running MSN Messenger (can't do without the latest version, how sad *rolls eyes*) and its still running at 20% cpu usage with my everyshowsucks.com stream and a webcam running in XP. Excellent stuff!

Anyway thanks again for your help

Laurie

---

### Post by buz on 2005-04-27
> **bobmitch]Ok, to swap the screens, change the desktopsetup option to "0x000000200"

You will need 2 Monitor sections, with the appropriate modelines and the appropriate settings for your 2 monitors. The driver will use the same modeline for both screens and it will select it according to the lower spec monitor. So if you have a 640x480 capable monitor and a 1600x1200 one, big desktop will use a 2x(640)x480.

Without seeing your config file, I can`t tell you what to type or where.  Even then, I`m pretty new to this myself, so take what I say as friendly advice, rather than gospel truth. :)

To make things easier (for me as well  said:**
> 
```
 Is there ANY way at all to either get radeon or fglrx on a Radeon 9000 to use DIFFERENT resolutions in Xinerama use (dual head is kinda useless if you can't drag stuff around :-(? 

I've got a 20" LCD on the VGA port which I'd obviosuly really rather run with 1600*1200 and a 17" one at the DVI port which sets my whole Xinerama setup down to 2*1280*1024.

It is NOT a hardware problem, Windows does it just fine!

---

