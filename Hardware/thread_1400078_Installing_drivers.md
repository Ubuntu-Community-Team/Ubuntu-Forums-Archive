---
title: "Installing drivers"
date: 2010-02-06
forum: Hardware
---

### Post by Mensch on 2010-02-06
I just installed ubuntu-9.10-desktop-i386 on a formatted HD that I am running through an USB port (using a SATA to USB cable). The problem is: I am a noob and don't know how to install the drivers. 

The first thing I wanted to take care of was my wireless card -- I have an Intel wifi 5100 AGN. I downloaded the microcode image from [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads) and unzipped the files to flash drive.

When I boot up ubuntu I don't know how to proceed. The text file which was included with the driver tells me that a iwlagn driver will look for the iwlwifi-5000-2.ucode file using the kernel's firmware_loader infrastructure. In order for this to work I must have it supported in my kernel. And it says I can find that option under  Device Drivers ->Generic Driver Options ->   Hotplug firmware loading support. (I am unable to find any Device Drivers directory).
                     

It also says: "You can determine if your kernel currently has firmware loader support 
by looking for the CONFIG_FW_LOADER definition on your kernel's 
.config." 

Where do I find this kernel config?

I am completely lost! Can someone help me? 

Thanks in advance.

---

### Post by IcarusR on 2010-02-06
You could try following this...

[http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html]("http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html")

Will need to install build-essential (compiler etc) package first...

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

---

### Post by Mensch on 2010-02-07
Thanks for your reply. 

I tried what you suggested but to no avail. I unpacked the files cd'd to the directory and typed in the commands (sudo make install I think). Then it was doing something in the terminal for several minutes, but nothing really changed. When I typed the command "lshw -C network", it still said UNCLAIMED (or something). Then I read in the help file that comes with ubuntu that I needed something called ndisgtk so I downloaded that, but to install it I needed something else (again...) called ndiswrapper for this to work. So I got that one extracted it, built it but nothing really happened. When I tried to use the ndiswrapper commands the terminal said something like: ndiswrapper not installed. To install package type sudo apt-get install ndiswrapper-common. Did that but then it complained package not found.

Isn't there a standard procedure to installing drivers in ubuntu? If not does anyone else have any suggestions? Getting a bit frustrated now.

Thanks!

---

