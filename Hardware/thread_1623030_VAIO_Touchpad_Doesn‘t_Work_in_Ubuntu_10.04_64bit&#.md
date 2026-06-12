---
title: "VAIO Touchpad Doesn‘t Work in Ubuntu 10.04 64bit&#65293;&#65293;Something might missing"
date: 2010-11-16
forum: Hardware
---

### Post by yankee-whiskey on 2010-11-16
[Solved on 19 Nov.]

Hello and I just installed a Ubuntu 10.04 64bit on my Sony Vaio laptop and things are not going smoothly. My laptop has a touchpad but it doesen't work. I mean it totally can not operate and i can not find the option TOUCHPAD in the System -> Preference ->Mouse, which exists on my old laptop --also a VAIO one. I'm now somewhat frustrated after several hours of googling with no workable solution. Does anyone know how to settle this problem? I think that maybe I miss a driver or something like that, but I do have xserver-xorg-input-synaptics installed. Please help me! And by the way, sorry for the language and I'm not a native speaker. I'm exhausted with the touchpad problem...


Solution:
For Sony's laptop, edit /boot/grub/grub.cfg, and add these after the kernal line (You should be root):

i8042.reset i8042.nomux i8042.nopnp i8042.noloop

save and reboot. the touchpad should work. Good luck!

---

### Post by jfosorio on 2010-11-18
I've the same problem. 
juan

---

### Post by kliffs on 2010-11-18
I had the same problem. I used a regular mouse for awhile then after I updated to 10.10 it worked fine. You could try updating if that is an option. Other than that I don't know.

---

### Post by andrewgbl on 2010-11-18
> **yankee-whiskey said:**
> Hello and I just installed a Ubuntu 10.04 64bit on my Sony Vaio laptop and things are not going smoothly. My laptop has a touchpad but it doesen't work. I mean it totally can not operate and i can not find the option TOUCHPAD in the System -> Preference ->Mouse, which exists on my old laptop --also a VAIO one. I'm now somewhat frustrated after several hours of googling with no workable solution. Does anyone know how to settle this problem? I think that maybe I miss a driver or something like that, but I do have xserver-xorg-input-synaptics installed. Please help me! And by the way, sorry for the language and I'm not a native speaker. I'm exhausted with the touchpad problem...

[COLOR=Blue][SIZE=2]Didn't have the problem with that, I would like to know how to disable tap on the touchpad, it drives me completely nuts....Any ideas?[/SIZE][/COLOR]

---

### Post by yankee-whiskey on 2010-11-19
The problem has been solved. See the solution 1#

---

### Post by TheFatKid on 2011-01-19
Sorry about reviving an old post, but I'm a newbie on this. Which line is the "kernal line"? Thank you in advance.

---

### Post by yankee-whiskey on 2011-01-19
> **TheFatKid said:**
> Sorry about reviving an old post, but I'm a newbie on this. Which line is the "kernal line"? Thank you in advance.

I have sent you a mail explaining this and it may be better to post it here

take my grub.cfg as an example:

```

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set e3c8ba6f-a6c7-458b-b763-f9446b616d36
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=e3c8ba6f-a6c7-458b-b763-f9446b616d36 ro   quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop //The Kernal line and i8042.reset i8042.nomux i8042.nopnp i8042.noloop should be add at the end of the line
	initrd	/boot/initrd.img-2.6.32-26-generic





```

---

### Post by donmatas on 2011-08-29
It seems that when you upgrade the kernell the problem will reappear. Do you have a permanent solution?

---

### Post by dee_tewari on 2011-09-01
> **donmatas said:**
> It seems that when you upgrade the kernell the problem will reappear. Do you have a permanent solution?
If you change the following line 

GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7"

in /etc/grub.d/10_linux to

GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7 i8042.reset i8042.nomux i8042.nopnp i8042.noloop"

then whenever you run update-grub or whenever the update-manager upgrades the kernel and issues this command, the updated /boot/grub/grub.cfg will have these parameters added!

Solved the issue of these parameters going missing after every kernel upgrade for me! Hope this helps you!

---

### Post by donmatas on 2011-09-01
> **dee_tewari said:**
> If you change the following line 

GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7"

in /etc/grub.d/10_linux to

GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7 i8042.reset i8042.nomux i8042.nopnp i8042.noloop"

then whenever you run update-grub or whenever the update-manager upgrades the kernel and issues this command, the updated /boot/grub/grub.cfg will have these parameters added!

Solved the issue of these parameters going missing after every kernel upgrade for me! Hope this helps you!

Thanks! Finally I used following solution succesfully:

```
sudo gedit /etc/default/grub
```

Add the following line in the opened file:

```
GRUB_CMDLINE_LINUX="i8042.nopnp"
```

Close it and update the grub:

```
sudo update-grub
```

---

