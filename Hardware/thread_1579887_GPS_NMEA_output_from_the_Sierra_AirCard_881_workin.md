---
title: "GPS NMEA output from the Sierra AirCard 881 working"
date: 2010-09-22
forum: Hardware
---

### Post by mikehattingh on 2010-09-22
Couldn't find an explanation of how to get the GPS working on this card, so after a long night here it is.
Note: This is the 881 not the 881u, the 881 is a pcmcia version, as apposed to USB, but it's all USB in the end.

**Procedure: **
- Establish a connection to the serial ports on the card
- Find the names of the new com ports
- Install a terminal emulator
- Start tracking
- Option Reset the card

**Establishing a connection:**
Insert the card   
In a terminal run
```
~$ lsusb
```
      
Note the ID numbers of the card
In my case "ID 1199:6851 Sierra blah blah"
Using the numbers you obtained above, run
```
~$ sudo modprobe usbserial vendor=1199 product=6851
```
   
   
**Find the names of the new com ports**
run
```
~$ dmesg
```
      
The result should contain something about "...Sierra USB modem converter now attached to ttyUSB0 ...ttyUSB1 ...ttyUSB2 ...ttyUSB3"
    
**Install a terminal emulator**
I used minicom, run:
```
~$ sudo apt-get install minicom
```
       
**Start tracking**
in my case the AT command port for the card ended up being /dev/ttyUSB2. My NMEA port is /dev/ttyUSB3.
In a terminal start minicom:
```
~$ minicom -s
```
   
Pick "Serial port setup" 
Change "Serial device" to /dev/ttyUSB2 -hit enter, and enter again
Pick "Exit" - hit enter
   
The modem should initialize and the card will say "blah blah blah OK"
Enter the AT command:
```
AT!GPSTRACK=1,255,50,1000,1
```
   
Theres a description of AT!GPSTRACK in [[COLOR="Navy"]here[/COLOR]]("http://developer.att.com/devcentral/Docs/Sierra_Wireless_AirCard_890_Developer_Guide.pdf")
Open another terminal and use minicom to test the NMEA port. In my case ttyUSB3.The card should be printing out something. If it doesn't have a fix it still seems to print empty entries every second.
Close minicom -- ctrl + a then x --
   
Point your software at the NMEA port.
Try to get lost :P
   

**Option reset the card**
When I was trying to get this working one of the things I did was to reset the card. I don't know if it's necessary, and I haven't needed to do it again. Anyway the AT command is:
```
AT!GRESET
```
      
Card says "OK" then gos through a power cycle
the ports get reassigned and minicom loses its connection. after restarting the PC the port names went back to 0,1,2 and 3 
      
   
Thanks to:
[http://developer.att.com/devcentral/Docs/Sierra_Wireless_AirCard_890_Developer_Guide.pdf](http://developer.att.com/devcentral/Docs/Sierra_Wireless_AirCard_890_Developer_Guide.pdf)
[http://forums.reprap.org/read.php?12,4546](http://forums.reprap.org/read.php?12,4546)

---

