---
title: "How to show usb drive in Virtualbox ?"
date: 2015-05-14
forum: Hardware
---

### Post by mike311 on 2015-05-14
Im running Unbuntu from a portable hardrive ,and i would like to run Virtualbox on the same drive.I need run my new operating system from a usb pen drive which is a iso file . For some reason its not giving me the option to run from it, the usb doesnt get recognized.I only see the cd drive.Im not sure if its because i have 2 usb ports plugged in. Appreciate any help on this topic. Thanks.mike311

---

### Post by dino99 on 2015-05-14
at the bottom righ corner virtualbox have an icon about activating usb (if im not mistaking)

---

### Post by mike311 on 2015-05-14
Hi Dino.I can`t see anything in the bottom right corner. In the usb box the two usb controllers are ticked.

---

### Post by SeijiSensei on 2015-05-14
Did you install the [Extension Pack](https://www.virtualbox.org/wiki/Downloads)?  You'll need that for USB connectivity.

---

### Post by mike311 on 2015-05-14
Hi Seijisensei,i did install the extension pack using the software center , still having the problem with the usb stick i checked for the extension pack in software update, but i couldn`t see it listed so i managed to download it from google , used wine to install it , rebooted the pc but it did not solve my problem .Cheers

---

### Post by SeijiSensei on 2015-05-14
You need to install the Extension Pack in the guest.  Use RightCtrl-Home in VB session to bring up the VB minimenu, choose Devices, then "Insert the Guest Additions CD."  How this appears to the guest operating system depends on what it is, but it will be attached to the virtual CD drive.  If you have not created one, you'll need to run Settings on the VM when the machine is turned off.  Once you've navigated to the directory where the CD is mounted, run the command
```
sudo ./VBoxLinuxAdditions.run
```
Installing the additions in wine will not help; you need to install them at the OS level.

Have you read: [https://www.virtualbox.org/manual/ch04.html?](https://www.virtualbox.org/manual/ch04.html?)

I don't know what you mean about "downloading from Google."  The extension pack is here: [http://download.virtualbox.org/virtualbox/4.3.28/Oracle_VM_VirtualBox_Extension_Pack-4.3.28-100309.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.28/Oracle_VM_VirtualBox_Extension_Pack-4.3.28-100309.vbox-extpack)

---

### Post by mike311 on 2015-05-14
Thanks [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") .II will read up on it right now, looks like i have a challenge ahead .Cheers bud

---

### Post by leunam12 on 2015-05-14
Close VirtualBox.
Open Terminal.
Type:```
sudo adduser YOURUSERNAME vboxusers
```Press Enter
Reboot
Attach USB Devices.
Open VBox, select your virtual Machine, go to settings
Enable USB, add filters (pick your USB device)
Start your virtual machine.

---

### Post by mike311 on 2015-05-19
[**[COLOR=#000000]Thanks leunam12[/COLOR]**]("http://ubuntuforums.org/member.php?u=1449887"). i did try your method ,but still no joy.It seems the username vboxusers are already setup to my username.But even though i have a filter showing , it does not show up my usb .Im finding virtualbox very slow to use , i may have to give it up as my pcs only a 1.8 twin core

ps i do have a couple of fatal errors when i boot ubuntu , this cant help it

---

