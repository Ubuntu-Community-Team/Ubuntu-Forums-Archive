---
title: "Help with undoing a gedit that made ubuntu not boot"
date: 2012-06-01
forum: Hardware
---

### Post by mcwolves32 on 2012-06-01
Here is the fix:[INDENT]sudo gedit /etc/X11/xorg.conf
[/INDENT]Then add the following line at the bottom of the “device” section.[INDENT]Option “RegistryDwords” “EnableBrightnessControl=1&#8243;




i performed that and restarted and now it wont boot tried doing it in recovery console and still nothing

[/INDENT]

---

### Post by ajgreeny on 2012-06-01
> **mcwolves32 said:**
> Here is the fix:[INDENT]sudo gedit /etc/X11/xorg.conf
[/INDENT]Then add the following line at the bottom of the &#8220;device&#8221; section.[INDENT]Option &#8220;RegistryDwords&#8221; &#8220;EnableBrightnessControl=1&#8243;

i performed that and restarted and now it wont boot tried doing it in recovery console and still nothing[/INDENT]Sorry, but I'm confused!

Firstly, is this a wubi install within windows?

Did you add that line as a fix for a problem, but now find that the machine will not boot at all, or just not boot into ubuntu?

If you can not even boot into recovery mode from the grub menu, you may need to boot a live system (CD or USB) mount the ubuntu partition and then open and edit the xorg.conf file back to the original with command ```
gksudo gedit /media/[COLOR=Red]ubuntu[/COLOR]/etc/X11.xorg.conf
``` No password will be asked for in the live session, but you will have root privileges. Your system may name the partition which I called ubuntu differently, so search it out or repeatedly press the tab key to autocomplete and find what it is named.

---

### Post by coffeecat on 2012-06-01
> **ajgreeny said:**
> 
Did you add that line as a fix for a problem, but now find that the machine will not boot at all, or just not boot into ubuntu?

@ajgreeny, I can help with that slightly. I recognise the fix. It's a line to add to the Device section of xorg.conf if one is using the nvidia proprietary video driver in a laptop in order to get the Fn brightness key combinations to work. It works nicely on my Sony Vaio.

@mcwolves32, did you add that line inside the Device section, that is before the "EndSection" line or after the EndSection line. If the latter, then that's the wrong place, but even if you made an error editing the xorg.conf file, the worst that should happen is that the xserver (the GUI) fails to start. The operating system itself should still boot up to a text command prompt. Exactly what happens when you try to boot in recovery mode?

---

### Post by mcwolves32 on 2012-06-01
okay  yes it was indeed a fix for the brightness buttons and it would hang with all the ubuntu dots orange it wouldn't let me hit escape to view the commands that ran. Thank you very much for the help if either of you have some insight of what i did wrong that would be great im a noobie too linux just trying to get it to run like i want on my laptop to get familiar!

---

### Post by Bucky Ball on 2012-06-01
Boot the recovery kernel (generally the one below the kernel you are booting from normally) and drop to a root shell when you get to the screen of options. You could be able to fix that line and put it in the right place if it isn't already, as suggested by coffeecat, or remove that line, reboot, and you're back at square one. Start again.

You could also achieve this by booting from the LiveCD. ;)

---

### Post by mcwolves32 on 2012-06-01
ya i booted a live cd and mounted it and gedited it from there its all booted up now back to searching for a fix for the keys lol

---

### Post by Bucky Ball on 2012-06-02
> **mcwolves32 said:**
> ya i booted a live cd and mounted it and gedited it from there its all booted up now back to searching for a fix for the keys lol

Good news. Could you please mark thread as solved to help others and post a new one if you need any help with the keys problem. Have fun. ;)

---

