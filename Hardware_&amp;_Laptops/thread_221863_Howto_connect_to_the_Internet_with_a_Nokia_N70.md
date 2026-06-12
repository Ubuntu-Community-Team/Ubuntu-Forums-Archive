---
title: "Howto connect to the Internet with a Nokia N70"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by Ndlovu on 2006-07-24
**[SIZE="2"]Process[/SIZE]**

**Step 1**: Plug the data cable into your mobile phone and into your computer. Then see whether it was recognised by the kernel.

[INDENT]tail /var/log/messages[/INDENT]

Should result in something like the following output:

[INDENT]localhost kernel: [4295346.417000] usb 1-1: new full speed USB device using ohci_hcd and address3
localhost kernel: [4295348.125000] cdc_acm 1-1:1.8: ttyACM0: USB ACM device
localhost kernel: [4295348.133000] usbcore: registered new driver cdc_acm
localhost kernel: [4295348.133000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters[/INDENT]

According to this output, the kernel driver being used is cdc-acm (you don't need to know that, but it may be useful for other applications). We can deduce from the second line that linux can see the device at /dev/ttyACM0 - this you will need to know.

**Step 2**: Configure Ubuntu to be able to communicate with your phone and use it to connect to the Internet.

Install ppp (handles modems and dialing) if it's not installed already:

[INDENT]sudo apt-get install ppp[/INDENT]

You will need to create a configuration file that tells Ubuntu how to handle communication with the phone. If you prefer using a graphical text editor, replace "vi" in this and the following steps with "gedit". The files should be empty to start with.

[INDENT]sudo vi /etc/ppp/peers/mobile[/INDENT]

Enter the following text:

```
debug
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/mobile"
usepeerdns
/dev/ttyACM0 115200
defaultroute
crtscts
lcp-echo-failure 0
```

If the /var/log/messages output above showed something other than ttyACM0, substitute that in the above code.

Ubuntu will need to send some commands to your phone to tell it to connect to the Internet. These commands are stored in a chat script, and are sent when you try to connect.

[INDENT]sudo vi /etc/chatscripts/mobile[/INDENT]

Enter the following text:

```
TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      'AT+CGDCONT=1,"IP","INTERNET"'
OK      ATD*99***1#
CONNECT ""
```

You also need to be registered to use the modem connection. You are probably registered already, but this should take care of it if you're not (using your Ubuntu login name):

[INDENT]sudo adduser your-username-here dialout[/INDENT]

If you can connect to the Internet on your phone (without your computer), the configuration scripts above should work. If not, look around in the links given below and see whether you can resolve the problem. The most likely points of failure are the [FONT="Courier New"]'AT+CGDCONT=1,"IP","INTERNET"'[/FONT] and [FONT="Courier New"]ATD*99***1#[/FONT] sections.

Specifically where I have set "INTERNET" above, may well be different in your case. This is the Access Point Name (APN). It can (probably) be found in your phone's settings - I can get to it through the following path on my phone: Menu > Tools > Settings > Connection > Access Points. From there choose the access point you use to connect to the Internet (most probably the first one on the list). One of the settings there is "Access point name". Substitute what it says there where I have put "INTERNET" above.

**Step 3**: You should now be ready to connect. To dial, use the "pon" command, and to disconnect, use the "poff" command.

[INDENT]pon mobile
poff mobile[/INDENT]

Whatever messages are communicated between Ubuntu and your phone, should show up in /var/log/syslog. The easiest way to see what's happening in the process is to open another terminal and use the following command before connecting with the commands above:

[INDENT]tail -f /var/log/syslog[/INDENT]

Whatever messages are written to the log, will now be displayed on your terminal "live".

[B][SIZE="2"]
Useful Commands[/SIZE][/B]

```
tail /var/log/messages
lsusb
pon
poff
tail -f /var/log/syslog
```

[B][SIZE="2"]
External Resources
[/SIZE][/B]
[LIST]
[*][http://help.ubuntu.com/community/BluetoothDialup](http://help.ubuntu.com/community/BluetoothDialup)
[*][http://www.orthodox.org.za/CommunityResources/vodaphone3g.html](http://www.orthodox.org.za/CommunityResources/vodaphone3g.html)
[*][http://mybroadband.co.za/vb/showthread.php?t=21726](http://mybroadband.co.za/vb/showthread.php?t=21726)
[*][http://bitubique.com/content/view/26/42/](http://bitubique.com/content/view/26/42/)
[/LIST]

---

### Post by cvmostert on 2006-08-15
Great stuff, i have a connection, but tried it anyway... seemd to work by the soud of my speakers... 


great stuff! well done!

thank you..
C

---

### Post by Ausus on 2006-09-06
Hi Ndlovu,
I Used your guide and it works.
The only problem I experienced was that my on-board ethernet also wanted to use the connection.
It then disabled my ethernet cards, because I dont have a home lan setup.

Regards

---

### Post by troopy on 2006-10-12
Hello.

Firstly thanks for the guide it was very useful, but I do have a problem with my connection that I thought someone might be able to help with.

I followed the instruction to the note but when I go "pon mobile" I get the following from /var/log/messages:

Oct 12 18:44:21 ads-laptop chat[5310]:  -- got it
Oct 12 18:44:21 ads-laptop chat[5310]: send (AT+CGDCONT=1,"IP","INTERNET"^M)
Oct 12 18:44:21 ads-laptop chat[5310]: expect (OK)
Oct 12 18:44:21 ads-laptop chat[5310]: ^M
Oct 12 18:44:21 ads-laptop chat[5310]: AT+CGDCONT=1,"IP","INTERNET"^M^M
Oct 12 18:44:21 ads-laptop chat[5310]: OK
Oct 12 18:44:21 ads-laptop chat[5310]:  -- got it
Oct 12 18:44:21 ads-laptop chat[5310]: send (ATD*99***1#^M)
Oct 12 18:44:21 ads-laptop chat[5310]: expect (CONNECT)
Oct 12 18:44:21 ads-laptop chat[5310]: ^M
Oct 12 18:44:24 ads-laptop chat[5310]: ATD*99***1#^M^M
Oct 12 18:44:24 ads-laptop chat[5310]: CONNECT
Oct 12 18:44:24 ads-laptop chat[5310]:  -- got it
Oct 12 18:44:24 ads-laptop chat[5310]: send (^M)
Oct 12 18:44:24 ads-laptop pppd[5308]: Serial connection established.
Oct 12 18:44:24 ads-laptop pppd[5308]: Using interface ppp0
Oct 12 18:44:24 ads-laptop pppd[5308]: Connect: ppp0 <--> /dev/ttyACM0
Oct 12 18:44:27 ads-laptop pppd[5308]: PAP authentication succeeded
Oct 12 18:44:27 ads-laptop pppd[5308]: LCP terminated by peer
Oct 12 18:44:30 ads-laptop pppd[5308]: Connection terminated.
Oct 12 18:44:31 ads-laptop pppd[5308]: Hangup (SIGHUP)
Oct 12 18:44:31 ads-laptop pppd[5308]: Modem hangup
Oct 12 18:44:31 ads-laptop pppd[5308]: Exit.


Im thinking its a problem with maybe my service provider - I can connect to the internet normally with my phone browser. Any help would be great!

---

### Post by troopy on 2006-10-12
Hello!

Sorry about this I reread your instructions and found my access point was wrong.. This fixed the connection problem but I had to stop my other network interfaces using /etc/init.d/networking stop to get the routes to work correctly.

Thank you so much!

---

### Post by tripuz on 2006-12-20
Hi,
I also have an N70 and I've been trying for several hours to sync it with the addressbook on my (K)ubuntu box, first with Kitchensync and Kontact in KDE, then with Multisync (Opensync) via msynctool and Evolution in Gnome, but couldn't get any result. In KDE the sync won't find my phone, while in Gnome I managed to turn the phone in Sync mode via bluetooth, but then nothing happens.
I was wondering if anyone managed to find out how to complete the sync in Ubuntu with this phone or with other similar phones and if you have some suggestions about this :-)
Thanks in advance!

---

### Post by arjancwidlak on 2007-07-02
Hi Ndlovu

Thanx for your tutorial. I'm getting far, but not completely there. 
I have a Vodafone account. The output below is coming from a script that adds 'noccd' to /etc/ppp/peers/mobile, but is identical to your script besides that. 

It seems, that without a good reason the connection is terminated. Everyting goes fine until then. I can see the connection briefly on my phone's connections' tab. 

Any help would be appreciated,
Kind regards,
Arjan

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ed0fe63>]
Jul  2 02:28:57 ubuntu pppd[7971]: rcvd [LCP ConfRej id=0x1 <magic
0x9ed0fe63>]
Jul  2 02:28:57 ubuntu pppd[7971]: sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
Jul  2 02:28:57 ubuntu pppd[7971]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
Jul  2 02:28:59 ubuntu pppd[7971]: rcvd [LCP ConfReq id=0x0 <auth pap>
<mru 1500> <asyncmap 0xa0000>]
Jul  2 02:28:59 ubuntu pppd[7971]: sent [LCP ConfAck id=0x0 <auth pap>
<mru 1500> <asyncmap 0xa0000>]
Jul  2 02:28:59 ubuntu pppd[7971]: sent [LCP EchoReq id=0x0 magic=0x0]
Jul  2 02:28:59 ubuntu pppd[7971]: sent [PAP AuthReq id=0x1
user="vodafone" password=<hidden>]
Jul  2 02:28:59 ubuntu pppd[7971]: rcvd [LCP EchoRep id=0x0 magic=0x0]
Jul  2 02:28:59 ubuntu pppd[7971]: rcvd [PAP AuthAck id=0x1 ""]
Jul  2 02:28:59 ubuntu pppd[7971]: PAP authentication succeeded
Jul  2 02:28:59 ubuntu pppd[7971]: sent [IPCP ConfReq id=0x1 <compress VJ
0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jul  2 02:28:59 ubuntu pppd[7971]: rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
Jul  2 02:28:59 ubuntu pppd[7971]: sent [IPCP ConfAck id=0x0 <addr 10.6.6.6>]
Jul  2 02:28:59 ubuntu pppd[7971]: rcvd [LCP TermReq id=0x1]
Jul  2 02:28:59 ubuntu pppd[7971]: LCP terminated by peer
Jul  2 02:28:59 ubuntu pppd[7971]: sent [LCP TermAck id=0x1]
Jul  2 02:29:02 ubuntu pppd[7971]: Connection terminated.
Jul  2 02:29:03 ubuntu pppd[7971]: Hangup (SIGHUP)
Jul  2 02:29:03 ubuntu pppd[7971]: Modem hangup
Jul  2 02:29:03 ubuntu pppd[7971]: Exit.

---

### Post by leeyee on 2007-07-09
I did the same thing with wvdial, here is my wvdial.conf, all what i've done is edit it as following.
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","cmwap"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Password = B
Username = A
Stupid Mode = 1

```
what you need to modify is just "cmwap" to your own access point provided by your SP. After this, just type
```
sudo wvdial
```

Enjoy!

---

### Post by morngrar on 2008-04-07
I'm trying to get this to work:

I've edited the mobile file, but i get this output

```
Apr  7 22:25:50 bewar-laptop pppd[9823]: pppd 2.4.4 started by bewar, uid 1000
Apr  7 22:25:51 bewar-laptop chat[9825]: timeout set to 35 seconds
Apr  7 22:25:51 bewar-laptop chat[9825]: abort on (\nBUSY\r)
Apr  7 22:25:51 bewar-laptop chat[9825]: abort on (\nERROR\r)
Apr  7 22:25:51 bewar-laptop chat[9825]: abort on (\nNO ANSWER\r)
Apr  7 22:25:51 bewar-laptop chat[9825]: abort on (\nNO CARRIER\r)
Apr  7 22:25:51 bewar-laptop chat[9825]: abort on (\nNO DIALTONE\r)
Apr  7 22:25:51 bewar-laptop chat[9825]: abort on (\nRINGING\r\n\r\nRINGING\r)
Apr  7 22:25:51 bewar-laptop chat[9825]: send (^MAT^M)
Apr  7 22:25:51 bewar-laptop chat[9825]: expect (OK)
Apr  7 22:25:51 bewar-laptop chat[9825]: ^MAT^M^M
Apr  7 22:25:51 bewar-laptop chat[9825]: OK
Apr  7 22:25:51 bewar-laptop chat[9825]:  -- got it 
Apr  7 22:25:51 bewar-laptop chat[9825]: send (AT+CGDCONT=1,"IP","Tele2 GPRS modem"^M)
Apr  7 22:25:51 bewar-laptop chat[9825]: expect (OK)
Apr  7 22:25:51 bewar-laptop chat[9825]: ^M
Apr  7 22:25:51 bewar-laptop chat[9825]: AT+CGDCONT=1,"IP","Tele2 GPRS modem"^M^M
Apr  7 22:25:51 bewar-laptop chat[9825]: OK
Apr  7 22:25:51 bewar-laptop chat[9825]:  -- got it 
Apr  7 22:25:51 bewar-laptop chat[9825]: send (ATD*99***1#^M)
Apr  7 22:25:51 bewar-laptop chat[9825]: expect (CONNECT)
Apr  7 22:25:51 bewar-laptop chat[9825]: ^M
Apr  7 22:25:53 bewar-laptop chat[9825]: ATD*99***1#^M^M
Apr  7 22:25:53 bewar-laptop chat[9825]: CONNECT
Apr  7 22:25:53 bewar-laptop chat[9825]:  -- got it 
Apr  7 22:25:53 bewar-laptop chat[9825]: send (^M)
Apr  7 22:25:53 bewar-laptop pppd[9823]: Serial connection established.
Apr  7 22:25:53 bewar-laptop pppd[9823]: using channel 13
Apr  7 22:25:53 bewar-laptop pppd[9823]: Using interface ppp0
Apr  7 22:25:53 bewar-laptop pppd[9823]: Connect: ppp0 <--> /dev/ttyACM0
Apr  7 22:25:53 bewar-laptop pppd[9823]: rcvd [LCP ConfReq id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xadcabee5> <pcomp> <accomp>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [LCP ConfAck id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: rcvd [LCP ConfRej id=0x1 <magic 0xadcabee5> <pcomp> <accomp>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [PAP AuthReq id=0x1 user="bewar-laptop" password=<hidden>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: rcvd [PAP AuthAck id=0x1 ""]
Apr  7 22:25:53 bewar-laptop pppd[9823]: PAP authentication succeeded
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [IPCP ConfAck id=0x0 <addr 10.6.6.6>]
Apr  7 22:25:53 bewar-laptop pppd[9823]: rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Apr  7 22:25:53 bewar-laptop pppd[9823]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Apr  7 22:25:53 bewar-laptop pppd[9823]: rcvd [LCP TermReq id=0x1]
Apr  7 22:25:53 bewar-laptop pppd[9823]: LCP terminated by peer
Apr  7 22:25:53 bewar-laptop pppd[9823]: sent [LCP TermAck id=0x1]
Apr  7 22:25:56 bewar-laptop pppd[9823]: Connection terminated.
Apr  7 22:25:56 bewar-laptop pppd[9823]: Hangup (SIGHUP)
Apr  7 22:25:56 bewar-laptop pppd[9823]: Modem hangup
Apr  7 22:25:57 bewar-laptop pppd[9823]: Exit.
```

and i get a notice on the phone saying that i need to subscribe to packet data first.

so i wonder if "packet data" is something completely different to connecting with the phone browser? 'cause i can do that :/

---

### Post by ollesbrorsa on 2008-04-09
Hello morngrar,

You need to replace "Tele2 GPRS modem" with your APN. If you are a swedish Tele2 customer your APN is **internet.tele2.se**.

Good luck,
ollesbrorsa

---

### Post by SSJxGojita on 2008-04-25
BRAVO! :)
Following the instructions as is and everything JUST WORKS!!!
Excellent! Thanks a lot and keep up the good work.

---

### Post by uzzal on 2008-06-01
> **SSJxGojita said:**
> BRAVO! :)
Following the instructions as is and everything JUST WORKS!!!
Excellent! Thanks a lot and keep up the good work.
Howto connect to the Internet with a Nokia N70

---

