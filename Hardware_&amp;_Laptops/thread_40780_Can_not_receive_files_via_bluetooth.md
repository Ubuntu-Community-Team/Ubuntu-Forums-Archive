---
title: "Can not receive files via bluetooth"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by hesee on 2005-06-10
Hi,
I've been trying to send files from my nokia6230 to ubuntu pc and cannot get it working. I can search devices from phone and it finds ubuntu-0, i can pair them but cannot send files, then phone then says: no devices found(or something, don't know exactly in english). 

I made the binding (not exactly sure what it does) to my phone address to channel 10:

sudo rfcomm bind /dev/rfcomm0 MY_PHONE_ADDRESS 9

Does anyone know is this right channel, because in some debian howto they were using this and in ubuntu howto they were using ch. 10? If i should try with differerent channel, how can i change the channel? If anyone can send files from noki6230 to ubuntu, please let me know so i know that it's possible, Thanks!

---

### Post by saitoh on 2007-10-27
Ever since I upgraded to Gutsy I have not been able to receive bluetooth files from other devices. I can however send files to other devices.

I installed the obex apps:

sudo apt-get install gnome-vfs-obexftp obexftp obexpushd

and whether or not I have bonded the device using the bluetooth manager in gutsy I can see and send files to it using the following:

To locate nearby bluetooth devices
obexftp -b

Then to send the file to the address of the device you want from the list obtained from above command.
obexftp -b address -p thingIWantToSend

Supposedly I should be able to receive files using
obexpushd -B
however it doesn't seem to work correctly.

Sorry I couldn't answer your exact question, but I hope this at least helps.

---

