---
title: "Cannot install HL-2270DW Brother wifi printer"
date: 2018-08-13
forum: Hardware
---

### Post by ubantunovice2 on 2018-08-13
I have Ubuntu 18.04.1 installed within virtualbox on a Windows 10 host.
I cannot seem to install my **wifi Brother HL-2270DW printer** which works fine from the Windows 10 host.
From the ubuntu guest I can connect fine to the internet so wifi connection is not the problem.
I tried to instll a printer from within Ubuntu and what Ubuntu found and installed is a "CUPS-BRF-Printer".
I'm not sure what that is but Libre Office Writer cannot find it to print to.
Any suggestions n how to make Ubuntu find and install my Brother printer?

---

### Post by SeijiSensei on 2018-08-14
Try opening [http://localhost:631/](http://localhost:631/), click the Add Printer button, log in with your credentials, then see if it finds the printer on the network. It needs to have an IP address in the same subnet as the client.

If that doesn't work, go to the support page for your printer at the Brother site and download the Driver Install Tool. You need to unpack the tool from the archive and run it from the terminal using sudo.

---

### Post by ubantunovice2 on 2018-08-14
Thank you for helping.

Inside Ubuntu I opened  [http://localhost:631/](http://localhost:631/) in firefox. Attached image is what opened.
There was no add printer button. Everything else (printers, administration, etc.) gave me a blank page. Not sure why.
Does this indicate where the problem might be?

---

### Post by ubantunovice2 on 2018-08-14
I downloaded the linux-brprinter-installer-2.2.0-1.gz 
How do I run it? Double clicking on it opens its name etc. but does not run it.
(I'm a total Linux newbie)

When I tried to run (install) it in a terminal I got

$ sudo apt install linux-brprinter-installer-2.2.0-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-brprinter-installer-2.2.0-1
E: Couldn't find any package by glob 'linux-brprinter-installer-2.2.0-1'
E: Couldn't find any package by regex 'linux-brprinter-installer-2.2.0-1'

---

### Post by ubantunovice2 on 2018-08-14
I figured out the problem with Firefox. It was an addon.
I downloaded and extracted the gz file and got this

cd Downloads
~/Downloads$ gunzip linux-brprinter-installer-*.*.*-*.gz
jeff@jeff-VirtualBox:~/Downloads$ sudo bash linux-brprinter-installer-*.*.*-* HL-2270DW
[I]Driver-packages cannot be found.
 Confirm the model name.[/I]

jeff@jeff-VirtualBox:~/Downloads$ sudo bash linux-brprinter-installer-*.*.*-* Brother HL-2270DW
[I]Driver-packages cannot be found.
 Confirm the model name.[/I]

jeff@jeff-VirtualBox:~/Downloads$ sudo bash linux-brprinter-installer-*.*.*-* HL-2270DW

It is the correct printer name. It's what I used to find and download the installer.

Stuck there.......

---

### Post by SeijiSensei on 2018-08-15
On *nix systems you cannot run an executable from the directory it resides in wilthout prefixing its name with "./" like this:
```
sudo ./linux-brprinter-installer-2.0.0
```
or whatever the current release number is.

That prohibition keeps users from accidentally executing a file that they think is merely data.

You might need to first make the file executable like this:
```
sudo chmod a+x linux-brprinter*
```

---

### Post by ubantunovice2 on 2018-08-15
You are a great teacher! Thanks sensei.
I did need to use the chmod command and then it worked when I used
sudo ./linux-brprinter-installer-*.*.*-* HL-2270DW

Not intuitive but I had a good sensei.
**How does one thank someone on this forum?**

---

### Post by SeijiSensei on 2018-08-15
You just did.  You're welcome!

---

