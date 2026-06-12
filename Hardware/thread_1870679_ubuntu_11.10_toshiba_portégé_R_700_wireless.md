---
title: "ubuntu 11.10 toshiba portégé R 700 wireless"
date: 2011-10-27
forum: Hardware
---

### Post by drab17 on 2011-10-27
Hi @ all

I have a problem with the wirelesscard. it is blocked.

thatsme@Ubuntu:~$ rfkill list
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

how can i fix this issue?

thanks

---

### Post by wolfen69 on 2011-10-27
Is it physically turned on? Usually that's done with a combination of the Fn key + wireless key.

---

### Post by wolfen69 on 2011-10-27
Also, try:
```
rfkill unblock all
```
If you were physically plugged into the net via ethernet cable, removing it may help before you try to use wireless.

---

### Post by drab17 on 2011-10-28
hi wolfen69

thank you for your fast reply.

Yes there is a key combination for activating the wireless card. its Fn+F8. I figured out that it changes the attribute Soft blocked.

thatsme@Ubuntu:~$ rfkill list
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
thatsme@Ubuntu:~$ rfkill list
0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

But both advice didn't do the job. 

what should i do now? because the wireless network is essential for me. 


greez
drAb17

---

### Post by drab17 on 2011-10-28
i solved the problem with the assistance from google. i'm not sure if it is allowed to post link here. but the trick was to start windows and there activating the wireless card with the usual key combination. It is somehow different to the same combination under ubuntu.

im actually writing with the wireless connection.

thaaanks @ all readers.

greez
drAb17


:popcorn::popcorn:

---

