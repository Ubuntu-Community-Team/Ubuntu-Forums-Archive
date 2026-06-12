---
title: "Bluetooth &amp; S700i"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by casioubuntu on 2005-06-09
Hello !

      I have searched on the forums and followed this threads HOWTO:
[HOWTO:Nokia and Bluetooth](http://ubuntuforums.org/showthread.php?t=34740) 

although I am using an SE phone the posts in the thread indicated that this should work. Well it does, however after sending a file from my phone to the PC my Phone still thinks its communicating via bluetooth and I can only disable it by switching the phone off.

I am using Hoary Ubuntu 5.04 and so far I am very impressed as I have tried numerous other distros.
 
Any thoughts or ideas on this?

---

### Post by casioubuntu on 2005-06-09
I have tried mainly the obexserver from the command prompt when i get the above error. However if I try the gnome-obex-server the phone does not find it at all and I get :

conn_request:  bdaddr <mobie phone address>
conn_complete: status 0x00
conn_request: bdaddr <mobie phone address>


Any more thoughts on this?


Oh BTW I can send files from the PC to the phone and it doesnt cause the same problem  ](*,)

---

### Post by kb00heda on 2005-06-09
This probably is no good answer for you, but on my Motorola phone, I may shutdown the Bluetooth power separately, i.e., I don't need to switch off the phone. There is no menu entry like enable/disable bluetooth on your phone then? Otherwise I'm afraid to be of little help (I used the same step-by-step howto myself)...  :?

---

### Post by casioubuntu on 2005-06-09
Sorted it in the end. On reading the HOWTO it mentions that after a reboot either the following commands need adding into a script on boot up or run manual:

> 
sudo modprobe l2cap
sudo modprobe rfcomm
sudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
sudo rfcomm bind /dev/rfcomm0 YOUR_PHONE_ADDRESS 10


However I just rebooted my system and decided just to run the bluetooth file sharer from the GUI by itself - this has worked a charm and the phone does not think its active with bluetooth when finished.  \\:D/ 

Cheers anyway for your post and there is a bluetooth off/on option but this gets grayed out when it thinks bluetooth is in use.

---

