---
title: "usb-to-parallel cable unable to enumerate"
date: 2009-09-17
forum: Hardware
---

### Post by reikod on 2009-09-17
Hi, I'm having a bit of a problem here. I bought a USB-PARALLEL cable to set up a HP 1100 printer. I've installed UBUNTU SERVER 9.04 and when I plugged  in my cable the dmesg command comes up wtth:

[ 107.142522] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 107.322521] usb 4-2: device descriptor read/64, error -71
[ 107.620026] usb 4-2: device descriptor read/64, error -71
[ 107.850023] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 108.390012] usb 4-2: device not accepting address 3, error -71
[ 108.510017] usb 4-2: new full speed USB device using uhci_hcd and address 4
[ 108.546083] usb 4-2: device descriptor read/all, error -71
[ 108.660022] usb 4-2: new full speed USB device using uhci_hcd and address 5
[ 109.080013] usb 4-2: device not accepting address 5, error -71
[ 109.080030] hub 4-0:1.0: unable to enumerate USB device on port 2

on every USB port. Anyways, I checked my lsmod and found out that usblp was not loaded, so I changed my /etc/modules, rebooted and still the same message. Then I go to check the cable on another server that I have running with 8.04 (hardy-heron) and it worked perfectly. Sets up the device as /dev/usb/lp0 and I can print fine. I guess this is a jaunty problem, but I'm really frustrated because I've been at this for almost 3 days and can't get it to work. 

PLEASE HELP!

---

### Post by reikod on 2009-09-17
Hi, I was looking at the dmesg and noticed that I have usbcore running on my ubuntu 8.04 but not on my 9.04. On that one I don't have usbcore even at the modprobe, even though ehen i try "sudo apt-get install usbcore" it says already installed. Anyways in that system I do have running usbhid and usblp. 
I don't know if this helps, but that's the only difference I could find doing "lsmod | grep usb" on both systems. 

Anything you can do to help is highly appreciated.

---

### Post by Rasheeke on 2009-09-22
I'm also having this issue.  Long story short, needed HPIP download to install printer two days ago.  Unplugged printer, plugged it in today and wasn't detected, tried the HPIP download again, won't detect printer.  Now when restarting the computer has some 'enumerate' issue with the USB and wouldn't start until I unplugged the computer.  Nothing has changed since two days ago except unplugging computer and maybe a few updates.  

Long Story:

First, after being unplugged for 4 months my printer wouldn't not be detected by Ubuntu even though it worked for 4 months before that flawlessly(relatively).  

I go to plug it in, it doesn't work, I search the inernets to find this - [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) - which had a download (HPIP) from hp that I ran and it install my printer which then would run just fine.  

I unplugged it because it was in the way, go to plug it in again and it doesn't work. 

I try the hp download again, this time it's not working and the printer won't even be detected.  Upon restarting I got this enumerate message which wouldn't allow my computer to turn on again until I turned off or unplugged the printer.  

Now it's not being detected at all.  This is bogus.

---

### Post by Rasheeke on 2009-09-22
Update-ish...  I got fed up and tried a new usb port and it worked!  But the paper wasn't lined up properly so it thought it was out of paper and I didn't know how to tell it "yes there is" after I fixed it.

So I did was usually works which was turn it off and back on.  Then I was back to square one.  I tried it again with three different USB ports and now it's not working.

Interestingly enough, all 3 of these usb ports have had the printer in them at one time or another, which is why I bring this up.

Could it be once a usb port was assigned, then the printer was disconnected, upon reconnection it's not working and won't work again?  Like these three ports are now tainted unless I remove some information somewhere?  

Edit... again.  I turned off the printer, moved it from one of the 3 usb ports to another, (one of the same 3 'tainted' usb ports) turned it on, now the printer is detected, now the printer can print.

No word on what will happen next time I turn my computer on, I hope I won't have to do this every time but at least I don't have to buy a new computer.

So slight fix at least for me.  Have the printer off, plug it in, turn printer on and give it a try.

---

### Post by Rasheeke on 2009-10-05
another update... back to square one.  

Although now, even after reinstalling, no test page can be printed.

---

