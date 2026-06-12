---
title: "Mouse not working after re-install"
date: 2013-07-30
forum: Hardware
---

### Post by aspz on 2013-07-30
I had some problems with my graphics driver recently so I decided to try to fix it by re-installing Ubuntu 13.04 over the top of itself. This is in fact the second time I have done this due to graphics driver problems. The first re-install worked fine. This time however, after the installation was finished, the mouse no longer works at all. I can see the cursor but moving the mouse or clicking does nothing.

Here is the output from dmesg after unplugging and re-plugging the mouse into a different USB socket. Everything looks fine but I still get no mouse movement:
> 
[  569.215231] usb 2-1.5: USB disconnect, device number 4
[  572.481884] usb 2-1.2: new low-speed USB device number 5 using ehci-pci
[  572.578829] usb 2-1.2: New USB device found, idVendor=046d, idProduct=c069
[  572.578833] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  572.578836] usb 2-1.2: Product: USB Laser Mouse
[  572.578839] usb 2-1.2: Manufacturer: Logitech


The mouse works fine when I boot into Windows on the same machine and it worked fine on the previous ubuntu 13.04 installation as well as during the installation process.

I've pasted my full dmesg, Xorg.0.log and syslog files here (file attachment is not working at the moment for some reason): [https://gist.github.com/anonymous/be8f68fc38e1766f147d](https://gist.github.com/anonymous/be8f68fc38e1766f147d)
The syslog shows goes back about 3 days to when I first installed the system. 

Can anyone give me any clues as to where I can find out what the problem is?

---

### Post by angryfirelord on 2013-07-31
Do you know what motherboard you have?

---

### Post by aspz on 2013-08-01
The motherboard is a Asus P8P67-M PRO.

---

### Post by angryfirelord on 2013-08-04
Do you know if you're booting with UEFI or legacy mode?

---

### Post by aspz on 2013-08-05
That is an interesting point. I'm not sure whether my system fully supports UEFI boot. I ended up doing a clean reinstall which eventually worked but I did have an issue with UEFI. When I want to boot from a USB stick, I have to go into the BIOS and select the USB disk as the boot device. In the bios I get two options, UEFI and non UEFI. I didn't really understand the difference between these two but in all the recent installation attempts I have selected the UEFI boot option. I think what happened was this:


[LIST]
[*](Several months ago) I do a clean install 13.04 booting the USB with non-UEFI mode.
[*]Graphics card driver goes screwy forcing me to reinstall
[*]Reinstall Ubuntu using UEFI boot-mode.
[*]Installation is ostensibly successful but the mouse fails to work at login
[*]Attempt re-installation with UEFI boot-mode with the same result
[*]Attempt clean installation with UEFI boot-mode. Grub does not even load (with an error about a missing .mod file)
[*]Attempt another clean installation with non-UEFI boot-mode and everything works perfectly
[/LIST]

So I think there is a problem with UEFI on my system. Maybe there is something I can do to get it work but for now I am happy to have my mouse working again!

---

