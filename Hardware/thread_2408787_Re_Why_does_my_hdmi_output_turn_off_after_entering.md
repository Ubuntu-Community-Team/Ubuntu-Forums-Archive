---
title: "Re: Why does my hdmi output turn off after entering desktop environment?"
date: 2018-12-23
forum: Hardware
---

### Post by iamtheeggman2 on 2018-12-23
Dear All,

Thanks for your help in the past, 

The graphics card I have is 

$ lspci -nnk | grep -i vga -A3
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK208 [GeForce GT 710B] [10de:128b] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GK208B [GeForce GT 710] [1043:85f7]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia



, as you may recall from my prvious thread I had issues with my monitor being too bright but the card worked fine on the connected tv which was connected to its hdmi output. As I couldn't resolve the brightness issues, I had to buy another monitor off ebay. 

Today I wanted to try using my new monitor a LG flatron L1942PE using the dvi cable instead of the vga one, I was surprised to see things did indeed look better, however, although the computer starts up showing the tv connected through the hmi ok, when i enter my username and password to get into lubuntu, the hdmi screen turns off and the tv says there is no signal. But it did work fine working off the vga cable to the monitor with the hdmi to the tv.

Is it simply the case you cant have hdmi and dvi outputs working simultaneously? Thanks in advance.

Further to the above i have found when i reboot the computer with just the tv turned on and the monitor off, the same things happened, it shows password entry screen but then upon entry tot he desktop it turns off the signal.

ok after rebooting and just using the vga cable from the computer to the monitor, when I switch the screen mode to mirror the screens rather than use the tv as a second joined screen, the tv screen turns off - and surprisingly wont come back on again even when i select the setting to go back to joined screens. I might have to try my radeon card again to see i that resolves the issue if I cant resolve with settings,

Further to this I just logged out of lubuntu while it was running then the tv screen worked again, however upon going back in,the screen turned off again, surely must be a setting somewhere indicating the hdmi output has to be turned off upon entry to the desktop environment?

I just had a thought, it sounds unlikely, and although i haven't adjusted any settings on  he new monitor itself, is it possible the monitor is telling the computer not to output the hdmi?

All the above was done in gnome and when i tried logging back into lubuntu on the lubuntu mode it now shows the monitor fine on the second display, however, it is showing as an extended joined display but i want it to mirror the monitor, yet i cant find any settings in the nvdia settings to make it mirror the first screen, plus in lubuntu desktop I cant see any standard monitor settings besides on which lets you choose resolution, and refresh rates for either screen, but that hasn't got the same mirror request function as in the gnome environment,what on earth is going on?

---

### Post by CatKiller on 2018-12-23
> **iamtheeggman2 said:**
> Today I wanted to try using my new monitor a LG flatron L1942PE using the dvi cable instead of the vga one, I was surprised to see things did indeed look better, however, although the computer starts up showing the tv connected through the hmi ok, when i enter my username and password to get into lubuntu, the hdmi screen turns off and the tv says there is no signal. But it did work fine working off the vga cable to the monitor with the hdmi to the tv.

Is it simply the case you cant have hdmi and dvi outputs working simultaneously? Thanks in advance.

There may well be restrictions on which pairs of outputs can be in use at once. You'd need to check the documentation for your graphics card.

From your descriptions, it seems to me that it's trying to use the previously-configured outputs after you log in, while the bootup process is using automatic ones. Per-user monitor configurations are stored in ~/.config/monitors.xml and ~/.nvidia-settings-rc. I'd rename those files to something else, and try again.

---

### Post by iamtheeggman2 on 2018-12-24
> **CatKiller said:**
> There may well be restrictions on which pairs of outputs can be in use at once. You'd need to check the documentation for your graphics card.

From your descriptions, it seems to me that it's trying to use the previously-configured outputs after you log in, while the bootup process is using automatic ones. Per-user monitor configurations are stored in ~/.config/monitors.xml and ~/.nvidia-settings-rc. I'd rename those files to something else, and try again.

Thanks, does this mean it will write new ones?

---

### Post by CatKiller on 2018-12-24
> **iamtheeggman2 said:**
> Thanks, does this mean it will write new ones?

The next time you change from defaults it will create new ones to save the new settings, yes.

Renaming is safer than deleting, in case it all goes pear-shaped. It's easy to recover just by naming them back.

---

### Post by iamtheeggman2 on 2018-12-24
I cant find any folder even when showing hidden files called .config or indeed nvidia, are you sure this is the correct file path?

i just realised these are in the home directory, sorry

Hey I just had a result,I deleted those two files which i eventually found, however, to get the mirroring of the screens I had to lower the resolution, which kinda negates on the advantage of having a hdmi cable, but anyway 10244 * 768 not too shabby, I am now wondering would a better graphics card be any different or is this because the tv itself says it is set to 1024 * 768? maybe it couldn't handle the higher resolution.

---

### Post by CatKiller on 2018-12-24
> **iamtheeggman2 said:**
> I am now wondering would a better graphics card be any different or is this because the tv itself says it is set to 1024 * 768? maybe it couldn't handle the higher resolution.

1024×768 is the default when it can't detect the resolution automatically. It's possible that you can do better.

A new graphics card shouldn't be necessary: the most run-of-the-mill graphics adaptor can do high resolution, it's just that they can't necessarily do 3D graphics quickly at that resolution.

---

