---
title: "PDA sync with Ubuntu Feisty"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by _marco_ on 2007-08-27
Hello to everyone, this is my first post and i'm going to annoy you all with my problems :lolflag:
I bought an Asus A639 (with WindowsMobile 6 pre-inst) like my first PDA: GPS works fine in OziExplorerCE and CompeGPS, very large connectivity with all features available in this model also if there are some problems in tuning phases.... Problems come when syncing with Ubuntu as is, i tried to install all packages found and named in internet (this forum, blogs, web pages, guides, etc.) like gpilot, multisync, jpilot but i have found no solutions.
After command

[COLOR="Blue"]# sudo tail -f /var/log/messages[/COLOR]

and inserted the A639 in the dock, i discovered in which device Linux is mounting the peripherals (ttyUSB4 for example) so i configure it in all apps... starting the application chosen at the moment, PDA freezes saying "Connecting to host"!!! Aborting the connection on A639 and disconnecting it i can re-utilize my PDA.

Also trying with synce
 
[COLOR="Blue"]# marco@marco-laptop:~$ sudo synce-serial-config /dev/ttyUSB4

# You can now run synce-serial-start to start a serial connection.          

# marco@marco-laptop:~$ dccm -f
# dccm[19525]: Running in foreground
# dccm[19525]: Listening for connections on port 5679                           
[/COLOR]
terminal app freezes waiting input... Ctrl+C and then

[COLOR="Blue"]# marco@marco-laptop:~$ sudo synce-serial-start

# Warning!

# synce-serial-start cannot find the dccm process.
# Without dccm your PPP connection will soon terminate!


# synce-serial-start is now waiting for your device to connect
[/COLOR]
but no solution at all.... I'm newbie in Linux maybe i can made some error :confused:


[I]OS: Linux Ubuntu Feisty Fawn 7.04
PC: Packard-Bell Easynote mv85-005d
   Intel Core2 duo T5600 - 1Gb Ram - 120Gb HDD SATA - ATI Radeon Mobility X1600
   connected to internet by Option Globetrotter HSDPA Express Card - usbserial module (sorry no ADSL available in my city - Italy is the Digital Divide's country)
[/I]
Anyone could help me? Someone has experienced my problem yet? I don't want to use Microsoft Active Sync.....


P.S. probably my english is not correct at all, sorry for this. :popcorn:

---

