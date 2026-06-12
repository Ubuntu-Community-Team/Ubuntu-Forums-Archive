---
title: "Can't Install AMD Radeon Graphics Card"
date: 2011-06-25
forum: Hardware
---

### Post by HUGE17 on 2011-06-25
I have recently switched over Linux as I am really bored with Windows. I am a noob when it comes to Linux so I don't really know what I am doing.

I have a graphical error on boot up where the screen goes crazy. I also cannot add effects to my icons. I have put this down to not having the right graphics driver.

I am using a C-Series 14 Sony Vaio with a AMD Radeon HDxxxM Graphics card and using Ubuntu 10.04 64 bit. I have located the driver I need on the AMD website but have been unable to install it through the terminal. The only feed back I get is the file cannot be opened. I have no idea what to do really but I would like to get my system running smoothly.

Any help would be appreciated thanks!

---

### Post by Yellow Pasque on 2011-06-25
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by HUGE17 on 2011-06-25
I'm getting a no adapters detected from one of the commands. Do you know what this problem is? Thanks for the help so far.

---

### Post by Yellow Pasque on 2011-06-25
Well, it looks like you have hybrid graphics (intel and AMD GPU's): [http://www.sonystyle.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644784022](http://www.sonystyle.com/webapp/wcs/stores/servlet/CategoryDisplay?catalogId=10551&storeId=10151&langId=-1&categoryId=8198552921644784022)

So I doubt fglrx will work since you're using the intel GPU.

---

### Post by HUGE17 on 2011-06-27
Hmm this is a frustrating situation. Once I figure this out I will post my solution. If anyone else comes across this and can solve it please post.

---

### Post by Yellow Pasque on 2011-06-27
Hint: vgaswitcheroo ;)

---

### Post by HUGE17 on 2011-07-05
Hey so thanks for the help so far. VGA Switcheroo is a good call and I almost have but I was wondering if you could help me some more. First of all could you verify for me that when I do a lspci | grep VGA command only one graphics card is shown because I haven't installed the driver for my discrete one? And also can you recommend any drivers for the one I previously started this thread for because I'm pretty sure I need it. Thanks for the help.

---

### Post by Yellow Pasque on 2011-07-05
Please post the output of your lspci.

---

### Post by HUGE17 on 2011-07-05
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6760
01:00.1 Audio device: ATI Technologies Inc Device aa98
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e823 (rev 04)
03:00.1 System peripheral: Ricoh Co Ltd Device e232 (rev 04)
04:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
05:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)

---

### Post by Yellow Pasque on 2011-07-05
Do you have the intel IGP disabled in the BIOS? If so, you can install the ATI driver like so:  [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)
Note that your hardware is very new and you might get more informative data with: 
```
sudo update-pciids
sudo update usbids
```

---

### Post by HUGE17 on 2011-07-05
Alright thanks for taking the to help I really appreciate it. I'll look into this. Seems I just need to be patient.

---

### Post by Yellow Pasque on 2011-07-05
No problemo. Mark this thread solved if you don't need further assistance. I'm not really sure what happened in this thread :P

---

### Post by HUGE17 on 2011-07-06
So I had a bunch of problems with 10.04 so I updated to 11.04 and now I have graphics, sound, function keys all working straight off the bat.

---

