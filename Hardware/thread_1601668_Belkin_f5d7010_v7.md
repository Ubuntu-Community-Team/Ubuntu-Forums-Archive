---
title: "Belkin f5d7010 v7"
date: 2010-10-20
forum: Hardware
---

### Post by shiman6 on 2010-10-20
Hi, i recently tried updating the driver of this device (rtl8185l) by downloading the source and compiling it. This completely deactivated the device, and now i cannot use it.

lspci outputs this for it

```
03:00.0 Ethernet controller: Belkin Device 701f (rev 20)

```and lspci -v outputs this

```
03:00.0 Ethernet controller: Belkin Device 701f (rev 20)
    Subsystem: Belkin Device 701f
    Flags: medium devsel, IRQ 9
    I/O ports at 2800 [disabled] [size=256]
    Memory at 28000000 (32-bit, non-prefetchable) [disabled] [size=512]
    Capabilities: <access denied>


```

Soo... it looks like the system doesnt identify the device with the driver anymore. And i want to avoid using ndiswrapper.

Any help?

---

### Post by Rasa1111 on 2010-10-22
Hi bro, 
Sorry youve not received any replies yet. 
I can offer no help in this dept. other than to bump the thread to the top,
in hopes that someone more experienced in this area will chime in. 

 So, BUMP!

Can anyone shed any light on this brothers driver issue? :?:

---

### Post by shiman6 on 2010-10-22
I fixed both problems!! I'm proud of myself. Not only does the new driver work with this card, but it also solves the problem of the low signal reception!

ok, so heres what i did 

1. Get rtl8185l driver for linux from the website, it will be in source code. 

2. Extract the driver somewhere.

3. Go into the directory and then into the rtl8185 folder

4. Open r8180_core.c in an editor

5. Line 63 change the vendor ID to 0x701f.

6. line 97 or line 104, not both, change to device = 0x701. Save the file

7. cd into the main directory, then sudo make and sudo make install

8. Reboot.

---

### Post by Rasa1111 on 2010-10-23
wow niice!
 Good work man!
 Im proud of you to! lol :D
COngrats!<3

---

### Post by crackers8199 on 2010-11-17
have you been able to connect to wpa2 networks with this driver?  i was hoping to use the updated driver because i was looking for a solution to the low signal strength issue, but now i'm back to not being able to connect to wpa2 networks (i keep getting bad password errors using wicd, even though i know the passphrase is right).

your instructions at least have gotten me further than i was before, as i now have the driver attached to the card...but i still can't get into my home network, which is wpa2...

---

### Post by shiman6 on 2010-12-06
I do happen to have the same problem. I read somewhere that you have to manually start wpa_supplicant, but i dont remember where. It worked a couple of times for me, and most of the time, i just click enter again whenever it asks me for the password and i know it is right. It hasnt been a problem for me because most of the time, where i keep my laptop at home, there is an ethernet cable i just plug directly into.

so, try disabling the network by right clicking the network manager icon, and uncheck "enable networking", open up a command line and sudo wpa_supplicant, then re-enable networking.

It's a wild shot in the dark. I should try it myself. Let me know if it works.

---

### Post by Franklin383 on 2011-06-06
ok so how do you make and install??? foregive me im a newbe

---

### Post by shiman6 on 2011-07-07
you do have to have some linux experience to do this, here is a howto
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

its all done in the command line, so you have to have a terminal window open.

---

