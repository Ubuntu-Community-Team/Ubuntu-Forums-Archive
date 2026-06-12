---
title: "wireless on acer 5024 and ubuntu 5.10"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by stknightmare on 2005-11-08
I dont know what else to do,i have a broadcom 802.11g but i cant get it to work on my acer 5024 running ubuntu 5.10.I have done everything suggested at other threads.Looked over the internet.When i used sudo ndiswrapper-l  it shows me that bcmwl5 driver is installed and also that hardware is present but when i go to system---->administration----->networking i find only 2 things ethernet connection and modem connection no wlan0 can be found.What should do i do?I want to use ubuntu but i really need the wireless.Anu suggestions?

---

### Post by jml on 2005-11-08
First a question, was the wireless card inserted into the computer when you installed Ubuntu?  I've found that the best chance of getting hardware recognized is at the time of installation of the distro.  It has always seemed harder to accomplish after the fact.  Since NDISWRAPPER recognizes the driver and you are able to "see" the card, that may not be your problem.

Once you have the network settings dialog box open, if there is no icon for the "Wireless connection" then its possible that the networking application can't detect your card.  If the icon is there, click on it, then click on properties and click on "enable this connection" and fill in the appropriate settings.  Click on OK and then click on the "activate" radio button.  As long as you don't need WPA encryption, you should be good to go.  There may be others on this forum who have other ideas, but I've found that sometimes reinstalling the distro will work, even though I did the exact same thing before and it didn't work.  Go figure.  Hope this helps.

Joe

---

### Post by stknightmare on 2005-11-08
[QUOTE=jml]
Once you have the network settings dialog box open, if there is no icon for the "Wireless connection" then its possible that the networking application can't detect your card. 
Joe[/QUOTE]

The card is onboard the laptop or inside the laptop.No i only see the eth0 and the modem something but not the wirelless card.

---

### Post by sean.smithson on 2005-11-08
Did you modprobe ndiswrapper?

If so, "dmesg | grep ndis" might help.

---

### Post by stknightmare on 2005-11-08
I forgot to tell that i have ubuntu 5.10 64 bit version.And that the laptop haves amd 64 turion.I looked it a little bit more.I think there is a problem at the driver that they give for windows,he is not supported by the 64 architecture,i also tried the one that they give for windows 64.Nothing.

---

### Post by stknightmare on 2005-11-09
Dont ask me why because i dont know what did i do that made it worked.Maybe i installed the bcmwl5.inf with ndiswrapper mdprobed and everything so that diver present,hardware found and the i shold go to the windows and let the wirelless open then reboot again at ubuntu and everything from now on will be okay.At least i think so.

---

### Post by sean.smithson on 2005-11-09
snip

---

### Post by stknightmare on 2005-11-14
knightmare@stelios:~$ dmesg |grep ndis
[   40.443788] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[   40.527499] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   40.536035] ndiswrapper: using irq 21
[   41.042024] wlan0: ndiswrapper ethernet device 00:0e:9b:ca:87:93 using driver bcmwl5, configuration file 14E4:4318.5.conf


Here is the output.

---

### Post by GuyveR800 on 2005-11-14
You need to install acer_acpi to enable the wireless connection. One of the other threads about this issue even has a start-up script for it you can use.

---

### Post by stknightmare on 2005-11-15
If i use 2.6.11-1-amd64-generic the acer_acpi is compiled everything is fined but then i cant pass the module modprobe fails and it says illegal extention.When i try to compile it using the 2.6.12-9-amd64-generic i get lots of errors it does not produce anything after i press make.so i cant proceed.Any ideas?

---

### Post by GuyveR800 on 2005-11-15
It would help if you were a bit more descriptive, but I guess the problem is you need GCC 3.4 installed to compile acer_acpi.
As for which kernel to use, you should be using 2.6.12-9-amd-k8, because it really fixes a lot of problems with the Aspire 5024 compared to earlier kernel versions.

---

### Post by stknightmare on 2005-11-15
I installed gcc 3.4 but i dont know how to change from generic kernel to k8 kernel.

---

### Post by GuyveR800 on 2005-11-16
I don't know if the k8 kernel has any fixes compared to the generic one, but it will be faster for your CPU. You can install it from Synaptic.

---

### Post by stknightmare on 2005-11-16
Ok the nightmare is finally over.I am writing this post from my acer 5024 usin wireless.

---

### Post by GuyveR800 on 2005-11-16
Great :)

---

