---
title: "How to use bumblebee to disable the NVIDIA graphic card"
date: 2012-01-25
forum: Hardware
---

### Post by datangtujue on 2012-01-25
Hello experts,

I installed Ubuntu10.04LTS on my Lenovo Ideapad Y470 laptop which has one integrated video card and one NVIDIA Geforce GT 550M video card. I am very new to Linux, but I read some posts which suggest using bumblebee to disable the NVIDIA card and using optirun to use the NVIDIA card when necessary. So I installed both the latest version of bumblebee and the NVIDIA driver for the Geforce GT 550M card. 

Modify /etc/default/grub and type GRUB_CMDLINE_LINUX="nomodeset" in it.
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee
sudo apt-get install bumblebee-nvidia
sudo usermod -a -G bumblebee MyLoginName

After rebooting the computer, I ran these

sudo stop gdm
sudo service gdm stop
sudo sh NVIDIA-driver-filename.run

However, I was informed that Ubuntu was running in low video quality when it was rebooted. An error message showed that the screen was not detected. And when I checked the video cards with lspci, I found the NVIDIA card was not disabled.

I typed
lspci |grep -i vga

Then the line for NVIDIA ended with rev a1 rather than rev ff (which means it is disabled).

I just tried running optirun glxgears to see what happen.
The error message is like this:
[Error] Cannot access secondary GPU - error: [XORG] (EE) Jan-24-2012 ... Nvidia(0) 
Failed to initialize the Nvidia GPU at PCI:1:0:0. Please
[Error] Aborting because fallback start is disabled

Could anyone tell me what I should do? It seems both the bumblebee and the NVIDIA driver are installed successfully. But neither of them is working.

Thank you!

---

### Post by Starks on 2012-01-25
The Y470 and Y570 are not supported since Lenovo has s*** BIOS.

[https://github.com/Bumblebee-Project/bbswitch/issues/2](https://github.com/Bumblebee-Project/bbswitch/issues/2)
[https://raw.github.com/Bumblebee-Project/Bumblebee/master/doc/RELEASE_NOTES_3_0]("https://raw.github.com/Bumblebee-Project/Bumblebee/master/doc/RELEASE_NOTES_3_0")

The issue is specific to those laptops. Every other Optimus laptop out there works fine with Bumblebee.

---

### Post by datangtujue on 2012-02-04
It seems someone offers a hack solution for the Lenovo Y470 Y570 models. I wonder if any Y470 owner has tried this solution?

[http://linux-hybrid-graphics.blogspot.com/search?updated-min=2012-01-01T00:00:00-08:00&updated-max=2013-01-01T00:00:00-08:00&max-results=9](http://linux-hybrid-graphics.blogspot.com/search?updated-min=2012-01-01T00:00:00-08:00&updated-max=2013-01-01T00:00:00-08:00&max-results=9)

[http://github.com/Bumblebee-Project/bbs ... ack-lenovo]("http://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo")

Good  news for all owners of the Lenovo IdeaPad Y470 and Lenovo IdeaPad Y570  laptops, there is now an ugly but working solution to a detection issue  in the kernel
([https://bugzilla.kernel.org/show_bug.cgi?id=42696](https://bugzilla.kernel.org/show_bug.cgi?id=42696))

Until  a correct fix is committed for the kernel, you can use this temporary  solution for overwriting the wrongly detected ACPI handle. More  information on that is available in:
[http://github.com/Bumblebee-Project/bbs ... nt-3797568]("http://github.com/Bumblebee-Project/bbswitch/issues/2#issuecomment-3797568")





> **Starks said:**
> The Y470 and Y570 are not supported since Lenovo has s*** BIOS.

[https://github.com/Bumblebee-Project/bbswitch/issues/2](https://github.com/Bumblebee-Project/bbswitch/issues/2)
[https://raw.github.com/Bumblebee-Project/Bumblebee/master/doc/RELEASE_NOTES_3_0](https://raw.github.com/Bumblebee-Project/Bumblebee/master/doc/RELEASE_NOTES_3_0)

The issue is specific to those laptops. Every other Optimus laptop out there works fine with Bumblebee.

---

### Post by fabio.hipolito on 2012-05-14
Hy there,


> **datangtujue said:**
> It seems someone offers a hack solution for the Lenovo Y470 Y570 models. I wonder if any Y470 owner has tried this solution?

[http://linux-hybrid-graphics.blogspot.com/search?updated-min=2012-01-01T00:00:00-08:00&updated-max=2013-01-01T00:00:00-08:00&max-results=9](http://linux-hybrid-graphics.blogspot.com/search?updated-min=2012-01-01T00:00:00-08:00&updated-max=2013-01-01T00:00:00-08:00&max-results=9)

[http://github.com/Bumblebee-Project/bbs ... ack-lenovo]("http://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo")

Good  news for all owners of the Lenovo IdeaPad Y470 and Lenovo IdeaPad Y570  laptops, there is now an ugly but working solution to a detection issue  in the kernel
([https://bugzilla.kernel.org/show_bug.cgi?id=42696](https://bugzilla.kernel.org/show_bug.cgi?id=42696))

Until  a correct fix is committed for the kernel, you can use this temporary  solution for overwriting the wrongly detected ACPI handle. More  information on that is available in:
[http://github.com/Bumblebee-Project/bbs ... nt-3797568]("http://github.com/Bumblebee-Project/bbswitch/issues/2#issuecomment-3797568")

yes, I am using and it works properly.

Cheers.

---

