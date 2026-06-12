---
title: "EVDO Cell Phone as Modem"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by PlancksCnst on 2006-09-21
I am trying to connect to the internet over my cell phone (that's what I use for my connection - I'm not just trying something out for fun). I have a clean install of Kubuntu 6.06.1, which uses kernel 2.6. When I connect my modem, a bunch of stuff is spit out to /var/log/messages (listing is below). I see that it registers the cdc-acm driver.

I've tried doing "modprobe usbserial vender=#### product=####" as is suggested [here](http://72.14.203.104/search?q=cache:zNzcDgVy58cJ:kenkinder.com/evdo-pc5740/+samsung+a920+linux+kernel+2.6&hl=en&gl=us&ct=clnk&cd=1&client=opera"). I have also seen [this](http://www.sprintusers.com/forum/showthread.php?p=695747"), as well as some other posts. Generally, they say to modprobe some character device driver (whichever their phone works with; mine uses cdc-acm). Then linux should assign a /dev/something to it, and show that it has done so in /var/log/messages or dmesg. Then, optionally, they link the /dev/modem to it. And just dial away with ppp. The problem is (I think), mine doesn't create a /dev/ device.

Also, if I disconnect the phone from the USB port, funny things happen. It will do a memory dump to /var/log/messages. If kInfoCenter is running, it will hang. Then when I shutdown, it halts when it gets to bluetooth stuff, and I have to hit the reset switch.

Thanks in advance for your help.
-Shawn

P.S.  I have posted this in a couple of other forums (LinuxQuestions and Kubuntu), and it has gone several days with absolutely no responses.  Did I say something wrong, or is this just a stumper?  I would like some feedback to let me know I'm sane.


The following is the output to /var/log/messages when I plug my phone in.
```


Sep 16 23:46:18 shawn-desktop kernel: [ 137.405294] usb 1-1: new full speed USB device using ohci_hcd and address 3
Sep 16 23:46:19 shawn-desktop kernel: [ 137.613144] usbcore: registered new driver usbserial
Sep 16 23:46:19 shawn-desktop kernel: [ 137.613608] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Sep 16 23:46:19 shawn-desktop kernel: [ 137.614043] usbcore: registered new driver usbserial_generic
Sep 16 23:46:19 shawn-desktop kernel: [ 137.614172] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Sep 16 23:46:19 shawn-desktop kernel: [ 137.616542] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Sep 16 23:46:19 shawn-desktop kernel: [ 137.617033] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Sep 16 23:46:19 shawn-desktop kernel: [ 137.617516] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Sep 16 23:46:19 shawn-desktop kernel: [ 137.618989] visor 1-1:1.0: Handspring Visor / Palm OS converter detected
Sep 16 23:46:19 shawn-desktop kernel: [ 137.619871] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
Sep 16 23:46:19 shawn-desktop kernel: [ 137.620192] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
Sep 16 23:46:19 shawn-desktop kernel: [ 137.621446] visor 1-1:1.1: Handspring Visor / Palm OS converter detected
Sep 16 23:46:19 shawn-desktop kernel: [ 137.621786] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB2
Sep 16 23:46:19 shawn-desktop kernel: [ 137.622116] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB3
Sep 16 23:46:19 shawn-desktop kernel: [ 137.622265] usbcore: registered new driver visor
Sep 16 23:46:19 shawn-desktop kernel: [ 137.622371] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Sep 16 23:46:19 shawn-desktop kernel: [ 137.644619] usbcore: registered new driver cdc_acm
Sep 16 23:46:19 shawn-desktop kernel: [ 137.644764] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
Sep 17 00:04:10 shawn-desktop -- MARK --

```

---

### Post by jpattisonjr on 2006-09-22
I have a Fedora install that I hook my phone uo to and use it as a modem. I tried using my phone on a fresh install of ubuntu on a ibook G4. The modem is detected, but fails with an error saying that kppp could not not log in using any of the secret passwords. What secret passwords?

---

### Post by PlancksCnst on 2006-09-22
That's funny.  I guess the famed Ubuntu is just not going to be my distro, then.  I just d/l'd FC6 test 3.  I think I'll try that next.  What I really wanted in the first place was Gentoo, but the setup cd wouldn't even start boot for me.

---

### Post by johnh123 on 2006-10-13
Anybody had any luck with this?  This is a deal-killer for me, as well.  It seems to work on Mandriva.

---

### Post by Jason_25 on 2006-10-13
I use my Motorola Razr with EVDO almost constantly.  It works perfect using wvdial.

---

### Post by PlancksCnst on 2006-11-06
I'm sure mine would work with wvdial (or any dialer) too, if it actually assigned a driver.  Unfortunately, I can't get that far.

This is also a deal-killer for me, as well.  This is my internet connection.  Without it, I can't download software or updates, check email, etc.  These days a computer is almost useless without internet access.

---

### Post by Jim March on 2006-11-13
I use a Verizon-connected PCMCIA EVDO card (Kyocera 650) and just like you, could NOT figure out what new /dev/whatever was turning on.  Drove me crazy.

I was so disgusted with Windows though that I solved the problem with about $250 in hardware: a Kyocera KR1 EVDO router.

[http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=99](http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=99)

This bad boy has it's own PCMCIA slot for the modem, then delivers both Ethernet (four ports worth) and WiFi.  I'm running it right this second in Ethernet to my Edgy laptop, absolutely no drivers of any sort needed.

This thing has a USB port that is PLANNED for use with EVDO cellphones as an option instead of a PCMCIA card.  I don't know if they've got that working with the current firmware, you might want to ask at:

[http://www.evdoforums.com/viewforum.php?f=17](http://www.evdoforums.com/viewforum.php?f=17)

This chart:

[http://www.evdoinfo.com/customer_support/EVDO_Routers/](http://www.evdoinfo.com/customer_support/EVDO_Routers/)

...says they've got the Verizon Samsung SCH-A890 working now, Sprint phones are "future firmware".

It looks like Fiesty Fawn will have a lot of revised laptop hardware support.  Until then, if you can get a KR1 working, it's a zero-driver, zero-setup answer.

---

### Post by linuxn00b73 on 2006-12-14
Really hard finding information on using a cell phone as a modem. my phone isn't EVDO but 230k on older sprint internet isn't bad. I think I read somewhere that this seems to work better on Dapper Darke and Breezy Badger better...might have to try that out. I have gotten my phone to show up as /dev/ttyACM0 and it is in Device Manager as SCP-4900 (though the phone is model SCP-5500) under that it has USB communication interface and under that serial port (ttyACM0) so I figured I'd be set.

When I use wvdial however it does not detect the modem
[IMG]http://i58.photobucket.com/albums/g258/ffrriday31/wv.jpg[/IMG]

All I know is I need to dial #777 for sprint with no username/password. Any ideas?

---

### Post by supervman on 2006-12-31
I used wvdial to configure my samsung a920. Make sure the phone status shows USB connected. I went and edited the wvdial.conf file.  Mine looks like this:   
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
 Phone = <#777>
 Password = <>
 Username = <>

For sprint the username/password are embedded in the phone .  You just need to type in the #777 for the phone number.   You also have to edit the /etc/ppp/options and comment out these two lines : #lcp-echo-interval 30  &  #lcp-echo-failure 4.  This will keep the connection from timing out.  Hope this helps.

---

### Post by supervman on 2006-12-31
I forgot to add Stupid Mode = 1 after the username :  
Username = <>
Stupid Mode = 1

---

### Post by Mach1US on 2007-01-23
Check this  How to , it has all the info you need .

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo+motorola](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo+motorola)

---

### Post by frmach on 2007-12-24
:(
 I tried to set my Verizon PC5750 using the method described here. The problem is my copy of Gutsy did not contain the vendor product catalog.

---

