---
title: "nVidia GLX issue"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by Crab King on 2005-02-27
i have a Nvidia tnt2 and have recently installed the drivers.
i also installed "tuxracer" and when i finished installing it i tried to play it, and i get this problem:
> Tux Racer 0.61 -- a Sunspire Studios Production ([http://www.sunspirestudios.com)(c](http://www.sunspirestudios.com)(c)) 1999-2000 Jasmin F. Patry <jfpatry@sunspirestudios.com>
"Tux Racer" is a trademark of Jasmin F. Patry
Tux Racer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
*** tuxracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)

so i think there is a problem with the drivers or something, because the GLX is not working correctly.
could someone pleae help me fix this?

---

### Post by alastair on 2005-02-27
What does :

glxinfo

say when typed in a shell?

What about the "Driver" line in your X config file (either /etc/X11/XF86Config-4 or Xorg.conf)?

---

### Post by carney1979 on 2005-03-02
If you installed the 6629 driver (through apt or the "official" Nvidia driver), then the TNT2 card is incompatible with it due to a bug in the driver.

Don't feel singled out - my Geforce card won't work with it either.

Use the 6111 driver from Nvidia for now.

David

---

### Post by marvel on 2005-03-13
Had the same problem. In my case it was Option "NVAgp" in xorg.conf. I changed it from "1" to "2" and everything worked like a charm.
NVidia GeForce 4 on Toshiba Satellite 1410. Ubuntu Hoary, preview.

---

### Post by Mark Marple on 2005-03-13
I'm having somewhat of the same problem, as I installed the Preview on a second hd and installed the nvidia-glx.  When I reboot, I no longer have X.  I have an array 5 (with all the updates) on the 1st hd and the nvidia-glx is just fine.  I copied the Xorg.conf file from the array 5 to the Preview and nothing.  I really don't need the glx nvidia driver, but it would be nice to it installed.

Marvel.......
I don't have the NVAgp anywhere in the Xorg.conf file.  I'm looking in /etc/X11/ folder.  Is this the right folder for the file?  Also, how might I go about seeing what driver (the nvidia 6111) I'm using?  I have an old GF 2 card.  I did install from both array 5 and the preview, the nvidia thru synaptic.  Might they have changed the drivers in there from array 5 to preview?

Please help!

Thanks!

---

### Post by marvel on 2005-03-13
[QUOTE=Mark Marple]I'm having somewhat of the same problem, as I installed the Preview on a second hd and installed the nvidia-glx.  When I reboot, I no longer have X.  I have an array 5 (with all the updates) on the 1st hd and the nvidia-glx is just fine.  I copied the Xorg.conf file from the array 5 to the Preview and nothing.  I really don't need the glx nvidia driver, but it would be nice to it installed.
[/QUOTE]
Take a look at [this](http://ubuntuforums.org/showthread.php?t=19500) forum thread. I explained it as good as I could :)
To clarify things: you don't have NVAgp in your xorg.conf, you have to add it yourself. Just configure it in the right way.
Good luck :)

---

### Post by Mark Marple on 2005-03-13
thanks Marvel

Your write up looks great. I wll try the nvagp option.  Not sure about right now.  I'm using the 2.6.11-1-k7 linux image and when trying to install nvidia-glx from synaptic, it says it needs the 2.6.10-4-386 linux image and the restricted as well.

I may try in a few days when i get bored again................. :lol:

---

### Post by marvel on 2005-03-14
[QUOTE=Mark Marple]I'm using the 2.6.11-1-k7 linux image and when trying to install nvidia-glx from synaptic, it says it needs the 2.6.10-4-386 linux image and the restricted as well.
[/QUOTE]
You might want to try to compile the kernel mode yourself. It's quite easy - you need to apt-get kernel-headers-[your kernel here] and the driver from NVidia's page. Then reboot in recovery mode (X won't start), chmod +x nvidia-something.run file you downloaded and execute it. It will add the driver (see --help for adding the driver for multiple kernels). If your xorg.conf is tweaked for the binary driver (from previous kernel), it should work right away.

---

### Post by Mark Marple on 2005-03-14
NICE!!!

Thanks again Marvel, I will try this.  Always been pretty scared of the whole compile thing, but your info seems easy to follow.  I shall try and see how it goes.

1 last question, should I make a backup of the xorg.conf file before this?  I know it wouldn't hurt, but just don't want to mess something up and leave the system useless.  If not, xorg.conf, then anything that you might think of to save me a hassle.

---

### Post by marvel on 2005-03-14
[QUOTE=Mark Marple]Always been pretty scared of the whole compile thing, but your info seems easy to follow.  I shall try and see how it goes.[/QUOTE]
Yeah, me too. But I was once forced to compile the entire kernel (the sound card was not working on the default one), so I read some stuff, and it was quite easy. Compiling a single module is a snap - you just issue one command, and everything's automated.
[QUOTE=Mark Marple]1 last question, should I make a backup of the xorg.conf file before this?  I know it wouldn't hurt, but just don't want to mess something up and leave the system useless.  If not, xorg.conf, then anything that you might think of to save me a hassle.[/QUOTE]
Yup, a backup of xorg.conf would be nice. But the NVidia installer will not modify it - you have to do it yourself, so make a backup before you begin ;-)

---

### Post by Mark Marple on 2005-03-14
Hello again Marvel,
Just an update on the glx issue.  I went back to the 2.6.10-4-k7 kernel right now.  I installed the linux-restricted-modules-2.6.10-4-k7 (saw something on it) and I now have glx installed. Its even working without the NVAGP option in the xorg.conf file.

Not sure what I was gaining with the new 2.6.11-1-k7 kernel, but obvious not the nvidia glx........LOL

i tried to install the kernel-headers2.6-k7 and I get this error:
kernel-headers-2.6-k7:
 Depends: kernel-headers-2.6.8-2-k7  but it is not installable

Not sure if this is the right file, but I don't see anything with the exact linux--image (linux-image-2.6.11-1-k7)  that I was trying to get working.

Maybe I'm trying to be ahead of the game to fast.....LOL

With that being said, I will stick with what I have working and be content.  
Maybe I should apply that old saying to myself.............."if it ain't broke, don't fix it"

Thanks for all your replies!

---

