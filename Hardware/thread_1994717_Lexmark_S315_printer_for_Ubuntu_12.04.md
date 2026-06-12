---
title: "Lexmark S315 printer for Ubuntu 12.04"
date: 2012-06-03
forum: Hardware
---

### Post by Thirup on 2012-06-03
Hello everyone! Yesterday I bought myself a Lexmark S315 printer and I was assured that it is linux compatible, however I've had some problems about installing it. 

I tried installing the driver software from [http://support.lexmark.com/index?page=product&segment=DOWNLOAD&productCode=LEXMARK_IMPACT_S305&locale=en&userlocale=DE#1](http://support.lexmark.com/index?page=product&segment=DOWNLOAD&productCode=LEXMARK_IMPACT_S305&locale=en&userlocale=DE#1) but after installing lexmark-printer-utility-wJRE-1.0-1.amd64.deb I tried running it in Ubuntu software center, it refuses to install it proberly.

Have I picked a wrong file for the installation, or am I doing something else wrong? Hoping someone can help, and I'm willing to give more detailed information, if it's neccesary :)

---

### Post by Thirup on 2012-06-03
bumping... I really need my printer tomorrow, so I really need some help, if anyone can help me

---

### Post by sanderj on 2012-06-03
Which Ubuntu version are you using? So

```
cat /etc/lsb-release

```

.

---

### Post by Thirup on 2012-06-03
Like the headline says, I use ubuntu 12.04 :)

---

### Post by Thirup on 2012-06-03
update so far: I've managed to follow the guide on [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Get_the_Lexmark_printer_drivers_for_Linux](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Get_the_Lexmark_printer_drivers_for_Linux)

Right now I'm stuck at the Lexmark print driver setup wizard, where I'll have to say what the printer type is, but I can't see S315 among the suggestions - can I import it to the list somehow?

---

### Post by sanderj on 2012-06-03
> **Thirup said:**
> Like the headline says, I use ubuntu 12.04 :)

but 32-bit or 64-bit?

---

### Post by Thirup on 2012-06-03
> **sanderj said:**
> but 32-bit or 64-bit?

64 bit

---

### Post by sanderj on 2012-06-03
How is the printer connected: via USB, or Wifi?

If USB, what's the output of "lsusb"?

---

### Post by Thirup on 2012-06-03
It's connected to a usb cable - not sure what the "lsusb" is, but if you mean the connection, it is /dev/usb/lp0

---

### Post by sanderj on 2012-06-03
> **Thirup said:**
> It's connected to a usb cable - not sure what the "lsusb" is, but if you mean the connection, it is /dev/usb/lp0

"lsusb" is the command you should type in a terminal on your Ubuntu system with the usb-printer connected and turned on. It will show the id's of all usb devices.

---

### Post by Thirup on 2012-06-03
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 009: ID 043d:01fa Lexmark International, Inc. 
Bus 001 Device 004: ID 1c7a:0801 LighTuning Technology Inc. Fingerprint Reader
Bus 002 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 005: ID 0489:e011 Foxconn / Hon Hai

---

### Post by sanderj on 2012-06-03
Googling "043d:01fa Lexmark International, Inc." only gives this thread... :(

If you press the superkey (with the Windows symbol), and type "printing", and then select the "printing" program, can you see then see or add your Lexmark S315.

I'm assuming you were able to install the *.deb with the printer driver.

---

### Post by sanderj on 2012-06-03
I had a look at the 33 MB .deb you pointed to, and it looks like a printer_utility only. So not a printer driver.

So back to the main page of Lexmark. If you select Ubuntu 10.04, there are a lot more options. I selected "LINUX_UNIX
PPD (PostScript Printer Description) for CUPS-based systems", downloaded it, unpacked it, and run "sudo ./install_ppd.sh".

Does that help? I haven't got a Lexmark S315, so I can't test it for you. The printers I have, are just recognized by Ubuntu by plugging them in ...

---

