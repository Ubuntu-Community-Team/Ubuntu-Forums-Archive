---
title: "Brightness Issues on HP Pavilion 15-n042se Notebook PC"
date: 2014-03-15
forum: Hardware
---

### Post by mostafa_ragab on 2014-03-15
I have installed Ubuntu 12.04 LTS, i found that i can't [COLOR=#000000]control the display brightness with the hotkeys (F2 and F3)[/COLOR] or even from GUI (Brightness and lock screen), i don't have any control on the brightness.
I have searched for long time and i have tried many solutions, with no change in the issue status.
Solutions that i tried : 
i changed the file /etc/default/grub with one of the following suggestions :
[LIST]
[*]GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor"
[*]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
[/LIST]



[LIST]
[*]GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
[*]GRUB_CMDLINE_LINUX="acpi_backlight=linux"
[/LIST]

By run update-grub and reboot the machine after each change.

Also i added this line : 
echo 2 > /sys/class/backlight/acpi_video0/brightness
to the file : /etc/rc.local to control the brightness but it doesn't work too.

Here is some data could help on solving my problem :
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 0a16 (rev 09)

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=06ab0d93-ca49-4390-8135-78d25b50a3cc ro acpi_backlight=vendor quiet splash

Any recommendations please !!

---

### Post by Toz on 2014-03-15
Hello and welcome to the forums.

First, it would be helpful if you could post back your kernel module list:
```
lsmod
```



Now, here is a set of commands that I would like you to run:
```

cat /proc/cmdline
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

```
Can you post back the results of these commands under the following kernel parameter scenarios:
1. GRUB_CMDLINE_LINUX="acpi_backlight=vendor" -> your current kernel parameter
2. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" -> (no kernel parameters) - remove acpi_backlight=vendor
3. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
4. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

Remember to run "sudo update-grub after each change and reboot.

I think you're going to find that you have more than one backlight interface and this is the cause of the interference. I want to see if any of those kernel parameter combinations can bring you down to just one backlight interface.

---

### Post by mostafa_ragab on 2014-03-16
Hello and Thank you.

[B]First the lsmod output : 
[/B]**$ lsmod : **
```
Module                  Size  Used by
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_hda_codec_realtek   223867  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
nvidia              10618593  0 
joydev                 17693  0 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
rt3290sta            1182338  1 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87603  0 
uvcvideo               72627  0 
lp                     17799  0 
videodev               98259  1 uvcvideo
snd                    78855  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
mac_hid                13253  0 
serio_raw              13211  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
v4l2_compat_ioctl32    17128  1 videodev
video                  19596  0 
wmi                    19256  1 hp_wmi
r8169                  62099  0 
```



[SIZE=3]I followed the instructions, and considered run sudo update-grub after each change and reboot.
[/SIZE]
_1. GRUB_CMDLINE_LINUX="acpi_backlight=vendor" -> your current kernel parameter_
_2. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" -> (no kernel parameters) - remove acpi_backlight=vendor_
[B](Because that is my current configuration)
[/B]


**$cat /proc/cmdline**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=06ab0d93-ca49-4390-8135-78d25b50a3cc ro acpi_backlight=vendor quiet splash


**$for interface in /sys......**
  /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory






_3. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="_


**$cat /proc/cmdline**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=06ab0d93-ca49-4390-8135-78d25b50a3cc ro acpi_backlight=vendor quiet splash acpi_osi=


**$for interface in /sys......**
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory


[U]
4. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"[/U]

**$cat /proc/cmdline**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=06ab0d93-ca49-4390-8135-78d25b50a3cc ro acpi_backlight=vendor quiet splash acpi_osi=Linux acpi_backlight=vendor




**$for interface in /sys......**
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory





That's it, waiting for your reply please.
Thanks

---

### Post by Toz on 2014-03-16
Each one of those kernel parameter lines has acpi_backlight=vendor in it (which is what we didn't want in all instances). Can you post back your /etc/default/grub file? 

Interesting that its not providing a backlight interface with that parameter. Can you also post back your /var/log/Xorg.0.log file like this:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated?

---

### Post by mostafa_ragab on 2014-03-16
**/etc/default/grub file content : **
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```



**pastebinit /var/log/Xorg.0.log**
[http://paste.ubuntu.com/7102090/](http://paste.ubuntu.com/7102090/)

---

### Post by Toz on 2014-03-16
Okay, lets try this. In your /etc/default/grub file, change the line that reads:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
...to read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
We'll make all of our changes to the "GRUB_CMDLINE_LINUX" line.


Now the changes:
1. Try with the line empty:
```
GRUB_CMDLINE_LINUX=""
```
...run "sudo update-grub", reboot and post back results.

2. Try with **acpi_osi=**:
```
GRUB_CMDLINE_LINUX="acpi_osi="
```
...run "sudo update-grub", reboot and post back results.



I'll review your Xorg log file to see if there is anything interesting there.

---

### Post by Toz on 2014-03-16
> **Toz said:**
> I'll review your Xorg log file to see if there is anything interesting there.

Well there is definitely something interesting there. Your computer is using the VESA graphics driver instead of the Intel one. Have you configured something to force the system to use VESA (I don't see anything in the Xorg log file)?



Does this laptop only have the one video card, the intel one?
> [    27.654] (--) PCI:*(0:0:2:0) 8086:0a16:103c:2166 rev 9, Mem @ 0xb5000000/4194304, 0xc0000000/268435456, I/O @ 0x00006000/64
[    27.654] (--) PCI: (0:10:0:0) 10de:1292:103c:2166 rev 161, Mem @ 0xb3000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128
...seems like there is a second one hiding there.

---

### Post by mostafa_ragab on 2014-03-16
I always have interesting things :D
I'm dealing with a fresh installation Ubuntu 12.04 LTS, I didn't do any modifications except that modifications that we are dealing with it here.
This laptop has one video card** NVIDIA GeForce GT 740M (2 GB DDR3 dedicated)** [http://www8.hp.com/emea_middle_east/en/products/laptops/product-detail.html?oid=6552346#!tab=specs](http://www8.hp.com/emea_middle_east/en/products/laptops/product-detail.html?oid=6552346#!tab=specs)

Now i changed GRUB settings to be :
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi="

**$cat /proc/cmdline**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=2a6aafe8-2379-47d5-9d89-ae5e2d9811c7 ro acpi_osi= quiet splash vt.handoff=7

**$for interface in /sys......**
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory

I just installed a fresh ubuntu (again), please follow the Xorg.0.log from this new URL:
**pastebinit /var/log/Xorg.0.log**
[http://paste.ubuntu.com/7103049/](http://paste.ubuntu.com/7103049/)

So, no changes, and still i can't control the brightness, even i can't find it in brightness and lock screen in the system settings.

---

### Post by Toz on 2014-03-16
> **mostafa_ragab said:**
> I always have interesting things :D
I'm dealing with a fresh installation Ubuntu 12.04 LTS, I didn't do any modifications except that modifications that we are dealing with it here.
This laptop has one video card** NVIDIA GeForce GT 740M (2 GB DDR3 dedicated)** [http://www8.hp.com/emea_middle_east/en/products/laptops/product-detail.html?oid=6552346#!tab=specs](http://www8.hp.com/emea_middle_east/en/products/laptops/product-detail.html?oid=6552346#!tab=specs)
I believe that the answer to your backlight issues rests with you properly enabling and managing the dual graphics capabilities of your laptop. Unfortunately, I have no experience in this matter, though others here on the forums can help. As a starting off point, have a look at the [Ubuntu Bumblee wiki]("https://wiki.ubuntu.com/Bumblebee").

---

### Post by mostafa_ragab on 2014-03-18
About the video card, i discovered that i have two video card as you listed before : 

[COLOR=#000000]*[ 27.654] (--) PCI:*(0:0:2:0) 8086:0a16:103c:2166 rev 9, Mem @ 0xb5000000/4194304, 0xc0000000/268435456, I/O @ 0x00006000/64*[/COLOR]
[COLOR=#000000]*[ 27.654] (--) PCI: (0:10:0:0) 10de:1292:103c:2166 rev 161, Mem @ 0xb3000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128*[/COLOR] 

I hope anyone could help me in that, anyone !
Thank you .

---

