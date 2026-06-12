---
title: "strange prob with suspend and hibernate"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by it.henrik on 2006-06-20
I have a DELL C840 and suspend and hibernate almost works.

Suspend seems to work fine, it goes down as it should and when I press the power button it goes up again. The screensaver comes on but keyboard is unresponsive. ](*,) ... After a while even the led for numlock gets turned off. 

How can I resume control over my keyboard after a resume from suspension?

Hibernate seems to do everything it should and turns off nicely. When I power on again I am greeted by grub and the result is a normal boot.

How can I get hibernation to work as expected when I power on again?

---

### Post by it.henrik on 2006-06-20
bump

someone got any clues at all?

---

### Post by kashms on 2006-06-21
For the suspend problem: does your mouse work after resume? Do you have a ps2 or usb mouse? How about the touchpad?

For the hibernation problem: Did you specify the resume (swap) partition as grub boot option?

---

### Post by it.henrik on 2006-06-25
[QUOTE=kashms]For the suspend problem: does your mouse work after resume? Do you have a ps2 or usb mouse? How about the touchpad?

For the hibernation problem: Did you specify the resume (swap) partition as grub boot option?[/QUOTE]

I have a DELL Latitude c840 with a nvidia 440 2Go .. if it makes any difference :)

Suspend: I cant get the computer to wake up from the screensaver either with the keyboard, onboard touchpad, usb-mouse or usb-keyboard. ](*,) 

Hibernate: I tried to changed my menu.lst to look like this:

root            (hd0,4)
#kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda5 ro quiet splash
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda5 **resume=/dev/hda7** ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

because My swap is located at /dev/hda7

cat /etc/fstab | grep swap | cut -c0-12
/dev/hda7

And now when the computer wakes up I get this. 
After the boot screen with the progressbar has finished loading the esential parts, I get a striped screen for a while and then the screen goes black. I cant get the computer to respond in any way.

Please help :) its the last thing to have a fully functioning ubuntu laptop :)

---

### Post by it.henrik on 2006-06-25
Update:

Hibernate now works, I had to change my xorg.conf to look like this 

Section "Device"
        Option          "NoLogo"                "1"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 440 Go]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
     **   Option          "NvAGP" "0"**
EndSection

this made suspend react in a bit different way while it prepared the computer for going to sleep. I did get some strange patterns on the screen before it went off. Still the laptop runs the screensaver when waking up again and I cant wake it up from the screensaver with any input device.

---

