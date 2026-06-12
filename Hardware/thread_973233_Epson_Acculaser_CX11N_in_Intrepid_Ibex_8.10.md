---
title: "Epson Acculaser CX11N in Intrepid Ibex 8.10"
date: 2008-11-06
forum: Hardware
---

### Post by kWahab on 2008-11-06
I have the CX11N connected to my network and have finally managed to get it working (both printing and scanning) in 8.10 (32-bit). The usb setup should be similar but I haven't really tried it.

Make sure the network interface of your printer is enabled and it is connected to your network.

This is a mere compilation. I found all of the following on
[http://www.gedda.info/?p=132](http://www.gedda.info/?p=132)
so thanks to everyone there. :)

Here are the steps involved.
1. Go to [http://www.avasys.jp/lx-bin2/linux_e/mfp/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/mfp/DL1.do) for the Epson CX11N driver.
2. choose your model and fill in the required details. I chose distribution: others,  version: others.
3. Download Epson-ALCX11-filter-1.1.tar.gz for CUPS
4. install required dependencies and build environment (some might already be installed on your system)
```
sudo apt-get install libcups2-dev build-essential libstdc++5 bc
```
5. in the terminal cd to the directory/folder where you downloaded the tar file and type this
```

# tar -zxvf Epson-ALCX11-filter-1.1.tar.gz
# cd Epson-ALCX11-filter-1.1
# ./configure
# make install

```
6. Now the driver is installed and you can simply add the printer using the System > Administration > Printing menu. Your printer should show up in the list when you click add new printer button. select it and just click forward, the recommended driver is already selected so click forward and finish adding the printer. You may get an error about pstoalcx11.sh not installed, don't worry :)
7. Now copy the files alcx11 and pstoalcx11.sh from /usr/local/bin to /usr/lib/cups/filter
```
sudo cp /usr/local/bin/*cx11* /usr/lib/cups/filter/
```
8. It Works! that's what I said when i tried a test print. Hope you find yourself in a similar situation. The scanning just worked when I tried it using xsane. There is a scanner driver/software available from the avasys website but i didn't try it.

---

### Post by ubuntom on 2009-01-18
i did exactly what you supposed. The file are in the right directories id pstoalcx11.sh is in usr/lib/cups/filter. I checked it several times!
 when i tried to print it said that pstoalcx11.sh was not installed! how is that possible?

---

### Post by kWahab on 2009-02-07
Well i'm not really sure, but maybe something is wrong with the permissions of pstoalcx11.sh
everyone should have read permission on it.

---

### Post by karismatic on 2009-04-14
Changing the permissions of the files to 755 solved it for me.

---

### Post by littlehouse on 2010-05-09
Hi.
I use this procedure yesterday and it works also in 10.04.
Thanks.

No I would like to make work the scanner in a way that is controlled by the printer panel so the pc will receive a pdf in a folder.

Is there someone has done this?

Thanks

---

### Post by ubuntom on 2010-05-12
hi there,

my acculaser works. already for some time. the system says it misses  <pstoalcx11.sh> but nevertheless, it works. The only problem is the printer is in a network and everytime it starts up it  gets a new ip from the router and I have to find my printer before I can print. How can I let cups search the printer in the network? 

Tom

---

### Post by gn0st1c on 2010-09-14
this procedure didn't work for me (ubuntu 10.04) and after some investigation, i found what was missing for me; libstc++5

1) it's not in repos so you have to download from
[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

2) install
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_i386.deb

3) if you already have cx11 on you printers list, delete it and add it again
socket://printer_ip:9100

4) print test page and it works! :p

---

### Post by jomei64 on 2011-10-23
The procedure perfectly worked for Ubuntu 11.10 (Oneiric Ocelot)

Thanks.

Joe

---

### Post by sviola on 2011-11-28
Works for me in Ubuntu 11.10 also!

Thank you!

---

