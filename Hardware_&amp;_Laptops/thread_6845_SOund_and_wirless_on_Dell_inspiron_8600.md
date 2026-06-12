---
title: "SOund and wirless on Dell inspiron 8600"
date: 2004-12-02
forum: Hardware &amp; Laptops
---

### Post by Infatuated_iPod on 2004-12-02
I looked up some stuff on ubuntu.com but none of it worked.. the info was very confusing. Can anyone help me?

Its said that i need to add nsdiwrapper to /etc/apt/source.list  for wireless, but when i do it in the terminal it says that it is not a directory... 

then for sound it said that i need to add.... acpi_irq_isa=7 to boot options (sudo nano/boot/grub/source/menu.list , but that isnt a directory either... someone please help.

---

### Post by Magneto on 2004-12-02
/etc/apt/sources.list

/boot/grub/menu.lst

---

### Post by Infatuated_iPod on 2004-12-02
do i write sudo before  those and should i do it in the root terminal or the regular terminal?

---

### Post by Magneto on 2004-12-02
to edit those files you need root priviliges so you can use sudo or a root terminal whatever you prefer

sudo gedit /directory/filename        
if you want something like notepad

sudo nano -w /directory/filename
for a terminal

sudo vi /directory/filename

for commandline pimpin

---

### Post by Infatuated_iPod on 2004-12-02
Well i got to the menu, but i have no idea what do do from there? where exactly do i add "acpi_irq_isa=7"? Also, on the ubuntu website it said to add.. "http:nsdiwrapper.sourceforge.net/debian./" to the list, should i add the url or the acutal file? Thanks so much.

---

### Post by lockenkeyster on 2004-12-02
Do have the 2100 or 2200 miniPCI in your laptop. For me, with the 2100, the card is actually detected and setup just fine, but you have to go to "networking" and manually add it to the list (as eth0 for me) in order to use it...

Does the card show up in the device manager? I just ask b/c I haven't had to do anything with the ndiswrapper since I made the switch from sarge to ubuntu.

---

### Post by Infatuated_iPod on 2004-12-02
yea it shows up in the device manager, i have the 2100... so what exactly did you do to get it to work? and i assume you have the same computer so how did you get the sound to work?

---

### Post by Infatuated_iPod on 2004-12-02
How do you set up the card as eth0?

---> There seems to be some error with the driver.. ? I have no idea what to do, can someone help me..

```

CPU: Intel(R) Pentium(R) M processor 1400MHz stepping 05
agpgart: Detected an Intel 855PM Chipset.
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB (ICH4) USB UHCI #1
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB (ICH4) USB UHCI #2
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB (ICH4) USB UHCI #3
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
Intel ICH: probe of 0000:00:1f.5 failed with error -16
Intel ICH Modem: probe of 0000:00:1f.6 failed with error -16
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 0.53
ipw2100: Copyright(c) 2003-2004 Intel Corporation

```

THe driver seems to be there.. but then there is some error, and i cant get my wirless card to work. :(

---

### Post by lockenkeyster on 2004-12-02
[QUOTE=Infatuated_iPod]yea it shows up in the device manager, i have the 2100... so what exactly did you do to get it to work? and i assume you have the same computer so how did you get the sound to work?[/QUOTE]

WIRELESS

Sorry, I actually have a 500m, but its the same internal card. I went to Computer -> System Configuration -> Networking

click on "Add", then forward

one of the choices should be wireless, choose this and click on forward

choose one of the devices from next to "Wireless Device" (for me, the only option is eth0)

enter the SSID and WEP (if necessary) for the router/wireless network, click forward

in the configuration field, change to "Automatic DHCP"

click forward

make sure apply and activate connection is checked and click forward again, and you should now be connected!

______

SOUND

for sound, I don't think your laptop has the same card, but try this thread for possible answers:

[http://www.ubuntuforums.org/showthread.php?t=2743](http://www.ubuntuforums.org/showthread.php?t=2743)


Hope this stuff helps!

---

### Post by MikePB on 2005-02-15
I've got the same problem, I can connect fine using Ethernet, but for somereason it doesn't even see my wireless card, so it doesn't even give me a device in the network tab..

---

