---
title: "HP Deskjet 3050A connect issue"
date: 2013-12-11
forum: Hardware
---

### Post by plaxton on 2013-12-11
Hello,

I am trying to connect my laptop to my home network printer by wi-fi. I had this thing working at some point in the past, but can't seem to connect to the printer anymore. I've gone into CUPS, and it shows my network printer. When I try to print a test page, I get a message saying "usr/lib/cups/backend/hp failed". Not sure where to go from here. Any help would be appreciated. I'm using Ubuntu 12.04 LTS

---

### Post by squakie on 2013-12-12
Are the hp packages installed?  If you have already, installl Synaptic package manager via:

sudo apt-get install synaptic

then open it the menus.
 
Put hp in the search string - see what is installed.  I belive hplip also gives a gui.  You should be ablt to go to printers and if your printer is't shown add a networked printer - it should then come up in a list for you to select.

---

### Post by plaxton on 2013-12-12
Yes. HPLIP was already installed. I even removed, then reinstalled it. That doesn't seem to be the problem. I don't know if I need samba, but I will check later to see if it's on my laptop. It is on my box.

---

### Post by plaxton on 2013-12-12
Just to be clear, I can use the printer no problems on my desktop (box), but my laptop, when connected by LAN or Wireless can 'see' the printer; I just get an error when trying to print to it.

---

### Post by squakie on 2013-12-12
It is a wireless printer, correct?  If you have it hard-wired to another computer or to a LAN in your home then that's a little different matter.

---

### Post by plaxton on 2013-12-13
It is connected by USB to my box. But I can connect to it wirelessly with other devices.

---

