---
title: "VirtualBox can't load USB, any guides for 8.10?"
date: 2008-11-12
forum: General Help
---

### Post by ajwak95 on 2008-11-12
I've looked at all of the guides for USB support in VirtaulBox, but none of them work on 8.10, yet. So are there any good tutorials out there yet?

---

### Post by john183 on 2008-11-12
If you install VirtualBox from the repositories then you installed the OSE (Open Source Edition) which does not have support for USB devices. You can download the non-OSE version from the Virtual Box website, then search for the thread that explains the necessary steps to enable USB support for it here in the forums.

---

### Post by ajwak95 on 2008-11-12
> **john183 said:**
> If you install VirtualBox from the repositories then you installed the OSE (Open Source Edition) which does not have support for USB devices. You can download the non-OSE version from the Virtual Box website, then search for the thread that explains the necessary steps to enable USB support for it here in the forums.
Thanks for that quick response john183, I will be sure to try that, but, could you possibly provide some links to the USB enable, here on the forums? Thanks!

---

### Post by binbash on 2008-11-12
you gonna install : 

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

There are ubuntu repos there also

---

### Post by ajwak95 on 2008-11-12
> **binbash said:**
> you gonna install : 

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

There are ubuntu repos there also
Thanks, but I am installing VirtualBox from there now, I just need the links on how to get USB to work on it, e.g. my WebCam. And also, where do I go to access it?

---

### Post by ajwak95 on 2008-11-12
Okay, all is installed, I have USB enabled, just cant find any of the USB hubs.

---

### Post by ajwak95 on 2008-11-12
USB now works, but I can't access them on my VB?

---

### Post by binbash on 2008-11-12
I dont have virtualbox installed now but at preferences there is a setting with port(you will see port numbers etc) etc.You should enable it to get access

---

### Post by john183 on 2008-11-12
look in the menus i don't remember exactly where it is, but there sould be an option to connect to removable devices, select the ones you want to connect to and they should work. cannot guarantee that the camera will connect this way, but usb drives should. also the usb devices can only be connected to one machine at a time i.e you can either access it from the VB machine or the host, but not both at the same time.

---

### Post by howefield on 2008-11-12
Since enabling USB, you have rebooted ? 

Load up virtualbox and press settings button, then click on USB, enable the controllers and add the usb device using the buttons on the right hand side.

---

### Post by ajwak95 on 2008-11-12
Well, I don't know how to un-use it from 8.10, because I can't unmount a USB drive. I get a checklist, but am unable to click on the drive that I want.

---

### Post by Therion on 2008-11-12
If you simply can't get USB working in your Virtual Box VM (I never could get it working personally, no matter what I tried) you might want to look into using VMWare Workstation instead.  It's what I'm using now instead of Virtual Box.  

VMWare gives me easy USB aaand DirectX support... w00t!

---

### Post by ajwak95 on 2008-11-12
eh...Not a big advocate of VMware, not going to explain why, but I want to keep VBox. Again, I can see a list of the devices in the right hand corner, I just cannot select them.

---

### Post by ju2wheels on 2008-11-12
1. Install Virtualbox from their website
Intrepid 32 bit:
```

wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_i386.deb
sudo dpkg -i virtualbox*

```
Intrepid 64 bit:
```

wget http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb
sudo dpkg -i virtualbox*

```

2. Add your user to the vboxusers group [Applications->Accessories->Terminal]:
```

sudo adduser your_user_name vboxusers

``` 

3. Add the following line to /etc/fstab: none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 as follows:

```

gksudo gedit /etc/fstab

```

and add to the end of the file:

```

#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

Save the file and reboot.

Create a Virtual Machine in virtual box, make sure to enable the USB/USB 2.0 controller on the USB for the VM before starting it.

Once started, plug in your usb device. If it is a usb drive, make sure it does not get automounted by your host OS. If it does unmount it.

In your VM window, click Devices and under USB, select your device (there may be more than one option even you only have one device plugged in as one may be virtual and you dont want to use that one).

Your device should then show up in your VM. To release the device back to the host properly, be sure to unmount the device in the VM before unchecking it on the Device menu. You should do this before shutting off your VM as well to avoid complications.

---

### Post by ajwak95 on 2008-11-15
Thanks for al the replies, but I got it working! I just edited the fstab, so now it works. Thanks for all suggestions, but I figured out this one on my own.

---

