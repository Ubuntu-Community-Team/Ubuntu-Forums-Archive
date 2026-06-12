---
title: "Intel 945GM: Does anyone have Compiz working in Intrepid?"
date: 2008-11-01
forum: General Help
---

### Post by onlyconnect on 2008-11-01
I have a Toshiba M400 with Intel 945GM graphics. Compiz worked on Hardy, with wobbly windows etc, but since upgrading to Intrepid it does not work. Has anyone else with the same card got it working? I'm finding it hard to troubleshoot because of the changes with HAL detection and xorg.conf.

Here's what I get from compiz-check:

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

Tim

---

### Post by JECHO on 2008-11-01
> **onlyconnect said:**
> I have a Toshiba M400 with Intel 945GM graphics. Compiz worked on Hardy, with wobbly windows etc, but since upgrading to Intrepid it does not work. Has anyone else with the same card got it working? I'm finding it hard to troubleshoot because of the changes with HAL detection and xorg.conf.

Here's what I get from compiz-check:

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

Tim



upgrading never seems to work well for me... unless you can find a solution i would suggest backing up important data and doing a clean install. that always seems to work :)

---

### Post by prshah on 2008-11-01
Works fine for me:```

Sat Nov 01 17:49:00 ~:$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
Sun Nov 02 00:21:04 ~:$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
Sun Nov 02 00:21:06 ~:$ ps -e | grep -i compi
10758 ?        00:00:00 compiz
10914 ?        00:03:42 compiz.real
11232 ?        00:00:00 compiz-decorato

```

---

### Post by prshah on 2008-11-01
Works fine for me:```

Sat Nov 01 17:49:00 ~:$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
Sun Nov 02 00:21:04 ~:$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
Sun Nov 02 00:21:06 ~:$ ps -e | grep -i compi
10758 ?        00:00:00 compiz
10914 ?        00:03:42 compiz.real
11232 ?        00:00:00 compiz-decorato

```

---

### Post by onlyconnect on 2008-11-02
That's encouraging, thanks. I guess the next question is: any tips for getting this working? I'm using the default xorg.conf, ie. mostly empty.

Tim

---

### Post by rpwdh on 2008-11-02
I just got mine working in Intrepid thanks to [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=967631&highlight=compiz")

---

### Post by onlyconnect on 2008-11-02
FIXED! What did it for me was to install libgl1-mesa-dri. 

The clue was in the output from:

grep EE /var/log/Xorg.0.log

which said:

dlopen of /usr/lib/dri/i915_dri.so failed

Apparently the file was missing.

Tim

---

### Post by ekmandyn on 2008-11-09
I get this message with grep EE /var/log/Xorg.0.log

(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) intel(0): [dri] I830CheckDRIAvailable failed because of a version mismatch.
(EE) intel(0): underrun on pipe B!

>compiz-check
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems.../usr/bin/compiz-check: line 396: [: 800: unary operator expected
/usr/bin/compiz-check: line 396: [: 1280: unary operator expected
           [ OK ]

I also tried
>compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

any suggestion??...please

---

### Post by prshah on 2008-11-10
> **ekmandyn said:**
> 

(EE) intel(0): [dri] I830CheckDRIAvailable failed because of a version mismatch.
(EE) intel(0): underrun on pipe B!


Try switching to the latest intel driver; first, [install it]("apt://xserver-xorg-video-intel"): (or, if you prefer to do it manually, open a terminal (Applications-Accessories-Terminal) and give the below command) ```
sudo apt-get install xserver-xorg-video-intel
```

Then press Alt+F2, and give the command ```
gksudo displayconfig-gtk
```, click on the "Graphics Card" tab, and select the driver as "intel" or "Intel experimental modesetting driver"

---

### Post by ekmandyn on 2008-11-10
thanks for your replay. I followed your steps but the problem is that >gksudo displayconfig-gtk, doesn't work. I looked around and turns out that displayconfig-gtk is not included in Ubuntu Intrepid because is not longer supported

Do you know any other program that could be used in 8.10?

---

### Post by pluckypigeon on 2008-11-18
> **ekmandyn said:**
> thanks for your replay. I followed your steps but the problem is that >gksudo displayconfig-gtk, doesn't work. I looked around and turns out that displayconfig-gtk is not included in Ubuntu Intrepid because is not longer supported

Do you know any other program that could be used in 8.10?

I also would like to know. 

I would like to set the Intel experimental modesetting driver as my default card.

Any help would be appreciated

---

### Post by TFX360 on 2008-11-26
Let's do that without need of a GUI (Grapical User Interface).

You can always modify you X settings via /etc/X11/xorg.conf. Or automatically with configure. Which most of the time works better than the out of the box driver installed by the installation of Ubuntu.

I have the

```
sudo lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (Rev 02)
```


To get Graphics Acelleration working I did the following:

```
sudo init 1
```

To enter single-user mode. sudo init 3 doesn't work on Ubuntu Hardy Heron for me.

Select **root Drop to root shell prompt**

Backup the old xorg.conf

```
cp /etc/X11/xorg.conf /etc/X11/xolg.conf.old
```

Configure X automatically

```
X -configure
```

Mind the CAPITAL **X**.

Test the configuration if you want, then replace the old with the new config.

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

init 5

If all else fails go back to single-user mode and restore the old settings:

```
cp /etc/X11/xorg.conf.old /etc/X11/xolg.conf
```


Works for me, let me know if it works for you!

I use fusion-icon to open the management, you can also start/restart the window manager via this tool. Applications -> System Tools -> Compiz Fusion Icon. The icon appears at the top right of the panel.

To install **fusion-icon** and see if an update is available of **compizconfig-settings-manager** do

```
sudo apt-get install fusion-icon compizconfig-settings-manager -y
```


Tada!

---

### Post by ekmandyn on 2008-11-26
Thanks TFX360 but just yesterday I solved this problem. This is what I did:

1) As prshah suggested I installed

sudo apt-get install xserver-xorg-video-intel

but I couldn't install the gksudo displayconfig-gtk

2)However looking around I found a post (Sorry, I can't find it again) suggesting to uninstall using Synaptyc Package Manager all the packages containing "fglrx".

3)After I did that I ran "compiz-check" and all changed to OK.

4) I enabled desktop effects 

5) the only problem was that the borders of the windows disappeared (I'm using Emerald theme Manager), so every time from the terminal I had to run "emerald --replace" 

6) I solved this simply adding this command in system/Preferences/sessions

thanks everybody for the sugestions

---

### Post by TFX360 on 2008-11-26
You're welcome, thank you for repling anyhow!

---

### Post by satosh on 2008-12-09
> **ekmandyn said:**
> 
[...]
2)However looking around I found a post (Sorry, I can't find it again) suggesting to uninstall using Synaptyc Package Manager all the packages containing "fglrx".

3)After I did that I ran "compiz-check" and all changed to OK.

4) I enabled desktop effects 


Thank you so much ekmandyn!!!!!!!!! I had been fiddling with many many settings around in the system to get compiz working, but finally, this did the trick for me! I just had to remove packages containing "fglrx" in synaptic package manager. After this, compiz-check had all OKs and compiz has been working nicely ever since! The solution was very random and very hidden, in a few posts deep down in the archives, a little frustrating... Anyway, these forums are great! And the participants is what make them great!

---

### Post by Diffusr on 2008-12-09
Go to synaptic package manager, install ccsm. Worked for me after losing compiz functionality due to Intrepid upgrade.

---

### Post by ravindra_jain12 on 2008-12-26
Hello Everyone,

I'm new to Ubuntu and last week installed 8.10 (after using 8.04 for a month or so). Just today I noticed that compiz is not working and all the effects, which used to work fine in 8.04, are not working. 

I already did what all is listed in this thread (and some other threads on same topic) for a possible solution, but unfortunately compiz is still not working. I could see few effects working (like edge resistence), but others (e.g. wobbly windows) are not available.

Here is what I did and output of few commands:

[B]1. compiz-check script gives all OK.
[/B]
[INDENT][I]Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

[/I]
[/INDENT]
[B]2. Already removed all nvidia-* packages.
[/B]
**3. Already removed all packages containing "fglrx" from Synaptic package manager.**

Please let me know what else can I try to get compiz back.

Thanks in advance..
Ravindra..

---

