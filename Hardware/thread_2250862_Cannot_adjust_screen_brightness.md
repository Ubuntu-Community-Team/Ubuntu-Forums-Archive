---
title: "Cannot adjust screen brightness"
date: 2014-10-31
forum: Hardware
---

### Post by paul_b4 on 2014-10-31
After installing Ubuntu, I am not able to adjust the  screen brightness.  This is a bigger problem than it seems, because  after a while it makes my eyes hurt, and I can't compromise my eyes to  use Ubuntu.

Having searched online for some solutions, I added this file /usr/share/X11/xorg.conf.d/20-intel.conf and these lines

Section "Device"
        Identifier "card0"
        Driver "intel"
        Option "Backlight" "intel_backlight"
        BusID "PCI:0:2:0"
EndSection

[FONT=arial]That[/FONT] [FONT=arial]did not solve the problem, and I tried this

[/FONT]Update your Grub file, line no 11 in /etc/default/grub to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

update grub using the command
update-grub
Reboot and you are done.

[FONT=arial]This did not solve the problem, but  instead now when I put headphones into the computer, they do not work.   They do not work even after I changed the [/FONT]GRUB_CMDLINE_LINUX_DEFAULT [FONT=arial]back to what it was before.  Please help!

Thank you[/FONT]

---

### Post by Toz on 2014-10-31
Can you open a terminal window, type in the following commands and post back the results:

1. The version of ubuntu that you are running:
```
cat /etc/lsb-release
```

2. Your current kernel boot line:
```
cat /proc/cmdline
```

3. Info about your video card(s) and drivers:
```
lspci -k | grep -A2 VGA
```

4. Info about the recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

5. Your currently loaded kernel modules:
```
lsmod
```

6. What, if anything, xorg says about backlight:
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by paul_b4 on 2014-11-01
Hi Toz, thanks for the help.  

[SIZE=4]**1.**[/SIZE]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"


[SIZE=4]**2.**[/SIZE]
BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=730dc0d2-8142-4bc0-a5ee-a2928da9bd65 ro quiet splash acpi_backlight=vendor vt.handoff=7
[B]
[SIZE=4]3.[/SIZE][/B]
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device 14dd
    Kernel driver in use: i915


[SIZE=4]**4.**[/SIZE]
 /sys/class/backlight/asus-nb-wmi
100
100
100

 /sys/class/backlight/intel_backlight
7812
7812
7812

[SIZE=4]**5.**[/SIZE] (Sorry, I couldn't figure out how to paste this and keep the column separation)

Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
intel_rapl             18773  0 
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm_intel             143148  0 
kvm                   451729  1 kvm_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
arc4                   12608  2 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
ath9k                 164164  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ath9k_common           13551  1 ath9k
snd_timer              29482  2 snd_pcm,snd_seq
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
joydev                 17381  0 
snd                    69322  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              484040  3 ath,ath9k,mac80211
serio_raw              13462  0 
i915                  783961  3 
soundcore              12680  1 snd
drm_kms_helper         55071  1 i915
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
video                  19476  2 i915,asus_wmi
wmi                    19177  1 asus_wmi
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
psmouse               106714  0 
r8169                  67581  0 
mii                    13934  1 r8169
rtsx_pci               46202  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  4 
libahci                32716  1 ahci

[SIZE=4]**6.**[/SIZE]
[    20.205] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=730dc0d2-8142-4bc0-a5ee-a2928da9bd65 ro quiet splash acpi_backlight=vendor vt.handoff=7
[    20.589] (--) intel(0): found backlight control interface asus-nb-wmi (type 'platform')

---

### Post by Toz on 2014-11-01
Now that you are using "acpi_backlight=vendor" (which exposes the intel_backlight interface), can you now try again the /usr/share/X11/xorg.conf.d/20-intel.conf hack?
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

Log out and back in again to test. 

If it doesn't work, post back again:
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by paul_b4 on 2014-11-01
It didn't work.

This is what I get in the terminal after cat /var/log/Xorg.0.log | grep -i backlight 
[    20.511] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=730dc0d2-8142-4bc0-a5ee-a2928da9bd65 ro quiet splash acpi_backlight=vendor vt.handoff=7
[    20.855] (**) intel(0): Option "Backlight" "intel_backlight"
[    20.856] (**) intel(0): found backlight control interface intel_backlight (type 'user')

Also, every time I try to modify /usr/share/X11/xorg.conf.d/20-intel.conf with gedit, I this message in the terminal: (gedit:2400): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

---

### Post by Toz on 2014-11-01
> **paul_b4 said:**
> Also, every time I try to modify /usr/share/X11/xorg.conf.d/20-intel.conf with gedit, I this message in the terminal: (gedit:2400): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Can you post the contents of /usr/share/X11/xorg.conf.d/20-intel.conf?

How are you running gedit? Are you using gksudo?

Do the following commands adjust brightness?
```
echo 4000 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 5000 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 6000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

What happens if you:
```
sudo modprobe -r asus_nb_wni
```
...does the backlight work then? (using both the function keys and the brightness indicator).

---

### Post by paul_b4 on 2014-11-02
The contents of /usr/share/X11/xorg.conf.d/20-intel.conf:

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection

I am running gedit with this command:

sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf

Yes, those commands did adjust brightness.  When I run sudo modprobe -r asus_nb_wni, I get this message in the terminal: "modprobe: FATAL: Module asus_nb_wni not found".  I cannot adjust the brightness with the function keys, and there is no brightness indicator that I can find.

Please don't forget that my headphones are still not working with Ubuntu!

---

### Post by crcarson on 2014-11-02
Have similar problem on Gnome 14.10.  See forum entry "Brightness control not working" in Desktop Environments forum.

---

### Post by Toz on 2014-11-02
> **paul_b4 said:**
> Yes, those commands did adjust brightness.  When I run sudo modprobe -r asus_nb_wni, I get this message in the terminal: "modprobe: FATAL: Module asus_nb_wni not found".
Sorry, typo. That should be:
```
sudo modprobe -r asus_nb_wmi
```
...('m' instead of 'n'). Its one of the kernel modules listed with "lsmod".

> I cannot adjust the brightness with the function keys, and there is no brightness indicator that I can find.
If you type "Brightness" into the unity launcher, does it not bring up the "Brightness and Lock" application?

> Please don't forget that my headphones are still not working with Ubuntu!
You might want to create another thread to deal with the headphone issue - its not related to the brightness issue.

---

### Post by paul_b4 on 2014-11-02
Ok, I put in 
sudo modprobe -r asus_nb_wmi

[FONT=arial]and nothing happened in the terminal, it just gave me the normal "paul@paul-X551MA:~$". Then I tried to use the function keys again, but they did not work.  

I went to go to Brightness and Lock again, and this time the brightness slider appeared.  I promise you that every time I have gone before, it was not there.  
Maybe it was opened after entering the above command.  However, the function keys still do not work, and I believe that the headphone issue is related, because they were working before, and 
after following these instructions

> Update your Grub file, line no 11 in /etc/default/grub to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"



update grub using the command

update-grub

Reboot and you are done.

they did not work anymore, though in the Sound Settings it shows that headphones are plugged in.
[/FONT]

---

### Post by Toz on 2014-11-02
Okay try this. [Blacklist]("https://help.ubuntu.com/community/Loadable_Modules#Blacklisting_Modules") the asus_nb_wmi kernel module and reboot.

See if you have the brightness slider again and whether it works.

Try the function keys. (I have a feeling they won't work and we'll need to consider a workaround).

As for the headphones, that kernel parameter would have no effect on the headphones. I think its just a coincidence that they stopped working then. Double-check to make sure that the headphones are not muted when they are plugged in. If possible, log in as guest and try the headphones there. If they don't work, its indicative of a system issue. If they do work, then there is something wrong with your profile.

---

### Post by paul_b4 on 2014-11-03
I tried to blacklist asus_nb_wmi, but I get this message in the terminal when I try to save: [ Error writing /etc/modprobe.d/blacklist: Permission denied ] . I tried to do the same thing again from this command, 
sudo nano -w /etc/modprobe.d/blacklist

[FONT=arial]but I got the same error message again.[/FONT]  [FONT=arial]The headphones are not muted when plugged in, and they still do not work when I am using a Guest account. They do work in Windows 8 though.[/FONT]

---

### Post by Toz on 2014-11-03
Try this instead:
```
gksudo gedit /etc/modprobe.d/blacklist
```
...if you get an error that gksudo command is not found, then try:
```
sudo -i gedit /etc/modprobe.d/blacklist
```

---

### Post by paul_b4 on 2014-11-03
I was able to add asus_nb_wmi to /etc/modprobe.d/blacklist, but after rebooting, the function keys still do not work.  The brightness slider is still there though.

---

### Post by Toz on 2014-11-03
The proper way to fix this is to create a bug report against the linux kernel so that this module can get fixed.

All we can do now is workarounds to get around the issue. If you want, we can try to assign commands to the function keys to get them to change brightness. If you want to do this, can you tell me if the following commands adjust brightness:
```
xbacklight -inc 10%
xbacklight -dec 10%
```

If they do, simply assign those commands as keyboard shortcuts to the function key combinations. I don't use unity so I'm not sure exactly where the utility is for setting these shortcuts. Try searching for "keyboard" in the dash.

---

### Post by paul_b4 on 2014-11-04
Those commands do not adjust the brightness.  How do I create a bug report, and which kernel is it that I should report?

---

### Post by Toz on 2014-11-04
> **paul_b4 said:**
> Those commands do not adjust the brightness.
What does the following return now:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

> How do I create a bug report, and which kernel is it that I should report?
To start the bug reporting process:
```
ubuntu-bug linux
```

---

### Post by paul_b4 on 2014-11-05
Entering 
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; donegives me this:

 /sys/class/backlight/asus-nb-wmi
100
100
100

 /sys/class/backlight/intel_backlight
7812
7812
7812

I have submitted the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1389675](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1389675) .

---

### Post by miro-shining on 2014-11-06
[COLOR=#333333][FONT=Lucida Grande]This was my solution for my grafics adapter (NVIDIA GeForce 8400M G) but if you can figure out how it works with yours it might be good, too.

sudo gedit /etc/X11/xorg.conf[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]You will have to enter your root password.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Now, you should see:[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]___________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Section "Device"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Identifier "Device0"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Driver "nvidia"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]VendorName "NVIDIA Corporation"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]EndSection[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]___________________________________________________[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]If you see nothing, just enter all the lines above and follow up with the next step below[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Under the VendorName Line, add the following:[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]______________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Option "RegistryDwords" "EnableBrightnessControl=1"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]______________________________________________________[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Now, save and reboot. Check your brightness controls, and hopefully this fixed things.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I've tried so many solutions out of the net and nothing had helped me until I came to this solution. But be aware that these steps only working for NVIDIA Grafics and you must have chosen the NVIDIA Driver in your system in "Administration -> Driver Manager"[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I've posted this answer very often now and I believe if you're able to figure out what you have to insert instead of NVIDIA it should work for the intel device as well. Or just try the line with the Option "RegistryDwords" ... maybe this will work, too but as I wrote above it was NVIDIA in my case. so no guarantee [/FONT][/COLOR]

---

### Post by Toz on 2014-11-07
> **paul_b4 said:**
> Entering 
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; donegives me this:

 /sys/class/backlight/asus-nb-wmi
100
100
100

 /sys/class/backlight/intel_backlight
7812
7812
7812

I have submitted the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1389675](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1389675) .

Can you post back the contents of /etc/modprobe.d/blacklist ?

---

