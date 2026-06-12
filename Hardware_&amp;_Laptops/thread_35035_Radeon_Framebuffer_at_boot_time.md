---
title: "Radeon Framebuffer at boot time"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by goldenboy on 2005-05-17
Hi,
I have a HP/Compaq NX7000 with a ATI radeon mobility 9200 and a 1680x1050er widescreen TFT.

Till now I used the standard VESAFB driver to get a somehow more graphical textconsole, but since the the vesa framebuffer does not support the native resolution of my screen everythink looked badly scaled up.
So I tried to use the RADEONFB driver, but when I change my grub bootline to:

```

kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash video=radeonfb
```

No framebuffer at all is loaded.

When booting with the radeonfb option, the only time the string "radeonfb" is mentioned when repeating the boot options...

If no framebuffer is loaded modprobing radeonfb works fine and results in a beautiful textconsole in the native resolution.

But how do I manage to load the radeon framebuffer at boottime??

Do I have to add the radeonfb module to the initrd image?? If this is true, how do I do this? I got really no experience in changing or creating an initrd image...

thanks for your help

---

### Post by tmowerman on 2005-05-17
One way is to compile a kernel with the radeonfb support built in.  I had this working on gentoo, and then everything after grub was full screen on my laptop.  

I don't know anything about the initrd i am afraid.

---

### Post by goldenboy on 2005-05-17
[QUOTE=tmowerman]One way is to compile a kernel with the radeonfb support built in.[/QUOTE]

That's actually what I wanted to avoid. Compiling a working kernel is not that hard, but once one has started making ones own kernel it's kind of a never ending story I experienced... :? 

cheers

---

### Post by evermind on 2005-06-02
I wrote a script to achive that, but not tested  with ubuntu-kernels.
just edit and copy this script into /etc/mkinitrd/scripts/
make it executable
chmod +x /etc/mkinitrd/scripts/framebuffer_mkinitrd
now install an new kernel with apt-get
(the script will be executed by mkinitrd -- which generate the initrd)

This script was just tested with sisfb yet, but radeonfb is also supported but not
tested.

IT IS YOUR OWN RISK TO USE THIS SCRIPT!

this is the part of the script you should customize:
```
####settings begin##############################
# just settings to fit your needs
# here you can enter your custom fb-modul
# (you can set whatever you want)
# eg FB_MODULES_WITH_PARAMETERS=sisfb mode=1024x768x16 rate=60
# if you have more vga-cards
# FB_MODULES_WITH_PARAMETERS="sisfb mode=1024x768x16 rate=60,radeon mode=800x600 rate=85"
# FB_MODULES_WITH_PARAMETERS="" # this means autodetection (default)
# (please report your working modul-parameters)
FB_MODULES_WITH_PARAMETERS=""

# set the frequency rate, resolution and depth
# for your vga-card
# (only needed for autodetection of the fb-modul)
FREQUENCY="60"       #<-- edit here
RESOLUTION="1024x768"      #<-- edit here
DEPTH="16"          #<-- edit here

# print debugmessages
DEBUG="on"

# display infos values 0 - 3 higer-> more infos
INFO_LEVEL="2"
####settings end##############################
```


if you use an other vga card then a sis or a radeon and you have working modprobe parameters for it
eg. modprobe radeonfb mode-option=1024x768-16@60
you can edit setting FB_MODULES_WITH_PARAMETERS=""
with your settings.
you can also post your working settings here so I can add them to the script

how the script works:
first it try to detect which vga-card is used (supported sis and radeon)
if none found it will exit (future version maybe default to vesa-framebuffer - but until then the script exits)

next it generate the the desired parameters for modprobe.
And now it search for all needed modules and add them to the initrd
and also edit loadmodules.

If you want to try this script be sure  you have an other working kernel/initrd or you may run into troubles.


UPDATE:

# v0.2 	06-JUN-2005	now also 3dfx gets detected but the modul is lacking
#			to support parameters so you have to append the displayed
#			cmdline to your cmdline in your grub/lilo -list
#			enhancements: modul vesafb gets deleted from the image if not used
# v0.2.1 06-JUN-2005    hotfix: vesafb gets now really deleted :)
# v0.2.2 23-JUN-2005    if fbcon is not a modul remove fbcon from modul-list
# v0.2.3 24-JUN-2005    *now with --info you can list your vga-hardware (using lspci)
#                       the info switch is just if you want to see your vga-card added
#                       (post the output)
#                       *the scripts now check if it is called from mkinitrd

---

### Post by evermind on 2005-06-24
Has anyone tested this script with a radeon-card?
or want to have support for different cards
then run

./framebuffer_mkinitrd_v023_uf --info

and post the output

please comment

thx

---

### Post by blacksheep on 2005-06-30
I have a HP/Compaq nx7010 notebooks with a ATI Radeon Mobility 9200 at home. My widescreen display supports resolution 1280x800.

In my case was very easy to add framebuffer support @ boot time. The only thing I did was to add a new line containing "radeonfb" to the file /etc/modules.

Now everything works fine!

---

### Post by goldenboy on 2005-06-30
[QUOTE=blacksheep]I have a HP/Compaq nx7010 notebooks with a ATI Radeon Mobility 9200 at home. My widescreen display supports resolution 1280x800.

In my case was very easy to add framebuffer support @ boot time. The only thing I did was to add a new line containing "radeonfb" to the file /etc/modules.

Now everything works fine![/QUOTE]
 @evermind
I've to admit that I didn't try your above script till now :(

@blacksheep
That does work in some kind... But is no real solution for me, since I need radeonfb support before the other modules are loaded, to get a good lookin' bootsplash :)

And by the way, I would not recommend to use the radeonfb framebuffer with the fglrx driver and XFree86 X-server. I don't know why, but with this configuration some colors screwed up an especially fonts looked really ugly...

regards

---

### Post by Frankk on 2005-10-27
I have a Radeon 9700 laptop with 1280x768 display.
I tryed your script but I get:

```
# ./framebuffer_mkinitrd_v023_uf --info
ERROR: ###################################################
# your video card was not detected please post the following
# line and if possible also working modprobe parameters
##########################################################
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA])
```

Shouldn't be supported?

Thanks.
Frankk

---

### Post by evermind on 2005-10-27
[QUOTE=Frankk]I have a Radeon 9700 laptop with 1280x768 display.
I tryed your script but I get:
[/QUOTE]
edit the script and adjust it your resolution
RESOLUTION="1280x768"      #<-- edit here

and then put it into
/etc/mkinitrd/scripts/

and reinstall your kernel with apt-get or synaptic.
```
apt-get install linux-image-[VERSION]
```
after an reboot you should have a working framebuffer with your resolution
(but I´ve never tested it with a radeon card)

---

### Post by Frankk on 2005-10-28
That's exactly what I did (except that i did "sudo dpkg-reconfigure linux-image-2.6.12-9-686" instead of apt-get), but it seems not to work, I get normal VGA resolution VESA framebuffer.

Btw I think that the problem is that the card is not detected, maybe there is a problem with newer radeon cards not being detected?

Btw I put in /boot/grub/menu.lst this line:

kernel  /boot/vmlinuz-2.6.12-9-686 root=/dev/hda5 ro quiet splash video=radeonfb

is it correct to work with your script?

Thanks for your help.
Frankk

---

### Post by evermind on 2005-10-28
I´ll test this script with a radeon card soon.

---

### Post by evermind on 2005-10-28
Ok I tested it with a radeon and it works for me
(btw. you use breezy? I only tested it on hoary)

so try this:
dpkg-reconfigure inux-image-2.6.12-9-686
and post the output
if something similar to:
DEBUG: Modul &(parameter) radeonfb mode-option=1024x768-16@85
appears the mkinitrd should be generated fine.
next mount your initrd.img-2.6.12-9-686 to a directory
```
mount -t cramfs /boot/initrd.img-2.6.12-9-686 /tmp/whatever -o loop
```
go to /tmp/whatever and post the output of
```
grep radeon loadmodules;find -name 'radeon*'
```

my output is:
modprobe -k  radeonfb mode-option=1024x768-16@85  > /dev/null 2>&1
./lib/modules/2.6.10-5-k7/kernel/drivers/video/aty/radeonfb.ko

if all fails you can send me (per pm) the kernel-config (/boot/config-version)
loadmodules and linuxrc from initrd

---

### Post by Frankk on 2005-10-28
Sorry, but I just noted now that this is Hoary forum, but I did a search and didn't notice before.

So, yes, I'm using Breezy.

I will try anyhow what you told in the post.

Well, there seems to be something wrong withh my initrds or I'm doing something wrong...
When I do "dpkg-reconfigure linux-image-2.6.12-9-686" I get:

Not touching initrd symlinks since we are being reinstalled (2.6.12-9.23)
Not updating image symbolic links since we are being updated (2.6.12-9.23)

Btw this seems to go fine, no other output, no "DEBUG:" lines. (is there a flag to activate debug mode in dpkg-reconfigure?)

I also tryed to mount my initrds:

mount -t cramfs /boot/initrd.img-2.6.12-9-686 /tmp/mount-initrd -o loop

but I get:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I did dmesg|tail and got:

[4333126.346000] loop: loaded (max 8 devices)
[4333126.392000] cramfs: wrong magic

Wow, did initrd of breezy use another fs type?

Thank you for your help.
Frankk

---

### Post by evermind on 2005-10-28
The debug lines are generated from my script
so I seems to be not executed.
I have no access to a breezy machine and I'm not yet willing to install one 
cause my boxes just run fine with hoary.

first try to generate a initrd with this command
```
mkinitrd -o /tmp/tmp-initrd
```
If this will not produce any output with DEBUG than the script won't be lauched:

so try this

```
bash -x mkinitrd -o /tmp/tmp-initrd 2>&1|grep -i run-parts
```

my output is this
+ run-parts /usr/share/initrd-tools/scripts
+ run-parts /etc/mkinitrd/scripts

if just one directory appears with scripts to be launched put the script into this dir and hope the best :)

---

### Post by Frankk on 2005-10-29
I get this:
```
$ sudo mkinitrd -o /tmp/tmp-initrd
DEBUG: MODULDIR /lib/modules/2.6.12-9-686
DEBUG: FB_MODULES_WITH_PARAMETERS:"radeonfb mode-option=1280x768-16@60"
DEBUG: LOAD_CMDL_MODULES_REVERSED:"radeonfb mode-option=1280x768-16@60,fbcon"
DEBUG: LOAD_CMDL_MODULES_CLEAN: radeonfb fbcon
DEBUG: ALL_MODULS=bitblit cfbcopyarea cfbfillrect cfbimgblt fbcon font i2c-algo-bit i2c-core radeonfb softcursor tileblit
DEBUG: ALL_GIVEN_CMDL_MODULE:"bitblit cfbcopyarea cfbfillrect cfbimgblt fbcon font i2c-algo-bit i2c-core radeonfb softcursor tileblit "
INFO: MODUL: bitblit allready in image
INFO: MODUL: cfbcopyarea allready in image
INFO: MODUL: cfbfillrect allready in image
INFO: MODUL: cfbimgblt allready in image
INFO: MODUL: fbcon allready in image
INFO: MODUL: font allready in image
INFO: ADDING MODUL: i2c-algo-bit
INFO: ADDING MODUL: i2c-core
INFO: ADDING MODUL: radeonfb
INFO: MODUL: softcursor allready in image
INFO: MODUL: tileblit allready in image
DEBUG: This Modules will be added (deps are not listed here):
        -bitblit cfbcopyarea cfbfillrect cfbimgblt fbcon font i2c-algo-bit i2c-core radeonfb softcursor tileblit
        This Modules (additional with Parameters) will be loaded:
        -
DEBUG: Modul &(parameter) radeonfb mode-option=1280x768-16@60
DEBUG: 0
DEBUG: Modul &(parameter) fbcon
DEBUG: 1
```

So the script is executed. Ant it seems that the initrd in /boot is updated when I do "dpkg-reconfigure linux-image-2.6.12-9-686" (looking at the creation date and time).
How can I check if the modules needed are actually added to it?
One more question: what options do I have to put in /boot/grub/menu.lst ?
Mine looks like this:
```
kernel /boot/vmlinuz-2.6.12-9-686 root=/dev/hda5 ro quiet splash video=radeonfb
```

Thanks.
Frankk

EDIT: I just noticed that the command that you suggested me creates the initrd in /tmp, I will try with that one.

EDIT2: IT WORKS!! BUT: I dont have anymore splash (graphic boot process). With vesafb I get nice graphics, but and not correct resolutions. With radeonfb i get a perfect 1280x768 framebuffer but no more graphic boot. Any hint?

---

### Post by evermind on 2005-10-29
[QUOTE=Frankk]I get this:
```
kernel /boot/vmlinuz-2.6.12-9-686 root=/dev/hda5 ro quiet splash video=radeonfb
```
[/QUOTE]
you don´t need to put video=radeonfb at the commandline cause in the initrd-script the modul will be loaded with the right parameters

Nice to hear that it works.
I don´t know what kind of splash-method is used in breezy maybe there is something in your logfiles.

EDIT:
A quick search through the forums shows that more people experienced this problem (the package is called Usplash, or similar)

---

### Post by Frankk on 2005-10-29
Btw I dont think that after all I will use radeonfb.
After my tests I can't get a working framebuffer+3Dxorg+suspend combination:

Framebuffer:vesafb
X:radeon
	Work both splash graphics at 640x480 resolution and suspension
	At higher resolution cannot resume from suspend
	No 3D acceleration

Framebuffer:vesafb
X:fglrx
	Cannot resume from suspend at any vesafb resolution
	3D acceleration works.

Framebuffer:radeonfb
X:radeon
	I get real resolution framebuffer (1280x768) but no splash graphics
	Cannot resume from suspend
	No 3D acceleration

Framebuffer:radeonfb
X:fglrx
	I get real resolution framebuffer (1280x768) but no splash graphics
	Cannot resume from suspend
	3D acceleration works.

So I think that I will use vesafb at 640x480 resolution with the radeon xorg driver.

Bye and thank.
Frankk

---

