---
title: "USB Ports Not Working!"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by new2linux on 2005-10-01
Hi,

    I have a pentium III 450mhz with 128 mb. of ram.  I recently (2 days ago) installed the latest version of ubuntu (hoary 5.04), from a cd.  It has been great other than the fact that my usb ports aren't working at all.
   [SIZE="4"]I have a flash drive, and a usb keyboard.  Both of them worked perfectly with warty.  Now, neither of them work.[/SIZE]

Any help would be appreciated, I really love hoary, but if the usb ports won't work I may have to find something else.

EHD.

P.S. I started out with windows and just got into linux in the past year.  So  the easier the explanation the better.  (I do know how to open the terminal + synaptic, so I'm no completely clueless ;)  )

---

### Post by kleeman on 2005-10-01
Two useful commands at the terminal to find out what is going on are:

lsusb     

(this tells you whether any usb ports were detected)


dmesg | grep usb       

(this will tell you hopefully what went wrong as the system booted)

Post your output here and we will try to help.

---

### Post by new2linux on 2005-10-01
Thanks for the quick response!!

the lusb output is  " Bus 001 Device 001: ID 0000:0000"

the output for dmesg | grep usb is
> usbcore: registered new driver usbfs
usbcore: registered new driver hub
usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-1: khubd timed out on ep0in
usb 1-1: khubd timed out on ep0out
usb 1-1: khubd timed out on ep0out
usb 1-1: device not accepting address 2, error -110
usb 1-1: new full speed USB device using uhci_hcd and address 3
usb 1-1: khubd timed out on ep0in
usb 1-1: khubd timed out on ep0out
usb 1-1: khubd timed out on ep0out
usb 1-1: device not accepting address 3, error -110
usb 1-1: new full speed USB device using uhci_hcd and address 4
usb 1-1: khubd timed out on ep0in
usb 1-1: device descriptor read/64, error -110
usb 1-1: khubd timed out on ep0in
usb 1-1: khubd timed out on ep0out
usb 1-1: khubd timed out on ep0out
usb 1-1: device not accepting address 4, error -110
usb 1-1: new full speed USB device using uhci_hcd and address 5
usb 1-1: khubd timed out on ep0in
usb 1-1: khubd timed out on ep0out
usb 1-1: khubd timed out on ep0out
usb 1-1: device not accepting address 5, error -110


Any help you can give me will be greatly appreciated!!!

Thanks,

EHD

---

### Post by kleeman on 2005-10-01
I found this link which sounds useful
[http://www.linux-usb.org/FAQ.html#ts6](http://www.linux-usb.org/FAQ.html#ts6)
What I would suggest from this is passing one of the following to the kernel at bootup:
noapic
acpi=off
pci-noacpi
To do this issue
sudo gedit /boot/grub/menu.lst
page down and
Look for a line starting with
kernel		/boot/vmlinuz-2.6.10
there will be other stuff after this. Add one of the three things I suggested above AT THE END OF THIS LINE and then reboot. Good luck!
It sounds like this problems occurs fairly often so finding a solution may not be too hard.

---

### Post by new2linux on 2005-10-02
Thanks for the prompt response.

I tried everything that you said and it still isn't working.  I know that the usb hardware is working because 1. they were working 3 days ago and 2. when i plug in my usb stuff they always briefly flash to show that they are getting power.

Any more ideas?

Thanks for any and all help!!!!!!!!!!

---

### Post by kleeman on 2005-10-02
Here's a bugreport with a solution which looks like your problem:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=9454](https://bugzilla.ubuntu.com/show_bug.cgi?id=9454)

Looks like they added an extra option to the kernel boot to the ones I suggested above.

---

### Post by new2linux on 2005-10-02
It didn't work.

I looked at the boot-up screen and the only thing that I noticed that differed from the warty install, was that when the " initializing hotplug subsystem"  thing comes up, it used to say something like " error pciehp or something not working or disabled"  There were 2 of these messages.

If you want me to, I can post the contents of /boot/grub/menu.lst here.

Thanks for all your help.  Any more ideas?

Thanks!!!!!!!!!

---

### Post by kleeman on 2005-10-02
Yeah post it if you like.
Seems you have a few possibilities here:
1) Try a new kernel. Breezy is pretty close to release and not very buggy. Try  the latest livecd and see if that works. If it does try updating to breezy. You can do this by replacing all instances of hoary in /etc/apt/sources.list with breezy and then
doing
sudo apt-get update
sudo apt-get dist-upgrade
This assumes an internet link of course.
2) Looks like some have had success by updating the bios software. I've never done this so don't know the ins and outs. You want to be careful here because if you screw this up you can make your PC permanently unbootable.
3) Report your error messages to bugzilla and wait for the devs to respond. This might be a long wait.

---

