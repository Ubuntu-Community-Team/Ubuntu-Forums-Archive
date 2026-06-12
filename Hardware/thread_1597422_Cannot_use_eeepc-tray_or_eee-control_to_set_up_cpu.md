---
title: "Cannot use eeepc-tray or eee-control to set up cpu policies and settings"
date: 2010-10-15
forum: Hardware
---

### Post by enigmatichus on 2010-10-15
Hello. I have a problem with my Asus eeepc 1001ha. I previously used "eeepc-tray" applet in my 10.04 installation without problems, cpu policies were easy to change with a click, with combination "FN + spacebar" and it automatically changed when I plugged the AC power. It is important because my netbook can't properly reproduce heavy flash apps, for example, youtube or megavideo without setting it to "super high performances". Now I upgraded to maverick meerkat and I cannot use any programme for this task. Eee-tray appearently installs well, but I noticed that I cannot edit any setting, from cpu policies (it remains always on power saving) to screen rotation and resolution, I simply have no effect by clicking anywhere. 
Launching eee-tray from terminal I saw that when I click on an option, it give me an error: "xdg-open: file 'sudo /etc/acpi/eeepc/eeepc-cpu-control.sh super' does not exists", for example, when I click on the "super high performance" mode for the cpu. I tried to change permission with a chmod +x on these files, but nothing changed, and I receive this error with any option in the eeepc-tray.
So I tried to install an alternative, called eee-control.
At the end of the installation, I see the icon in the appropriate area, but it says that eee-control-daemon is not running, so I try to launch it manually and I receive another error: "Cannot access ACPI control files!
Make sure the modules eeepc_acpi (or eeepc_laptop) are loaded."
I don't know what to do, the other only thing I can report now is that I had a problem installing the package eeepc-laptop-dkms and it gave me a compilation error, even if I read that it is not requested with the last kernel versions. Please help me, as I told you I've an eeepc 1001ha with Maverick Meerkat desktop installed, default kernel on a clean installation.
Thank you very much..
PS: I forgot to say that I have no hotkeys problems (I can change brightness, audio volume, put standby etc etc using hotkeys); the problem only concerns cpu policies and other advanced features like force screen resolution and screen rotation.

---

### Post by enigmatichus on 2010-10-15
I know I speak too much, but the problem itself is simple: I only need something which allows me to select the cpu power, assuming that with the default power saving profile I cannot even watch a 480p youtube video and compiling new software is very hard. Is there a way to do this? (in windows xp the key shortcut FN + space switch between these profiles, I don't need nothing else..)
Thank you for your patience. :)

---

### Post by kingmanowar on 2010-10-15
Have you tried to use Jupiter ? I know it is not 'supported' on ubuntu, however it works well for most users. I have myself installed it on my 1000h and it works very well. Have a look on here:
[http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)

I suggest to uninstall all your acpi scripts, eee-control... before.

I hope it helps

---

### Post by enigmatichus on 2010-10-15
Thank you very much for the suggestion..
I don't know why, but just 5 minutes again the problem went away after I, as you suggests, removed all of -acpi or -eeepc packages related to this problem. The strange thing is that, even if I actually have no application of that kind installed, I can now switch between usual power profiles (power saving, high performance and super high performance) simply with the keyboard shortcut Fn+spacebar just like in windows xp, and now everything works! The only thing I did (in addition to uninstalling the mess, of course) is to add "acpi_osi=Linux" in the grub booting command. Anyway, this Jupiter project seems like to be what I was looking for! Thank you for your kindness, kingmanowar!! I appreciate!!

---

