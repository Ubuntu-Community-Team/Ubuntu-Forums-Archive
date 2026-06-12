---
title: "connect to internet through phone's bluetooth"
date: 2009-10-20
forum: Hardware
---

### Post by map7 on 2009-10-20
I'm running ubuntu 904 64bit on my notebook with built in bluetooth support and my phone is a Nokia N95 series 1.  I can successfully connect to the internet through my phone if I use a usb cable, but i don't always have this cable on me and it would be nice to be wireless.  My provider is Optus (Australia) and my APN is correctly setup.

I've been following the how-to [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup) without any much luck. 

Here is what I put in my BluetoothDialup file:
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
OK      ATD*99***1#
CONNECT ""
```


Here is the error message i get from the /var/log/syslog
```
Oct 21 10:46:30 hal9000 pppd[18341]: pppd 2.4.5 started by map7, uid 1000
Oct 21 10:46:32 hal9000 bluetoothd[6505]: link_key_request (sba=00:25:56:D0:71:4E, dba=00:1A:DC:CE:56:04)
Oct 21 10:46:33 hal9000 chat[18348]: timeout set to 35 seconds
Oct 21 10:46:33 hal9000 chat[18348]: abort on (\nBUSY\r)
Oct 21 10:46:33 hal9000 chat[18348]: abort on (\nERROR\r)
Oct 21 10:46:33 hal9000 chat[18348]: abort on (\nNO ANSWER\r)
Oct 21 10:46:33 hal9000 chat[18348]: abort on (\nNO CARRIER\r)
Oct 21 10:46:33 hal9000 chat[18348]: abort on (\nNO DIALTONE\r)
Oct 21 10:46:33 hal9000 chat[18348]: abort on (\nRINGING\r\n\r\nRINGING\r)
Oct 21 10:46:33 hal9000 chat[18348]: send (^MAT^M)
Oct 21 10:46:33 hal9000 chat[18348]: expect (OK)
Oct 21 10:46:33 hal9000 chat[18348]: ^MAT^M^M
Oct 21 10:46:33 hal9000 chat[18348]: OK
Oct 21 10:46:33 hal9000 chat[18348]:  -- got it 
Oct 21 10:46:33 hal9000 chat[18348]: send (ATD*99***1#^M)
Oct 21 10:46:33 hal9000 chat[18348]: expect (CONNECT)
Oct 21 10:46:33 hal9000 chat[18348]: ^M
Oct 21 10:46:35 hal9000 chat[18348]: ATD*99***1#^M^M
Oct 21 10:46:35 hal9000 chat[18348]: CONNECT
Oct 21 10:46:35 hal9000 chat[18348]:  -- got it 
Oct 21 10:46:35 hal9000 chat[18348]: send (^M)
Oct 21 10:46:35 hal9000 pppd[18341]: Script /usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup finished (pid 18347), status = 0x0
Oct 21 10:46:35 hal9000 pppd[18341]: Serial connection established.
Oct 21 10:46:35 hal9000 pppd[18341]: using channel 3
Oct 21 10:46:35 hal9000 pppd[18341]: Using interface ppp0
Oct 21 10:46:35 hal9000 pppd[18341]: Connect: ppp0 <--> /dev/rfcomm0
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [LCP ConfReq id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
Oct 21 10:46:36 hal9000 pppd[18341]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4c4d7382> <pcomp> <accomp>]
Oct 21 10:46:36 hal9000 pppd[18341]: sent [LCP ConfAck id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [LCP ConfRej id=0x1 <magic 0x4c4d7382> <pcomp> <accomp>]
Oct 21 10:46:36 hal9000 pppd[18341]: sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
Oct 21 10:46:36 hal9000 pppd[18341]: sent [LCP EchoReq id=0x0 magic=0x0]
Oct 21 10:46:36 hal9000 pppd[18341]: sent [PAP AuthReq id=0x1 user="hal9000" password=<hidden>]
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [LCP EchoRep id=0x0 magic=0x0]
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [PAP AuthAck id=0x1 ""]
Oct 21 10:46:36 hal9000 pppd[18341]: PAP authentication succeeded
Oct 21 10:46:36 hal9000 pppd[18341]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Oct 21 10:46:36 hal9000 pppd[18341]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
Oct 21 10:46:36 hal9000 pppd[18341]: sent [IPCP ConfAck id=0x0 <addr 10.6.6.6>]
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Oct 21 10:46:36 hal9000 pppd[18341]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Oct 21 10:46:36 hal9000 pppd[18341]: rcvd [LCP TermReq id=0x1]
Oct 21 10:46:36 hal9000 pppd[18341]: LCP terminated by peer
Oct 21 10:46:36 hal9000 pppd[18341]: sent [LCP TermAck id=0x1]
Oct 21 10:46:39 hal9000 pppd[18341]: Connection terminated.
Oct 21 10:46:40 hal9000 pppd[18341]: Modem hangup
Oct 21 10:46:40 hal9000 pppd[18341]: Exit.
```

I don't know why it's hanging up the modem.  Any suggestions welcome.
Is there an easy way to do this that I'm missing.

---

### Post by pistacoppu on 2009-10-30
maybe i'm wrong but if you can connect via usb and not via bluetooth, maybe it is a problem of rfcomm0 ?
If you will update to 9.10, now network-manager recognise bluetooth mobile phones and you can easily connect trough nm, so it may work.

---

### Post by map7 on 2009-11-02
I'm running 9.10 now and although I can see my phone through the bluetooth manager and send and recieve files to the phone I cannot find a way to connect to the internet using bluetooth.

---

