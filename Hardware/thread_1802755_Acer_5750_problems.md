---
title: "Acer 5750 problems"
date: 2011-07-12
forum: Hardware
---

### Post by Sda1986 on 2011-07-12
Hi all, I've just bought a new Acer 5750

Intel i3-2310M
Intel HD Graphics 3000
15.6 HD Led monitor
4Gb Ddr3 Ram
Ub11.04

I have a couple of trouble
[LIST=1]
[*]No Brightness control
[*]No touchpad scroll
[/LIST]

I have an additional problem with the quality of audio, but right now it's not urgent at all. 
I'm searching online since Saturday but I'm not able to find the solution to this problem. Brightness control is the most urgent, I need to save energy and have a better battery life!
Can you help me? I can give you all information you need, you have only to ask! Thanks!

THANKS!!!

---

### Post by Manyette on 2011-07-12
I have a 5750 also, and the brightness control is on the arrow keys (with Fn) and the scroll does work just find. Do you have the scroll enabled?

---

### Post by Sda1986 on 2011-07-12
Yes, I know I can control brightness with Fn+Arrows L\R, but when I do it, the brightness doesn't change.

But inside /sys/class/backlight/acpi_video0/actual_brightness the number change when I change the level with FN+Arrow...

I don't have in mouse option the tab about scrolling...

This is how it is just after installed...

Do you have a different situation? what OS? anything to change?

---

### Post by Manyette on 2011-07-12
Well, if the numbers change, but the brightness does not, it seems to be a hardware problem, I suppose.  As for the scrolling, I am running Ubuntu 10.10 and it is under Prererences->Mouse->Touchpad.  But I did believe that the selection was in all versions of Ubuntu.  Perhaps I'm in error, or perhaps you are running another distro? Anyway, sorry I couldn't help.

I will add that the changes to brightness are not as large as with other machines. It takes rather dim lighting to see them.

---

### Post by Sda1986 on 2011-07-12
I run Ubuntu 11.04

I tried Ubuntu 10.10, same problem both Video and Pad...

No change of back light and no pad tab

---

### Post by Manyette on 2011-07-12
I sent to you a private message, quite long, with some details which may help.  But a conversation with the Dell folks might be in order.

---

### Post by Sda1986 on 2011-07-12
So according with "Manyette", brightness control doesn't work with a 1.10+ bios, he had a 1.05 and it worked.

So maybe (i hope) soon they will fix this. Does anybody know if LED monitor can save energy with less brightness? or change brightness is the same as use the command xgamma -gamma n, with n a number?

EDIT: It might be better talk about BACKLIGHT not brightness...

Any idea for the touchpad?

---

### Post by Kirkhelek on 2011-08-20
> **Sda1986 said:**
> So according with "Manyette", brightness control doesn't work with a 1.10+ bios, he had a 1.05 and it worked.

So maybe (i hope) soon they will fix this. Does anybody know if LED monitor can save energy with less brightness? or change brightness is the same as use the command xgamma -gamma n, with n a number?

EDIT: It might be better talk about BACKLIGHT not brightness...

Any idea for the touchpad?

hi, i have an acer 575 too and i solved the touchpad and screen problems on ubuntu 10.04 installing the last kernel-> 2.6.38  (nvidia optimus doesn.t have support yet, so don't install the private drivers)

but, the problem with the brightness is already unfixed. anyone solved it?

---

### Post by sbraz on 2011-08-20
> **Sda1986 said:**
> Does anybody know if LED monitor can save energy with less brightness? or change brightness is the same as use the command xgamma -gamma n, with n a number?

EDIT: It might be better talk about BACKLIGHT not brightness...

Any idea for the touchpad?
yes, lowering the brightness saves power. led screens use leds (duh) for the exact same purpouse lamps did in the past: provide white light to be filtered by the pixels.
the problem might have something to do with the module **acer_wmi**; its source code changed a lot from 2.6.39.4 to 3.0.0 (so much that my bluetooth didn't work anymore :D). it is possible that a recent 3.0.0 kernel will fix your problem about brightness.



about the touchpad, post the output of **xinput list**, like this:
```
root@sbraz-netbook:/usr/src/broadcom# xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® SideWinder&#8482; X3 Mouse	id=12	[slave  pointer  (2)]
&#9116;   &#8627; **PS/2 Generic Mouse**                      	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=10	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=11	[slave  keyboard (3)]
    &#8627; 1.3M WebCam                             	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=16	[slave  keyboard (3)]

```
that in bold is my alps touchpad, wrongly recognized as a ps2 mouse. :( that's why in my case scrolling doesn't work.

i'm testing a kernel patch with some successes (i'm running an unpatched kernel as i type).
this is what i changed:
[https://confluence.nau.edu/confluence/display/~cmg238@nau.edu/Recognize+ALPS+Touchpad+on+Dell+E6510+in+Ubuntu](https://confluence.nau.edu/confluence/display/~cmg238@nau.edu/Recognize+ALPS+Touchpad+on+Dell+E6510+in+Ubuntu)


> **Sda1986 said:**
> It might be better talk about BACKLIGHT not brightness...
i think given the context that brightness is correct too, i'm using 10.10 english and in "power management preferences" it says "set display _brightness_ to". :)

---

### Post by Mr.Pytagoras on 2011-08-21
Hi I also bough this type of laptop, I have 5750G with i5 2410m procesor and nvidia GT540/intel GPU(optimus)

I've been googling to find a solution for the brightness problem and it seem that the only way how to control the brightness is to add acpi_osi=Linux to grub.cfg, right now I not on my new laptop, but when i get there i will post my grub.cfg

I had also problems with power consuption, the system was gradually consuming more power, starting at 16-18w/h since start, ending(and holding) at 30w/h I manage to solve it with some configurations.

Not to mention Nvidia card, if you want to use you system then DO NOT INSTALL NVIDIA DRIVER, otherwise you will end with a black screen, however there is ongoing project to support the Optimus technology under linux, so maybe someday we will be able to use the Optimus and Nvidia card.

I had also problem with webcam(solved), touchpad and system lags(solved)

I will post a new reply when I get on my laptop

---

### Post by Mr.Pytagoras on 2011-08-21
hi again 

the acpi_osi=Linux workaround

```

...
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2a9dfb30-ef75-4ae1-ab3c-b7ecbd7893dc
    linux    /vmlinuz-2.6.38-8-generic root=UUID=9a065b58-2033-4bcc-943e-1586e8a168b4 ro   quiet splash vt.handoff=7 **acpi_osi=Linux**
    initrd    /initrd.img-2.6.38-8-generic
}
...

```to save some battery I've been using this script:
```

#!/bin/sh
# A script to enable laptop power saving features for #! & Debian GNU+linux.
# http://crunchbanglinux.org/forums/topic/11954

# List of modules to unload, space seperated. Edit depending on your hardware and preferences.
modlist="uvcvideo"
# Bus list for runtime pm. Probably shouldn't touch this.
buslist="pci spi i2c"

case "$1" in
    true)
    # Enable some power saving settings while on battery
       # Enable laptop mode
        echo 5 > /proc/sys/vm/laptop_mode
       # Less VM disk activity. Suggested by powertop
        echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
       # Intel power saving
        echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
        echo 1 > /sys/module/snd_hda_intel/parameters/power_save
       # Set backlight brightness to 50%
        echo 5 > /sys/devices/virtual/backlight/acpi_video0/brightness
       # USB powersaving
        for i in /sys/bus/usb/devices/*/power/autosuspend; do
            echo 1 > $i
        done
       # SATA power saving
        for i in /sys/class/scsi_host/host*/link_power_management_policy; do
            echo min_power > $i
        done
       # Disable hardware modules to save power
        for mod in $modlist; do
            grep $mod /proc/modules >/dev/null || continue
            modprobe -r $mod 2>/dev/null
        done
       # Enable runtime power management. Suggested by powertop.
        for bus in $buslist; do
            for i in /sys/bus/$bus/devices/*/power/control; do
                echo auto > $i
            done
        done
    ;;
    false)
       #Return settings to default on AC power
        echo 0 > /proc/sys/vm/laptop_mode
        echo 500 > /proc/sys/vm/dirty_writeback_centisecs
        echo N > /sys/module/snd_hda_intel/parameters/power_save_controller
        echo 0 > /sys/module/snd_hda_intel/parameters/power_save
        echo 10 > /sys/devices/virtual/backlight/acpi_video0/brightness
        for i in /sys/bus/usb/devices/*/power/autosuspend; do
            echo 2 > $i
        done
        for i in /sys/class/scsi_host/host*/link_power_management_policy
            do echo max_performance > $i
        done
        for mod in $modlist; do
            if ! lsmod | grep $mod; then
                modprobe $mod 2>/dev/null
            fi
        done
        for bus in $buslist; do
            for i in /sys/bus/$bus/devices/*/power/control; do
                echo on > $i
            done
        done
    ;;
esac

exit 0

```just copy it and save it as** /etc/pm/power.d/powersave**
 and make it executable:
```

chmod +x /etc/pm/power.d/powersave

```
I was using this script also on my old asus laptop, and now using it on my new acer laptop and it works :)

---

### Post by Peter Parkorr on 2011-10-06
Hi,

I'm new to Linux, and just about to buy the Acer 5750 with core i7 and the Geforce 540 (with optimus technology).

I'm planning on installing Ubuntu Studio 11.04, so am I right in thinking I should install the distro but skip installing the Nvidia drivers for now, and until I use the workaround here or [this]("http://ubuntuforums.org/showthread.php?t=1835123&highlight=acer+5750") it should all be working fine except for brightness control and the touchpad only?

I can live without those while I figure it out...
Thanks

PP

---

### Post by Peter Parkorr on 2011-10-14
> **Peter Parkorr said:**
> Hi,

I'm new to Linux, and just about to buy the Acer 5750 with core i7 and the Geforce 540 (with optimus technology).

I'm planning on installing Ubuntu Studio 11.04, so am I right in thinking I should install the distro but skip installing the Nvidia drivers for now, and until I use the workaround here or [this]("http://ubuntuforums.org/showthread.php?t=1835123&highlight=acer+5750") it should all be working fine except for brightness control and the touchpad only?

I can live without those while I figure it out...
Thanks

PP

I bought the laptop, [installed]("http://ubuntuforums.org/showthread.php?t=1858510") Ubuntu 11.04 and the touchpad, networking etc, are working fine. The backlight adjustment isn't working but no biggie. No problems witht the screen but I havent installed any extra drivers.

---

### Post by markitzero on 2011-10-14
I have an Acer 5742 and I fixed the brightness controls using 
 sudo gedit /etc/default/grub
And replacing 
GRUB_CMDLINE_LINUX=""
With 
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Credit to [http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html](http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html)

---

### Post by Peter Parkorr on 2011-10-14
> **markitzero said:**
> I have an Acer 5742 and I fixed the brightness controls using 
 sudo gedit /etc/default/grub
And replacing 
GRUB_CMDLINE_LINUX=""
With 
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Credit to [http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html](http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html)

Ah, thanks dude, looks simple enough. My line looks like this though;

GRUB_CMDLINE_LINUX=" vga=771" so maybe best to leave it?
Shane

---

### Post by sbraz on 2011-10-16
> **Peter Parkorr said:**
> Ah, thanks dude, looks simple enough. My line looks like this though;

GRUB_CMDLINE_LINUX=" vga=771" so maybe best to leave it?
Shane

removing that **vga=771** shouldn't break anything important, anyway you can add that parameter to your /etc/default/grub separated by a space, here's mine (different computer):

```
GRUB_CMDLINE_LINUX="no_console_suspend vga=0 pcie_aspm=force"

```

---

### Post by Peter Parkorr on 2011-10-16
Righto, will give it a pop then and report back!
Shane

---

### Post by Peter Parkorr on 2011-10-23
> **markitzero said:**
> I have an Acer 5742 and I fixed the brightness controls using 
 sudo gedit /etc/default/grub
And replacing 
GRUB_CMDLINE_LINUX=""
With 
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Credit to [http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html](http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html)

Worked a charm (the keys for brighter/darker are reversed for the record)

Thanks markitzero / sbraz

Going to try powersaving stuff now. Only stealing this thread from OP as it is Acer 5750 so keeping it all in one place for other newbies.
Shane

---

### Post by thedebster on 2011-11-21
I'm still having problems with the brightness control not actually changing the brightness. The graphic on the top right indicates the brightness is going up and down but the brightness doesn't actually change.

Any insight?

---

### Post by Peter Parkorr on 2011-11-30
> **thedebster said:**
> I'm still having problems with the brightness control not actually changing the brightness. The graphic on the top right indicates the brightness is going up and down but the brightness doesn't actually change.

Any insight?

Hi Deb,

Sorry for the late reply...

Did you add "acpi_osi=Linux" and then update grub? If you didnt update grub then no changes will have taken effect I think.

running "sudo update-grub" in Terminal may fix it for you.

Peter

---

### Post by super123hit on 2011-12-01
yes, decreasing the brightness saves energy. brought screens use leds (duh) for that identical purpouse lamps did previously: provide whitened light to become strained through the pixels.

the issue may have something related to the module acer_wmi its source code transformed so much from 2.6.39.4 to three.. (a lot that my bluetooth did not work any longer ). it's possible that the recent 3.. kernel will fix your condition about brightness.
_____________________
[Hip Hop Songs]("http://songs4hiphop,com/")

---

### Post by cucisan on 2011-12-17
hello!

thanks a lot for the hint with acpi_osi=Linux

this fixed the brightness problem on my Packard Bell TSX66 (which is actually an Acer 5750 or something similar) and also it seems it fixed my not-working usb3.0 :)

that is on oneiric with kernel 3.0.0-14.23

fyi: ironhide (aka bumblebee) works flawlessly with this laptop and battery reports 9.9w discharge rate which is great for an core i5 :)

---

### Post by Manyette on 2011-12-17
Brightnewss solution.  Modify  /etc/default/grub using "gksudo gedit grub".

Change this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

To:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

Then save the file.

Then before rebooting issue the command in terminal
sudo update-grub

Reboot and the brightness controls should now work properly on the Acer 7550 series of machines.

---

### Post by durilka on 2012-01-25
well, today after the kernel update the touchpad stopped working.

3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

there's no "touchpad" tab in mouse settings and xinput shows none. ideas?

EDIT. The touchpad is magically after couple of reboots back(orly?) but having acpi_osi=linux hasn't changed anything after grub-update. maybe it's the lowercase l in linux. it got offended. i'll try after next reboot again.

---

### Post by aspi12 on 2012-09-03
> **Manyette said:**
> Brightnewss solution.  Modify  /etc/default/grub using "gksudo gedit grub".

Change this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

To:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

Then save the file.

Then before rebooting issue the command in terminal
sudo update-grub

Reboot and the brightness controls should now work properly on the Acer 7550 series of machines.

Are you right?

acpi_osi=
or 
acpi_osi=Linux?

I changed it to acpi_osi=Linux on my acer 5750 and it works. But the system saves not the value and if I switch to Batterie mode I have to switch the Brightnews mysef.

If I change the value I didn't become a notification from ubuntu. Before I changed acpi_osi=Linux i got the notification message but it dosn't works.

---

### Post by sunkumar on 2013-05-24
Thank you

---

