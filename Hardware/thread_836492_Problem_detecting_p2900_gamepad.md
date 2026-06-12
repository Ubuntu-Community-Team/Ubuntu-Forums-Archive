---
title: "Problem detecting p2900 gamepad"
date: 2008-06-21
forum: Hardware
---

### Post by malaTG on 2008-06-21
Hi everyone

I am having problem to connect my p2900 with my receiver. I have a dual-boot machine and in windows it finds my gamepad instantly but in ubuntu 8.04 it just searches for the usb receiver without finding it. I know that it should work in linux because it worked under fedora core 5.

The receiver is detected because I get this with dmesg

> [  695.145379] usb 8-5.4.4: new low speed USB device using ehci_hcd and address 10
[  695.241958] usb 8-5.4.4: configuration #1 chosen from 1 choice
[  695.249611] input: Saitek Saitek P2900 Wireless Pad as /devices/pci0000:00/0000:00:1d.7/usb8/8-5/8-5.4/8-5.4.4/8-5.4.4:1.0/input/input8
[  695.310105] input,hidraw0: USB HID v1.00 Gamepad [Saitek Saitek P2900 Wireless Pad] on usb-0000:00:1d.7-5.4.4


I read something about udev being broken in ubuntu? Does anyone know how to solve this problem?

UPDATE: I managed to get contact with one of my controls but then I lost it again when I tried to pair my other control with the other receiver. Is ther some way to "lock" the connection or something similar?

Thank you in advance!

/mala

---

### Post by acomputerdood on 2008-06-22
i too am having this exact same problem!  except not in ubuntu.

i'm running the 2.6.20 kernel and can't always get my gamepad to sync with my computer.  it seems that if it doesn't work, then it's not going to -- no matter how many times i try.  at least until i reboot, where it *might* start working.

some (hopefully) helpful information:

# lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0666:0101
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 06a3:040c Saitek PLC
Bus 002 Device 001: ID 0000:0000

# tail /var/log/messages
Jun 22 12:40:43 poppa-serve usb 2-2: new low speed USB device using uhci_hcd and address 2
Jun 22 12:40:43 poppa-serve usb 2-2: configuration #1 chosen from 1 choice
Jun 22 12:40:43 poppa-serve input: Saitek Saitek P2900 Wireless Pad as /class/input/input3
Jun 22 12:40:43 poppa-serve input: USB HID v1.00 Gamepad [Saitek Saitek P2900 Wireless Pad] on usb-0000:00:1d.0-2


# cat /proc/bus/usb/devices
T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=06a3 ProdID=040c Rev= 1.30
S:  Manufacturer=Saitek
S:  Product=Saitek P2900 Wireless Pad
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

---

### Post by acomputerdood on 2008-06-23
actually, just last night i got it to sync up without having to reboot.

i tracked the device down to being "/dev/input/event3" (yours will probably be different).  then, i did a "cat /dev/input/event3" while trying to get the gamepad to sync.  i started pushing all the buttons, and lo and behold, it sync'd.

*shrugs*

---

### Post by malaTG on 2008-08-29
Hello everyone,

I think it is time for a ](*,)

My p2900 syncs perfect in windows XP. 

It is discovered in ubuntu perfect but when I try to sync it doesn't find any connection.... 

It synced one time but then lost the connection later. 

Ohhhhh and one more thing, I have two controls, same problem with both. 

Does anyone know how to track down this problem or should I just buy two new controls?!

/mala

---

### Post by malaTG on 2008-09-02
bump...

---

### Post by malaTG on 2008-09-14
bump

---

### Post by malaTG on 2008-09-15
bump

---

### Post by malaTG on 2008-11-29
Hi everyone, 

I am bumping this one more time because I still have the same problem and I feel that it is some kind of bug in ubuntu since it worked for me in fedora 6. What is the correct way of reporting a bug?

---

### Post by malaTG on 2008-12-07
For those interesting in following the progress on this one I created a bug on launchpad

[https://bugs.launchpad.net/ubuntu/+bug/305930](https://bugs.launchpad.net/ubuntu/+bug/305930)

/mala

---

### Post by Triptoph on 2008-12-10
I have the same problem.  When I plug it in a new event* appears in /dev/input, as well as an entry /dev/input/js0

however it doesn't seem to work.  using cat /dev/input/js0 produces a bit of jargon, but adds nothing more when i press buttons.  I assume this command would produce more characters by pressing joystick buttons if it were working? 

dmesg has similar lines to yours as well.

---

### Post by kitsune ravo on 2010-01-01
There is justifiable reason for a bump of this topic.

I can confirm that I have this bug as well. I have tried all the suggestions here, none worked (event3 just gives me gibberish, and the others don't detect anything other then the keyboard/mouse), and Joy2key was no help ether. I'm using a Saitek P2900 wireless controller, and Ubuntu Karmic. I have all the latest updates as of this post. Before Karmic, the controller was working fine, but on Karmic it seems that it won't work at all.

This bug had been here for a while now, and it it high time that  it get looked at. This worked before, so fixing should be a matter of finding out what broke it. I really don't think I should have to buy another controller because a karmic refuses to register this one.

---

### Post by jellyfisharepretty on 2010-01-10
Hi, I'm using this gamepad too, on karmic... It works about 1/4 of the time, for some reason.  Used to work perfectly.  I've tried changing the battery, that didn't help.  But I tried these [_instructions_]("http://www.saitek.com/uk/supp/p2900repair.htm") from Saitek.  So far so good... so give it a try.

---

### Post by jellyfisharepretty on 2010-01-12
Well, it seems taking out the battery and holding the scan button for > 5s is the only way to get it to work.  But if I turn off the gamepad, I'll have to do that whole procedure again to get it to work.  If I leave the game pad on for the whole movie (I use it as a remote control for videos), then it seems to work.

---

