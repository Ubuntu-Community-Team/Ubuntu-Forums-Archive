---
title: "Nokia N95 as modem"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by andkuh on 2007-07-05
Hi,

I would like to know if anyone has got the Nokia N95 mobile phone to work as a bluetooth modem in Feisty? I haven't really tried and don't even know where to begin, but I would love to get it to work as a 3G modem on my laptop.

Br,

Andréas

---

### Post by Cyfr on 2007-07-05
me too! :D Anyone know how?

---

### Post by rgclegg on 2007-12-21
Yes.  You need to pair the devices first.

/etc/bluetooth/rfcomm0

rfcomm0 {
bind yes;
device 00:1C:D4:49:8F:AE;
channel 2; 
comment "Dial-up networking";
}

replace device number with correct one for your mobile -- easy enough to find out.

Here's the difficult bit -- this seems to be carrier specific -- I am on o2

/etc/ppp/peers/o2blue

hide-password
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/o2"
debug
/dev/rfcomm0
460800
defaultroute
noipdefault
nodeflate
nobsdcomp
remotename o2
ipparam o2
usepeerdns
lcp-echo-interval 0

 /etc/chatscripts/o2 
TIMEOUT 5
ECHO ON
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TON
E' ABORT 'NO ANSWER' ABORT DELAYED
'' \rAT
TIMEOUT 12
OK     AT+CGDCONT=1,"IP","mobile.o2.co.uk"
OK ATE1
OK     ATD*99***1#
TIMEOUT 12
CONNECT ""

You will need to replace the last bits with the correct runes for your provider.  These may be tricky to find.

OK -- then for me it was

rfcomm connect 0

and while this is running, in another window

pon o2blue

You can also use the usb modem by removing all the bluetooth bits and creating
/etc/ppp/peers/o2usb

hide-password
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/o2"
debug
/dev/ttyACM0
460800
defaultroute
noipdefault
nodeflate
nobsdcomp
remotename o2
ipparam o2
usepeerdns
lcp-echo-interval 0

Then run
sudo modprobe usbserial vendor=0x0421 product=0x04f0

The numbers you need might vary -- find them using lsusb with the correct parameters.

Finally 
pon o2usb should get you connected

tail -f /var/log/messages should give helpful output.

Sorry I can't provide a more thorough guide.

---

### Post by ramakann on 2008-06-06
Hi,

I don't have /etc/chatscripts folders.Instread i had /etc/ppp.Is it perfectly right to use /etc/ppp instead of /etc/chatscripts?I am using RedHat 9 linux.Thanks

---

