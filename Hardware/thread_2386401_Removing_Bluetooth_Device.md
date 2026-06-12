---
title: "Removing Bluetooth Device"
date: 2018-03-05
forum: Hardware
---

### Post by angel mike on 2018-03-05
I cannot remove a device from the Bluetooth Settings List because clicking the Bluetooth Icon in Settings give a window which has the message 'No Bluetooth found - Plug in a dongle to use bluetooth'. 
So I cannot proceed to use the instructions given below. I need a command to remove this window. I will then be able to reinstall the device to the list which hopefully will be paired again.

After clicking on Bluetooth Settings which is shown from the Bluetoothin your second image, with the menu title Bluetooth  Select the item you want to **remove**.  Then click the - Button. 

Thanks Mike

---

### Post by mc4man on 2018-03-05
If you open a terminal & run this does it show a "Controller"?
bluetoothctl
(to exit bluetoothctl enter quit command..

---

### Post by angel mike on 2018-03-05
Thanks for the response mc4man I did that but got
 [bluetooth]#
then terminal did not finish.
 What is the quit command?

---

### Post by #&amp;thj^% on 2018-03-05
[s]Just keyboard shortcut>>[ctrl+c][/s]
Woops just type>> exit

---

### Post by jeremy31 on 2018-03-05
Actually CTRL+d or type quit

---

### Post by mc4man on 2018-03-05
Certainly hesitant to suggest such seeing as though most of the packages he installed shouldn't have done anything but I guess you could take a look here - 
[https://askubuntu.com/questions/1011536/bug-on-bluetooth-settings-in-ubuntu-16-04-lts](https://askubuntu.com/questions/1011536/bug-on-bluetooth-settings-in-ubuntu-16-04-lts)
Looking at the list 'shown' don't see much, maybe bluman??
(likely the poster installed more than the screen shows

Edit, sorry, should have been specific, as mentioned type quit
(- when at a bluetoothctl prompt typing help should show all valid commands..

---

### Post by angel mike on 2018-03-06
Thanks for all the suggestions.
On putting bluetoothctl in terminal it gives just [bluetooth]# and then typing is not registering - I did try quit the first time.

I have looked at the link from mc4man post and tried the following command - any thoughts on the output?
```

~$ sudo service bluetooth status
[sudo] password for michael: 
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
     Docs: man:bluetoothd(8)

```
The final suggestion on the link was to install everything 'bluetooth' in the software centre - I am a bit hesitant of just installing a random set of applications - but will to do as a last resort. The web page on that link showing 'no bluetooth found' is just what I get.
Mike

---

