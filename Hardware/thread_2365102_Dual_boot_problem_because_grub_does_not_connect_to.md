---
title: "Dual boot problem because grub does not connect to Bluetooth keyboard"
date: 2017-07-02
forum: Hardware
---

### Post by makem2 on 2017-07-02
I have a dual booted system which defaults to Xubuntu, meaning that if I need Windows 10 for the one reason I use it (Internet Explorer), I can never select Windows using my BT keyboard from grub.

Xubuntu and Windows 10 are both happy connecting automatically with the keyboard after logging in to the OS. In the case of Windows, I can use the on screen keyboard to log in but grub does not see any screen input so that is out too.

I know screen touch can be enabled in Xubuntu but presume the same problem occurs with grub - cannot work.

Am I right in thinking that as things stand there is no way to use a tablet which is dual booted with a BT keyboard or for that matter even if not dual booted?

The 'tablet' I am using is a Teclast X2 Pro which has it's own detachable keyboard that is cumbersome and not suitable for my purposes. (The machine was a gift rather than a purchase)

---

### Post by QIII on 2017-07-02
Unlike USB connectivity, BT can be a pain during that mysterious ethereal world between POST and OS startup.

To rule out other problems, would you please use the cumbersome keyboard to confirm that you are able to select your desired OS at the GRUB screen by that means?

Thanks.

---

### Post by makem2 on 2017-07-02
Yes, the cumbersome keyboard works perfectly, giving the choice of OS. The BT keyboard also works whilst the cumbersome keyboard is attached. eg. I can type part of a word with BT and the remainder with the default keyboard.

---

### Post by efflandt on 2017-07-04
One option might be a Logitech keyboard that uses their tiny USB Unifying receiver that can work with a mouse as well. That should work without any OS running. There is a package called solaar that can associate Logitech devices with the Unifying receiver.

If looking for something relatively small they have K400 keyboard/mousepad without numeric keypad or different K360 model with numeric keypad, and no mousepad.

[http://www.logitech.com/en-us/product/wireless-touch-keyboard-k400-plus?crid=27](http://www.logitech.com/en-us/product/wireless-touch-keyboard-k400-plus?crid=27)
[http://www.logitech.com/en-us/product/keyboard-k360?crid=27](http://www.logitech.com/en-us/product/keyboard-k360?crid=27)

---

### Post by makem2 on 2017-07-04
Thank you. I will bear that in mind but I do have two new small Bluetooth keyboards which are redundant.

---

### Post by makem2 on 2017-07-05
> **efflandt said:**
> One option might be a Logitech keyboard that uses their tiny USB Unifying receiver that can work with a mouse as well. That should work without any OS running. There is a package called solaar that can associate Logitech devices with the Unifying receiver.

If looking for something relatively small they have K400 keyboard/mousepad without numeric keypad or different K360 model with numeric keypad, and no mousepad.

[http://www.logitech.com/en-us/product/wireless-touch-keyboard-k400-plus?crid=27](http://www.logitech.com/en-us/product/wireless-touch-keyboard-k400-plus?crid=27)
[http://www.logitech.com/en-us/product/keyboard-k360?crid=27](http://www.logitech.com/en-us/product/keyboard-k360?crid=27)

I have done  some research and it appears this unit needs drivers and 'pairing' so it may use wifi in a similar way to Bluetooth pairing. In that case (and there have been problems with the software), the OS needs to be running for the drivers to start.

I have asked a question at Logitech tech but expect the answer to the question, "Will the device work before an OS is started?" to be,"no".

---

### Post by efflandt on 2017-07-06
Keyboard and mouse HID devices that use Logitech USB wireless dongles do not need drivers to work in BIOS or UEFI or grub menus, as long as they have been previously associated with each other. The dongle included with a keyboard or mouse should work with that device out of the box. In an earlier Ubuntu version, my Logitech Dinovo Edge keyboard (which uses a different type of Logitech wireless dongle or alternately can connect to Bluetooth) worked for BIOS and grub, but stopped working when I got to Ubuntu because somebody had changed something in udev of that Ubuntu version, and I had to use a wired keyboard to change something in udev to re-enable it. I think that was fixed in more recent Ubuntu. I misplaced its dongle and have not tried booting it using Bluetooth, although it works within Ubuntu using Bluetooth.

Note that function keys are reversed (blue) like some laptops, so you need to use blue FN+F# keys on K400. But I booted an HP Win10 laptop using wireless Logitech K400 keyboard with its Unifying receiver, the hotkey (Esc) worked on K400 to get into UEFI, FN+F9 to get into UEFI boot menu, I was able to boot into Ubuntu 16.04, and K400 keyboard and mousepad work in Ubuntu.

I also tested same unifying receiver in an old Dell laptop from 2007. FN+F2 on K400 I got into BIOS, was able to navigate BIOS just fine with the K400, and it worked as well in 16.04 on that laptop.

So basically if a wired keyboard works, a Logitech wireless keyboard using Unifying or other included receiver should work for normal keyboard functions, without any OS drivers.

Things might be a little different with a tablet PC that includes a detachable keyboard. I have an Acer W500P that came with Win7 Pro on 32 GB SSD (1 GHz 2-core AMD C-50 w/2 GB RAM, AMD HD 6250 graphics) and I boot Ubuntu from grub on SD card (internally USB connected). If I boot normally with its own keyboard detached and using Unifying receiver, a very brief BIOS splash does not display hot keys for BIOS or boot device selection and it goes right to Win7. But if I hold Windows button on the tablet while powering on, it automatically boots either SD, or external USB has highest priority. So that boots to grub on the SD card and from that I can select Ubuntu with the K400, and Ubuntu works. If I have external bootable USB storage attached, that would take priority, so it can either reinstall Windows from external DVD drive, or install Linux to SD card from USB memory stick. It currently has 64-bit Ubuntu and Lubuntu 12.04 on separate partitions of 32 GB SD with common /home partition (no swap). I did install 16.04 to another SD card using a different computer, but have not tried that in the tablet PC yet. It is very slow, but I used to use it for field programming electronic controllers with Windows software in awkward locations (underground valve vaults) without having to worry about crashing a hard drive.

PS: I also have an even smaller Gear Head "Windows Smart Touch Keyboard" (with mousepad) KB3800TPW with its own wireless dongle that works fine in old BIOS or newer UEFI before any operating system is started, and works fine in Linux. Its only shortcoming is that due to it's small size it has no Shift, Ctrl, or Alt keys on its right side.

---

### Post by oldfred on 2017-07-06
I do not have bluetooth, but saved a couple of older threads.
 Sharing bluetooth mouse between Windows and Ubuntu 
[http://ubuntuforums.org/showthread.php?t=1479056](http://ubuntuforums.org/showthread.php?t=1479056)
[http://ubuntuforums.org/showthread.php?t=764756](http://ubuntuforums.org/showthread.php?t=764756)
[http://askubuntu.com/questions/240577/ubuntu-12-10-and-windows-8-dual-boot-bluetooth-pairing](http://askubuntu.com/questions/240577/ubuntu-12-10-and-windows-8-dual-boot-bluetooth-pairing)
[http://askubuntu.com/questions/669012/bluetooth-pairing-on-dual-boot-of-windows-linux-mint-ubuntu-stop-having-to-p](http://askubuntu.com/questions/669012/bluetooth-pairing-on-dual-boot-of-windows-linux-mint-ubuntu-stop-having-to-p)
[https://wiki.archlinux.org/index.php/bluetooth](https://wiki.archlinux.org/index.php/bluetooth)
[http://askubuntu.com/questions/838697/share-files-between-2-computers-via-bluetooth-from-terminal](http://askubuntu.com/questions/838697/share-files-between-2-computers-via-bluetooth-from-terminal)

---

### Post by makem2 on 2017-07-07
Thank you for taking the time to present that information.

I gather that I need to purchase a WiFi enabled keyboard and mouse which use the unifying properties to choose which OS to boot whilst presented with the grub choices.

It is a pity I can't use the existing Bluetooth key boards to achieve the same result. For me it only meant moving the cursor down one line. I cannot justify at present purchasing more equipment solely for that reason.

Instead I have installed Xubuntu solely on the machine and will use a Virtualbox install of Windows 10 for the odd occasion when I need Internet Explorer.

I believe there is a way to dual boot in such a manner that the OS is chosen before grub, but I don't really need to dual boot on this machine. I have others with that facility but no 'unifying'.

---

