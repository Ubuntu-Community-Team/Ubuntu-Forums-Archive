---
title: "switching mobile broadband usb between ubutnu and windoes?"
date: 2009-04-08
forum: Hardware
---

### Post by Quift on 2009-04-08
hi all,

I currently have a problem which I guess has a very simple solution but I cannot seem to find it. I have an huwai usb modem from swedish 3, and I wish to alternate between using it on ubuntu and windows lap tops. ie, my private laptop and my work laptop, meaning I have to use this setup.

if I just close the internet connection and pull the usb fro ubuntu i cannot get the usb to work with the 3 connection program in windows. i guess this is because Ineed to properly unmount the usb but where and how do i do this?

---

### Post by GeorgeVita on 2009-04-08
Hi **Quift**,

what is the model of your Huawei modem? Using it in Ubuntu from a terminal window: **lsusb** (post here the output)

How do you connect in Ubuntu? If you are using **wvdial** post the **/etc/wvdial.conf** file.

Do you know how to add an extra init AT command and enable modem activity log into windows? (from control panel, modem & dialing, properties, advanced)

The idea is to try find any "bad" setup parameter driving the modem to a "strange" (for windows) state. Possible solution is to add AT&F (restore factory settings) command.

Regards,
George

---

### Post by Quift on 2009-04-08
hi and thank you for your help.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


this is the result of lsusb. I just plug it into the usb port, let the network manager find it, configure it and connect. Total amoiunt of time spent configuring = 5s.

really smooth really. Only problem is that I cannot figure out where to unmount it. I'm quite sure that this would solve the problem since I cannt connect in linux if I havn't unmounted it properly in windows either. I would really like to just have a switch when I right click on something to unmount since I would have to do this quite regularly, but not so often as to remembering something to complicated.

---

### Post by GeorgeVita on 2009-04-08
Ok, lets try something.

While connected via Network Manager icon, right click it and the click on **Connection Information**. Find and remember the communication port it uses to connect (propably /dev/ttyUSB0).

Disconnect, open a terminal window and run:
**echo AT&F > /dev/ttyUSB0** (change the port number if it is different)

This will send a **Restore Factory Settings** command to the modem. Remove the modem and try it with windows.

Waiting your test to continue...

---

### Post by Quift on 2009-04-08
Oh, if that wold be translatable to "hardware adress" then that field is blank.

running the command gives

pierre-emil@pierre-emil-laptop:~$ echo AT&F > /dev/ttyUSB0
AT
[1] 5712
bash: /dev/ttyUSB0: Enhet eller resurs upptagen
[1]+  Done                    echo AT
pierre-emil@pierre-emil-laptop:~$ 

unit or resource is busy would be a decent translation. tried with sudo with the same result, ie, no sandwich.

---

### Post by GeorgeVita on 2009-04-08
I just test it to my ZTE modem (Ubuntu 8.10), and have a similar problem.

**bash: /dev/ttyUSB3: Device or resource busy** appears when I DID NOT disconnect from Network Manager!

Another problem caused bt the **&** so use double quotes (after disconnecting):
**echo "AT&F" > /dev/ttyUSB0**

If the problem exists, try **echo "AT&F" > /dev/ttyUSB1**

G

---

### Post by Quift on 2009-04-08
Thanks a lot, will try this tomorrow at the office.

Again, thanks for your time.

regards, Quift

---

