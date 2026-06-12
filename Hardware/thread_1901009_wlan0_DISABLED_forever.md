---
title: "wlan0 DISABLED forever"
date: 2011-12-27
forum: Hardware
---

### Post by xedth2 on 2011-12-27
I've tried installing ubuntu minimal twice and every time I do wlan0 is DISABLED.  I try "sudo ifconfig wlan0 up" and get no changed.  I've tried installing the driver so I do "sudo apt-get install rtl8192ce-dkms" and get unable to locate rtl8192ce-dkms.  So I tried "sudo add-apt-repository ppa:lexical/hwe-wireless" and get "add-get-repository command not found".  So I do "sudo apt-get install python-software-properties" and then try add-get-repository again but still the command can not be found.  I tried hitting FN-F8 to enable the wireless that way but still doesn't work.  I have no idea how to fix this nor do I have any clue whats going on.  I know the wireless card works because I did a ubuntu minimal install before and had it working but had to reinstall to try and get the sound to work.  Mind you I know thats not going to work either once I get the wifi working.  I'll attach the output from both "lshw -C network" and "lspci -v".  It's a Toshiba NB505-N500BL.

Thank You

---

### Post by xedth2 on 2011-12-27
I should also mention that I have NO GUI.  I'm doing all this through command line! And yes this is on purpose.

---

### Post by xedth2 on 2011-12-27
Heres the output for "sudo iwconfig" and "ifconfig -a" after running "sudo iwconfig wlan0 essid "HarveyHome""

---

### Post by wolfen69 on 2011-12-27
You mention 2 different commands, **sudo add-apt-repository**, and **sudo add-get-repository**. Make sure to do **sudo add-apt-repository**.

---

### Post by xedth2 on 2011-12-27
So I just got the repo to added it reinstalled the driver but it still doesn't work.

---

