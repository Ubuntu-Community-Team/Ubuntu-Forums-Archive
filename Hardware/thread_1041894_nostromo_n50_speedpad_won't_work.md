---
title: "nostromo n50 speedpad won't work"
date: 2009-01-17
forum: Hardware
---

### Post by MrCr0 on 2009-01-17
So I was trying to get my [[color=blue]nostromo n50 speedpad[/color]](http://web.archive.org/web/20060612232943/http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=2071&pcount=&Product_Id=107727&Section.Section_Path=/Root/Nostromo...ingTools/) working on my laptop. I followed the instructions [[color=blue]here[/color]](http://ubuntuforums.org/showthread.php?t=538319). 


[quote="[Ironlenny](http://ubuntuforums.org/member.php?u=357335)"]Here is the steps I took to install my Nostromo n52 on Kubuntu 7.04, but these instructions should still be valid for all flavors of Ubuntu, and the entire line of Nostromo products.

First download the Nostromo linux (nostromo_n50-1.3.tar.gz NOT nostromo_driver-0.1.3.tar.gz) driver from [http://sourceforge.net/project/showf...ease_id=382235](http://sourceforge.net/project/showf...ease_id=382235)

Then download and install these dependencies:
libxtst-dev
g++
libgtk2.0-0
libxml++2.6-dev
fluid
libfltk1.1-dev
libxtst-dev
libgtk2.0-dev

type:
sudo modprobe evdev (please make sure that your speed pad is not plugged in)
sudo chmod a+rw /dev/input/event1

unpack nostromo_Driver-0.1.3.tar.gz
cd into the directory

Next type:
sudo ./configure
sudo make
sudo make install

Once you have install the driver, plug in your device before running the daemon and type:
nostromo_config

You need to run nostromo_config before running nostromo_daemon

You need to create a profile for your device before you can load the driver. Simple saving an empty profile will do.

Now type:
sudo nostromo_daemon

You should see an icon in your system try, and the mode lights on your device should cycle.

I hope this is helpful and I would appreciate any feed back. Specific feed back that I would like includes whether or not the alternate install method works, is automake1.9 necessary, and how to uninstall the driver.[/quote]


When I type "nostromo_config" in the terminal, the key binding configuration menu appears. The configuration profile I made got saved. When I type "nostromo_daemon" in the terminal, nothing happens. No error message, but I still can't use the device. I didn't see anything in "system > preferences" or "system > administration" related to the n50. It all seemed to work fine up until that last step. I am still rather noobish at Ubuntu. Any ideas on getting it to work would be appreciated.

---

### Post by MrCr0 on 2009-01-28
Nobody knows? :frown: Should I have put this thread in the gaming and leisure section?

---

