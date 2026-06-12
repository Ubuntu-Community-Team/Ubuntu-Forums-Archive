---
title: "ATI Mobility Radeon HD 3650 &amp; Ubuntu 10.04"
date: 2010-05-06
forum: Hardware
---

### Post by neu5eeCh on 2010-05-06
Just installed 10.04 on my VAIO with the aforementioned video card. After installation, Ubuntu asked to install the proprietary drivers for full 3d (and some 2D) acceleration. However, after installing, Ubuntu had trouble recovering from screen savers (on screen graphics would go chaotic when trying to log back in from the screen lock). Even though I couldn't see the logon window (there only being gobbledygook), if I typed in my username and password, the desktop would reappear in all its former glory.

(My system is 64Bit by the way.)

Secondly, I notice that the initial splash screen (when booting Ubuntu) was no longer high resolution but 600x480 or some such thing. After uninstalling the ATI drivers, everything has gone back to normal. I still have Compiz effects, etc...

Question: I'm not a gamer. Is the proprietary driver really necessary?

---

### Post by pavmav on 2010-05-24
My problem is very close to this one: 

Ati Radeon 3650 HD is my video
64-bit system 

Even with the drivers there is not smoothness in maximizing or minimizing the windows/players/etc it actually freezes for like half a second. I have the 3D effects and compiz and they run smoothly but maximizing and minimizing windows is ... idk not working good.

---

### Post by Yellow Pasque on 2010-05-24
> Even with the drivers there is not smoothness in maximizing or minimizing the windows/players/etc it actually freezes for like half a second.
You can try enabling Direct2D.
```
sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
```
Log out and back in to restart X and make the setting apply.

To undo:
```
sudo aticonfig --del-pcs-key=DDX,Direct2DAccel
```
Again, you need to restart X to make it take effect.

---

### Post by Yellow Pasque on 2010-05-24
> Secondly, I notice that the initial splash screen (when booting Ubuntu) was no longer high resolution but 600x480 or some such thing.
This is unavoidable with Catalyst/fglrx and also the nvidia binary drivers, because the don't use KMS (kernel mode-setting) like the open-source drivers.

---

### Post by NeverHide on 2010-06-29
> **Temüjin said:**
> You can try enabling Direct2D.
[code]sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE[/code





I tried this and i got this [http://img696.imageshack.us/i/screenshotpdw.png/](http://img696.imageshack.us/i/screenshotpdw.png/)
Then i tried the "aticonfig --initial"
and i got this [http://img812.imageshack.us/i/screenshot1nl.png/](http://img812.imageshack.us/i/screenshot1nl.png/)

Any suggestions?[IMG]http://img696.imageshack.us/i/screenshotpdw.png/[/IMG][IMG]http://img696.imageshack.us/i/screenshotpdw.png/[/IMG][IMG]http://img375.imageshack.us/i/screenshottm.png/[/IMG]

---

### Post by Yellow Pasque on 2010-06-29
> **NeverHide said:**
> I tried this and i got this [http://img696.imageshack.us/i/screenshotpdw.png/](http://img696.imageshack.us/i/screenshotpdw.png/)
Then i tried the "aticonfig --initial"
and i got this [http://img812.imageshack.us/i/screenshot1nl.png/](http://img812.imageshack.us/i/screenshot1nl.png/)

Any suggestions?[IMG]http://img696.imageshack.us/i/screenshotpdw.png/[/IMG][IMG]http://img696.imageshack.us/i/screenshotpdw.png/[/IMG][IMG]http://img375.imageshack.us/i/screenshottm.png/[/IMG]
Back up your xorg.conf and create a clean one: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file)

---

### Post by yannoo on 2010-12-29
I'm using Ubuntu 10.10 64bit with the same graphic card.

The aticonfig --initial does create a new xorg.conf file for me, but restarting gdm didn't get me back into the graphic session (disconecting, failed, then sudo /etc/init.d/gdm restart, failed again).

I had to recover my initial xorg.conf to make it work again after another /etc/init.d/gdm restart:

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

For some reason, now that I have restarted, it seems xorg.conf has been deleted (obviously in 10.10 things are handled a bit differently by default).

Still looking around for a solution to use my nice Radeon HD 3650...

---

### Post by sethtriggs on 2011-01-25
> **yannoo said:**
> I'm using Ubuntu 10.10 64bit with the same graphic card.

The aticonfig --initial does create a new xorg.conf file for me, but restarting gdm didn't get me back into the graphic session (disconecting, failed, then sudo /etc/init.d/gdm restart, failed again).

I had to recover my initial xorg.conf to make it work again after another /etc/init.d/gdm restart:

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection

For some reason, now that I have restarted, it seems xorg.conf has been deleted (obviously in 10.10 things are handled a bit differently by default).

Still looking around for a solution to use my nice Radeon HD 3650...

I'm in the same boat here. I can force the system to use vesa, but for some reason the vesa driver makes my mouse act up (the vertical and horizontal scrolling is out of control and it makes it all but impossible to select things). I upgraded from 9.10 to 10.04 in order to get another program working. I hope I haven't made a critical mistake.

I have a Radeon HD 3650 as well; that was the last AGP card I could get.

-Seth

---

