---
title: "How to install wireless drivers via CD"
date: 2011-04-06
forum: Hardware
---

### Post by mike243 on 2011-04-06
I have not used ubuntu before and have not used unix in like 15 years. I have only a wireless router connection to the internet. I am trying to get a new box up and running Ubuntu on it. Ubuntu installed ok. However when I try to install the drivers that I put on a CD, I get the following error message.
 
you do not have the right permissions to extract archives in the folder "[file:///media/UDF%20Volume](file:///media/UDF%20Volume)"
 
The permission on the DVD drive are rwxrwxrwx . The drivers are in a .bz2 file.
 
Thats the first question. The next one is I can not find any directions on how to install the drivers once I get access. 
 
I ran a command (i dont remember which one) that did find the wireless card.
 
I someone could point me in the correct direction, I would certainly appreciate it.
 
Thanks mike

---

### Post by mike243 on 2011-04-06
?

---

### Post by cbowman57 on 2011-04-06
Copy the driver to the HD before you try to extract it.

---

### Post by mike243 on 2011-04-06
Thanks Chuck that allowed me to extract it.
 
WHen I tried to find a procedure for installing drivers, the referenced instructions were not there.
 
Do you know where I can find instructions for installing the drivers?

---

### Post by cbowman57 on 2011-04-06
What drivers are you trying to install?

---

### Post by mike243 on 2011-04-07
The following is from the driver release notes.
 
*              RALINK TECHNOLOGY, CORP.                  
*              RALINK RT73 Wireless Card          
*             SOFTWARE DRIVER RELEASE NOTE
*                                                                                                                                
*******************************************************************
[V 1.1.0.5]
1.) Support Kernel 2.6.35
 
The file name for the archived driver is 2011_0210_RT73_Linux_STA_Drv1.1.0.5.bz2

Hope this is sufficient
 
Mike

---

### Post by cbowman57 on 2011-04-07
Not exactly sure about that one, I use a different ralink driver myself but you need to open a terminal and navigate to the directory created when you extracted the drivers.  Once there you can try:
make
sudo make install
sudo modprode rt73sta

then see if your network manager is populated with available networks.

If it's more involved than that you might want to refer to this link.

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73")

---

### Post by mike243 on 2011-04-09
Thanks Chuck.
 
I will give it a shot this weekend,  I hope.
 
Mike

---

