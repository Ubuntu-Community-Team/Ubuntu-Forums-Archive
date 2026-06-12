---
title: "No programs can see BT GPS data, but cat /dev/rfcomm0 works"
date: 2013-07-17
forum: Hardware
---

### Post by smssms on 2013-07-17
I have a generic bluetooth GPS receiver connected to my Sony Vaio (via Blueman 1.23) running 12.04 LTS 64-bit.

I can display the steaming NMEA data with ```
cat /dev/rfcomm0
``` but that is about it!

I have tried all sorts of live GPS programs e.g. GPSD, XGPS, FoxtrotGPS, GPS Drive, GPS Prune, Viking, etc But _none of them ever show *any* GPS data or sort of connection to the unit_. I've also tried 'chmod of /dev/rfcomm0 to 777', run gpsd at root, use /dev/ttyS0, configuring GPSD, run GPSD -b, and other tips I've found on-line. 

The nearest I've got to doing anything useful is using 'awk' to pull some relevant bits out of the streaming data from /dev/rfcomm0.

**Has anyone got any ideas on how I can get programs to 'see' and use my bluetooth GPS data?**

---

### Post by Cheesehead on 2013-07-17
Well, some of those applications rely upon gpsd. xgps, for example, cannot use NMEA data.

So what happened when you told gpsd to use /dev/rfcomm0 ?
Nothing?
An error message?

---

### Post by smssms on 2013-07-18
When I try ```
gpsd /dev/rfcomm0
``` nothing really happens, the terminal just goes back to the input prompt after a couple of seconds. No error messages. Then when I start xgps, it starts but there is no data/inputs into any of the boxes. Same results if I try both/either as root too. I also went through the gpsd configuration process, but no results from that either. 

Also no output from ```
gpsmon /dev/rfcomm0
```

---

### Post by Cheesehead on 2013-07-18
Have you checked the hardware compatibility list on the gpsd website?

Are you sure the device is sending NMEA 0183 strings, or any format recognized by gpsd? Could it be sending some other (proprietary) format? 
See man gpsd and gpsd -l for the list of recognized formats.

Have you tried gpsd's -b (read-only) flag? That's sometimes handy with bluetooth.

---

### Post by smssms on 2013-07-18
Well, it is a cheap generic unit (Copilot ms3) so does not appear on the hardware compatibility list of gpsd 

The spec says it puts out NMEA by default but can be programmed to give SIRF(?), looks like NMEA to me ```
$GPGGA,075240.556,5514.5370,N,00116.1377,W,1,09,2.9,-47.6,M,47.5,M,,0000*5C
$GPGSA,A,2,18,26,24,,,,,,,,,,3.1,2.9,1.0*30
$GPGSV,3,1,12,26,50,124,26,24,42,261,22,18,30,301,29,15,75,270,*7F
$GPGSV,3,2,12,28,39,054,22,09,19,074,,17,17,107,22,27,12,033,*78
$GPGSV,3,3,12,08,08,070,16,22,08,326,,12,07,203,,05,05,179,*7F
$GPRMC,075240.545,A,5514.5370,N,00116.1377,W,2.33,32.28,170713,,,A*42
$GPVTG,32.28,T,,M,2.33,N,4.3,K,N*3C
``` But I will look at the format in more detail to check. 

I did try ```
gpsd -b
``` - no results.

```
sudo cgps /dev/rfcomm0
``` does not work either, but it is the first one to give an error message, it says: ```
{"class":"ERROR","message":"Can't assign /dev/rfcomm0"}
```

---

### Post by smssms on 2013-07-19
[COLOR=#808080]Could this be a/the problem:

I do not seem to be a member of the **dialout** group. ```
[I]$ groups

$ name [/I]adm cdrom sudo dip plugdev lpadmin sambashare usrp
```

But when I try ```
sudo usermod -a -G dialout *name*
``` and then run 'groups' again, nothing has changed.

Do I need to be a member of dialout? If so, how do I add myself to that group?

Mind you; ```
$ id [I]name

$ [/I]uid=1000(*name*) gid=1000(*name*) groups=1000(*name*),4(adm),**20(dialout)**,24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare),1001(usrp)
``` makes it look like a AM a member of dialout - confused??????[/COLOR]

---

### Post by smssms on 2013-07-19
**Close to just giving up!** :mad:

I've just tried uninstalling gpsd and gpsd-clients to enable me to connect OpenCPN directly to the data on /dev/rfcomm0

Guess what - exactly the same, can still see the data streaming with sudo cat /dev/rfcomm0 but OpenCPN sees NOTHING* when I point it to /dev/rfcomm0

_I think bluetooth just does not work with the Ubuntu/Sony Vaio combo_. Even when I connect my Samsung Galaxy to my Vaio via bluetooth, it all looks ok until you try to send a file; it always fails...

*While in OpenCPN I tried all sorts of baud rates, calling "rfcomm0" "ttyS0" instead, the "ignore NMEA sentences" option, Show NMEA data, do/don't control checksums, etc

---

