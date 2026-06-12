---
title: "Dapper - How to make suspend work???"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by mexp on 2006-06-03
I've got a Dell Latitude C640, and I'm using 'ati' driver for Radeon Mobility M7 LW [Radeon Mobility 7500]. System suspends ok, but doesn't resume properly, and I need to hard-reboot to get it working again. On resume, I get some random stripes on screen, nothing else.

First thing I did was to uncomment the ACPI_SLEEP=true in /etc/default/acpi-support, and I tried also tinkering with other options there, such as the VBE settings and modules, but the result is the same garbled. Tried also commenting out the POST_VIDEO=true line, but then on resume, the display remained all black...

What steps do I need to take to find out where's the problem? If I could get both hibernate and suspend working, that would be fantastic.

---

### Post by edm1 on 2006-06-03
Sounds like the same problem i had. Had to change ACPI_SLEEP_MODE=mem to ACPI_SLEEP_MODE=standby to get it to work.

---

### Post by mexp on 2006-06-03
If I do that, the fan and the network adapter stays on while the display goes blank and the hard drive spins down. Resume works ok, thou. Is that the difference between S1 and S3 states?

Tried also adding acpi_sleep=s3_bios to the kernel options in /boot/grub/menu.lst, so that the line read 

# kopt=root=/dev/hda1 ro acpi_sleep=s3_bios resume=/dev/hda3 (where hda3 is my swap) 

and ran update-grub after, but then when I put the machine to sleep, on resume it just boots up again as from power-up.

---

### Post by mexp on 2006-06-05
Argh... Still can't get it to work... For a while I thought SAVE_VIDEO_PCI_STATE=true made it, but... Sometimes the video comes back again and sometimes not - which is really irritating. Anyone got some good ideas????

Do I need to restart GDM in order the changes in /etc/default/acpi-support take effect?

---

### Post by mexp on 2006-06-07
Just found this link - will need to try out: [http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)

---

### Post by Nevermore on 2006-06-07
Same problem at me with a radeon mobility 7500..
seems that this video cards is giving problems since i have a panasonic laptop..
i keep doing test and tests but nothing works..
i hope u found something that will make it work!

---

### Post by mexp on 2006-06-07
[QUOTE=Nevermore]Same problem at me with a radeon mobility 7500..
seems that this video cards is giving problems since i have a panasonic laptop..
i keep doing test and tests but nothing works..
i hope u found something that will make it work![/QUOTE]

Have you tried the fglrx driver? I would, but I didn't figure out how to *change* the driver in Ubuntu...

---

### Post by mexp on 2006-06-17
Gave up :( What a pity no Magical Ubuntu Guru stumbled across this post and gave the patent fix for the annoying problem... Will try again with next release.

---

### Post by wiresquire on 2006-06-18
I've got the same problems here. Hibernate shuts down OK, but when I resume, I get thin vertical stripes on the screen. Keyboard etc seems unresponsive (Ctrl-Alt-Fx) does nothing. Also it seems that the hard disk becomes 'stuck'. The hd access light is on, but I don't seem to get anywhere.

Mine is a brand new install. I converted from SuSE this weekend :razz:  and hibernate was working fine on that.

I'm using the default updated kernel 2.6.15-25-386 with all latest updates. I have a Mitac 8355, which has AMD Athlon64, and using the open source radeon driver with the Mobility Radeon 9600.

Can anyone help?

TIA
ws

---

### Post by patrickfromspain on 2006-06-18
you could try to:

sudo gedit /etc/default/apci-support

search for modules whitelist
and add your driver module, so that it ends the following:
 MODULES_WHITELIST="ati"
or:
MODULES_WHITELIST="fglrx"

deppending on which driver you're using.

Hope it helps

---

### Post by wiresquire on 2006-06-20
I'm using the ATI driver (open source). 

Thanks for the tip.:p  I'll try playing with the /etc/default/acpi-support file.

Will post if I happen to get it to work

---

### Post by nanotube on 2006-06-22
hey 

so, i am having a very similar problem, and having no luck getting a good resume after a suspend (although suspend itself works normal - just the resume part that's the problem :))

please see my thread here, shows all the stuff i tried: 
[http://ubuntuforums.org/showthread.php?t=201960](http://ubuntuforums.org/showthread.php?t=201960)

i will join my voice to this thread and call for help and ideas with this issue.

edit: i think i have solved the problem. please check that link i posted above, it is updated with the latest :)

---

### Post by mexp on 2006-07-14
Gee, thanks for the tip... BUT! Still no luck with my C640 :(

---

### Post by MiaAlexiou on 2006-09-04
I've got a Toshiba Satellite M50, ATI Radeon 600SE
I'm using the 8.25.18 drivers provided in the restricted repository.

I just commented SAVE_VBE_STATE & POST_VIDEO in the /etc/default/acpi-support file (or you could set them to false) and everything worked like a dream.

# SAVE_VBE_STATE=true
# POST_VIDEO=true

Commenting SAVE_VBE_STATE got suspdend/hibernate to work.
Commenting POST_VIDEO stopped the screen from flashing junk as it resumed

Everything else in the file was left as it came so if you've messed with the file already, you might want to revert back to the default one provided at install.

Good luck!

---

### Post by Erik Andrén on 2006-10-05
I got it to work ok by adding vga=0 to the kernel booting options. 
YMMV.

---

### Post by gilsoncav on 2006-10-12
The problema for a newbye is... HOW to add this vga=0 and WHERE is the booting options.
  I'm about to conclude that Ubuntu is not ready to be a reliable solution to a job laptop (the one that you relie to do your work, show presentations for clients, etc).
  Suspend properly it's a must-have feature, and i lost good potential hours at the beach trying to fix this.

thanks in advance,

Gilson Cavalcanti
Rio de Janeiro, Brazil

> **Erik Andrén said:**
> I got it to work ok by adding vga=0 to the kernel booting options. 
YMMV.

---

### Post by linuxguiri on 2006-10-21
Gilson,

You would add vga=0 to the kernel boot up options by typing at a command line:

```
sudo gedit /boot/grub/menu.lst
```

Find the line that says:
```
# kopt=root=/dev/hda3 ro

```

and add vga=0 so that the line reads:

```
# kopt=root=/dev/hda3 ro vga=0

```

Save changes and exit gedit.

then at a command line, type:

```
sudo update-grub
```

Then reboot and try running suspend/resume.

---

### Post by linuxguiri on 2006-10-21
I am grateful for all the ideas posted here.

Unfortunately, adding vga=0 to the kernel, commenting out SAVE_VBE_STATE and POST_VIDEO in acpi-support, and/or adding acpi_sleep=s3_bios to the kernel don't work on my DELL Inspiron 4150 (Radeon 7500) Dapper system. Bug posted here: [https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/31425](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/31425)

The only way I've been able to successfully resume with video functionality from suspend is by manually running the following two scripts, but they don't work anymore. Caused by kernel update?

The scripts use vbetool commands.

saveVideoState.sh
```
#!/bin/bash
statedir=/root/s3/state
mkdir -p $statedir
chvt 2
sleep 1
vbetool vbestate save >$statedir/vbe
```

suspendToRam.sh
```
#!/bin/bash
statedir=/root/s3/state
curcons=`fgconsole`
fuser /dev/tty$curcons 2>/dev/null|xargs ps -o comm= -p|grep -q X && chvt 2
sync
echo platform > /sys/power/disk; echo mem > /sys/power/state
sync
vbetool post
vbetool vbestate restore <$statedir/vbe
chvt $[curcons%6+1]
chvt $curcons
```

---

### Post by mexp on 2006-11-19
Any ideas how suspend/resume works with Edgy? Still keen on moving on to Linux, but the resume is a bummer :(

---

### Post by linuxguiri on 2006-11-19
> **mexp said:**
> Any ideas how suspend/resume works with Edgy? Still keen on moving on to Linux, but the resume is a bummer :(

Well, since my last post on this thread, I've gotten a new computer (Dell Inspiron 9400 with an NVIDIA graphics card) and installed Edgy. I never did get resume to work consistently on the Inspiron 4150 (with an ATI Radeon Mobility 7500 card). I don't know if it's the ATI card but that's my suspicion. There must be some specific set of commands that could be issued to restart the video, I just never figured out what they were. There is a confirmed bug on this issue here: [https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/31425](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/31425)
You could chime in there and see if you get any response. You have a different laptop, but again I suspect it's the video card that's the issue.

Resume from suspend does work with my new computer (Edgy and NVIDIA). 

I'm sure you've already tried changing all the settings but here's my current /etc/default/acpi-support:
```

ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST=""
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
# SAVE_VIDEO_PCI_STATE=true
USE_DPMS=false
# RADEON_LIGHT=true
# DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
# DISABLE_DMA=true
# RESET_DRIVE=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false
```

---

