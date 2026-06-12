---
title: "Epson SylusPhoto R265 driver"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by grimreaperwithalawnmower on 2007-01-06
Hey chaps,

I bought a brand spanking new Epson StylusPhoto R625 today and have had a bugger of a time getting it to work.  But there are some geniuses on here who I'm sure can help me.  I've done what's on this forum: [http://forums.freestandards.org/read.php?26,400](http://forums.freestandards.org/read.php?26,400) with no success (I'm the user "Matt_K" btw) so any other suggestions are most gratefully received.

Usual specs: Edgy, Gnome, as up to date as I see possible etc etc

Cheers
Matt

---

### Post by gatiba on 2007-01-11
Hi!
I'm using an Epson r265 with the Epkowa Lite drivers ( [http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm) )...
For now it's supporting just basic settings, but... Hey!... I can print! ;)

---

### Post by F43RY on 2007-02-14
Hi,
I've a problem with setup of Epkowa.
The procedure tells:
> lpadmin -p printer_name -E -v ekplp:/var/ekpd/ekplp0 -m ppd_file

Where can I find the ppd_file? Sould I build it in someway?

Please, could you explain it to me step by step? My printer doesn't work with any gutenprint driver.

I'm using edgy


Thx in advance

---

### Post by gatiba on 2007-03-01
First of all sorry F43RY for the my absurd delay on answering you... And sorry for my very bad english!
Here are some instructions:

1) download the driver from the link in my reply above. Be sure to download the **RPM version**.
2) Install **alien** with:
```
sudo apt-get install alien
```
3) Convert the rpm file into deb using:
```
sudo alien -d --scripts **name_of_the_rpm.rpm**
```
4) install the deb:
```
sudo dpkg -i **name_of_the_rpm.deb**
```
5) install some libraries we need later:
```
sudo apt-get install libgtk1.2
```
6) run this script:
```
 sudo /usr/local/EPAva/LITE/setup
```
Answer some questions and you are quite ready to go...
7) run this other script:
```
sudo /usr/local/EPAva/LITE/pipslite-install
```
And you'll create the PPD file requested from CUPS.
Now install the printer using the Add printer tool in Gnome and choose EPSON->Name_you_give_the_printer_using_the_setup_above

Enjoy your new Epson r265! :D

---

### Post by yahooadam on 2007-06-29
> **grimreaperwithalawnmower said:**
>  I've done what's on this forum: [http://forums.freestandards.org/read.php?26,400](http://forums.freestandards.org/read.php?26,400) with no success (I'm the user "Matt_K" btw) so any other suggestions are most gratefully received.
just a quick note, while visiting that forum i got a lovely virus warning

---

