---
title: "KTX BM17E 17&quot; Monitor Xsever problem?"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Omnios on 2005-04-12
Hi I have a 17" KTX BM17E monitor (I think the company is now defuct). My WinXp has a problem with it to as it detects it as a Bridge BM17C Lucky the res settings are about the same and it runs on it. Its mounted on a Nvidea GeFOrce 2 MX 100/200. Im doing an install and keep getting Xserver errors. This monitor is known as a problem monitor for older windows 9x etc.  Im wondering if anyone has any idea for horizontal setting? Think thats about the only left that it could be? Any help would be apreciated as I searched the web and only found windows drivers. [-o<

---

### Post by heimo on 2005-04-12
I'd try this:
```

Option        "DPMS"
HorizSync    30-70
VertRefresh 50-160

```

Edit: Tip of the day. ;) You can find this kind of information from INF files on Windows drivers.

---

### Post by Omnios on 2005-04-12
K tryed that still the same problem. Noticed something in my biosy DPMS is set as off. Im not shure how that impact linux DPMS and down think it has just a DPMS option?

---

### Post by heimo on 2005-04-12
:( Could you include those errors and the surrounding text in a "code" box (# sign in message editor) here on the forum, and also module, monitor and screen sections of you xorg.conf?

---

### Post by Omnios on 2005-04-12
Im in winXP right now and seems my floppy is not working in Ubuntu either that of im not using it right refrenced a real old dos command web site. I have network so I downloaded nvidia-settings but I can't seem to use sudo nvidia-glx-config enable in recovery and dont know any short cuts to get to dos in main boot.

---

### Post by heimo on 2005-04-12
I don't know if I understand your problem, but is it that you don't know how to get to command prompt (also known as shell / console / terminal)? You can switch between shells by hitting CTRL+ALT+F1 F2 F3 and so on, typically your graphical user interface is on F7. If you have working X, most of the time you can just right click on the desktop and select 'Terminal'.

Please correct me if completely misunderstood.

One way to run complete reconfiguration of X is
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Omnios on 2005-04-12
I could post the error into the forum, way to long. I did attack attackments though. 

 I can only boot into recover mode, when I first installed I got a xserver error and tweeked things abit, I do not get a xserver error on a normal Ubuntu boot but rather everything loads then I get a black screen. ALso I tryed the default detected settings to no avail. Also cant seem to find the errors on wikki.X.org. Think its the monitor but not shure?

K files are here sorry about the zip only way to upload it.

---

### Post by heimo on 2005-04-12
So when you boot to Ubuntu, the screen goes completely black? No text at all? No *Login:*? Hmm... You could try to press CTRL+ALT+BACKSPACE, which should kill X if it's running but not showing anything. Or you could press CTRL+ALT+F1 to go to first virtual console where you should see 'Login:'. There you should be able to log in to shell and try to reconfigure X (sudo dpkg-reconfigure xserver-xorg) and see if there's something useful in /var/log/Xorg.0.log (use less to view that file).

BTW, I don't see attachment.

---

### Post by Omnios on 2005-04-12
I can not get into terminal on a normal boot there is a flashing promt line on the bottom of the screens sometimes but no text. Using ctlf alt f1 etc seems to change things between unusable prompts and a total black screen. Gnome loaded but I just cant see anything.

 ALso managed to upload the files

---

### Post by NickB on 2005-04-12
I noticed that the Nvidia driver wanted to drive my monitor higher than the max frequencies, regardless of the fact that I had the monitor's horizontal and vertical frequencies explicitly listed in the xorg.conf file.  I fixed the problem by reducing the frequency to something smaller, something I knew wouldn't be too low a frequency for the resolution I wanted to use.

Nick

---

### Post by Omnios on 2005-04-12
[QUOTE=NickB]I noticed that the Nvidia driver wanted to drive my monitor higher than the max frequencies, regardless of the fact that I had the monitor's horizontal and vertical frequencies explicitly listed in the xorg.conf file.  I fixed the problem by reducing the frequency to something smaller, something I knew wouldn't be too low a frequency for the resolution I wanted to use.

Nick[/QUOTE]

 Tryed the mininum hres for 1024-*** got it off a Ubuntu how to. But still didnt work. I came accros a few bugs on xorg bugszilla with sililar errors one was where xserver could not get the legal pixel count and another a user had a KTX but another model and used a no ddp option to work around it. Generaly sounds very similar.

---

### Post by Omnios on 2005-04-12
K I posted a bug on Bugzilla the other day and found out today that the it seems that the nvidia driver thinks my monitor is a flat panel and doing all kinds of wierd stuff to it. Hopefully it will be fixed by nvidia

---

### Post by heimo on 2005-04-12
Maybe you could make one spesific modeline for your monitor and set the HorizSync and VertRefresh so narrow that it'll select only that one modeline? If it's really the nvidia driver that is messing things up, maybe you should try nv or some generic driver until the thing gets fixed?

I just wrote lengthy instructions for how to setup xorg.conf:
[http://www.ubuntuforums.org/showthread.php?t=26420](http://www.ubuntuforums.org/showthread.php?t=26420)

I haven't looked your attachments yet, but I'll do it later.

---

### Post by Omnios on 2005-04-12
I am using the nv driver. I have no idea of what other drivers I could use. And isnt nv a Nvidea supplied open source basic driver?

---

### Post by heimo on 2005-04-12
I'd try something like this:

```
Section "Monitor"
        Identifier      "KTX BM17E"
        Option          "DPMS"
        HorizSync       55-70   
        VertRefresh     65-105

        # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
        Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
        # 1280x1024 @ 70.00 Hz (GTF) hsync: 74.62 kHz; pclk: 128.94 MHz
        Modeline "1280x1024_70.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -HSync +Vsync
        # 1280x1024 @ 65.00 Hz (GTF) hsync: 69.09 kHz; pclk: 119.40 MHz
        Modeline "1280x1024_65.00"  119.40  1280 1368 1504 1728  1024 1025 1028 1063  -HSync +Vsync
        # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
        Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

        # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
        Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
        # 1024x768 @ 82.00 Hz (GTF) hsync: 66.01 kHz; pclk: 90.83 MHz
        Modeline "1024x768_82.00"  90.83  1024 1088 1200 1376  768 769 772 805  -HSync +Vsync
        # 1024x768 @ 80.00 Hz (GTF) hsync: 64.32 kHz; pclk: 88.50 MHz
        Modeline "1024x768_80.00"  88.50  1024 1088 1200 1376  768 769 772 804  -HSync +Vsync

        # 800x600 @ 100.00 Hz (GTF) hsync: 63.60 kHz; pclk: 68.18 MHz
        Modeline "800x600_100.00"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync
        # 800x600 @ 90.00 Hz (GTF) hsync: 56.88 kHz; pclk: 60.07 MHz
        Modeline "800x600_90.00"  60.07  800 840 928 1056  600 601 604 632  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
        Monitor         "KTX BM17E"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

EDIT: There was error 767->768

---

### Post by heimo on 2005-04-13
[QUOTE=Omnios]I am using the nv driver. I have no idea of what other drivers I could use. And isnt nv a Nvidea supplied open source basic driver?[/QUOTE]

you should probably be able to use also nvidia (needs nvidia-glx package) or download drivers from [www.nvidia.com](www.nvidia.com) (I tried to install these yesterday and failed, have done that successfully on other boxes earlier). Or you could use some generic driver like vga or vesa - if absolutely neccessary (I don't know what the limitations are or if these will work for you.)

Try that config I posted abowe with nv driver. :)

---

### Post by Omnios on 2005-04-13
will the config file work if I write it in windows notpad?

---

### Post by heimo on 2005-04-13
[QUOTE=Omnios]will the config file work if I write it in windows notpad?[/QUOTE]

I'm not sure. Windows and Linux have different line ending characters. But you can at least make it in Notepad and try if it works.

---

### Post by Omnios on 2005-04-13
> # 1024x768 @ 80.00 Hz (GTF) hsync: 64.32 kHz; pclk: 88.50 MHz

 Um one question on the end of these lines it states MegaHz just playing it safe is this right even though the line is commented out?

---

### Post by heimo on 2005-04-13
Yes, that's mega herz (MHz), it's called "dot clock" - the frequency your video card must use to send the signal to monitor. (I didn't know that, had to look it up in Google.)

---

### Post by Omnios on 2005-04-14
Going to try the nvidia driver if I can I managed to download it and it did sort of a config but I could not use sudo cp/etc/X11/xorg.conf _backup (no such file found) or 
"sudo nvidia-glx-conf enable" gave me a no a command error for nvidia. also heard that you have to manualy chang nv to nividia. This might just be an error in the nv driver as there must be lots of linux systems using XTK in a hole they where pretty popular in the day. It might have just been an error in the nv vertion of it.

 I dont want to play with the res to much as its detecting as a lcd intead of a crt and dont want to cook my monitor its the only one I have, maybe using the nvidia may solve the problem for now

 Wap du I thing it does this auto config thing lol.

---

### Post by Omnios on 2005-04-14
K two questions. 
I downoaded  "sudo apt-get install nvidia-settings
In showed it was configing
was the configing doing
sudo cp /etc/X11/xorg.conf_backup
and
sudo nvidia-glx-config enabable
?

 If so it safely possible to manualy config the driver in xorg.conf from "nv" to "nvidia"?

 I have a hunch that there is an error in the nv driver pertaining to my monitor.

---

### Post by Omnios on 2005-04-14
Hi finaly got it working by downloading:

 sudo apt-get install nvidia-settings
 sudo apt-get install nvidia-glx
  
moding
 
  nano /etc/X11/xorg config 
  added line in  
                       Section  
                                     Device
                                                show driver 'nvidia"

 running
  
             sudo dpkg-reconfigure xserver-xorg

 I was told that it was not a good idea to run the nvidia driver if you cant get your monitor set up under nv but my problem turned out to be a nv specific bug . Cheers and thanks for the help all.

---

