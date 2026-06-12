---
title: "Installing wireless HP printer in Lubuntu 20.04"
date: 2020-06-01
forum: Hardware
---

### Post by jamesmck on 2020-06-01
I am unable to figure out how to get Lubuntu 20.04 to recognize an existing wireless HP printer on my home network.  Many posts in my search for an answer mention a printer option in System Tools, but there is no such option on mine.  This is the "Live" version of Lubuntu if that matters.  I would appreciate any guidance, keeping in mind that I am not very expert in anything needing terminal work.  Thanks in advance.
-- James

---

### Post by brian_p on 2020-06-01
Does this existing wireless HP printer have a model name?

---

### Post by DuckHook on 2020-06-01
In addition to brian_p's requested info:

[list=1][*]Make sure that your router is configured to assign a static IP address to the printer.
[*]Record what this IP address is.
[*]```
sudo hp-setup -i ip_address_previously_recorded
```
[*]Answer all the questions that will be asked, making sure that the recommended driver is for the model of your printer.
[*]Because this is a LiveUSB session, these changes will all be lost at your next reboot.
[/list]
Though LiveUSB sessions are great for trying out Lubuntu, they leave much to be desired for setting up permanent things like printers, etc. If you can, running Lubuntu in a VM with bridged networking is more robust and less troublesome.

---

### Post by jamesmck on 2020-06-01
> **brian_p said:**
> Does this existing wireless HP printer have a model name?

It is HP OfficeJet Pro 8210.  Thanks.

---

### Post by brian_p on 2020-06-01
> **jamesmck said:**
> It is HP OfficeJet Pro 8210.  Thanks.

Please post the outputs of ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` ```
driverless
```

---

### Post by jamesmck on 2020-06-02
Thanks for the suggestions, everyone.  It looks like hplip-gui is going to work.

---

