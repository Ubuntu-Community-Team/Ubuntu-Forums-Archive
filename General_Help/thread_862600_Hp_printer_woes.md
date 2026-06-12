---
title: "Hp printer woes"
date: 2008-07-17
forum: General Help
---

### Post by tigernerd on 2008-07-17
I have a Hp printer, a deskjet 3940.

Can't see it in printer configuration.

In short, I'm stuck

---

### Post by bmac on 2008-07-17
You probably need to install the HPLIP printer driver. See enclosed site. I used the Self-Extracting Archive with the Auto Installer and it worked perfectly.

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Hope this helps.......

---

### Post by cybrsaylr on 2008-07-17
There are so many printer models.
I had the same problem. I just picked the model number that matched the closest and tried it and it worked out OK. 

I have a couple dual boot PCs with Windows & Ubuntu.
Funny thing is the 'ink level indicators' no longer work on Windows but they show the proper ink level readings on linux, after I installed the HP Toolbox from the Add & Remove section.

---

### Post by jonian_g on 2008-07-17
> You probably need to install the HPLIP printer driver.

To install it. Open a terminal and type:

```
sudo apt-get install hplip
```

Your printer is supported. I just checked it ;)

---

### Post by ramjet_1953 on 2008-07-18
Don't forget that to successfully use [COLOR="Blue"]hplip[/COLOR], you also need to install the [COLOR="Blue"]Python-QT3 bindings[/COLOR].

[COLOR="Red"]sudo apt-get install python-qt3[/COLOR]

When both [COLOR="Blue"]hplip[/COLOR] and [COLOR="Blue"]python-qt3[/COLOR] are installed type this in a terminal:

[COLOR="Red"]sudo hp-setup[/COLOR]

A window will then open and guide you through your printer's installation.
It will then print a test page.

now type this in a terminal:

[COLOR="Red"]hp-toolbox[/COLOR]

A window will open, giving you access to all of your printer's options and maintenance facilities.

Regards

---

### Post by Mattevt on 2008-07-28
I followed all instructions, but my HP 3940 is on a network...It's shared and I can see it in Printer Configuration (Windows Printer via Samba), but after I do sudo hp-setup and select "Network/Ethernet/Wireless" it tells me no printers were found.

The printer is shared and the network is open.

---

### Post by Camilia on 2008-08-25
Have you tried turning it on and see if it is recognized by your computer. I have hp deskjet printer 3930 and all I had to do was turn it on.

---

