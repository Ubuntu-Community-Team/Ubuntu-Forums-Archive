---
title: "How to change screen resolution"
date: 2005-11-05
forum: General Help
---

### Post by woopud on 2005-11-05
Currently the maximum is 1024 X 786 but I would like it in 1152 x 800 something.
If i type /etc/X11/xorg.conf it tells me permission denied even as root

Bert

---

### Post by taurus on 2005-11-05
You're supposed to edit that file with a text editor, not running it!!!

sudo pico /etc/X11/xorg.conf

---

### Post by rplantz on 2005-11-05
[QUOTE=taurus]You're supposed to edit that file with a text editor, not running it!!!

sudo pico /etc/X11/xorg.conf[/QUOTE]

You can, of course, use any text editor. And it's generally a good idea to save a backup copy, just in case you screw something up and need a fallback. For example, you can do
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

```

Before you do this, you should dig out the manual for your monitor and look up the specs for horizontal and vertical synchronization. Use these numbers for HorizSync and VertRefresh. Your manual should also provide a table of resolutions.

So, for example, here's a portion of my xorg.conf file:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        .... etc...

```
where ".... etc..." means the pattern continues.

Bob

---

### Post by woopud on 2005-11-05
Thanks guys,

Now, if it fails and X won't start after I change it, how do I get it back ?
I know that's why I make the back-up file but how do I get that back in place ?

Bert

---

### Post by rplantz on 2005-11-05
[QUOTE=woopud]Thanks guys,

Now, if it fails and X won't start after I change it, how do I get it back ?
I know that's why I make the back-up file but how do I get that back in place ?

Bert[/QUOTE]

(I'm assuming the default grub here.)

Restart your computer, and get ready to push the esc key.

As it's booting up, you may have noticed that one of the screens gives you two seconds to push the esc key. Do that.

Then use the arrow keys to select one of the kernels that puts you into recovery mode.

You will be prompted for a root password, which is simply your regular ubuntu password, the same one you use for sudo.

If you forget where xorg.conf is located, do
```

locate xorg.conf

```
cd into the directory where both xorg.conf and xorg.conf_backup (or whatever name you used for the backup file) are located. Then do
```

cp xorg.conf_backup xorg.conf

```

You could also use the mv command, but that would effectively delete your backup file. Presumably, you will want to try changing your xorg.conf file again, so you might as well keep your backup intact.

Finally, use the reboot command.

You might want to do a "dry run" on this before changing your xorg.conf file. Better to try new things on a system you know is working. Debugging is easier when you change only one thing at a time.  :-)

Bob

---

### Post by jonzep on 2005-11-06
or try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

choose the new resolution you want and restart...

---

### Post by rplantz on 2005-11-09
[QUOTE=jonzep]or try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

choose the new resolution you want and restart...[/QUOTE]

But this set HorizSync to 28-64 and VertRefresh to 43-60 on my machine.

When I use an editor to set these values according to my monitor manual, I can get a higher refresh rate (according to System -> Preferences -> Screen Resolution).

I have to admit that I don't see any differences between the 60Hz and 85Hz refresh rates, so I'm not sure if this has any effect.

Bob

---

### Post by nszabolcs on 2005-11-09
this problem has been discussed many times:

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
[http://www.ubuntuforums.org/showthread.php?t=76387](http://www.ubuntuforums.org/showthread.php?t=76387)
[https://wiki.ubuntu.com//FixVideoResolutionHowto](https://wiki.ubuntu.com//FixVideoResolutionHowto)

fixing resolution / refresh rate is not trivial in ubuntu (there is a nice gnome app, but with that you can only choose between the settings given in xorg.conf and xorg won't detect your monitor's capabilities so you should edit it by hand or with dpkg-reconfigure)
i hope it will be easier in the new ubuntu release.

---

### Post by mechanic on 2005-11-09
[QUOTE=rplantz] I have to admit that I don't see any differences between the 60Hz and 85Hz refresh rates, so I'm not sure if this has any effect.
[/QUOTE]

Well it depends a lot on what kind of monitor  you have. A TFT display should run at (around) 60 HZ refersh rate, whereas a CRT will show annoying flicker at that rate and will need to be set at 85Hz or greater.

m.

---

### Post by rplantz on 2005-11-09
[QUOTE=mechanic]Well it depends a lot on what kind of monitor  you have. A TFT display should run at (around) 60 HZ refersh rate, whereas a CRT will show annoying flicker at that rate and will need to be set at 85Hz or greater.

m.[/QUOTE]

I have a CRT. Yes, when I temporarily changed it back to 60 Hz, the flicker was awful. I wonder if it was actually running at 60 Hz before I changed my xorg.conf to give me 85 Hz? Oh well, it's fine now.

Bob

---

