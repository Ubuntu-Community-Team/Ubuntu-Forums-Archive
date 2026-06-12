---
title: "SiPix pocket Printer setup"
date: 2010-03-29
forum: Hardware
---

### Post by Brando753 on 2010-03-29
I have purchased a Sipix portable Printer, as of now I have been unable to connect to it. My laptop has Infrared and I had purchased a usb to Serial adapter. Does anyone know how to connect to an infared printer? If I could use IR that would be great. Also I have been unable to get my printer detected using the Serial adapter. 

_lsusb outputs_ 
"brandon@brandon-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002"


_and dmesg outputs (Condensed)_
[13471.087512] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13477.951265] wlan0: deauthenticating from 00:1d:7e:f4:2f:bb by local choice (reason=3)
[13478.188035] wlan0: direct probe to AP 00:1d:7e:f4:2f:bb (try 1)
[13478.192029] wlan0: direct probe responded
[13478.192041] wlan0: authenticate with AP 00:1d:7e:f4:2f:bb (try 1)
[13478.195150] wlan0: authenticated
[13478.195210] wlan0: associate with AP 00:1d:7e:f4:2f:bb (try 1)
[13478.197464] wlan0: RX AssocResp from 00:1d:7e:f4:2f:bb (capab=0x411 status=0 aid=3)
[13478.197484] wlan0: associated
[13478.201583] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13488.380062] wlan0: no IPv6 routers present
[14959.568138] usb 3-2: new full speed USB device using uhci_hcd and address 2
[14959.728688] usb 3-2: configuration #1 chosen from 1 choice
[14959.825664] usbcore: registered new interface driver usbserial
[14959.830301] USB Serial support registered for generic
[14959.830676] usbcore: registered new interface driver usbserial_generic
[14959.830692] usbserial: USB Serial Driver core
[14959.842970] USB Serial support registered for pl2303
[14959.843762] pl2303 3-2:1.0: pl2303 converter detected
[14959.855697] usb 3-2: pl2303 converter now attached to ttyUSB0
[14959.855745] usbcore: registered new interface driver pl2303
[14959.855751] pl2303: Prolific PL2303 USB to serial adaptor driver


Any help would be appreciated. [http://www.amazon.com/SiPix-Pocket-Palm-Printer-Blue/dp/B00005LDPR/ref=cm_cr_pr_pb_i](http://www.amazon.com/SiPix-Pocket-Palm-Printer-Blue/dp/B00005LDPR/ref=cm_cr_pr_pb_i) Also It is in the Cups drivers.

---

### Post by IcarusR on 2010-03-29
The Linux Infrared HOWTO would be a good place to start reading...

[http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html]("http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html")

---

### Post by Brando753 on 2010-03-29
that would be helpful however even better would be if I could get some help using my serial to usb which is identified and registered. If anyone could help me with this it would be greatly appreciated.

---

### Post by Brando753 on 2010-03-30
Bump. Anyone?

---

### Post by Brando753 on 2010-04-02
Bump, Bump. Anyone Please.

---

### Post by Brando753 on 2010-04-08
Is there not one person out there with a solution??????:confused:

---

### Post by IcarusR on 2010-04-09
> Does anyone know how to connect to an infared printer? If I could use IR that would be great.

I pointed you to a website helping to answer your question, but you decided that you did not want to even try it !!! You expect someone else to help now ??? !!

[http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html]("http://tuxmobil.org/Infrared-HOWTO/Infrared-HOWTO.html")

---

### Post by Brando753 on 2010-04-29
Im sorry if I came off with the wrong impression, I had tried connecting through the information presented in that site however it would not connect. The two options are IR as previously said or a usb to serial pl2303. if anyone knows how to connect or can give me advice on how to connect via IR please help, I couldn't figure it out from that site and yes I went to the Printer connections area. Im using a HP dv5 with intergrated IR if anyone has an idea for the cups URI just let me know.

---

### Post by jimbolaya on 2010-05-08
I'm not sure I can help as I have been having the same problems.  However, I have some investigations to go on.  First, following the directions [_here_]("http://www.linuxforums.org/forum/slackware-linux-help/126064-installation-sipix-pocket-printer-slax.html") I was able to get my printer to print something.  You may wish to follow these directions to make sure that your printer and USB->serial cable works.  

However, getting it to work with CUPS has been a little more frustrating and fruitless at the moment.

Going to the System|Administration|Printing app, it does not list the USB->serial port as a valid port to use, it only lists the serial ports on the motherboard, ttyS0 and ttyS1.  I think this is primarily because somehow the permissions are not correct and can't be read by CUPS for some reason.  One suggestion I read, said to set the URI manually, so I selected Other and put in:

```
serial:/dev/ttyUSB0?baud=115200+bits=8+parity=none+flow=hard
```

Unfortunately, when I attempt to print I get 

```
Unable to open device file "/dev/ttyUSB0": Permission denied
```

I set the permissions of /dev/ttyUSB0 to the most liberal possible, but it still gives that error.  Here's the permissions of /dev/ttyUSB0:

```
crw-rw-rw- 1 lp lp 188, 0 2010-05-08 17:10 /dev/ttyUSB0
```

Curiously, if I run the backend manually, I can get it to work fine, but I'm running as root:

```
root@myhost:/usr/lib/cups/backend# export DEVICE_URI=serial:/dev/ttyUSB0?baud=115200+bits=8+parity=3Dnone+flow=hard
root@myhost:/usr/lib/cups/backend# ./serial "5" "anonymous" "Test Page" "1" "job-originating-host-name=localhost" "/tmp/test.bin"
STATE: +connecting-to-device
STATE: -connecting-to-device
PAGE: 1 1
DEBUG: Wrote 1152 bytes...
DEBUG: Wrote 1152 bytes...
DEBUG: Wrote 1152 bytes...
...
DEBUG: Wrote 1152 bytes...
DEBUG: Wrote 1152 bytes...
DEBUG: Wrote 764 bytes...

```

Any other suggestions to take?

James

---

### Post by Brando753 on 2010-05-14
Well im using ubuntu 10.4 I couldn't even get it to print anything with information you have provided, Thank you though for responding and im glad to see there are others trying to figure this out as well. If anyone can help us out, I keep getting the permission error as well.

---

### Post by bruceleo on 2010-05-18
Have you guys tried the driver at:
[http://www.openprinting.org/printer/SiPix/SiPix-Pocket_Printer_A6](http://www.openprinting.org/printer/SiPix/SiPix-Pocket_Printer_A6)

---

### Post by jimbolaya on 2010-05-18
The driver isn't really the issue, since I've been able to print output with it using other means.  The problem seems to exist in the CUPS usage of USB serial ports.

I've used the procedure describe [_here_]("http://www.openprinting.org/driver/sipixa6.upp") with success on 9.10.  It would be disappointing to find out this doesn't work in 10.04.

James

---

### Post by Brando753 on 2010-05-29
I do hate to bump threads but I would love to get this working. I also agree it isnt as much a driver issue as a permission one.

---

### Post by jimbolaya on 2010-05-30
I finally submitted a detailed bug report and got a very quick reply:

Dave Gilbert to me
	
This looks like a problem with the apparmour config for cups, I suggest if you add /dev/ttyUSB* to /etc/apparmor.d/usr.sbin.cupsd
in the same way as the /dev/ttyS* rw,   line it should fix it.

Dave

I tried this fix and it worked great!!

James

---

### Post by Brando753 on 2010-06-04
Im afraid I cannot mark this thread solved for that did not work on my side. :( But I did find that the sipix printer works out of the box with fedora 13 which I will dual boot until someone can post another possible solution.:?

---

### Post by Brando753 on 2011-03-04
Ok, I found a solution that works for me :D. Do not have the printer or serial adapter attached. 

[LIST=1]
[*]First open a terminal Applications -> Accessories -> Terminal
[*]type in (without quotes) "sudo gedit /etc/apparmor.d/usr.sbin.cupsd"
[*]Scroll down to "/dev/ttyS* rw" and add right below it "/dev/ttyUSB* rw," and save this now close your editor and go back to the terminal
[*]Type in (without quotes) "lsusb"
[*]Plug in the printer with serial adapter and wait ten secconds
[*]once again type in "lsusb"
[*]find the new line that was added since you plugged in the device, for me it was > Bus 004 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
 
[*]Type into the terminal "sudo modprobe usbserial vendor=0x067b product=0x2303" (**Remember** to replace vendor=0x067b product=0x2303 with the one that corresponds to your lsusb output. Making it vendor=0x---- product=0x----)
[*]now go to system -> administration -> printing
[*]Click Add printer, under devices should be listed USB Serial Port #1 click that and choose "115200" as the baud Rate, "none" for parity, "8" for data bits, and "RTS/CTS (Hardware)" as flow control, Hit next.
[*]choose Sipix as Makes, hit next
[*]only one option should be availale for models and drivers "Pocket Printer A6, SiPix Pocket Printer A6 ....", hit next 
[*]Hit Apply
[*]load a sheet of paper and click "print test page" to see if it works. (Notice the driver will pull the page 8 returns forward so be prepared for that)
[*]**VERY IMPORTANT!!!!** to make sure this will last every time you reboot go back to the terminal type in "sudo gedit /etc/modules" and add "modprobe usbserial vendor=0x067b product=0x2303" using the correct vendor and product numbers [/LIST]

That it! Your done! Good luck I hope this helps someone. =D>

P.S. If your printer finishes printing but does not release the paper or move it far enough simply hold the power button down, this makes it act like a feed button.

---

