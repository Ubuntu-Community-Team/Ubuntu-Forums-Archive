---
title: "How to troubleshoot a bluetooth adapter in Ubuntu 9.04?"
date: 2009-04-24
forum: Hardware
---

### Post by INTERPEGASUS on 2009-04-24
My bluetooth adapter is not working in Ubuntu 9.04 64 bit. It was working fine on previous Ubuntu versions. When I try to search for bluetooth devices using the bluetooth applet, the message states that there is no bluetooth adapter enabled.

I would like to know if there is a guide or link that explains how to troubleshoot bluetooth issues in Ubuntu.

Thanks

---

### Post by coffeeaddict22 on 2009-04-24
Hi,
There's a bit of stuff on the wiki- see [https://help.ubuntu.com/community/CategoryBluetooth]("https://help.ubuntu.com/community/CategoryBluetooth") for a list.
Your problem is probably not quite that though.  It appears to be that the Bluetooth adaptor has not been sensed.  What does ```
lshw | grep Bluetooth -A15
``` report?  And ```
hciconfig
``` may tell you if your card is working- post the outputs back here if you need more help.

---

### Post by INTERPEGASUS on 2009-04-24
Thank you for the reply. After entering the commands there is no output. Please let me know if you have any ideas on how to get the bluetooth adapter sensed / recognized? Thanks

ubuntu@pegasus:~$ sudo lshw | grep Bluetooth -A15
ubuntu@pegasus:~$ hciconfig 
ubuntu@pegasus:~$ 


> **coffeeaddict22 said:**
> Hi,
There's a bit of stuff on the wiki- see [https://help.ubuntu.com/community/CategoryBluetooth]("https://help.ubuntu.com/community/CategoryBluetooth") for a list.
Your problem is probably not quite that though.  It appears to be that the Bluetooth adaptor has not been sensed.  What does ```
lshw | grep Bluetooth -A15
``` report?  And ```
hciconfig
``` may tell you if your card is working- post the outputs back here if you need more help.

---

### Post by coffeeaddict22 on 2009-04-25
Could be 
1) card isn't working or connected.
2) no driver present.
Have you got the bluetooth stack?  Try 
```
 locate bluez-utils
```
and if you don't find anything, ```
 sudo apt-get install bluez-utils
```
Once you've done that, restart and try lshw again.

---

### Post by INTERPEGASUS on 2009-04-25
I reinstalled 9.04 and bluetooth is now working.

Solved :)

Thanks for the help.

---

### Post by coffeeaddict22 on 2009-04-25
Escellent.  Enjoy!

---

### Post by t4thfavor on 2009-06-18
Same issue, I have an AMD64 install of jaunty, and my bluetooth adapter is not woring. 

It worked last week briefly, and then stopped.

It had a blue light that flashes on it, and now the light is dark.

I have tested it on my Jaunty x64 laptop, and it DOES work.

The output of the above commands is a follows:
lshw |grep Bluetooth -A15

Nothing

hciconfig:
chance@AMD64:~$ hciconfig 
hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:0 acl:0 sco:0 commands:0 errors:0
Is there any reason this should not work?

Also, the dmesg when I plug it in does not register it as a bluetooth device:

[178024.188033] usb 3-1: new full speed USB device using ohci_hcd and address 16
[178024.465122] usb 3-1: configuration #1 chosen from 1 choice
[178028.773278] usb 3-1: USB disconnect, address 16
[178100.188047] usb 3-5: new full speed USB device using ohci_hcd and address 17
[178100.467785] usb 3-5: configuration #1 chosen from 1 choice


I have tried multiple USB ports, and am now at a loss. I will continue searching Google in the mean time. 

Thanks for any help I may recieve.

---

