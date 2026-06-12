---
title: "Realtek Driver"
date: 2010-07-25
forum: Hardware
---

### Post by Denicia on 2010-07-25
I can someone please tell me where i can find a driver for a realtek wireless card thats on a toshiba laptop?

---

### Post by anglican on 2010-07-26
> **Denicia said:**
> I can someone please tell me where i can find a driver for a realtek wireless card thats on a toshiba laptop?
Which wireless card and laptop? Both Realtek and Toshiba make quite a few!

H

---

### Post by Denicia on 2010-07-26
Its the toshiba A505-6005 and it has a realtek rtl8191se wireless adapter.

---

### Post by anglican on 2010-07-26
> **Denicia said:**
> Its the toshiba A505-6005 and it has a realtek rtl8191se wireless adapter.
Looks like you might be in luck then. Take a look at this thread:

[http://ubuntuforums.org/showthread.php?p=8957805](http://ubuntuforums.org/showthread.php?p=8957805)

In short:

```
sudo apt-get install build-essential linux-headers-generic 

Download the file from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) 

By default, file downloads go to your  desktop. Right-click the file and select 'Extract 
Here'. A folder will  be created called something like rtl8192se_linux_2.6.0014.0115.2010 
(version numbers may be slightly different).

Open a terminal and type:

cd Desktop/rtl8192se_linux_2.6.0014.0115.2010
sudo su
make
make install
modprobe r8192se_pci
exit
iwconfig 

Do you now have a wireless interface, wlan0, perhaps? Can you click the Network Manager icon, see networks and connect?
```H

---

### Post by Denicia on 2010-07-27
thank u, i tried it but i get a error when i try the make command. i read that i needed to installl gcc and i did but it still doesnt work. the error i get is: make: *** /lib/modules/2.6.33.6-147.fc13.i686/build: No such file or directory.  Stop.
make: *** [all] Error 2

---

### Post by anglican on 2010-07-28
> **Denicia said:**
> thank u, i tried it but i get a error when i try the make command. i read that i needed to installl gcc and i did but it still doesnt work. the error i get is: make: *** /lib/modules/2.6.33.6-147.fc13.i686/build: No such file or directory.  Stop.
make: *** [all] Error 2
Are you actually using ubuntu? The command "sudo apt-get install build-essential linux-headers-generic" installs everything you need to compile this module including gcc. But the output above suggests you're using fedora core 13. You'll need to ask this question on a fedora forum, my answer only applies to ubuntu (and I've tested it there - it works).

H

---

