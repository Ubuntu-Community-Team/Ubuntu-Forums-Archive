---
title: "Function key works *sometimes* on Toshiba Satellite L305"
date: 2009-04-23
forum: Hardware
---

### Post by swinky on 2009-04-23
In Ubuntu 8.10, there were some problems with the fan/brightness keys on the Toshiba Satellite L305. I am running the Release Candidate for 9.04 (32-bit) and now it seems fixed by adding acpi_osi="Linux" to the kernel parameters. Thankfully, the fan now runs (though not flawlessly) and that is the important part, but I am still having problems with the function keys.

The problem is that, while these keys now work to adjust the brightness, they only work about 30-50% of the time: sometimes I boot and they work fantastically, other times, they don't work at all until a reboot or two later.

The interesting thing is that it doesn't seem to be a problem with the inability to adjust the brightness, it seems to be a problem with the fn key not registering. Without acpi_osi="Linux", while the brightness controls don't work, pressing fn+Esc mutes the volume. With acpi_osi="Linux", IF the brightess works, the mute also works, but if the brightness doesn't work, fn+Esc does nothing. Also, if I have a terminal open, pressing F6 types a ~ in the terminal, when the brightness is working, fn+F6 adjusts the brightness, when it is not working, fn+F6 types a ~ in the terminal, just like I wasn't holding down the fn key!

I suppose the final release of 9.04 might fix it, but considering how much Linux and the Satellite L305 like to fight each other, I'm not holding my breath so I am posting it now. When the final release hits tomorrow, I'll update on the status of the problem in the final release.

---

### Post by swinky on 2009-04-23
My Ubuntu 9.04 installation is now up to date and is the official release, still having this problem. Any suggestions?

---

### Post by frito_x on 2009-05-23
i have a satellite L300 with the same issue as yours... right now i'm running hardy (8.04) but i've already tried with a live 9.04 cd and still doesn't work... makes me mad cause all fn keys work flawlessly in my wife's... wait for it... VAIO!!!


funny that you mention that it sometimes works and sometimes doesn't, cause i've also noticed this happening when booting windowsXP with the toshiba drivers (the original installation)... could be a hardware/BIOS issue?

i updated mine's BIOS but nothing changed...

let me know how it works out for you.

cheers!

---

### Post by swinky on 2009-05-23
I never had any problems with the keys in Vista with Toshiba's drivers, nor with the Windows 7 Beta/RC. The keys always work fine for me in Windows.

I updated my BIOS ages ago when I was having different problems (related to the fan) in 8.10, though I don't know if I am running the latest revision.

I spent hours upon hours trying to find a solution but can't find any. Instead, I developed my own workaround that uses the super (Windows) key in conjunction with the F keys to change brightness (so rather than Fn+F6 for brightness down, super+F6 turns it down.) I wrote up a howto on my blog, if you are interested at [http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html]("http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html"). The specific keycodes might be different for you since you are running an L300 rather than an L305, but you might get it to work for you. 

The other, simpler workaround is to just install screenlets and put a brightness screenlet on the desktop. I find it less convenient, but a lot simpler than my workaround.

---

### Post by rocdoc on 2009-11-28
I can respond that even using Karmic (9.10) I have the same issue on a Satellite L300 machine as the original poster. No solution as of yet.

---

### Post by swinky on 2009-11-29
In my experience, though I did switch to Windows 7 after a lot of difficulty getting the entire laptop to work with Linux, is that if you add the line:
```
acpi_osi=Linux
```
in the boot parameters in your /boot/grub/menu.lst, the fan and function keys work fine. Give it a shot, see if it helps.

---

### Post by zxMarce on 2010-03-17
Be warned: Real newbie talking here!

Maybe -just maybe- the **Fn** key suddenly stops working because of a system update of sorts?
I don't really know, but while editing my **menu.lst** file, I found a -pretty big- section that starts saying:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs
```What I think is that the options we people enter get removed -or better, disabled- when there's an update to either the kernel or GRUB, as the paragraph above says.
What I did, by reading the header a little further was to add the following, in that same section:
```
## ##This is zxMarce's section! ##
## This is to add support for the Fn key
# acpi_osi=Linux
```It survived at least ONE reboot, after which I tested my -until then- dead **Fn** key, and I saw it started working. I don't know if this edit will survive any updates to **menu.lst**, but I'm posting this here just in case for others to see if it's of utility.

Regards,
zxMarce.

---

### Post by rocdoc on 2011-01-29
I finally fixed the Function Key and fan control issues with my Satellite L300 by upgrading the BIOS from version 1.5 to version 2.2. Read this:
[https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300)

---

