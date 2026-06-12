---
title: "PPP dials then disconnects"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by Locke897 on 2005-05-20
Hi,

I'm relatively new to Linux and seem to be having problems connecting to the internet with ppp/pon. My modem is a Lucent Microelectronics 56K winmodem; I installed build-essential and linux-headers in order to compile the necessary "ltmodem-2.6-7-alk" drivers (from [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) ), but after compiling, I could not load ltserial using *sudo modprobe -v ltserial*; I kept on receiving the error "FATAL: Module ltserial not found." Then I installed "linux-restricted-modules-2.6.10-5-386_2.6.10.4-1_i386.deb" using *dpkg -i*, and that finally installed ltserial (checked it with *lsmod*). I then ran pppconfig, both as sudo and as root, and added my connection, but after typing *sudo pon [provider]*, the connection only lasted a few seconds and then terminated. Here are the outputs of *plog* and *tail -f /var/log/messages/*, both after the connection terminated and while it was dialing:

jwbohling@ubuntu:~$ sudo pon DSL
jwbohling@ubuntu:~$ plog
May 20 18:06:45 localhost chat[6568]: abort on (NO ANSWER)
May 20 18:06:45 localhost chat[6568]: abort on (DELAYED)
May 20 18:06:45 localhost chat[6568]: send (ATZ^M)
May 20 18:06:45 localhost chat[6568]: expect (OK)
May 20 18:06:45 localhost chat[6568]: ATZ^M^M
May 20 18:06:45 localhost chat[6568]: OK
May 20 18:06:45 localhost chat[6568]:  -- got it
May 20 18:06:45 localhost chat[6568]: send (ATL1DT2464087^M)
May 20 18:06:46 localhost chat[6568]: expect (CONNECT)
May 20 18:06:46 localhost chat[6568]: ^M
jwbohling@ubuntu:~$ plog
May 20 18:06:46 localhost chat[6568]: ^M
May 20 18:07:20 localhost chat[6568]: ATL1DT2464087^M^M
May 20 18:07:20 localhost chat[6568]: CONNECT
May 20 18:07:20 localhost chat[6568]:  -- got it
May 20 18:07:20 localhost chat[6568]: send (\d)
May 20 18:07:21 localhost pppd[6551]: Serial connection established.
May 20 18:07:22 localhost pppd[6551]: using channel 1
May 20 18:07:22 localhost pppd[6551]: Using interface ppp0
May 20 18:07:22 localhost pppd[6551]: Connect: ppp0 <--> /dev/modem
May 20 18:07:23 localhost pppd[6551]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4337eb0> <pcomp> <accomp>]
jwbohling@ubuntu:~$ plog
May 20 18:07:26 localhost pppd[6551]: sent [LCP ConfRej id=0x1 < 00 04 00 00> <mrru 1524> < 1b 04 02 02>]
May 20 18:07:26 localhost pppd[6551]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x4337eb0> <pcomp> <accomp>]
May 20 18:07:26 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:26 localhost pppd[6551]: sent [LCP ConfNak id=0x2 <auth pap>]
May 20 18:07:27 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:27 localhost pppd[6551]: sent [LCP ConfNak id=0x2 <auth pap>]
May 20 18:07:27 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:27 localhost pppd[6551]: sent [LCP ConfNak id=0x2 <auth pap>]
May 20 18:07:27 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:27 localhost pppd[6551]: sent [LCP ConfNak id=0x2 <auth pap>]
jwbohling@ubuntu:~$ plog
May 20 18:07:29 localhost pppd[6551]: sent [LCP ConfRej id=0x2 <auth chap MD5>]
May 20 18:07:29 localhost pppd[6551]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x4337eb0> <pcomp> <accomp>]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:30 localhost pppd[6551]: sent [LCP ConfRej id=0x2 <auth chap MD5>]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:30 localhost pppd[6551]: sent [LCP ConfRej id=0x2 <auth chap MD5>]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP TermReq id=0x3]
May 20 18:07:30 localhost pppd[6551]: sent [LCP TermAck id=0x3]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP TermReq id=0x4]
May 20 18:07:30 localhost pppd[6551]: sent [LCP TermAck id=0x4]
jwbohling@ubuntu:~$ plog
May 20 18:07:29 localhost pppd[6551]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x4337eb0> <pcomp> <accomp>]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:30 localhost pppd[6551]: sent [LCP ConfRej id=0x2 <auth chap MD5>]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP ConfReq id=0x2 <mru 1524> <asyncmap 0xa0000> <auth chap MD5> <pcomp> <accomp> <endpoint [MAC:00:d0:52:01:32:e7]>]
May 20 18:07:30 localhost pppd[6551]: sent [LCP ConfRej id=0x2 <auth chap MD5>]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP TermReq id=0x3]
May 20 18:07:30 localhost pppd[6551]: sent [LCP TermAck id=0x3]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP TermReq id=0x4]
May 20 18:07:30 localhost pppd[6551]: sent [LCP TermAck id=0x4]
May 20 18:07:32 localhost pppd[6551]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4337eb0> <pcomp> <accomp>]
jwbohling@ubuntu:~$ plog
May 20 18:07:30 localhost pppd[6551]: sent [LCP ConfRej id=0x2 <auth chap MD5>]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP TermReq id=0x3]
May 20 18:07:30 localhost pppd[6551]: sent [LCP TermAck id=0x3]
May 20 18:07:30 localhost pppd[6551]: rcvd [LCP TermReq id=0x4]
May 20 18:07:30 localhost pppd[6551]: sent [LCP TermAck id=0x4]
May 20 18:07:32 localhost pppd[6551]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4337eb0> <pcomp> <accomp>]
May 20 18:07:35 localhost pppd[6551]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4337eb0> <pcomp> <accomp>]
May 20 18:07:36 localhost pppd[6551]: Hangup (SIGHUP)
May 20 18:07:36 localhost pppd[6551]: Modem hangup
May 20 18:07:36 localhost pppd[6551]: Connection terminated.


jwbohling@ubuntu:~$ tail -f /var/log/messages
May 20 17:46:48 localhost pppd[8225]: Using interface ppp0
May 20 17:46:48 localhost pppd[8225]: Connect: ppp0 <--> /dev/modem
May 20 17:47:00 localhost pppd[8225]: Hangup (SIGHUP)
May 20 17:47:00 localhost pppd[8225]: Modem hangup
May 20 17:47:00 localhost pppd[8225]: Connection terminated.
May 20 17:47:17 localhost pppd[8225]: Terminating on signal 15.
May 20 17:47:17 localhost pppd[8225]: Exit.
May 20 17:48:14 localhost kernel: Loading Agere/Lucent WinModem Controller driver version 8.31
May 20 17:48:14 localhost kernel: Detected Parameters Irq=11 BaseAddress=0xd400 ComAddress=0xd000
May 20 17:48:14 localhost kernel: serial8250_init: uart_register_driver returns err code -16


Did I neglect to change something in one of the config files? When I set up my connection in PPP, I did not specify my DNS numbers; I choose the Dynamic DNS option. Thanks in advance for any replies.

---

### Post by David Kaisemann on 2005-05-21
Today i'm have same problem. Until I'm was don't specify DNS (Servers and Search Domains) and Host (local and remote) in Network settings I can't get stable connection to the Internet. After that all was started work OK.

---

### Post by Locke897 on 2005-05-22
Here are my PPP config files; hope they help.

/etc/ppp/peers/DSL:
[INDENT]
# This optionfile was generated by pppconfig 2.3.10. 
# 
#
hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/DSL"
debug
/dev/modem
115200
defaultroute
noipdefault 
user "********"
remotename DSL
ipparam DSL

persist
usepeerdns[/INDENT]

/etc/chatscripts/DSL:

[INDENT]# This chatfile was generated by pppconfig 2.3.10.
# Please do not delete any of the comments.  Pppconfig needs them.
# 
# ispauth PAP
# abortstring
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED
# modeminit
'' ATZ
# ispnumber
OK-AT-OK "ATL1DT2464087"
# ispconnect
CONNECT \d\c
# prelogin

# ispname
# isppassword
# postlogin

# end of pppconfig stuff[/INDENT]

Is there anything else (files, logs, etc) that I should post?

---

### Post by britbrian on 2005-05-23
Locke897

Try editing   /etc/ppp/options and change auth to noauth.

---

