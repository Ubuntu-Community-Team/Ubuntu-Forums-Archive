---
title: "Problems after upgrade from 8.04 to 8.10"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by mreyeros on 2008-12-06
Good afternoon, hopefully someone will be able to assist me.  I just updated to 8.10 and am getting the following after the Ubuntu progress bar:
Starting up ...
[     0.004000] Aperture pointing to e820 RAM. Ignoring.
[     0.004000] Your BIOS doesn't have a aperture memory hole
[     0.004000] Please enable the IOMMU option in the BIOS Setup
[     0.004000] This costs you 64 MB of RAM
Laoding, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/2470238e-09bf-4a05-afa3-02b57c95c518) = dev(8,5)
kinit: trying to resume from dev/disk/by-uuid/2470238e-09bf-4a05-afa3-02b57c95c518
kinit: No resume image, doing normal boot...

Then I am taken to a login prompt where I am asked for username and password and taken to command prompt after successful authentication.  I cannot access the desktop though any help would be appreciated.  I did the upgrade through the update manager upgrade option, I did not install from a CD/DVD.

---

### Post by inobe on 2008-12-06
their are several things that will fix this problem.

in your system bios' set the aperture size to highest.


also you can check the manufacture site of your computer for the latest bios update.

try aperture first

edit: i also found this thread

[http://ubuntuforums.org/showthread.php?t=911768](http://ubuntuforums.org/showthread.php?t=911768)

---

### Post by mreyeros on 2008-12-06
the aperture setting is not an option in my bios setup screens.  I saw another post in the forums that discussed a problem with having 2 video cards installed on the system.  I have two pci-e cards installed on my system.

---

### Post by inobe on 2008-12-06
it's sli isn't it ?


it has to be a buggy video driver

lets try to get you to a desktop so that someone or i can help you install the drivers.

if you are in root shell, type this command and follow the on screen directions, it should get you to see your desktop.

```
dpkg-reconfigure xserver-xorg
```

or as a normal user

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mreyeros on 2008-12-06
ok just ran command and followed prompts and am back at the command prompt...

EDIT:  Just to add i was reviewing my menu.lst file and the UUID that the kernel is referring to is not the same one that is being displayed on the error as posted above.  Not sure if this means anything but thought I would add piece of info as well.

---

### Post by inobe on 2008-12-06
here are many things that involved your error

[http://www.google.com/search?q=Please+enable+the+IOMMU+option+in+the+BIOS+Setup&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=Please+enable+the+IOMMU+option+in+the+BIOS+Setup&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

some were a success after bios update

---

### Post by mreyeros on 2008-12-09
Good afternoon everyone hope this post helps some of you out with this issue.  After doing a complete clean install I was able to access the desktop.  At the moment I installed the proprietary nvidia drivers I was faced with the same issue on reboot.  Therefore I was able to pinpoint that this has to be caused by a graphics issue.  There are several posts in the forum that discussed adding a BusId value to the xorg.conf file for the video card device section if you have more than one video card installed on the system.  It just so happens that I have two.  After obtaining the BusId value for my video card, you can get this by entering lspci command at the prompt, and adding this value to my xorg.conf file and performing a reboot, voila! a desktop.  It seems that 8.10 has an issue recognizing multiple video cards and does not know which one to use.  I did not have this problem on 8.04 version but all is good now.

---

