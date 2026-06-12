---
title: "MS MCE keyboard and LIRC: Need help adding MOD_MCE driver to LIRC in Edgy"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by flashfasbo on 2007-01-31
Hello! I'm looking for help and/or guidance on how I would go about using my new **Microsoft MCE keyboard with LIRC** and MythTV. Here's a link to the keyboard homepage: [[COLOR="Blue"]http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=038[/COLOR]]("http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=038")

I have already successfully configured use of my Microsoft MCE remote control (version 2) with the Microsoft IR receiver with MythTV (0.20) via LIRC driver MCEUSB2. So far, so good. Now when I try to use the keyboard, right out of the box all the "remote control" keys work just like on the remote proper. However none of the "standard keyboard" keys work.

After many searches I see there's a sourceforge project [[COLOR="Blue"]mod-mce [/COLOR]]("https://sourceforge.net/projects/mod-mce/")which claims appears to have created a driver to use with LIRC, but there are no instructions on how to install it, and I don't have enough experience compiling from source under Linux to make it happen. (Yes, I've asked on that project's forum for help but no responses yet)

The contents of the lirc_mod_mce driver source archive is as follows:
[FONT="Lucida Console"]COPYING
kcompat.h
lirc_dev.h
lirc.h
lirc_mod_mce.c
Makefile[/FONT] 

This looks to roughly match what is found in the other drivers subdirectories under /usr/src/modules/lirc/drivers, except for the addition of the .h files. I might guess I'm supposed to overwrite the standard LIRC lirc.h and lirc_dev.h files in /usr/src/modules/lirc/drivers and ./drivers/lirc_dev and then recompile or something but not really sure of the steps there, or if that's the wrong way to go about all this. I figure there's got to be more involved than simply replacing these files and compiling. For example I see that the existing Makefile has references to the other drivers and so I guess I'd have to add a reference to lirc_mod_mce as well. 

Anyway, I'm grasping at straws now. I'll keep experimenting, but if someone can shed any light on this for me it might save me from a complete system meltdown...

If more info about my system is required to respond just let me know and i'll dump more configs in here.

thanks.

---

### Post by roofchop on 2007-03-20
I am trying to do this too, did you have any luck?

---

### Post by lucaspr on 2007-04-02
Looks like you will have to compile the 'drivers' ...

I'm looking for this too. These can be compiled using the make command, but you will have make sure you've got the 'right' compile tools installed:
```

cd /dir/where/you/placed/driver/
sudo make
```

Post the outcome.. Maybe I can help. Not a total neebie, but I've had no success with Lirc and a mce remote (v2) last time I tried. But then again, I didn't have LiveTV and no 'good' backend. Now I'm watching TV and I can switch channels. So far so good... Now for the remote. 

Hope you get it and if.. You post how you did it.
Have you seen these pages:
[http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install]("http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install")
[http://www.mythtv.org/wiki/index.php/MCE_Remote]("http://www.mythtv.org/wiki/index.php/MCE_Remote")
and most important in this case: [http://mod-mce.sourceforge.net/]("http://mod-mce.sourceforge.net/")

---

### Post by Dubstar_04 on 2007-04-07
I have a mce usb2 remote and mce keyboard from my windows mce days. What i have found is that the keyboard is not properly supported under linux as yet, and i have been un able to get anything but the remote functions to work!!

I do hope that more work is done to support this as it is a really nice keyboard for a htpc.

Dubstar

---

### Post by Churusaa on 2007-05-23
Hey guys!  Typing on my Microsoft MCE keyboard right now.  Very schwank!

I'm using the mod_mce driver from [here]("https://sourceforge.net/project/showfiles.php?group_id=171688"), and the instructions from [here]("http://sourceforge.net/forum/forum.php?thread_id=1710616&forum_id=588333").

Works like a charm, though you have to insmod the driver after installing if you want it to work right away without rebooting.

I've fallen in love with this driver, and it makes me happy in the  face... ^.^

So far as I can see, it's a kernel level driver, so lirc is only needed if you want it.

Always Vigilant
---Churusaa, the Ronin AlienKitten

---

### Post by LinuxBob on 2007-06-28
Have USB IR receiver came with HP MCE PC.  Have MS MCE keyboard.  As I understand I only need mod_mce to use the keyboard.  OK then, very simply cookbook style how do I load mod_mce and get the USB receiver and MCE keyboard to work.  New ot Ubuntu so please do not overlook any step in the process.

Your help would be immensely appreciated.

---

### Post by paulmovricbigbird on 2007-09-28
hi,

I am not to Ubuntu and lirc, I to have a ir Microsoft KB and am trying to get it working. I tried the susgestion and it cames up with these errors:

make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/paul/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "lirc_register_plugin" [/home/paul/lirc_mod_mce/lirc_mod_mce.ko] undefined!
WARNING: "lirc_get_pdata" [/home/paul/lirc_mod_mce/lirc_mod_mce.ko] undefined!
WARNING: "lirc_unregister_plugin" [/home/paul/lirc_mod_mce/lirc_mod_mce.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'

Can you please help.

Thank you.

---

### Post by rafynet on 2007-10-09
> **Churusaa said:**
> Hey guys!  Typing on my Microsoft MCE keyboard right now.  Very schwank!

I'm using the mod_mce driver from [here]("https://sourceforge.net/project/showfiles.php?group_id=171688"), and the instructions from [here]("http://sourceforge.net/forum/forum.php?thread_id=1710616&forum_id=588333").

Works like a charm, though you have to insmod the driver after installing if you want it to work right away without rebooting.

I've fallen in love with this driver, and it makes me happy in the  face... ^.^

So far as I can see, it's a kernel level driver, so lirc is only needed if you want it.

Always Vigilant
---Churusaa, the Ronin AlienKitten

Can you post a NOOB guide on how you got yours to work? please.

---

### Post by bmilleker on 2007-10-26
Lets bump this thread for some answers.

---

### Post by bmilleker on 2007-11-01
Solution here:  [http://ubuntuforums.org/showthread.php?t=592057](http://ubuntuforums.org/showthread.php?t=592057)

---

