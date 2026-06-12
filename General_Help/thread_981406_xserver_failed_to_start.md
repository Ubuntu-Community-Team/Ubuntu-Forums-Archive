---
title: "xserver failed to start"
date: 2008-11-13
forum: General Help
---

### Post by garryzn on 2008-11-13
I have been using ubuntu Feisty for about 6 months.

I had to replace my mother board today after a power surge blew the old one last night. 
When i started up my computer i got the xserver failed to start message . I tried the 'sudo dpkg-reconfigure xserver-xorg' command,i stayed wth the default settings and re-started using 'sudo /etc/init.d/gdm restart' but no joy. My new board is a MSI945GCM7 with  945GC Express chipset, so i tried again changing the 'vesa' driver setting to 'intel i8' but still the xserver failed to start.

I've been searching the forums for hours, and almost pulled out all my hair.

 I'd be very grateful if one of you boffins out there could offer some suggestions. Thanks in advance.


Garry

---

### Post by nikgare on 2008-11-14
What does it say in the log files, eg /var/log/Xorg.0.log (maybe different name for fiesty)?

---

### Post by PmDematagoda on 2008-11-14
Could you also post the contents of:-
```
cat /etc/X11/xorg.conf
```

---

### Post by igknighted on 2008-11-14
This might be an opportune time to upgrade... Feisty is no longer supported with updates, so it is a security risk running it.

---

### Post by garryzn on 2008-11-14
Thanks for the response guys

I tried the '/var/log/Xorg.0.log' and '/etc/X11/xorg.conf' and it said "permission denied" on each attempt. I hope i'm not supposed to remember another password.

Help!

---

### Post by garryzn on 2008-11-14
I have a copy of Hardy but i don't think it can upgrade safely on top of Feisty. Interestingly, when i run it (Hardy) on live cd i have no gui problems.

---

### Post by PmDematagoda on 2008-11-14
> **garryzn said:**
> Thanks for the response guys

I tried the '/var/log/Xorg.0.log' and '/etc/X11/xorg.conf' and it said "permission denied" on each attempt. I hope i'm not supposed to remember another password.

Help!

Can you post the output of:-
```
ls -la /var/log
```

Also, as mentioned earlier, Ubuntu 7.04 support has been over for quite a long time, so why not upgrade, or do a clean install to Ubuntu 8.04?

---

### Post by garryzn on 2008-11-15
OK! I managed to get the information from the log files, using cat /var/log/Xorg.0.log (it says bash doesn't recognise eg)

and the contents of cat /etc/X11/Xorg.conf

but there are pages of info. How do i post it? do i have to copy it all down on paper, or can i put it on a flash drive or something? Don,t laugh i'm feeling my way here, it took me a hour to discover how to page up and down the text.

if i have to copy it onto paper first is there a specific part you are looking for?

I haven't backed up any of my files, but a clean install of 8.04 is looking more appealing by the minute.

---

### Post by PmDematagoda on 2008-11-15
Are you able to access the Ubuntu installation externally?

---

### Post by nikgare on 2008-11-15
If you can get yourself either a cd of 8.04 or 8.1, you could boot from that, copy out your important files and then install.

---

### Post by garryzn on 2008-11-16
> **nikgare said:**
> If you can get yourself either a cd of 8.04 or 8.1, you could boot from that, copy out your important files and then install.

Now we're getting somewhere. 
I managed to print out some documents that i had neglected to put on hard copy, so i'm much relieved there, but the live cd doesn't recognise my usb flash drive so i can't back up pics and music, but that doesn't worry me too much.

One other thing. 

I use the sent items of Evolution mail as a kind of record of stuff i've sent out. Is there any way i can retrieve that stuff.

---

### Post by garryzn on 2008-11-16
I managed to get Xorg.0.log and Xorg.conf files by running the live cd, copying it onto my usb flash drive abd then opening it in notebook by changing the file extension to .txt The result is very scratchy, see if any of it means anything to you.

Thanks

---

### Post by PmDematagoda on 2008-11-16
This looks interesting:-
```
(WW) VESA: No matching Device section for instance (BusID PCI:0:2:0) found
```

Can you post the output of:-
```
lspci
```

---

### Post by garryzn on 2008-11-17
Hope this helps

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
03:00.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
ubuntu@ubuntu:~$

---

### Post by PmDematagoda on 2008-11-17
Your config file seems to be really messed up, are you using wacom?

Anyway, try this:-
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo X -configure && sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
```
and see if that fixes it.

---

### Post by garryzn on 2008-11-18
> **PmDematagoda said:**
> Your config file seems to be really messed up, are you using wacom?

Anyway, try this:-
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo X -configure && sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
```
and see if that fixes it.

Thanks for persevering with me. I followed your instruction and i got the following.

rendition
imstt
sisusb
glint
neomagic
s3virge
via
nsc
chips
fbdev
vesa
vga

(++) using config file "/home/garry/xorg.conf.new"
Xorg detected your mouse at /dev/input/mice
please check your config if the mouse is still not operational, as by default Xorg tries to autodetect the protocol
your xorg.conf file is /home/garry/xorg.conf.new
to test the server run " X -config /home/garry/xorg.conf.new
cp: cannot stat '/root/xorg.conf.new' no such file or directory

I copied the above by hand as accurately as possible 

Thanks

---

### Post by PmDematagoda on 2008-11-18
Oh, seems like I made a slight mistake. The last part of the command should be:-
```
sudo cp /home/garry/xorg.conf.new /etc/X11/xorg.conf
```
now see if it works.

---

### Post by garryzn on 2008-11-19
Thanks for your help PmD

In a fit of frustration i decided to go ahead and do a clean install of 8.04 as you previously advised. I managed to save most of my files and i figured staying up to date should prevent further problems.

Thanks again, Garry

---

### Post by PmDematagoda on 2008-11-19
> **garryzn said:**
> Thanks for your help PmD

In a fit of frustration i decided to go ahead and do a clean install of 8.04 as you previously advised. I managed to save most of my files and i figured staying up to date should prevent further problems.

Thanks again, Garry

No problem, sorry I couldn't solve your X problem though.

---

