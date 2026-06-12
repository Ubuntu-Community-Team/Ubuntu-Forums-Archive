---
title: "Toshiba laptop atheros wifi"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-02-19
Hello I have 6.10 Ubuntu installed and everything works except the wireless portion.  Here are the specs.

Toshiba Satellite A135-S2446 laptop.
Atheros AR5BXB61 wireless card.  The orange light is on and that should mean that the wireless card is powered up.

I installed the restricted modules 2.6.17-11 and the wireless card still does not work.  I have tried both the -386  and -generic kernels to no avail.  The restricted modules are supposed to work with Atheros madwifi.

What to do to get it to work?

Thanks

---

### Post by Turmoyl on 2007-02-19
Try this:

sudo modprobe -r ath_pci
sudo modprobe ath_pci
sudo iwpriv ath0 mode 2

Then use the card as normal, i.e. attempt to gain a DHCP assignment.

---

### Post by stchman on 2007-02-19
> **Turmoyl said:**
> Try this:

sudo modprobe -r ath_pci
sudo modprobe ath_pci
sudo iwpriv ath0 mode 2

Then use the card as normal, i.e. attempt to gain a DHCP assignment.

I tried and I get:

ath0        no private ioctls

I then check the Network settings and there is no wireless present.

If I do an lspci at the terminal I get the following:

02:00.0 Ethernet controller: Atheros Communications, Inc.  Unknown device 001c (rev 01)

Thanks

---

### Post by stchman on 2007-02-19
It has to be right under my nose.

---

### Post by buMPer on 2007-04-17
> **Turmoyl said:**
> Try this:

sudo modprobe -r ath_pci
sudo modprobe ath_pci
sudo iwpriv ath0 mode 2

Then use the card as normal, i.e. attempt to gain a DHCP assignment.

This worked like magic to me.  Sometimes the answer to the most difficult problem is the simplest one.  After the reboot, everything went perfect.

Kids, always remember, when you toy with modprobe, make sure you REBOOT to make it work.

Thanks turmoyl!


bumper

---

### Post by zoetrope666 on 2007-04-17
I have a similar problem with my WiFi on my Toshiba Portege 4010. Sometimes it works, sometimes it doesn't.. and it has nothing to do with signal. The Wifi is built in in this model. I'm not really sure what's wrong with it. I use Dapper, too. If anyone has the same model and has figured out how to get their Wifi working, I'd love to hear from you.

Cheers

---

### Post by jimbob on 2007-04-17
I began to have a problem with my Toshiba/Atheros when I did the latest Edgy upgrade and the kernel changed from 2.6.17-10-generic to 2.6.17-11-generic.  Everything wireless that had been working fine stopped working completely.  If I rebooted the previous 17-10 kernel everything was fine again.

When I did an lsmod on the 17-11 kernel I found the following modules were completely missing - wlan_scan_sta, ath_pci, ath_rate_sample, wlan, and ath_hal.  No wonder nothing works.

Does anyone know if there is a bug report on this?  I haven't tried the fix listed above yet but will report my findings when I do.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

