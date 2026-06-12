---
title: "[SOLVED] Wireless on Acer TravelMate 6413 WLMi"
date: 2008-12-14
forum: Hardware
---

### Post by Drengur on 2008-12-14
Hello.

I haven't gotten the wireless to work on an Acer TravelMate 6413. Everything else pretty much worked out of the box with Ubuntu 8.10.

What should I do?

---

### Post by nixscripter on 2008-12-14
Getting wireless working almost always follows a similar procedure. Let's start from the beginning.

What kind of card is it? Please run this in the Terminal, and post the output: ```
lshw -C network
```

---

### Post by Drengur on 2008-12-15
Thank you for your reply.

I would also like to note that this is an Acer laptop which means that you have a switch on the front by which you can turn your wireless on and off. That switch does not work since I installed Ubuntu.

The output for the wireless is something like this:

*-network DISABLED

PRO/Wireless 3945ABG [Golan] Network Connection
Logical name: wmaster0
Capabilities: cap_list logical ethernet physical wireless 
Configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

Do you need any more information from lshw? (I need to type this in on another computer).

With regards,
Drengur

---

### Post by Drengur on 2008-12-15
[http://ubuntuforums.org/showthread.php?t=964956](http://ubuntuforums.org/showthread.php?t=964956)

Seems to be a bug with the Acer thing as I suspected.

---

### Post by nixscripter on 2008-12-15
Did their suggestions work?

---

### Post by Drengur on 2008-12-15
Funny enough, yes.

First: 
sudo rmmod iwl3945

Then I pressed the Acer wireless button
Then:
sudo modprobe iwl3945

Works like a charm. Haven't tried rebooting but I'll post information for that later.

---

### Post by Drengur on 2008-12-15
After reboot the connection is still on. That is to say; you do not need to unload the module and reload it again each time you start up.

---

### Post by nixscripter on 2008-12-16
Great. Please mark the thread as solved (under the Thread Tools menu).

---

### Post by Drengur on 2008-12-17
Update: 

If the power goes off, that is to say if you take the battery out and unplug the computer, you get back at square one.

I've constructed a script which I use (or let my senile father use).

> #!/bin/bash
sudo rmmod iwl3945
echo "Press the Acer-wireless button ONCE. And then press enter"; read line
sudo modprobe iwl3945

This works after complete power-down. Someone who better understands this might be able to make a script that could probe the position of the wireless button or something. But please note you can only press the button once. If you fail, try, try again.

With regards,
Drengur

---

