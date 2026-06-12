---
title: "Apply NVIDIA GPU Overclock on Startup"
date: 2015-07-10
forum: Hardware
---

### Post by tristan16 on 2015-07-10
I just got a stable overclock working on my GTX 760, but I can't seem to find a way to apply the settings on startup. I tried following this tutorial, but the commands were deprecated: [http://ubuntuforums.org/showthread.php?t=387019](http://ubuntuforums.org/showthread.php?t=387019)
I tried following this thread, but the commands said that GPU and memory clock offsets were read-only attributes: [https://devtalk.nvidia.com/default/topic/831612/losing-overclock-after-reboot-346-59/](https://devtalk.nvidia.com/default/topic/831612/losing-overclock-after-reboot-346-59/)

Is there any way to load overclock settings on startup? I tried copying the .nvidia-settings-rc file, and specifying it with --config, but it doesn't apply the offsets.

---

### Post by tristan16 on 2015-07-16
Bump. Is this the right place for a question like this, or should I ask over on Nvidia?

---

### Post by dino99 on 2015-07-16
since a while only a few nvidia chipsets can be overclocked by user; the others are hardcoded and you cant do anything against the pre-defined powersaving algos

---

### Post by tristan16 on 2015-07-16
> **dino99 said:**
> since a while only a few nvidia chipsets can be overclocked by user; the others are hardcoded and you cant do anything against the pre-defined powersaving algos
[LEFT]I have a GTX 760 SuperClocked edition from EVGA. **I already have this chipset overclocked. **All I'm looking for is a way to *apply* these overclock settings on startup, rather than manually setting them at every boot.
[/LEFT]

---

### Post by dino99 on 2015-07-16
you can try to set the cpu governor to performance

[http://askubuntu.com/questions/523640/how-i-can-disable-cpu-frequency-scaling-and-set-the-system-to-performance](http://askubuntu.com/questions/523640/how-i-can-disable-cpu-frequency-scaling-and-set-the-system-to-performance)

---

### Post by tristan16 on 2015-07-16
Please re-read the original question. I'm trying to apply a GPU overclock on system startup. My CPU is already overclocked in BIOS.

---

### Post by dino99 on 2015-07-16
> **tristan16 said:**
> Please re-read the original question. I'm trying to apply a GPU overclock on system startup. My CPU is already overclocked in BIOS.

only said that the marketing palace is not the lovely place you dream to. ;)

---

### Post by tristan16 on 2015-07-18
> **dino99 said:**
> only said that the marketing palace is not the lovely place you dream to. ;)

I have no idea what you are trying to say. I've asked my question over on the Nvidia forums. Hopefully they'll have more helpful replies.

---

### Post by tokyobadger on 2015-07-19
Aside from the .nvidia-settings-rc file have you added the Option "Coolbits" to your xorg.conf?
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "Coolbits" "12" 
EndSection
```
The older guide you followed does not work for your card - read [here](http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item)
The value 12 is 8 (bit3) enabling overclocking plus 4 (bit2) enabling manual configuration of GPU fanspeed (depending where you are you might need it in summer).
The value 16 (bit4) enables overvoltage (after driver version 346.16). So if you want overclock, overvolt and fanspeed the value would be 28 (8+4+16)

As for the command nvidia-settings --load-config-only, as Ubuntu doesn't have .xinitrc, I believe you need to add it to the .dmrc file in your /home folder <-- and that should tell you that I haven't tried this myself so proceed with caution :-)

---

### Post by tristan16 on 2015-07-19
> **tokyobadger said:**
> Aside from the .nvidia-settings-rc file have you added the Option "Coolbits" to your xorg.conf?
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "Coolbits" "12" 
EndSection
```
The older guide you followed does not work for your card - read [here]("http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item")
The value 12 is 8 (bit3) enabling overclocking plus 4 (bit2) enabling manual configuration of GPU fanspeed (depending where you are you might need it in summer).
The value 16 (bit4) enables overvoltage (after driver version 346.16). So if you want overclock, overvolt and fanspeed the value would be 28 (8+4+16)

As for the command nvidia-settings --load-config-only, as Ubuntu doesn't have .xinitrc, I believe you need to add it to the .dmrc file in your /home folder <-- and that should tell you that I haven't tried this myself so proceed with caution :-)

Yes, I have enabled Coolbits in my xorg.conf. I found a description of the different Coolbits settings here: [http://discourse.ubuntu.com/t/lets-burn-it-nvidia-overcloking-now-available-on-linux/1610/5](http://discourse.ubuntu.com/t/lets-burn-it-nvidia-overcloking-now-available-on-linux/1610/5)

I'm not quite sure what you're getting at by adding the command to .dmrc. I've already tried running "nvidia-settings --load-config-only" as a startup program, a startup script, from a script, and by just entering it into terminal. It loads the saved configuration, but doesn't load or apply the clock offsets. In another thread on Nvidia, it seems that the .nvidia-settings-rc file doesn't store the clock settings.

I've gotten no replies so far on the Nvidia forums. To re-cap, the closest I got was reading the GPU and memory clock offsets in the terminal, but the values are read-only. I'm wondering if maybe what I'm trying to accomplish is not supported on the Linux platform.

---

### Post by tokyobadger on 2015-07-19
Have a look at one of your linked links [here](http://manpages.ubuntu.com/manpages/precise/en/man1/alt-nvidia-current-settings.1.html)
[quote="Ubuntu Manpage nvidia-settings]
   **3.** **Loading** **Settings** **Automatically**
       The NVIDIA X driver does not preserve values set  with  **nvidia-settings**
       between  runs  of  the X server (or even between logging in and logging
       out of X, with **[xdm]("http://manpages.ubuntu.com/manpages/precise/en/man1/xdm.1.html")**(1), **gdm,** or **kdm** ).   This  is  intentional,  because
       different users may have different preferences, thus these settings are
       stored on a per-user basis in a configuration file stored in the user's
       home directory.

       The configuration file is named _~/.nvidia-settings-rc_.  You can specify
       a different configuration file name  with  the  **--config**  command  line
       option.

       After   you   have  run  **nvidia-settings**  once  and  have  generated  a
       configuration file, you can then run:

            nvidia-settings --load-config-only

       at any time in the future to upload these  settings  to  the  X  server
       again.   For  example,  you  might  place  the  above  command  in your
       _~/.xinitrc_ file so that your settings are  applied  automatically  when
       you log in to X.

       Your  _.xinitrc_  file,  which  controls  what  X  applications should be
       started when you log into X (or  startx),  might  look  something  like
       this:

            nvidia-settings --load-config-only &
            xterm &
            evilwm

       or:

            nvidia-settings --load-config-only &
            gnome-session

       If  you  do  not already have an _~/.xinitrc_ file, then chances are that
       **[xinit]("http://manpages.ubuntu.com/manpages/precise/en/man1/xinit.1.html")**(1) is using a system-wide xinitrc file.  This system wide file is
       typically here:

            /etc/X11/xinit/xinitrc

       To  use  it,  but  also  have **nvidia-settings** upload your settings, you
       could create an _~/.xinitrc_ with the contents:

            nvidia-settings --load-config-only &
            . /etc/X11/xinit/xinitrc

       System administrators may choose  to  place  the  **nvidia-settings**  load
       command directly in the system xinitrc script.

       Please  see  the  **[xinit]("http://manpages.ubuntu.com/manpages/precise/en/man1/xinit.1.html")**(1)  man page for further details of configuring
       your _~/.xinitrc_ file.
[/quote]
What I was saying re .dmrc was that Ubuntu doesn't seem to have a.xinitrc file in the /home/yourname directory - the closest I found was the .dmrc (hope a wiser soul than I could verify)

As I hinted, I haven't overclocked my nvidia cards, I was just looking at where you trying to go

---

### Post by tristan16 on 2015-07-19
> **tokyobadger said:**
> Have a look at one of your linked links [here]("http://manpages.ubuntu.com/manpages/precise/en/man1/alt-nvidia-current-settings.1.html")

What I was saying re .dmrc was that Ubuntu doesn't seem to have a.xinitrc file in the /home/yourname directory - the closest I found was the .dmrc (hope a wiser soul than I could verify)

As I hinted, I haven't overclocked my nvidia cards, I was just looking at where you trying to go

The point still stands that the command doesn't apply the overclock settings. Even if you open the file directly, it doesn't have any of those settings stored. It only has attributes and the settings from the "nvidia-settings Configuration) section.

---

### Post by tokyobadger on 2015-07-19
ah well, time for a pro to step up :-)

---

