---
title: "How can I update the driver for my Sapphire Nitro 4Gb R9 380x GPU?"
date: 2015-12-24
forum: Hardware
---

### Post by josh159 on 2015-12-24
I just built my first computer from scratch and updating drivers on Ubuntu is not as simple as Windows. I've installed Wine in an attempt to run the [.exe off the product website]([http://www.sapphiretech.com/productdetial.asp?os=Linux_64&Pid=B520A2A6-4D37-4499-9584-B6BE8823AAC0&tag=download&lang=eng](http://www.sapphiretech.com/productdetial.asp?os=Linux_64&Pid=B520A2A6-4D37-4499-9584-B6BE8823AAC0&tag=download&lang=eng)) to update the driver for the GPU but it couldn't recognize the OS. 

I ran the terminal command " sudo lshw -c display " and it returned incorrect information: " 
       description: VGA compatible controller
       product: Amethyst XT [Radeon R9 M295X Mac Edition] "

I also need to update the GPU in order to get audio from the HDMI. 

How can I manually update the driver?

---

### Post by matt_symes on 2015-12-24
Hi

> **josh159 said:**
> I just built my first computer from scratch and updating drivers on Ubuntu is not as simple as Windows.

It is usually easy. It is different than using windows though. 

Don't confuse unfamiliarity for difficulty. That being said, it is occasionally a pain. 

> I've installed Wine in an attempt to run the [.exe off the product website]([http://www.sapphiretech.com/productdetial.asp?os=Linux_64&Pid=B520A2A6-4D37-4499-9584-B6BE8823AAC0&tag=download&lang=eng](http://www.sapphiretech.com/productdetial.asp?os=Linux_64&Pid=B520A2A6-4D37-4499-9584-B6BE8823AAC0&tag=download&lang=eng)) to update the driver for the GPU but it couldn't recognize the OS.


You don't use Wine to install drivers. That is not Wines purpose. Wine is an emulation layer for user space programs. Drivers work in kernel space (just like in Windows) and not in user space.

> I ran the terminal command " sudo lshw -c display " and it returned incorrect information: " 
       description: VGA compatible controller
       product: Amethyst XT [Radeon R9 M295X Mac Edition] "


What did you expect it to return ? Please itemise the hardware of your build.

What version of Ubuntu did you install ?

> I also need to update the GPU in order to get audio from the HDMI. 

How can I manually update the driver?

You need to supply more information before any useful help can be given.

Kind regards

---

### Post by Yellow Pasque on 2015-12-25
> **josh159 said:**
> I ran the terminal command " sudo lshw -c display " and it returned incorrect information: " 
It's a matter of semantics (the human-readable device name is unimportant to the driver as it looks at the numeric PCI ID). The R9 380X and M295X Mac Edition apparently share the same ID: [http://pci-ids.ucw.cz/read/PC/1002/6938](http://pci-ids.ucw.cz/read/PC/1002/6938)
Someone has updated the name to include "R9 380X", so if you want to update the PCI and USB names, you can run (with internet connection):
```
sudo update-pciids
sudo update-usbids
```

> updating drivers on Ubuntu is not as simple as Windows
Normally, it's very easy to install Catalyst on Ubuntu (you can either type one command or use Ubuntu's custom driver GUI if you're allergic to the command line).
The reason you're struggling is because AMD has completely reorganized their driver structure for newer GPU's ( [http://www.phoronix.com/scan.php?page=search&q=AMDGPU](http://www.phoronix.com/scan.php?page=search&q=AMDGPU) ) and it has led to some delays in the driver supporting newer components (kernel,X,gcc) found in newer distros. Ubuntu also deserves some blame for letting an important fix languish in the proposed repo where n00bs can't find it. The good news is that  this should be resolved in Ubuntu 16.04
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1510573](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1510573)

Long story short: Assuming you're running Ubuntu 15.10, enable the proposed repo: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)
Then run:
```
sudo apt-get update
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

EDIT: You'll probably want to disable the proposed repo after you install the driver.


> .exe off the product website
You've got to break yourself of that habit quickly. Downloading non-packaged executables off the manufacturer's website is usually a recipe for heartache, especially when it comes to video and sound drivers. Learn to use packages made for your distro where possible.

---

