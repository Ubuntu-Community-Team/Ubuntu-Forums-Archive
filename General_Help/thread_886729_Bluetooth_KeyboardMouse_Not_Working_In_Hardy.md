---
title: "Bluetooth Keyboard/Mouse Not Working In Hardy"
date: 2008-08-11
forum: General Help
---

### Post by bc90021 on 2008-08-11
All,

I have installed Hardy from scratch on a Dell Vostro 200.  However, no matter what I do, I can't get the BT keyboard and mouse to work.  I have followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

Running "hcitool scan" or "sudo hidd --search" shows nothing.  However, if I go into Bluetooth preferences, I can see the keyboard and mouse as bonded devices.  However, I get no input from either one.  The same keyboard and mouse work fine with my Thinkpad laptop running XP.

Does anyone have any ideas?

Thanks.

Update:
Here is how I solved it:

You have to use "hidd --connect <bt addr>" to get it to recognise the devices, but only after you push the Bluetooth button underneath the device.

Steps:

sudo hidd --connect <keyboard bt addr>
[press bluetooth button on bottom of keyboard]
[enter pairing key - 1234 works fine]

The keyboard will then be paired.

sudo hidd --connect <mouse bt addr>
[press bluetooth button on bottom of mouse]

The mouse will then be paired.

There's no need to scan or anything - you can edit the files in the above thread with the addresses that are printed on the bottom of the devices.

---

