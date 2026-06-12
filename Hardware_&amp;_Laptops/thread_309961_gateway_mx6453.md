---
title: "gateway mx6453"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by stabface on 2006-11-30
[EDIT]

I have finally after much searching and head banging found out how to get the wireless card working under EDGY 

in this help post it goes to show you how-to get the card working with ndiswrapper. 

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")


there are few things i had to change to get this to work. 
 first make sure you follow all of the steps, configure and installing from source. 
[U][B]
second use ndiswrapper 1.28 [/B][/U]
for 1.29 gave me and error saying it could not find the device. 

i tried the driver from gateway first but ran into problems the HP driver in the how works great though. 

i attached the .inf file for you if you have a slower connection and don't want to download the whole driver and cabextract the .exe 

any way

lastly and most important. 


ubuntu found my card as eth1
so i had to edit 
/etc/iftab 
i made a backup just in case. 
edited the file to read 
after deleting the eth0 and eth1. ( dont worry after reboot eth0 will still work ) 
[



lo
wlan0
 

]



after finishing all of the steps up to step 7 edit the file above

and restart show be configured and working

---

### Post by mekas2024 on 2007-01-12
Hi pal, thx for this solution i will try with this in a while, but i wish to know if u have the same problem as me with the sound... i have no sound :S and i dont know how to fix it :S... do u have the same problem? do u have a hda-intel sound card??

Thanks bro

regards

MeKaS

---

### Post by mekas2024 on 2007-01-14
HELL YEHAAAA

Thank You sooo much bro, i already have wireless working!!! :D

Im happy now !! but i will be really happy if i get sound working!! if u have any idea or something to make it work please let me know, i apreciate!

Regards

MeKaS

---

