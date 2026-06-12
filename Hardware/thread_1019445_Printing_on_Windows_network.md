---
title: "Printing on Windows network"
date: 2008-12-23
forum: Hardware
---

### Post by gwatts on 2008-12-23
If a manufacturer's Linux printer driver is installed, can a Ubuntu computer then print through a Windows PC network? 

Specifically I am looking for a Ubuntu supported laser monochromic wireless multifunction device for a Windows network.

Thank you.

---

### Post by MeURi on 2008-12-23
Well, the answer is yes, both if you want to print to a Windows shared printer, and if you want to print from Windows to a printer shared by Ubuntu.

In the latter case, you have to install Samba in Ubuntu and configure it to meet your needs. If youre afraid of editing configuration files by hand, you can try to use "system-config-samba": it's a GUI for configuring Samba, available through the repositories.

In the former, you have to configure just CUPS to use a shared printer. Yet I'm not able to tell you how to do this, 'cause my printer is attached to my pc. It should be straightforward, though.

---

### Post by gwatts on 2008-12-24
Thank you for your comments. Do think I would be safe buying any Lexmark of Brother device for which a Linux driver is made.

Are additional driver's required for scanning, copying, and faxing functions.

Brother for example, does have several devices with Linux  driver's but is that the whole story?  Would you expect all the functions to function properly?

I most sincerely appreciate your advice.
gwatts

---

### Post by MeURi on 2008-12-24
I'm sorry I cannot give you any advice on this.

I have a Brother laser printer, and works just fine (recognized by Ubuntu and automatically set up after being plugged with usb cable). But I have never had multi-function products, so I don't know if everything works fine in Ubuntu. Also, I've been using linux for 4 years, and bought my printer about one year earlier, so my experience with drivers and printing in general is quite poor.

I hope to hear other users' opinions on this topic.

---

