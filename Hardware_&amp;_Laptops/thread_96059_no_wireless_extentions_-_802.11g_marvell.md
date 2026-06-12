---
title: "no wireless extentions - 802.11g marvell"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by masingerz on 2005-11-28
Dear Ubuntu Forum:

I have a wireless 802.11g Marvell PCI card, that is not recognized on 2.6.12-9-386

I have 2 NIC's:

1. Regular PCI NIC (the type that uses RJ-45)
2. A PCI wireless 802.11g "marvell" brand

When I do an ifconfig I see the NIC mentioned in #1
When I do a iwconfig I see ""no wireless extentions" and no sign of #2

In the Ubuntu GUI I see #1 but I do not see #2

Please help get the wireless card recognized.

---

### Post by xristos on 2005-11-28
Check the ndiswrapper project

---

### Post by Lambert on 2005-11-28
There's no native linux driver for a marvel chipset so as stated in the previous post you need to use an app called ndiswrapper. In a nutshell it makes the windows drivers work in linux.

There's a link in my signature on ndiswrapper

---

### Post by masingerz on 2005-11-28
This is as far as i got:


carlos@ubuntu:~$ lspci
0000:06:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)

carlos@ubuntu:~$ lspci -n
0000:06:00.0 0200: 11ab:1faa (rev 03)

I went to the list ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)) 
---o---
I tried the driver that came with the cd and another one that downloaded an neither worked

---

### Post by Lambert on 2005-11-29
It looks like it's supported with ndiswrapper. 

When you say it didn't work give a little more detail. What actually tells you it didn't work?

did you run ndiswrapper -l and get hardware present driver present
were you able to run modprobe ndiswrapper with no problems
were you able to run iwconfig and see wlan0 or go to gui menu in system>admin>networking and see wlan0

---

### Post by masingerz on 2005-11-30
Here is what I do:

I go into the cd that came with the card, I copy the Win xp driver to /home/driver/ (a new folder) I paste the 3 files that were in the cd:

Mrv8000c.cat
Mrv8000c.INF
Mrv8000c.sys

Now the folder contains the 3 files.

I open a terminal screen and I type:

carlos@ubuntu:~$ dir
Desktop  driver
carlos@ubuntu:~$ cd driver
carlos@ubuntu:~/driver$
carlos@ubuntu:~/driver$ dir
Mrv8000c.cat  Mrv8000c.INF  Mrv8000c.sys
carlos@ubuntu:~/driver$ sudo ndiswrapper -i /home/driver/Mrv8000c.INF
Installing mrv8000c
cp: cannot stat `/home/driver/Mrv8000c.INF': No such file or directory
carlos@ubuntu:~/driver$ sudo ndiswrapper -l
Installed ndis drivers:
mrv8000c        invalid driver!
carlos@ubuntu:~/driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

carlos@ubuntu:~/driver$
carlos@ubuntu:~/driver$
carlos@ubuntu:~/driver$
carlos@ubuntu:~/driver$ sudo ndiswrapper -e mrv8000c
carlos@ubuntu:~/driver$ sudo ndiswrapper -l
No drivers installed
carlos@ubuntu:~/driver$

---

### Post by Lambert on 2005-11-30
This doesn't look correct.

carlos@ubuntu:~/driver$ sudo ndiswrapper -i /home/driver/Mrv8000c.INF

Should be

carlos@ubuntu:~/driver$ sudo ndiswrapper -i /home/[COLOR="Red"]carlos[/COLOR]/driver/Mrv8000c.INF

If you're in that directory you don't even have to type out the full path as it will read the files in the directory you're currently in.

carlos@ubuntu:~/driver$ sudo ndiswrapper -i Mrv8000c.INF

should work.

---

### Post by masingerz on 2005-11-30
:o it worked

---

