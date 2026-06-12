---
title: "RTL 8168 Issue"
date: 2008-06-28
forum: Hardware
---

### Post by andyd34 on 2008-06-28
I wonder if someone can shed some light on an issue i am havibg with my NIC's. Here is the current set up.

ASROCK 1333-GLAN c/w RTL8168C onboard
RTL8168 FAMILY PCI

When I have the cards configured to DHCP they work fine. When 1 is static or both static neither work. 

One is connected to a LinkSYS router with a cable modem on the WAN port and 1 PC and 2 Laptops running on a home network.

The Other is connected directly to a cable modem and is been run as a server. I want to set up a DNS server on this box hence the static IP.

Can someone please advice as its driving me crazy, I have read somewhere ther is an issue in UBUNTU 8.04 with the RTL8168 and UBUNTU using the 8169 driver but for the life of me i can'y find the forum it was in, I have spent the last 6 hours trawling google trying to find it.

---

### Post by andyd34 on 2008-06-29
I have found some thread which specify Ubuntu may have a problem with this card as it uses the r8169 driver. I have found a thread which shows you how to replace the driver.

> 1. Download the latest driver from Realtek from here. We shall assume that the version you just downloaded is r8168-8.005.00. If not, change the file names that follow in these instructions appropriate to the name of the download.

2. Copy the downloaded file to the Ubuntu Desktop

3. Right click the file and extract it to the Desktop

4. Open a terminal by Menu -> Accessories -> Terminal

Note: all commands are preceded by the $ symbol and a space. When pasting into the terminal, do not include them (note - to paste into the terminal, hold down Ctrl and Shift, then press v). I don't know if point 14 is needed, but thought it best to leave it in - it won't harm your computer.

5. $ cd Desktop

6. $ sudo mv r8168-8.005.00 /usr/src

7. $ cd /usr/src/r8168-8.005.00

9. $ sudo make clean modules

10. $ sudo make install

11. $ sudo depmod -a

12. $ sudo insmod ./src/r8168.ko

13. $ cd /etc/modprobe.d

14. $ sudo touch blacklist-network

15. $ sudo gedit blacklist-network

16. This opens up a notepad like program. In this, type the words "blacklist r8169" (without quotes) and save then exit the program

17. $ sudo update-initramfs -u #to make the change permanent

18. $ sudo reboot

Step 18 reboots the computer so if you dual boot, select Ubuntu and wait for it to boot up, then test the internet connection (ie, open Firefox and go to a website).


I have tried this but get erros when i type


> sudo make clean modules

It can't find /src/MAKEFILE the directory does not exist

Does anyone have a suggestion on what I can do to resolve this.

---

### Post by John Linq on 2008-08-15
use "sudo bash" + "make clean modules" instead.

However, this is only to avoid the error message; I am not sure about the cause and side-effect. After I made the r8168.ko, I encountered some other problems.

---

