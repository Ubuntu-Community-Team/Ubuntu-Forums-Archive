---
title: "install fail 10.10 UNR Asus ee pc 701"
date: 2010-10-23
forum: Hardware
---

### Post by nobodie on 2010-10-23
First prep details:
This is a first gen Asus sold in China with xp and bought 2nd hand 1.5 years ago. I have previously installed UNR 10.04, fedora 13, fedora 12, easy peasy, jolicloud, and probably others that I don't recall.

Install medium: reliable kingston USB pendrive, 4Gb with 10.10 UNR downloaded from the Ubuntu repos and installed in drive with UNetbootin using my fedora 14 desktop system. All this is SOP for me and I handle this kind of thing often (but not daily). The ISO was md5sum (ed)with the sum given on the ubuntu hash page. Everything checked.

Other notes: I just had this in for a battery/ charging problem and they tore the thing apart and rebuilt it, selling me a new charging block and wires (the real problem, $7.50)  and something else on the system board (can't read the damn receipt in illegible Chinese, @ $50.00 but while it wasn't the problem i took it in for, there was, apparently , a problem with it) 

The existing OS: UNR 10.4 still boots up and runs fine, no problems at all. I could continue to use it without difficulty and will unless i can solve this or decide to switch it back to fedora or some other linux just for the fun of it.

The problem: Booting off the Kingston medium fails. The first error is: 
immediately after choosing the default boot mode:
"undefined video mode number: 314"

i press <enter> to see the choices and they do, indeed, not include 314.
They do not, also include any 800x480 screens which is what the specs for this screen are. choosing any of the available choices gives a crash into busybox that suggests a problem finding init scripts as well, perhaps because of the display failure. 

Since the hash checks it obviously isn't the iso, so what is up with this? this is a 4G variety, but not exactly the "surf" that was sold in the US and Europe. Still I have installed lots of different things in it and it is functioning just fine right now and i was just updating it. The straight up update doesn't work because there is not enough space in the drive to do it (common problem for this machine, actually i think it is possible that this is really a 2G jacked to say it is 4G: this is China)

Ideas?
Thanks in advance

---

### Post by BradP on 2010-11-05
I had the same error message using a 1GB Kingston DataTraveler trying to install to the EeePC 701SD.  I had created the USB using Unetbootin.  When I created the USB again like it told me to on ubuntu.com using Universal USB Installer 1.8.1.0 everything worked fine.

---

