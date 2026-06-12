---
title: "sakis3g not connecting"
date: 2011-08-18
forum: Hardware
---

### Post by Iqbal_ on 2011-08-18
Hi,

I have a usb modem of Micromax no mmx 352G and a laptop with 64bits and Natty thereon.

I tried to use sakis3g to connect to internet through the usb modem. Whrn I run sakis3g (64 bits) and chose the option Connect to 3G, sakis3g switches, prepares and other steps successfully. In the last step it a message box shows Connecting.... then Connecting (Second Attempt)..... finally it shows Failed.

I am using these settings

./sakis3g --interactive usbdriver=option usbmodem="1c9e:9605" APN="pps3g"

or

./sakis3g --interactive --pppd usbdriver=option usbmodem="1c9e:9605" APN="pps3g" 

or

./sakis3g --interactive --noprobe usbdriver=option usbmodem="1c9e:9605" 
APN="pps3g"

None of the above settings work.

How to connect using sakis3g?
Any other way to connect!

---

### Post by chandra2730 on 2012-09-23
Open terminal
type the following codes
"sudo gedit /etc/modules"

and then at the end of the line
type this

"usbserial
option"




and then restart your computer and connect the modem
then you'll see your modem
now create a new mobile broadband profile clicking on the edit connections and add new on mobile broadband tab
you must put RIGHT APN for your carrier


for
Indian carriers


TATA DOCOMO=tata.docomo.internet
AIRTEL=airtelgprs.com
AIRCEL=aircelweb
BSNL=bsnlnet
VODAFONE=www
VIRGIN MOBILE=vinternet.in





---------THIS WORKS FOR MY MICROMAX 352G MODEM WITH UBUNTU 12.04.

---

