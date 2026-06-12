---
title: "Many hardware related problems"
date: 2004-10-25
forum: Hardware &amp; Laptops
---

### Post by nutty on 2004-10-25
Hi,
  Total Linux newbie facing a bunch of problems with Ubuntu (my lack of knowledge???).... but i'd like to solve every one of them.....  rather than going back to Microsoft... so here they are:

1) PS/2 mouse (generic scroll mouse) not recognized - worked with MEPIS
2) Sound does not work (has not worked with RH, MEPIS, Ubuntu)
3) Windows partitions not automounted. Correct me if i'm wrong... but I think that I need to update the /etc/fstab file


System: 
Dell Inspiron 3500 laptop
128MB RAM
Neomagic magicmedia 256AV sound card

Alsa runs at boot and shuts down with message: ALSActl not found... : No soundcards found. Did manage to find out that the correct driver is snd-256. Don't know how to check whether the driver has been installed.

Can't run 'alsaconfig' - do I need to install any dev packages?

Waiting for help...

Best Wishes

---

### Post by LongTooth on 2004-10-26
I have a related problem. I have an old pc with a ISA sound card. I had it working with Slackware. Ran Alsaconf on it and got sound. When I first load Ubuntu on the same machine I ran alsaconf but still no sound. 

Bye the way, the command is 'alsaconf'. I did the same thing and keyed in alsaconfig. 

I still have no sound. Any solutions when one is using an old ISA sound card?

---

### Post by nutty on 2004-10-26
Tried the command 'alsaconf'. Get the message 'bash:alsaconf: command not found'.

Do I have to install any extra packages? (Already have alsa and alsa-utls)

Best Wishes

---

### Post by cacofonix on 2004-10-27
Try typing in the console "whereis alsaconfig" (Without quotes) if it finds it, type in sudo  /location/alsaconfig. If it doesnt print any location you need to install it. :D

---

### Post by flashball on 2004-10-27
switch to root and post results of the following commands

# fdisk /dev/hda -l
 
&

# cat /etc/fstab

---

### Post by nutty on 2004-10-27
hi Cacofonix. Here are the outputs:

Command: fdisk /dev/hda -l

Output:

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       20325    10243768+   7  HPFS/NTFS
/dev/hda2           20326       77520    28826280    f  W95 Ext'd (LBA)
/dev/hda5           20326       40635    10236208+   7  HPFS/NTFS
/dev/hda6           40636       60945    10236208+   c  W95 FAT32 (LBA)
/dev/hda7   *       67366       71415     2041168+  83  Linux
/dev/hda8           71956       77520     2804728+   c  W95 FAT32 (LBA)
/dev/hda9           71416       71955      272128+  82  Linux swap
/dev/hda10          60946       67365     3235648+  83  Linux


Command: cat /etc/fsab

Output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda10      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/ntfs_sys   ntfs    ro,dmask=0222,fmask=0333        0      0

Hope you guys can help. The only thing I really consider important is getting the PS2 mouse working. Hate using the touchpad all the time.

Thank you.
Best Wishes

---

### Post by nutty on 2004-10-27
Oops !!!

The earlier post was for flashball. This one is for you Cacofonix.

Tried the /location/alsaconfig command. Returns 'No such file or directory'. Looks like i'll have to reinstall alsa.

Thanks.

---

### Post by flashball on 2004-10-28
$ sudo mkdir /mnt/hda5 /mnt/hda6 /mnt/hda8

&

add the following lines into your fstab :

/dev/hda5 /mnt/hda5 ntfs auto,user,ro 0 0 
/dev/hda6 /mnt/hda6 vfat auto,user,rw 0 0
/dev/hda8 /mnt/hda8 vfat auto,user,rw 0 0

---

### Post by flashball on 2004-10-28
[QUOTE=nutty]Oops !!!

The earlier post was for flashball. This one is for you Cacofonix.

Tried the /location/alsaconfig command. Returns 'No such file or directory'. Looks like i'll have to reinstall alsa.

Thanks.[/QUOTE]

$ sudo /usr/sbin/alsaconf

---

### Post by cacofonix on 2004-10-28
[QUOTE=cacofonix]Try typing in the console "whereis alsaconfig" (Without quotes) if it finds it, type in sudo  /location/alsaconfig. If it doesnt print any location you need to install it. :D[/QUOTE]

It might help if I had it right in the first place #-o Thanks for the correction flashball, sorry nutty.

---

### Post by flashball on 2004-10-28
[QUOTE=nutty]
1) PS/2 mouse (generic scroll mouse) not recognized - worked with MEPIS
[/QUOTE]

$ cat /etc/X11/XF86Config-4

---

### Post by nutty on 2004-10-28
cat /etc/X11/XF86Config-4 gives me

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/Speedo"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "xtt"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Section "Device"
        Identifier      "NeoMagic Corporation NM2200 [MagicGraph 256AV]"
        Driver          "neomagic"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       28-49
        VertRefresh     43-72
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NeoMagic Corporation NM2200 [MagicGraph 256AV]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

-------------------

Looks like the mouse has been recognized, but the touchpad is activated by default. Am I correct???

Best Wishes

---

### Post by nutty on 2004-10-28
[QUOTE=flashball]$ sudo /usr/sbin/alsaconf[/QUOTE]


There's no directory or file at ' /usr/sbin/alsaconf '.

The only file is 'alsactl'.

The packages currently installed are:
alsa-base
alsa-utils
gnome-alsamixer
gstreamer
libpt-plugins-alsa

Do I have to mkdir /usr/sbin/alsaconf ? or is it a file ?

Best Wishes

P.S. Thank you telling me about the changes to the fstab.It works now.

---

### Post by im_ka on 2004-10-28
nutty,

if you don't wanna use your touchpad at all, edit the x config file by
```
sudo gedit /etc/X11/XF86Config-4
```
and comment the part with the touchpad. if you wanna use it again -> uncomment.

hope this helps

---

### Post by flashball on 2004-10-28
[QUOTE=nutty]

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
[/QUOTE]

are you sure to have  a ps2 mouse ? because /dev/input/mice is for usb mouse  



if you have a ps 2 mouse change  /dev/input/mice to 
/dev/mouse 


alsa problem :  on my debian ( sid ) /usr/sbin/alsaconf is installed with the alsa-utils package, maybe this package is corrupted so try  do this :
$ sudo apt-get update && sudo apt-get remove --purge alsa-utils && sudo apt-get install alsa-utils -y 

and try run     

$ sudo alsaconf

sorry for my english

---

### Post by nutty on 2004-10-28
[QUOTE=im_ka]nutty,

if you don't wanna use your touchpad at all, edit the x config file by
```
sudo gedit /etc/X11/XF86Config-4
```
and comment the part with the touchpad. if you wanna use it again -> uncomment.

hope this helps[/QUOTE]


Tried it. Breaks XServer. Back to base one. Thanks for the effort.

Best Wishes

---

### Post by nutty on 2004-10-28
[QUOTE=flashball]are you sure to have  a ps2 mouse ? because /dev/input/mice is for usb mouse  



if you have a ps 2 mouse change  /dev/input/mice to 
/dev/mouse 


alsa problem :  on my debian ( sid ) /usr/sbin/alsaconf is installed with the alsa-utils package, maybe this package is corrupted so try  do this :
$ sudo apt-get update && sudo apt-get remove --purge alsa-utils && sudo apt-get install alsa-utils -y 

and try run     

$ sudo alsaconf

sorry for my english[/QUOTE]

# I'm sure that it is a PS/2 mouse. Infact, the output also identified it as 'ImPS/2 mouse'. I feel that the problem is that both the PS/2 mouse and the touchpad are identified as valid input devices... and synaptics touchpad is given preference (default). Tried to 'uncomment' the mouse section... but it broke XServer.

# Removed and purged alsa-utils and reinstalled it. There is no alsaconf file in /usr/sbin. Looks like the alsaconf file was simply not created.

Best Wishes

---

### Post by daniels on 2004-10-28
[QUOTE=flashball]are you sure to have  a ps2 mouse ? because /dev/input/mice is for usb mouse[/QUOTE]

/dev/input/mice works for PS/2 mice also.

What sort of hardware do you actually have?  'My soundcard doesn't work' isn't really very useful, unfortunately.  The output of lspci is needed as a minimum.

---

### Post by nutty on 2004-10-29
[QUOTE=daniels]/dev/input/mice works for PS/2 mice also.

What sort of hardware do you actually have?  'My soundcard doesn't work' isn't really very useful, unfortunately.  The output of lspci is needed as a minimum.[/QUOTE]

Hi Daniels. Here's my system hardware

System:
Dell Inspiron 3500 laptop
128MB RAM
Neomagic magicmedia 256AV sound card
Neomagic video card (don't remember which model)

Anyway, I check alsa-project.org for the card and it seems to be supported ([http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Neomagic#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Neomagic#matrix))

Hope its helpful.

Best Wishes

---

### Post by herweg on 2004-10-29
[QUOTE=im_ka]nutty,

if you don't wanna use your touchpad at all, edit the x config file by
Code:

sudo gedit /etc/X11/XF86Config-4


and comment the part with the touchpad. if you wanna use it again -> uncomment.

hope this helps
[QUOTE=nutty]Tried it. Breaks XServer. Back to base one. Thanks for the effort.

Best Wishes[/QUOTE][/QUOTE]
Did you comment out the part at the bottom too under 
```
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection
```
? I had to remove an extra mouse, and I forgot to comment that out, and it broke X. Just a suggestion.

---

### Post by nutty on 2004-10-29
[QUOTE=daniels]/dev/input/mice works for PS/2 mice also.

What sort of hardware do you actually have?  'My soundcard doesn't work' isn't really very useful, unfortunately.  The output of lspci is needed as a minimum.[/QUOTE]

Output from 'lspci'

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
0000:06:00.0 Ethernet controller: D-Link System Inc DFE-690TXD CardBus PC Card (rev 10)

Note: the ethernet card is not built-in.

Best Wishes

---

### Post by nutty on 2004-10-29
[QUOTE=herweg]Did you comment out the part at the bottom too under 
```
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection
```
? I had to remove an extra mouse, and I forgot to comment that out, and it broke X. Just a suggestion.[/QUOTE]

Hi Herweg,
  Thank you for the suggestion. I tried doing, that as you suggested and rebooted the laptop... just to make sure.
Result: 
The PS/2 mouse did not work
The synaptic touchpad half worked - could move the arrow using the touchpad but could not tap the touchpad to start apps. Till now I could tap the touchpad and that would emulate the left button of the mouse.

Conclusion: The synaptic touchpad is one persistent  #$@%^. Does not want to give up control..... hehehehehehe

---

### Post by bewilkinson on 2004-11-24
for proper mouse support make sure BIOS is set to PnP OS and legacy USB is DISABLED

---

### Post by brihas on 2006-07-02
[QUOTE=bewilkinson]for proper mouse support make sure BIOS is set to PnP OS and legacy USB is DISABLED[/QUOTE]
Thanks for this tip :-) I have installed Kubuntu 6.06 Dapper Drake on a Inspiron 3500 and could not get the mouse to work, only the touchpad was working. The trick is in BIOS to change the trackpad setting to Auto-off.

---

