---
title: "usb keyboard stops to work and works again after unplugging dvb-t usb receiver"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by un1 on 2008-02-02
hello i have following problem:

i have kubuntu guts (7.10) 64bit on my pc.
there is connected an usb dvb-t receiver, here the lsusb description:

Bus 006 Device 003: ID 0ccd:0038 TerraTec Electronic GmbH Cinergy T^2 DVB-T Receiver

my keyboard and mouse is connected through an kvm-switch wich has an usb-connector for connecting to the pc.

i watch tv with mythtv (sometimes kaffeine).

now the backend of mythtv regulary checks the dvb-t device for epg-data.

if i don't turn off the backend, i get the following strange problem after an indefinite time (i don't turn off my pc):

- the keyboard doesn't work anymore on the pc, no reaction on key presses - but the mouse works perfectly! now both mouse and keyboard work perfectly on my notebook..

- the curious thing: when i plug off the cable of the dvb-t receiver from the pc, the keyboard works again!

so i suggest something is conflicting with the usb-devices.. but i have no idea how to find out. 

thank you for help!

---

### Post by zupermanz on 2008-05-16
i have the same problem with a cinergy hybrid t xs usb...
i've googled around but havent found an answer yet.




solved! at least for me:
modprobe em2880-dvb and then plug the device


[https://bugs.launchpad.net/ubuntu/+bug/204578](https://bugs.launchpad.net/ubuntu/+bug/204578)

---

