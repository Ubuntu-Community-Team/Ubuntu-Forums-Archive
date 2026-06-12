---
title: "Mouse clicking not working - Question if IOMMU?"
date: 2014-07-20
forum: Hardware
---

### Post by Electronblue on 2014-07-20
Hey guys,

I am trying to use Ubuntu 14.04 via Live DVD on my new computer, which is an MSI Gp60 2PE notebook with an Intel Core i7 4710CPU (64 bit) and a Micro-Star International MS16GH Mainboard. The Live disc boots just fine via UEFI, but there seems to be a problem with the USB hubs. The touchpad works, but as soon as I plug in a mouse (I tried several), I cannot click on most things anymore (not even via touchpad). I can move around the pointer though and sometimes, after pressing CRTL+ALT+Shift to switch between open programs, it works for some seconds. Also, it usually works when I click on the Logout button.
I have already read several other threads on this and it seems that this problem exists not only on Ubuntu but also on other newer distros. I tried a Fedora live DVD as well - same problem.
From what I have found out so far, many people could solve this issue by enabling IOMMU in their BIOS/UEFI. However I cannot find any IOMMU entry on my mainboard. So, I wonder, does anybody know of a solution to this problem? I would love to run Ubuntu on this computer but not if I cannot use a mouse on it.

---

### Post by varunendra on 2014-07-20
Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
xinput
lsmod
cat /proc/bus/input/devices
```
..while the mouse is plugged in. If you have trouble selecting the text in the terminal to copy-paste it using the mouse/touchpad, you can redirect the outputs to a text file as follows -
```
cd Desktop
xinput > mouse.txt
lsmod >> mouse.txt
cat /proc/bus/input/devices >> mouse.txt
```
This will put all the outputs into a file named "mouse.txt" on your Desktop. You can then disconnect the mouse to get proper control, and copy-paste the contents from this file into your next post here.

---

