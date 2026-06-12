---
title: "Nvidia Driver Problem :|"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by vaska94 on 2009-01-29
hi all :| Today i ran Upgrade manager
and it upgraded kernel....
and when i restarted my PC it gave Nvidia Driver error....
and im right now running ubuntu with default settings :|
and i cant install Nvidia Drivers any Help ? :|
right now im using Vesa Driver :|

---

### Post by x33a on 2009-01-29
which version of nvidia drivers were you using before?

what graphic card are you using?

and, try logging into the previous kernel.

when grub loads, select the previous kernel and see if the issue remains.

---

### Post by aeon on 2009-01-29
hi everyone!

i'm having the same problem on my machine, running an old GF6600GT..
i tried running the old kernel but that didn't help.. also tried downloading the new drivers from nvidias homepage and installing them, but that just messes up my xorg.conf.. :( 
tried running nvidia-xsettings & reinstalling nvidia-glx-new but nothing seems to help..

I'm running a pretty specialized xorg.conf so that could be the problem, but the new one that nvidia-xsettings spat out didn't work either so.. :](*,)

so that's it, i'm running out of ideas here..

---

### Post by abraxas334 on 2009-01-29
I am having a similar problem after running the update. I have the following graphics card: Nvidia GeForce73000Gs and was/ am running it with 2 screens.
Under preference monitor resolution settings i only get a very minimal display window giving me a 2560x1024 screen resolution not even recognizing my 2 screens.
My xorg.conf file seem to have been altered and my additional info for the 2 screens were removed. It says this in it:

```


Section "Screen"

        # Removed Option "metamodes" "CRT-0: 1280x1024@60 +0+0; CRT-0: 1280x960@60 +0+0; CRT-0: 1152x864@75 +0+0; CRT-0: 1024x768@60 +0+0; CRT-0: 1024x768@70 +0+0; CRT-0: 1024x768@75 +0+0; CRT-0: 832x624@75 +0+0; CRT-0: 800x600@60 +0+0; CRT-0: 800x600@75 +0+0; CRT-0: 800x600@72 +0+0; CRT-0: 800x600@56 +0+0; CRT-0: 640x480@75 +0+0; CRT-0: 640x480@72 +0+0; CRT-0: 640x480@60 +0+0"
        # Removed Option "TwinView" "0"
        # Removed Option "metamodes" "CRT-0: 1280x1024@60 +0+0; CRT-0: 640x480@60 +0+0; CRT-0: 640x480@72 +0+0; CRT-0: 640x480@75 +0+0; CRT-0: 800x600@56 +0+0; CRT-0: 800x600@72 +0+0; CRT-0: 800x600@75 +0+0; CRT-0: 800x600@60 +0+0; CRT-0: 832x624@75 +0+0; CRT-0: 1024x768@75 +0+0; CRT-0: 1024x768@70 +0+0; CRT-0: 1024x768@60 +0+0; CRT-0: 1152x864@75 +0+0; CRT-0: 1280x1024@75 +0+0; CRT-0: 1280x960@60 +0+0; CRT-0: 1280x960@75 +0+0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1280x1024_60 +1600+0; CRT-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: 1280x1024_60 +1280+0; CRT-0: NULL, CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

                  


```
The result is weird resulution on both screens and tiny fonts, i.e. a general nuisance!
My Nvidia drivers are apparently active not sure which ones i am using tho.

Any help on this would really greatly be appreciated!

---

### Post by abraxas334 on 2009-01-29
Well, after 3 hours of wasting time to do anything i have somehow restored my dual screen setting by installing the driver from the nvidia website and not using the repositories. 
The font issue however is still not resolved my launch bar and all my firefox terminal etc all these applications seem to be displaying tiny fonts. How can this be resolved without having to spend another 3 hours to mess around with the nvidia drivers any thoughts?

---

### Post by abraxas334 on 2009-01-29
the ubuntu driver issue is probably easiest resolved by doing this:
back up ur xorg file as it is at the moment and then reconfigure it to its very basic state, so it won't be all corrupted.
then remove all the existing nvidia stuff u still might have by saying:
```

sudo apt-get remove --purge nvidia*

```
then go to the nvidia website and download their linux installer.
Extract it to a file somewhere like this:
```

sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run --extract-only cd NVIDIA-Linux-x86-100.14.11-pkg1

``` 
or wgatever the latest version of the driver is. Then to run it, you need to kill ur xserver session this works like this: go to etc/init.d/ and then type
```

sudo gdm stop

```
then u are on a terminal with no x session running u login move to ur nvidia directory and type this to install:
```

sudo ./nvidia-installer

```
which then goes through the install process once that is done u activate your xsession again by saying
```

sudo gdm start

```
and then if you want to edit ur nvidia setting u need to apt-get install nvidia-settings and you should have ur graphics back on the go. Or you can just copy the old information from the xorg file missing in the new one, to make sure you restore your specialized settings.
There may be a different way of doing this but after 3 hours of trying to follow all sorts of installation advice this was the only way that worked for me.
Good luck! Oh and are ur fonts all a bit funny too?

---

### Post by aeon on 2009-01-31
thanks for the info abraxas!

i purged the old nvidia drivers and that cleared things right up :)

seems that both the old and new drivers where trying to take control of the screens at the same time and that's why it crashed..


i'm not having any problems with fuzzy fonts but i have them set up to fall back to 75dpi if 100dpi fails in my xorg and thats been working for me so far..

hopefully you'll get the fonts sorted out and thanks for the help with the nvidia drivers!

---

