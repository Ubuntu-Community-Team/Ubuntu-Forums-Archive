---
title: "Struggling with screen resolutions!  :("
date: 2008-08-20
forum: Hardware
---

### Post by danduq on 2008-08-20
Hi,

I'm really struggling to get my graphics driver working on anything over 800x600 on my Sony Vaio PCG-SRX41P. I have been following the guide in [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) and going through the forums, but have not had any luck.

I have tried reconfiguring x with "sudo dpkg-reconfigure xserver-xorg" but my monitor is not picked up. Using ddcprobe does not return either sync rate for my laptop screen.

According to "sudo lspci | grep -i vga" I have a;
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)

I have installed xserver-xorg-video-intel and added Driver "intel" to my xorg.conf, but still I only have 800x600 available.

Here is the result of my "ddcprobe"
[INDENT]vbe: VESA 3.0 detected.
oem: Intel815M(TM) Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: i815M Graphics Controller Hardware Version 0.0
memory: 1024kb
mode: 1280x1024x256
mode: 640x480x16m
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x32k
mode: 800x600x64k
edid: 
edidfail[/INDENT]

And here is the relevant section of my current xorg.conf;
[INDENT]Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection[/INDENT]

I did manage to track down the manual for the laptop online, and it said the LCD screen specs are; "10.4'' XGA (1024x768) p-Si TFT screen"

I'm not quite sure how to proceed, can anyone point me in the right direction please?

Thanks.

---

### Post by ggaaron on 2008-08-20
Can you post output of 'xrandr' command?

---

### Post by danduq on 2008-08-20
Here is the output of xrandr;
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0     56.0* 
   640x480        60.0  

Thanks!

---

### Post by danduq on 2008-08-20
I just launched displayconfig-gtk and changed my monitor to a generic LCD Panel 1024x768 and restarted X. I was overjoyed when I got a full screen back, instead of the inch think black edging framing the 800x600 screen.

Unfortunately, it reloaded my session, the restarted X again, and continued to loop until I logged into a failsafe xterm and copied back my old xorg.conf.

Back to square one...  :(

---

### Post by danduq on 2008-08-20
And right back up the ladder to square 99!

I gave the generic "Monitor 1024x768" a go in displayconfig-gtk and it works!

I spent almost the whole day yesterday editing xorg.conf and running diagnostics, and all I had to do was pick "monitor 1024x768". Sometimes Windows does have it's advantages...

Just got to figure out why my login screen has grown bigger than the actual screen now!

---

### Post by danduq on 2008-08-20
ARGH!!!

It all went wrong again. After a reboot it just won't log me in again and keeps dropping back to the login screen.

So I'm back to my 800x600 shrunken desktop. It actually displayed in 1024x768 for a bit though, so it IS capable...

Any suggestions greatly received!

---

### Post by ggaaron on 2008-08-20
You could try with i810 driver (old one, will work if you have older intel card). You can also look at this: [http://ubuntuforums.org/showthread.php?t=887958](http://ubuntuforums.org/showthread.php?t=887958).

---

### Post by danduq on 2008-08-20
Thanks ggaaron, but that resulted in my xorg session 'looping'. I had to revert my xorg.conf back to my basic one again.

---

### Post by ggaaron on 2008-08-20
Do you use a standard ubuntu xorg.conf or a modified one? By looping you mean that X starts up and gdm shows, but login fails and restarts X? To force bigger resolution if you know it is possible you can try the steps in the thread I've posted, but you'd need to generate a modeline for this. You can also post your /var/log/Xorg.0.log produced after X break and restart. As attachment or something as it is probably big.

---

### Post by danduq on 2008-08-20
> **ggaaron said:**
> Do you use a standard ubuntu xorg.conf or a modified one? By looping you mean that X starts up and gdm shows, but login fails and restarts X? To force bigger resolution if you know it is possible you can try the steps in the thread I've posted, but you'd need to generate a modeline for this. You can also post your /var/log/Xorg.0.log produced after X break and restart. As attachment or something as it is probably big.

I'm using the standard one. The only thing I've added is the Driver "intel" entry.

When I change the selected monitor and resolution and restart X it drops back to the login screen. I then login, my sessions loads, everything looks great. Then, when my session attempts to restore the only two running programs I have - Terminal and Firefox - the screen goes black, and reloads X as if I'd hit Ctrl + Alt + Backspace.

I've tried using an online modeline generator to come up with a modeline, but this resulted in the same reloading of X. Also, without knowing the laptop screen's specs, I was using best guesses for sync rates.

I've zipped and attached the Xorg.0.log as requested, although I may make another one as I'm not sure I captured a X auto-restart in it.

Thanks again for your help.

---

### Post by danduq on 2008-08-20
Just realized that the Xorg.0.log re-writes itself when X starts, so have attached the Xorg.0.log.old file as this stops at an interesting point...

(WW) intel(0): xf86UnMapVidMem: cannot find region for [0xb394c000,0x3000000]

---

### Post by ggaaron on 2008-08-20
Is this version of xorg in default repositories, or do you have something like unsupported updates enabled?

I'd try setting 16 bit depth instead of 24 one - this card can't work fully with 24 bit - dri disabled for example. Unfortunately it is the only thing I can think of.=(

---

### Post by danduq on 2008-08-21
OK, thanks ggaaron. How do I set 16 bit depth?

No unusual updates, just a base xubuntu install with wicd added for WLAN config.

Oh well, looks like a graphics cul-de-sac.  :(

---

### Post by ggaaron on 2008-08-21
Try adding ```
DefaultDepth 16
``` in Section "Screen".

---

### Post by Andrew Stone on 2009-02-14
I had the same problem and finally hacked a xorg.conf to get 1024x768 full screen on my Sony Vaio PCG-SRX41P, running Ubuntu 8.10 Intrepid Ibex.  Copy the attached file to /etc/X11/xorg.conf (not xorg.conf.txt!), and restart x (/etc/init.d/gdm stop; /etc/init.d/gdm start) and it *should* work!

---

### Post by flaci on 2009-10-04
> **Andrew Stone said:**
> I had the same problem and finally hacked a xorg.conf to get 1024x768 full screen on my Sony Vaio PCG-SRX41P, running Ubuntu 8.10 Intrepid Ibex.  Copy the attached file to /etc/X11/xorg.conf (not xorg.conf.txt!), and restart x (/etc/init.d/gdm stop; /etc/init.d/gdm start) and it *should* work!

Hi, here is the REAL solution :)

Yes, it works. Almost... The login screen was 1024x768, but after login, the desktop went back to 800x600.
I had the same problem with this Vaio. The trick is that the i815 chip dynamically allocates memory. My X server saw exactly the same amount of 1 Mbyte of video RAM which seemed impossible to me. This could be the reason of the low resolution.
Put a line in the Device section of /etc/X11/xorg.conf :

VideoRam 32768

...and voila... (provided you've set the default resolution to 1024x768...)

Good Luck!

---

