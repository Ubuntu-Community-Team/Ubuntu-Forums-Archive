---
title: "kworld 115 intrepid ibex updated"
date: 2008-11-01
forum: Hardware
---

### Post by Cresho on 2008-11-01
hello!  I am just updating the tutorial for this card.  It is now shorter than original.

we need to fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources. in add and remove programs, under show, select "all available applications"
********************************************************************************
Installing the kworld atsc 115 Driver*******************************************
********************************************************************************

terminal, line by line

--------------------------------------------------------

sudo apt-get install linux-doc-2.6.27 (get the one closest to your kernel look for it in synaptic "linux-doc")

intrepid ibex uses 

cd /usr/share/doc/linux-doc-2.6.27/dvb


others uses
cd /usr/share/doc/linux-doc-2.6.27/dvb
sudo gzip -d get_dvb_firmware.gz
sudo chmod +x get_dvb_firmware
sudo ./get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware
--------------------------------------------------------

reboot!
we are done with driver install

open up "add remove" in applications menu and install "digital television" aka  "metv"

start it up and choose your area then let it scan.  Takes a long time.  after scan, start it up and you can right click on screen to change channel because it opens up a menu with selections.













original is here.
[http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld](http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld)

---

