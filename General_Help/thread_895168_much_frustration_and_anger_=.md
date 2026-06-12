---
title: "much frustration and anger =/"
date: 2008-08-19
forum: General Help
---

### Post by windoze87 on 2008-08-19
does gnome and xfce just not get along? lol... i just made the move to xfce two days ago by installing xubuntu-desktop and removing ubuntu-desktop through aptitude, which from what i gather pretty much means i run Xubuntu now. I like xfce, it has a lot more basic customizing options than gnome does, and my computer now runs faster (i have a 2ghz amd sempron processor)...but here's my gripe. When i was running Gnome as my desktop manager, i could install pretty much whatever as far as apps are concerned, whether they were gnome or kde. Thing is, i like some gnome apps, like banshee, awn, etc... well, awn runs fine, and most everything else too, but a couple of things dont and i wanted some feedback if at all possible because ive spent two frustrating nights trying to figure this one out =/ Banshee will only work sometimes. Yes, i have pulseaudio installed, along with alsa...sometimes when i log in, banshee will play fine, but other times it'll give me (unknown error) and roll through the playlist till i have to force quit it. also, im having a beast of a time trying to get my nvidia driver to work. I found what i could about XGL but there doesnt seem to be a lot of documentation that i could find, maybe i'm just looking in the wrong place... i also have a problem with my nvidia card in that if i try using the driver from the ubuntu repos i can only have 800x600 resolution, but if i use the one that envy provides i get perfect resolution, just no hardware acceleration, and when i try to enable it, it wigs out and i have to reconfigure my X server. So...can anyone help with any of these problems i'm having? If i can at least get Banshee to play consistently i'll be happy, i only use a few compiz effects like the minimize animations and window previews, so that wouldn't be a big loss, but if someone can help me with that, too, i'd be really greatful. Thanks in advance.

---

### Post by SoloSalsa on 2008-08-19
> **windoze87 said:**
> also, im having a beast of a time trying to get my nvidia driver to work. I found what i could about XGL but there doesnt seem to be a lot of documentation that i could find, maybe i'm just looking in the wrong place... i also have a problem with my nvidia card in that if i try using the driver from the ubuntu repos i can only have 800x600 resolution, but if i use the one that envy provides i get perfect resolution, just no hardware acceleration, and when i try to enable it, it wigs out and i have to reconfigure my X server.
Sorry: I cannot help.  But I do want to tell you that you are not alone with bad NVIDIA drivers.  I ended up taking high resolution with no acceleration over accelerated 800×600.

---

### Post by windoze87 on 2008-08-20
:confused: anyone...? here, i tried playing a sample .wav file in terminal and this is the output i got ```
rick@source:~$ aplay -vv /usr/share/firefox/res/samples/test.wav
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
```

obviously it looks like i've got pretty much nothing built for alsa but i have it installed, along with pulseaudio...so...wtf? when i do aplay -l in terminal it tells me i have no soundcard. however, doing "sudo lspci -v | grep -A 5 [Aa]udio" tells me the following-- ```
rick@source:~$ sudo lspci -v | grep -A 5 [Aa]udio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9222
	Flags: medium devsel, IRQ 5
	I/O ports at e000 [size=256]
	Capabilities: [c0] Power Management version 2

``` so....wtf? im going to keep googling in the hopes that i find an answer, but in the meantime, if anyone can help i'd really appreciate it

---

### Post by windoze87 on 2008-08-20
okay, i removed everything to do with alsa and manually compiled the driver using dpkg-reconfigure alsa-source, and then added the driver to /etc/modules, so that's gravy now. so i guess my only problem left is with xgl, compiz, and my nvidia driver... and i basically feel as if that's a luck of the draw type deal haha if any mods happen by, feel free to move this to a different category if need be, ill post back when and if i get my nvidia card working w/ xgl so other people will know what to do

---

### Post by windoze87 on 2008-08-20
Okay! Apparently all i needed was a few hours of not banging my head against the keyboard haha i dont know if this will work for everyone, but here i'll list what i did to get my Nvidia Geforce FX5500 card to work under Xubuntu.

First, if you have any existing Nvidia drivers installed, either from the ubuntu repositories or from Envy, you need to remove them. If you used Envy, it has a neat utility built-in to remove any drivers. If you went through the Ubuntu repository (Synaptic, aptitude, apt-get) i recommend bringing up Synaptic and completely remove any nvidia packages you have installed. After that, if you have compiz installed you need to remove it and all config files by typing in terminal ```
sudo aptitude remove compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compizconfig-backend-gconf compizconfig-settings-manager --purge
```

Next, you need to remove the linux restricted drivers module. to do so, first figure out exactly what kernel you're running by opening a terminal and typing in "uname -a". On my system, i have Linux source 2.6.24-19-386. Your output may be different, but what you need is the output after "Linux source". Next, in terminal type ```
sudo aptitude remove linux-restricted-modules-#.#.#-#-# --purge
```, replacing the #'s with the numbers from the output of uname -a. This command will purge the linux restricted module package from the system along with configuration files. Next, in terminal type ```
sudo dpkg-reconfigure xserver-xorg
```, which will rewrite your current xorg.conf to a new one without nvidia drivers. Reboot your computer. Most likely when it comes back up, you'll be in lo-res mode, accept whatever you can get from it and proceed with booting. 

Now here comes the fun part-reinstalling most everything you just took out! The reason why I went through all the trouble of removing everything just to reinstall it is when you purge everything, it goes back to defaults, which is useful if you were like me and spend three nights solid trying to get hardware acceleration to work. First of all, you need to reinstall the linux-restricted-modules package. If you remember what your kernel was, just open a terminal and type ```
sudo aptitude install linux-restricted-modules#.#.#-#-#
```, once again replacing # with your output fron uname -a. next, you need to install xgl and compiz. type in ```
sudo aptitude install compiz xserver-xgl libgl1-mesa libglitz-glx1 
```. After those packages install themselves, open up Envy. You must manually select the driver to install but -DO NOT INSTALL THE NEWEST ONE!!!!!!!!!- i believe it is 173.something... the next driver down for me was 96.43.04, which is what i selected. Let envy do its magic... once everything has been installed, restart your computer. Then when you log back into Xubuntu, open a terminal and type in ```
Xgl :1 -fullscreen -ac -accel glxbuffer -accel xv:fbo &
``` and then hit Ctrl+Alt+Backspace to restart your session. Log back in and Voila! hardware acceleration galore! If anyone knows how to write that XGL code into a seperate login mode, please contribute to this thread... i don't know how. In any case, i would like to thank mucnix for that xgl run code...don't know where he/she got it from, but this is the thread where i got most of my info ([http://ubuntuforums.org/showthread.php?t=203877](http://ubuntuforums.org/showthread.php?t=203877)). I hope this thread helps someone else out, because banging your head on your keyboard isn't too comfortable :guitar:

---

