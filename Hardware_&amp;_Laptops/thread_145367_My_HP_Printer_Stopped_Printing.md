---
title: "My HP Printer Stopped Printing"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by OffHand on 2006-03-16
Hi
My printer will not print anymore (unless I press the test button on the printer itself).
I got a HP Deskjet 843C. It worked before both under Breezy and Dapper.
When I open the printer in the computer (to see the queued printing jobs) it says: printing: job-printing, but nothing happens.
Anyone got a clue how I could solve this small inconvienience?

---

### Post by OffHand on 2006-03-16
[attach]7130[/attach]

---

### Post by OffHand on 2006-03-16
Anyone?

---

### Post by Lord Illidan on 2006-03-16
Try re-installing it.

---

### Post by OffHand on 2006-03-16
I've already tried to remove the printer and add a new one. 
I have re-installed the drivers with the synaptic too.
First I thought it was a font issue but installing the msttcorefonts didn't work.

---

### Post by Lord Illidan on 2006-03-16
A problem with CUPS, maybe..

```
sudo /etc/init.d/cupsys restart
```

---

### Post by OffHand on 2006-03-16
That didn't work  :( Is there a way to 'ping' the printer to see if it's getting the data?

---

### Post by Ensnared on 2006-03-16
If the printer is receiving data the power-lamp should be blinking. If it doesn't, the printer is not receiving anything.

Seems like a problem with the driver or printing-system to me, but I'm not very familiar with the printer-system in Linux. I'm very familiar with HP printers though, and since it's printing it's internal testpage the printer is most likely working as it should. You should check your cable anyway - reconnect both ends of it to make sure. You can also do a hardware reset of the printer just in case. You do that by opening the cover, removing both cartridges, closing the cover, unplugging the power, wait for a couple of minutes before plugging the power back in, wait for the printer to ask for the cartridges and then putting them back in.

---

### Post by 11hjpphty76lkjj on 2006-03-16
Can you post the cups log?

and post the output of this:

```
dpkg --list 'hplip*'
```

to turn on cups debug mode edit the /etc/cups/cupsd.conf file find loglevel change "info" to "debug" save/exit restart cups (sudo /etc/init.d/cupsys restart) then run tail -f /var/log/cups/error_log

try printing, post the error_log results.  as well run 

/usr/lib/cups/backend/hp 

and post the output.

Aaron

---

### Post by OffHand on 2006-03-16
admin@linux:~$ dpkg --list 'hplip*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          0.9.6-1ubuntu6 HP Linux Printing and Imaging System (HPLIP)
un  hplip-base     <none>         (no description available)
ii  hplip-data     0.9.6-1ubuntu6 HP Linux Printing and Imaging - data files
ii  hplip-ppds     0.9.6-1ubuntu6 HP Linux Printing and Imaging - PPD files
admin@linux:~$

---

### Post by 11hjpphty76lkjj on 2006-03-16
looks good.  can you post the cups log? :)

---

### Post by OffHand on 2006-03-16
admin@linux:~$ /usr/lib/cups/backend/hp
unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 94
unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 720
direct hp:/no_device_found "Unknown" "hp no_device_found"
admin@linux:~$

---

### Post by 11hjpphty76lkjj on 2006-03-16
```
sudo /etc/init.d/hplip restart
```

then run the backend check again and post it.

Aaron

---

### Post by OffHand on 2006-03-16
admin@linux:~$ tail -f /var/log/cups/error_log
D [16/Mar/2006:23:47:22 +0100] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [16/Mar/2006:23:47:22 +0100] cupsdReadClient: 5 POST / HTTP/1.1
D [16/Mar/2006:23:47:22 +0100] cupsdAuthorize: No authentication data provided.
D [16/Mar/2006:23:47:22 +0100] cupsdProcessIPPRequest: 5 status_code=1 (successful-ok-ignored-or-substituted-attributes)
D [16/Mar/2006:23:47:27 +0100] cupsdReadClient: 5 POST / HTTP/1.1
D [16/Mar/2006:23:47:27 +0100] cupsdAuthorize: No authentication data provided.
D [16/Mar/2006:23:47:27 +0100] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)
D [16/Mar/2006:23:47:27 +0100] cupsdReadClient: 5 POST / HTTP/1.1
D [16/Mar/2006:23:47:27 +0100] cupsdAuthorize: No authentication data provided.
D [16/Mar/2006:23:47:27 +0100] cupsdProcessIPPRequest: 5 status_code=1 (successful-ok-ignored-or-substituted-attributes)
D [16/Mar/2006:23:47:32 +0100] cupsdReadClient: 5 POST / HTTP/1.1
D [16/Mar/2006:23:47:32 +0100] cupsdAuthorize: No authentication data provided.
D [16/Mar/2006:23:47:32 +0100] cupsdProcessIPPRequest: 5 status_code=0 (successful-ok)

---

### Post by OffHand on 2006-03-16
admin@linux:~$ /usr/lib/cups/backend/hp
direct hp:/no_device_found "Unknown" "hp no_device_found"
admin@linux:~$

---

### Post by 11hjpphty76lkjj on 2006-03-16
hmm if the backend isn't reporting any devices that's a big problem.  When did it stop working?  Do you have a different USB cable/port you can plug it into?

also try running ```
dmesg
``` with the printer connected and see if it lists any HP devices (your printer specificly)

you can also try disconnecting the printer, then run

```
tail -f /var/log/syslog
```

plug in the printer and post the output.

as well can you try deleting and reinstalling your printer?

Aaron

---

### Post by 11hjpphty76lkjj on 2006-03-16
I'm also assuming that when you did the hplip restart that you didn't get any failed or any error messags?

---

### Post by OffHand on 2006-03-16
> I'm also assuming that when you did the hplip restart that you didn't get any failed or any error messags?
admin@linux:~$ sudo /etc/init.d/hplip restart
 * Stopping HP Linux Printing and Imaging System                         [ ok ]
 * Starting HP Linux Printing and Imaging System                          [ ok ]
admin@linux:~$

---

### Post by OffHand on 2006-03-16
dmesg

[   35.748414] parport0: Printer, HEWLETT-PACKARD DESKJET 840C

I think that's my printer (although it isn't the 843C)

BTW I really appreciate your help  :)

---

### Post by OffHand on 2006-03-16
admin@linux:~$ tail -f /var/log/syslog
Mar 16 23:49:48 localhost hpiod: 0.9.6 accepting connections at 48616...
Mar 16 23:50:28 localhost kernel: [ 3881.452518] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=82.76.145.179 DST=82.73.137.60 LEN=90 TOS=0x00 PREC=0x20 TTL=118 ID=11778 PROTO=UDP SPT=17761 DPT=32459 LEN=70
Mar 17 00:01:07 localhost kernel: [ 4519.256048] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=204.16.208.115 DST=82.73.137.60 LEN=307 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=46909 DPT=1026 LEN=287
Mar 17 00:01:07 localhost kernel: [ 4519.257213] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=204.16.208.115 DST=82.73.137.60 LEN=307 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=46909 DPT=1027 LEN=287
Mar 17 00:02:57 localhost hpiod: 0.9.6 accepting connections at 54595...
Mar 17 00:04:05 localhost kernel: [ 4697.162415] APIC error on CPU0: 02(02)
Mar 17 00:06:16 localhost kernel: [ 4828.767757] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=51.206.144.107 DST=82.73.137.60 LEN=343 TOS=0x00 PREC=0x00 TTL=50 ID=40495 PROTO=UDP SPT=0 DPT=1025 LEN=323
Mar 17 00:06:16 localhost kernel: [ 4828.767811] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=51.206.144.107 DST=82.73.137.60 LEN=343 TOS=0x00 PREC=0x00 TTL=50 ID=40496 PROTO=UDP SPT=0 DPT=1026 LEN=323
Mar 17 00:09:02 localhost kernel: [ 4994.202096] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=142.227.56.45 DST=82.73.137.60 LEN=48 TOS=0x00 PREC=0x60 TTL=110 ID=4282 DF PROTO=TCP SPT=1252 DPT=80 WINDOW=65535 RES=0x00 SYN URGP=0
Mar 17 00:09:05 localhost kernel: [ 4997.180132] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=142.227.56.45 DST=82.73.137.60 LEN=48 TOS=0x00 PREC=0x60 TTL=110 ID=4547 DF PROTO=TCP SPT=1252 DPT=80 WINDOW=65535 RES=0x00 SYN URGP=0

---

### Post by 11hjpphty76lkjj on 2006-03-16
hmm something odd going on here.  Honestly I haven't tested parallel on dapper yet.  but I just tried it with an HP DeskJet 930C and I'm having the same problem. 

Can you disconnect the printer open the syslog and then reconnect the printer?

disconnect printer
run;
```
sudo tail -f /var/log/syslog
```
reconnect the printer.

post the output.  

sorry for the delay.

Aaron

---

### Post by OffHand on 2006-03-16
No Problem. This is the output:

admin@linux:~$ sudo tail -f /var/log/syslog
Password:
Mar 17 00:34:20 localhost kernel: [ 6510.033359] usb 1-1: new low speed USB device using uhci_hcd and address 6
Mar 17 00:34:20 localhost kernel: [ 6510.218902] input: Logitech USB-PS/2 Optical Mouse as /class/input/input6
Mar 17 00:34:20 localhost kernel: [ 6510.218996] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:07.2-1
Mar 17 00:34:24 localhost cupsd: Unable to open log file "/var/log/cups/error_log" - Permission denied
Mar 17 00:34:39 localhost last message repeated 23 times
Mar 17 00:34:42 localhost kernel: [ 6532.055290] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=204.16.208.113 DST=82.73.137.60 LEN=446 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=35175 DPT=1026 LEN=426
Mar 17 00:34:42 localhost kernel: [ 6532.055348] Inbound IN=eth0 OUT= MAC=00:10:a7:07:b8:09:00:0f:35:bd:80:01:08:00 SRC=204.16.208.113 DST=82.73.137.60 LEN=446 TOS=0x00 PREC=0x20 TTL=52 ID=0 DF PROTO=UDP SPT=35175 DPT=1027 LEN=426
Mar 17 00:34:44 localhost cupsd: Unable to open log file "/var/log/cups/error_log" - Permission denied
Mar 17 00:35:19 localhost last message repeated 42 times
Mar 17 00:36:24 localhost last message repeated 78 times
Mar 17 00:37:29 localhost last message repeated 78 times

---

### Post by 11hjpphty76lkjj on 2006-03-16
Just for the heck of it..have you tried deleting and re-adding the printer?

Still researching..

Aaron

---

### Post by OffHand on 2006-03-16
> Just for the heck of it..have you tried deleting and re-adding the printer?Ofcourse I have  ;)
It might be a bug in Dapper. I can't remember the last time I printed.
I think it was in Dapper but I am not 100% sure.
Either way, the problem is there.

---

### Post by 11hjpphty76lkjj on 2006-03-16
Can you run:

```
lsmod | grep par
```

and post the output.

Aaron

---

### Post by OffHand on 2006-03-16
admin@linux:~$ lsmod | grep par
parport_pc             35780  1
parport                36296  2 lp,parport_pc
admin@linux:~$

---

### Post by 11hjpphty76lkjj on 2006-03-16
hmm try

```
sudo modprobe ppdev
```

and then restart hplip and cups and try:

```
/usr/lib/cups/backend/hp
```

anything?

---

### Post by 11hjpphty76lkjj on 2006-03-16
may want to play disconnect/reconnect printer too. ;)

---

### Post by OffHand on 2006-03-16
> may want to play disconnect/reconnect printer tooI did that, it was in one of the instructions you gave me  ;)

admin@linux:~$ sudo modprobe ppdev
Password:
admin@linux:~$ sudo /etc/init.d/hplip restart
 * Stopping HP Linux Printing and Imaging System                         [ ok ]
 * Starting HP Linux Printing and Imaging System                         [ ok ]
admin@linux:~$ sudo /etc/init.d/cups restart
sudo: /etc/init.d/cups: command not found
admin@linux:~$ /usr/lib/cups/backend/hp
direct hp:/par/DESKJET_840C?device=/dev/parport0 "HP DESKJET_840C" "hp:/par/DESKJET_840C?device=/dev/parport0"
admin@linux:~$

---

### Post by 11hjpphty76lkjj on 2006-03-16
hmm that looks better now.  try printing?  you may need to readd the printer now that it's showing up...

---

### Post by 11hjpphty76lkjj on 2006-03-16
sorry if I'm duplicating my own efforts.  doing many things at once lol

---

### Post by OffHand on 2006-03-16
Still doesn't print  :(

---

### Post by OffHand on 2006-03-16
Should I report it as a bug?

---

### Post by 11hjpphty76lkjj on 2006-03-16
hmm if the the printer is showing up on the backend, and you deleted and re-added it...it should be working now..

naughty ubuntu! naughty!

did that work?

okay ehrm..lemme finish stuff and think about this.

---

### Post by 11hjpphty76lkjj on 2006-03-16
Would you be willing to let me remote log into your box and check it out?

---

### Post by OffHand on 2006-03-16
Alright, take your time. I don't know how long I will be up though. It's quite late already hehe. Well, I removed/added the printer again and ran the backend command. This is the output:

admin@linux:~$ /usr/lib/cups/backend/hp
unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 94
unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 720
direct hp:/no_device_found "Unknown" "hp no_device_found"
admin@linux:~$ sudo /etc/init.d/hplip restart
Password:
 * Stopping HP Linux Printing and Imaging System                         [ ok ]
 * Starting HP Linux Printing and Imaging System                         [ ok ]
admin@linux:~$ /usr/lib/cups/backend/hp
direct hp:/no_device_found "Unknown" "hp no_device_found"
admin@linux:~$

---

### Post by browneyedgirl65 on 2006-04-01
*bump*

I have a similar sort of problem, only i have an hp office jet 5510.  *most* everything seems to be okay, but looking at tail -f /var/log/syslog shows this:
Apr  1 19:45:52 localhost hpiod: invalid uri:hp:/no_device_found
Apr  1 19:45:52 localhost no_device_found: unable to send Event hp:/no_device_found 2 5012: Broken pipe
Apr  1 19:45:52 localhost no_device_found: INFO: open device failed; will retry in 30 seconds...

over and over again. 

Some info:

beg@nemesis:~$ dpkg --list 'hplip*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          0.9.5-2ubuntu2 HP Linux Printing and Imaging System (hplip)
ii  hplip-base     0.9.5-2ubuntu2 HP Linux Printing and Imaging System - base
ii  hplip-data     0.9.5-2ubuntu2 HP Linux Printing and Imaging - data files
ii  hplip-ppds     0.9.5-2ubuntu2 HP Linux Printing and Imaging - PPD files
beg@nemesis:~$ /usr/lib/cups/backend/hp
direct hp:/usb/officejet_5500_series?serial=MY47JG109896 "HP officejet_5500_series" "hp:/usb/officejet_5500_series?serial=MY47JG109896"
beg@nemesis:~$ lsmod | grep par
parport_pc             31812  0
parport                32072  2 parport_pc,lp
beg@nemesis:~$ sudo modprobe ppdev
Password:
beg@nemesis:~$ /usr/lib/cups/backend/hp
direct hp:/usb/officejet_5500_series?serial=MY47JG109896 "HP officejet_5500_series" "hp:/usb/officejet_5500_series?serial=MY47JG109896"
beg@nemesis:~$

this is 5.10, pretty standard... would appreciate any pointers, I'm kind of stuck at this point.  Oh one last thing, if I go to system->administration->printing, it shows the icon for the printer, with 3 items in the queue (the three things I've tried to print).  If i look through its properties, under connection, it comes up with the infamous hp:/no_device_found

Thanks for any pointers!
BEG

---

### Post by browneyedgirl65 on 2006-04-01
Weeeeellll...seems in my case I was able to resolve the problem by going to systems->administration->printing
right click on the printer icon in question
going to the connection tab
and changing it from networking to local 

voila...started printing out all the hundreds of test pages I sent it...ack!!

Next up: scanner!

---

### Post by Sef on 2006-04-04
> Next up: scanner!

Try downloading this:  (it got my PSC 1610 scanner working)

Via Syaptic:  download libsane-extras

or 

Via the terminal:  sudo apt-get install libsane-extras

---

### Post by alarmer on 2008-05-26
Had the same problem with my HP LJ 1020 on Hardy.
Tried as advised and nothing helped.
Then I just put it to my laptop with WinXP, printed test page and connected to Ubuntu back again. It continued printing.
Well.. probably HP requires WinXp as a drug from time to time :):roll:

---

### Post by canadianbaptist on 2008-05-26
> **alarmer said:**
> Had the same problem with my HP LJ 1020 on Hardy.
Tried as advised and nothing helped.
Then I just put it to my laptop with WinXP, printed test page and connected to Ubuntu back again. It continued printing.
Well.. probably HP requires WinXp as a drug from time to time :):roll:


Hello! I am not sure if this has been solved for the original poster or not, but i had the same problem on a laserjet 1018. I even sent it back to the dealer...it didn't work still.

I found this: [http://sourceforge.net/projects/hplip/](http://sourceforge.net/projects/hplip/)

It is a utility to get HP printers going. It works great for me. I hope this helps somebody avoid the HOURS I messed around with it!!!

---

