---
title: "modem  - hangup (SIGHUP)"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by pugrit on 2005-03-23
i've done some reading in here and was abled to solved winmodem driver instalation, and read more about connecting to the net. but still i cant connect. i hear  the modem sounds. but it wont connect when i clicked on activate:

heres is the var/log/messages:

:pppd2.4.2 started by root, uid 0
:serial connection established
:using interface ppp0
:connect ppp0 <--> /dev/modem
:Hangup (SIGHUP)
:modem hangup
:connection terminated
:terminating on signal 15
:exit

tried also setting it in pppconfig. then sudo pon (provider_name) but i dont here any sound at all.

im on a dualboot and in windows my modem is on com3.  i think im close in solving this ready since i could here the modem sound but i guess i missed something. any suggestions?help please.

by the way, what does "serial line is looped back" mean? thast the mesages when i click on 'autodetect' 

thank you very much.

---

### Post by az on 2005-03-23
What kind of modem is it and what driver are you using?

Did you leave out any entries from your /var/log/messages?  Also, the times would be helpful since they can give an idea about the timing (duh! What a sentence!) of certain things.

---

### Post by pugrit on 2005-03-23
puresoft pci v.92 fax/modem

im using the linuxant modem.

i can dial but wont connect.

---

### Post by pugrit on 2005-03-24
this is the command i did and its corresponding logs.

**********

pugrit@DigitalFart:~ $ sudo pon provider

Mar 24 10:04:00 localhost pppd[3755]: pppd 2.4.2 started by root, uid 0

Mar 24 10:04:02 localhost pppd[3755]: Exit.

**********

pugrit@DigitalFart:~ $ sudo wvdial

--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

**********

computer
system configuration
networking 
modem port (/dev/modem)


Mar 24 10:16:07 localhost pppd[5150]: pppd 2.4.2 started by root, uid 0
Mar 24 10:16:08 localhost pppd[5150]: Serial connection established.
Mar 24 10:16:08 localhost pppd[5150]: Using interface ppp0
Mar 24 10:16:08 localhost pppd[5150]: Connect: ppp0 <--> /dev/modem
Mar 24 10:16:10 localhost pppd[5150]: Serial line is looped back.
Mar 24 10:16:10 localhost pppd[5150]: Connection terminated.
Mar 24 10:16:11 localhost pppd[5150]: Exit.

**********

after it ends, when i click activate again, nothing happens.
and also in windows my modem is on com3 and i believe its ttyS2 in ubuntu. i tried to use that in modem port and the same, it dials but wont connect.

---

### Post by jllitvay on 2005-04-06
I have the same problem with my USR2976 hardmodem. I got a script that make linux detect, dial, make noise but do not connect.

Any help?

---

