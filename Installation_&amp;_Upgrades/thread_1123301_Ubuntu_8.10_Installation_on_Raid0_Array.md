---
title: "Ubuntu 8.10 Installation on Raid0 Array"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by fast-Eddie on 2009-04-12
Hi All,

I'm trying to install Ubuntu 8.10 on my PC with no luck. Ubuntu will be the only O/S as I am not dual booting with any other O/S. 

My PC has 4 HDD's; 2 of which are in a Raid0 array which is where I want to install Ubuntu.

I've booted from a Live CD and followed the 'FakeRaidHowto' at <https://help.ubuntu.com/community/FakeRaidHowto> with some luck. The raid array is detected and I can install Ubuntu to it without any problems. Once the installation completes however and I restart my PC, it gets to the point where it should load Grub and just stalls; nothing happens. I've also tried re-installing it without grub and get the same problem - it stalls at the point where Grub is usually loaded. If I split the Raid0 array into individual hard drives and try an installation to one of them, I still get the same problem. Prior to a re-installation (again), I checked the settings in the 'Advanced' tab right before the O/S installation begins and that is the section where it asks me if I want to install a bootloader. By default, it is selected and the location is 'hd0'. I tried changing the location /dev/sda and ran through with the installation and rebooted my system. This time, it actually worked and Ubuntu loaded on the system as normal!! 

Right now I'm up and running without Raid0. Is anyone able to provide an explanation as to why the installer behaves like this?? What is hd0?? If I try to put the bootloader on the raid array during installation, it won't let me and the 'OK' button is greyed out. As mentioned above though, if I put the bootloader on /dev/sda it works fine. I eventually want to try to re-install onto the Raid0 array and would just like to understand the installation a little more.

Thanks

---

### Post by inobe on 2009-04-12
get the alternative cd here [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

it has the tools needed for raid, the live cd doesn't.

---

### Post by fast-Eddie on 2009-04-15
I reconfigured the Raid0 array and downloaded the Alternate CD as advised and ran it to perform the installation which went well. After rebooting though, it gets to the screen where it says 'Ubuntu' in the middle with the progress bar beneath it and loads. When the progress bar gets full, the screen goes black and nothing happens. It never prompts me with a login window as it should. 

Any suggestions??

---

