---
title: "keyboard driver for HP mini 210"
date: 2010-11-10
forum: Hardware
---

### Post by martin r on 2010-11-10
Hi everybody!
Just bought an HP mini 210 netbook, deleted Win7 and started with a new installation using ubuntu 10.10. After installed from an USB stick I plugged in the network cable and after some updates nearly everthing works fine, except the WLAN.
After running the updates there was a seperated driver for the WLAN-Card. In the menu this installed driver is "activated but not used".

So I think the problem is in sphere of the keyboard. It is a model with space between the keys and with led-lamps on several keys. The led for "sound off" (F11) is always on (altough the function works) and the led for WLAN is always off (doesnt work)(F12) and cannot change this. Also the led in the left corner of the touchpad (Synaptic multitouch clickpad) does not work. 

Can you please help me to find a driver for a "QWERTZ"-Keyboard (german style), I think this would also solve my problem with activating the WLAN-Card.

Please think about, that this is my first experience with Ubuntu. Instructions given by professional users (hope so) should be understood by an two-left-hand-newbie ;-)

Thank you
martin

---

### Post by ajgreeny on 2010-11-10
I am sure everything you need to change keyboard layout can be done from the System ->Preferences ->Keyboard -Layouts tab.  Have a look there.

---

### Post by martin r on 2010-11-10
Thank you ajgreeny!

Had already tried the layouts for hp (for example ther e is one for HP mini 110). But there is none that solves the problem. 

best regards
martin

---

### Post by martin r on 2010-11-11
Are there any other ideas, please!

---

### Post by Basfriends on 2010-12-27
Hi Martin R,

I can't do anything about your keyboard layout, but I might be able to help you with your wlan issue. 

First, open up a terminal window and execute ifconfig (just type ifconfig and press enter). It shows you information about your network interfaces. Find out which interface belongs to your wlan card (mine is called wlan0, for instance). Once done, execute "sudo ifconfig wlan0 up" to activate your interface. Of course you've got to replace wlan0 with the name of the wlan interface you want to activate. I might be wrong, but as far as I know this does the same as the wlan interface button does.

I wish you luck solving your problems,
Bas

---

