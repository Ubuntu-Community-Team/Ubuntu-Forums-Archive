---
title: "Messed up my printer..."
date: 2009-07-02
forum: Hardware
---

### Post by ROY.G.BIV on 2009-07-02
I just got my printer working, but I noticed that it was only printing in B&W, so I selected a different driver(similar, but it was the one I actually downloaded rather than the one from the drop down list) and now my printer doesn't work at all anymore. I assume that I to delete a driver or something, but I don't know how to do that.

My printer is a Lexmark(ah!) X6100, using the Z55 driver. Help?

---

### Post by zepita on 2009-07-02
I had two days of fighting with my printer, I think I learned a lot.

A tip would be to delete the printer from the printers list and then unplug the power cable and usb.

Restart the computer and when in the desktop, plug everything back on. You should get the detected printers screen and you may select a driver.

I hope it helps.

---

### Post by PatrickVogeli on 2009-07-02
So, from the linux-as-only-os poing of view I'd say: give that printer away and get something supported from brother, hp or epson. [www.openprinting.org](www.openprinting.org) can give you more information.

If you can't change the printer now, deleting the printer under System -> Administration -> Printing and then creating a new one should do the job I believe. But be aware you'll have a hard time with that device: printing is B & W only and the scanning function doesn't work.

[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X6100](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X6100)

---

### Post by ROY.G.BIV on 2009-07-02
I tried just deleting it and making a new one, but that didn't work. I'll have to try totally disconnecting, I guess.

And no, I'm dual-booting windows xp, which is what the printer was originally for. Otherwise, I would have bought an HP. I do my hardware research first. 

Well, if my printer will only work in b&w, then there's really no point in even having it work in Ubuntu... I'll have to go over to XP if I want to do any real printing work. Unless I can set up a VM, but I have no idea of how, or even if, I can do that. Linky?

---

### Post by zepita on 2009-07-02
I used to start a virtual windows xp to check my ink levels.
Just get virtualbox and make an iso of your windows xp. It's very intuitive the wizard.

sudo apt-get -y install virtualbox-ose

---

### Post by scrooge_74 on 2009-07-02
> **zepita said:**
> I had two days of fighting with my printer, I think I learned a lot.

A tip would be to delete the printer from the printers list and then unplug the power cable and usb.

Restart the computer and when in the desktop, plug everything back on. You should get the detected printers screen and you may select a driver.

I hope it helps.

You don't really need to reboot, you can just reboot CUPS, open a terminal type

sudo sh /etc/init.d/cupsys restart

You can also manage CUPS from the web browser: in the address bar type localhost:631

---

### Post by ktp on 2009-07-06
> **zepita said:**
> I used to start a virtual windows xp to check my ink levels.
Just get virtualbox and make an iso of your windows xp. It's very intuitive the wizard.

sudo apt-get -y install virtualbox-ose

Printers with wireless/networking, you can check the ink level using the browser.  Lexmark uses linux and has web interface running on port 80.

---

### Post by ROY.G.BIV on 2009-07-12
> **zepita said:**
> I used to start a virtual windows xp to check my ink levels.
Just get virtualbox and make an iso of your windows xp. It's very intuitive the wizard.

sudo apt-get -y install virtualbox-ose

Could I use that to use the scanner and print in color?

[QUOTE=scrooge_74]sudo sh /etc/init.d/cupsys restart[/QUOTE]

I had to use: "sudo /etc/init.d/cups restart" for that to work. Just pointing that out...

---

### Post by bpalone on 2009-07-12
> **ROY.G.BIV said:**
> Could I use that to use the scanner and print in color?



I don't know for sure on your particular printer.  But, I use the PUEL version of VirtualBox and access a printer that Linux doesn't like.  I am networked to it and all my printers for that matter.  But, with PUEL version you can connect via USB which should allow the Windows OS and drivers to work.

Hope that helps a bit.

---

