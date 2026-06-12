---
title: "Problem by WIFI after Installation Ubuntu 16.04.1"
date: 2016-10-16
forum: Hardware
---

### Post by willy549 on 2016-10-16
Hello Form Members,

I've a problem with the WIFI WLAN after installing Ubuntu 16.04.1 as a dual boot system.
Network is working when I'm conneted with a cable on the router, but without cable no way.
In win10 the WIFI is working fine, but not in Ubuntu Gnome.

If tried many things which are posted in internet but notthing is working.

I've an HP Laptop type willy-HP-Pavilion-Gaming-Notebook / Intel® Core™ i7-6700HQ CPU @ 2.60GHz × 8 and using Ubuntu 16.04.1 LTS 64-Bit

May somebody has the same problem and have an idea to fix it.

Thanks a lot in advance for your hep.

Willy


Some deteails:
illy@willy-HP-Pavilion-Gaming-Notebook:~$ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.

willy@willy-HP-Pavilion-Gaming-Notebook:~$ ^C
willy@willy-HP-Pavilion-Gaming-Notebook:~$ 


eno1      Link encap:Ethernet  Hardware Adresse dc:4a:3e:f6:38:43  
          inet Adresse:46.127.49.236  Bcast:46.127.63.255  Maske:255.255.240.0
          inet6-Adresse: fe80::e96:8118:526a:7a93/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:275299 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:109207 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:144379893 (144.3 MB)  TX-Bytes:14668222 (14.6 MB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX-Pakete:11317 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:11317 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1 
          RX-Bytes:1139522 (1.1 MB)  TX-Bytes:1139522 (1.1 MB)

willy@willy-HP-Pavilion-Gaming-Notebook:~$

---

### Post by prakharsr on 2016-10-16
What wireless network interface card  is in your laptop?

run the following commands in terminal - 

sudo lspci | grep -i Network ( this will tell your wireless card's specs)


example -

in my laptop -( sudo lspci | grep -i Network ) gives - 03:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)

goto the driver manager and check if the correct drivers are installed.

if they are , then run the command : sudo modprobe wl ( this command actually turns on my wifi card and shows the available networks )

---

### Post by prakharsr on 2016-10-16
also check out this post by chili555 : [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by willy549 on 2016-10-18
Thanks a lot for your answers.

Network controller:
08:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
willy@willy-HP-Pavilion-Gaming-Notebook:

I've tried the "sudo modprobe wl" command, but this is not working on my computer:
willy@willy-HP-Pavilion-Gaming-Notebook:~$ sudo modprobe wl
modprobe: ERROR: could not insert 'wl': Required key not available

I've checked the post from Chili555, my case would be case 2, but the solution is only for ubuntu 12.04 / 12.10, is it also valid for 16.04.1?
Thats why I've not installed the driver, suppose these are drivers to install in the tread from chili555.

willy@willy-HP-Pavilion-Gaming-Notebook:~$ lspci -nn -d 14e4:
08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

My driver list:
willy@willy-HP-Pavilion-Gaming-Notebook:~$ sudo ubuntu-drivers list
intel-microcode
nvidia-361
bcmwl-kernel-source

or

willy@willy-HP-Pavilion-Gaming-Notebook:~$ sudo ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

== /sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0 ==
vendor   : Broadcom Corporation
modalias : pci:v000014E4d00004365sv0000103Csd0000804Abc02sc80i00
model    : BCM43142 802.11b/g/n
driver   : bcmwl-kernel-source - distro non-free

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd0000139Asv0000103Csd0000816Bbc03sc02i00
model    : GM107M [GeForce GTX 950M]
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-361 - distro non-free recommended

Which alternate driver from where should I install?

Thanks a lot for your help

---

