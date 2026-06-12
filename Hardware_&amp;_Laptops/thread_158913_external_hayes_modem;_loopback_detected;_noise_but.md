---
title: "external hayes modem; loopback detected; noise but no results; ?log messages?"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by rolypolycat on 2006-04-11
Hello!
First of all, i apologize for the length of this post, but I wanted to make sure I included enough information to help. I have a Hayes Accura 56k + fax external serial modem, model 5674US on ttyS1 (com 2). I've tried several things to get this little monster working, and this is what I have so far.
1. created wvdial.conf file because there wasn't one. edited wvdial.conf. setup modem through Networking under System. modem makes noise; does nothing. network and wvdial can't find modem unless I add link /dev/modem, instead of correct port.
2. re-installed Ubuntu Breezy with modem connected and on.  edited chatscripts that had little or no info in them. edited wvdial.conf with correct info in it. edited ppp scripts with correct sign-on info.  modem makes noise; sits there.
3. Used info from Dial-up on Ubuntu Howtos to set up ppp file from command line. made logfiles of modem under wvdial and pon (from command line; I gave up just using Network under System) Here are the logs from PLOG< WVDIAL, and tail -f syslog:

PLOG:
michelle@mainframe:~$ pon
michelle@mainframe:~$ plog
Apr  9 01:37:52 localhost chat[8571]: ^M
Apr  9 01:38:16 localhost chat[8571]: ATDT8225473^M^M
Apr  9 01:38:16 localhost chat[8571]: CONNECT
Apr  9 01:38:16 localhost chat[8571]:  -- got it
Apr  9 01:38:16 localhost chat[8571]: send (\d)
Apr  9 01:38:17 localhost pppd[8566]: Serial connection established.
Apr  9 01:38:17 localhost pppd[8566]: using channel 1
Apr  9 01:38:17 localhost pppd[8566]: Using interface ppp0
Apr  9 01:38:17 localhost pppd[8566]: Connect: ppp0 <--> /dev/ttyS1
Apr  9 01:38:18 localhost pppd[8566]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <m agic 0xdd706821> <pcomp> <accomp>]
michelle@mainframe:~$ plog
Apr  9 01:37:52 localhost chat[8571]: ^M
Apr  9 01:38:16 localhost chat[8571]: ATDT8225473^M^M
Apr  9 01:38:16 localhost chat[8571]: CONNECT
Apr  9 01:38:16 localhost chat[8571]:  -- got it
Apr  9 01:38:16 localhost chat[8571]: send (\d)
Apr  9 01:38:17 localhost pppd[8566]: Serial connection established.
Apr  9 01:38:17 localhost pppd[8566]: using channel 1
Apr  9 01:38:17 localhost pppd[8566]: Using interface ppp0
Apr  9 01:38:17 localhost pppd[8566]: Connect: ppp0 <--> /dev/ttyS1
Apr  9 01:38:18 localhost pppd[8566]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xdd706821> <pcomp> <accomp>]
michelle@mainframe:~$ plog
Apr  9 01:38:42 localhost pppd[8566]: rcvd [LCP ConfReq id=0xa <asyncmap 0x0> <magic 0xf193e1ca> <pcomp> <accomp>]
Apr  9 01:38:42 localhost pppd[8566]: sent [LCP ConfNak id=0xa <magic 0xe69f51c4>]
Apr  9 01:38:42 localhost pppd[8566]: rcvd [LCP ConfNak id=0xa <magic 0xe69f51c4>]
Apr  9 01:38:42 localhost pppd[8566]: Serial line is looped back.
Apr  9 01:38:42 localhost pppd[8566]: sent [LCP TermReq id=0xb "Loopback detected"]
Apr  9 01:38:42 localhost pppd[8566]: rcvd [LCP TermReq id=0xb "Loopback detected"]
Apr  9 01:38:42 localhost pppd[8566]: sent [LCP TermAck id=0xb]
Apr  9 01:38:42 localhost pppd[8566]: rcvd [LCP TermAck id=0xb]
Apr  9 01:38:42 localhost pppd[8566]: Connection terminated.
Apr  9 01:38:43 localhost pppd[8566]: Exit.
michelle@mainframe:~$ pon
michelle@mainframe:~$ plog
Apr  9 01:45:42 localhost chat[8824]: abort on (NO ANSWER)
Apr  9 01:45:42 localhost chat[8824]: abort on (DELAYED)
Apr  9 01:45:42 localhost chat[8824]: send (ATZ^M)
Apr  9 01:45:42 localhost chat[8824]: expect (OK)
Apr  9 01:45:42 localhost chat[8824]: ATZ^M^M
Apr  9 01:45:42 localhost chat[8824]: OK
Apr  9 01:45:42 localhost chat[8824]:  -- got it
Apr  9 01:45:42 localhost chat[8824]: send (ATDT8225473^M)
Apr  9 01:45:43 localhost chat[8824]: expect (CONNECT)
Apr  9 01:45:43 localhost chat[8824]: ^M
michelle@mainframe:~$ plog
Apr  9 01:45:42 localhost chat[8824]: abort on (NO ANSWER)
Apr  9 01:45:42 localhost chat[8824]: abort on (DELAYED)
Apr  9 01:45:42 localhost chat[8824]: send (ATZ^M)
Apr  9 01:45:42 localhost chat[8824]: expect (OK)
Apr  9 01:45:42 localhost chat[8824]: ATZ^M^M
Apr  9 01:45:42 localhost chat[8824]: OK
Apr  9 01:45:42 localhost chat[8824]:  -- got it
Apr  9 01:45:42 localhost chat[8824]: send (ATDT8225473^M)
Apr  9 01:45:43 localhost chat[8824]: expect (CONNECT)
Apr  9 01:45:43 localhost chat[8824]: ^M
michelle@mainframe:~$ plog
Apr  9 01:45:42 localhost chat[8824]: abort on (NO ANSWER)
Apr  9 01:45:42 localhost chat[8824]: abort on (DELAYED)
Apr  9 01:45:42 localhost chat[8824]: send (ATZ^M)
Apr  9 01:45:42 localhost chat[8824]: expect (OK)
Apr  9 01:45:42 localhost chat[8824]: ATZ^M^M
Apr  9 01:45:42 localhost chat[8824]: OK
Apr  9 01:45:42 localhost chat[8824]:  -- got it
Apr  9 01:45:42 localhost chat[8824]: send (ATDT8225473^M)
Apr  9 01:45:43 localhost chat[8824]: expect (CONNECT)
Apr  9 01:45:43 localhost chat[8824]: ^M
michelle@mainframe:~$ plog
Apr  9 01:46:33 localhost pppd[8823]: rcvd [LCP ConfReq id=0xa <asyncmap 0x0> <magic 0x495ef85b> <pcomp> <accomp>]
Apr  9 01:46:33 localhost pppd[8823]: sent [LCP ConfNak id=0xa <magic 0x4a0a3381>]
Apr  9 01:46:33 localhost pppd[8823]: rcvd [LCP ConfNak id=0xa <magic 0x4a0a3381>]
Apr  9 01:46:33 localhost pppd[8823]: Serial line is looped back.
Apr  9 01:46:33 localhost pppd[8823]: sent [LCP TermReq id=0xb "Loopback detected"]
Apr  9 01:46:33 localhost pppd[8823]: rcvd [LCP TermReq id=0xb "Loopback detected"]
Apr  9 01:46:33 localhost pppd[8823]: sent [LCP TermAck id=0xb]
Apr  9 01:46:33 localhost pppd[8823]: rcvd [LCP TermAck id=0xb]
Apr  9 01:46:33 localhost pppd[8823]: Connection terminated.
Apr  9 01:46:34 localhost pppd[8823]: Exit.

PON FILE
Apr  9 02:19:13 localhost pppd[9856]: pppd 2.4.3 started by michelle, uid 1000
Apr  9 02:19:14 localhost chat[9857]: abort on (BUSY)
Apr  9 02:19:14 localhost chat[9857]: abort on (NO CARRIER)
Apr  9 02:19:14 localhost chat[9857]: abort on (VOICE)
Apr  9 02:19:14 localhost chat[9857]: abort on (NO DIALTONE)
Apr  9 02:19:14 localhost chat[9857]: abort on (NO DIAL TONE)
Apr  9 02:19:14 localhost chat[9857]: abort on (NO ANSWER)
Apr  9 02:19:14 localhost chat[9857]: abort on (DELAYED)
Apr  9 02:19:14 localhost chat[9857]: send (ATZ^M)
Apr  9 02:19:14 localhost chat[9857]: expect (OK)
Apr  9 02:19:14 localhost chat[9857]: ATZ^M^M
Apr  9 02:19:14 localhost chat[9857]: OK
Apr  9 02:19:14 localhost chat[9857]:  -- got it
Apr  9 02:19:14 localhost chat[9857]: send (ATDT8225473^M)
Apr  9 02:19:14 localhost chat[9857]: expect (CONNECT)
Apr  9 02:19:14 localhost chat[9857]: ^M
Apr  9 02:19:38 localhost chat[9857]: ATDT8225473^M^M
Apr  9 02:19:38 localhost chat[9857]: CONNECT
Apr  9 02:19:38 localhost chat[9857]:  -- got it
Apr  9 02:19:38 localhost chat[9857]: send (\d)
Apr  9 02:19:39 localhost pppd[9856]: Serial connection established.
Apr  9 02:19:39 localhost pppd[9856]: using channel 3
Apr  9 02:19:39 localhost pppd[9856]: Using interface ppp0
Apr  9 02:19:39 localhost pppd[9856]: Connect: ppp0 <--> /dev/ttyS1
Apr  9 02:19:40 localhost pppd[9856]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x37cdabf3> <pcomp> <accomp>]
Apr  9 02:20:05 localhost last message repeated 8 times
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x37cdabf3> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x1 <magic 0x1108a49f>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x1 <magic 0x1108a49f>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xa08949e4> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xa08949e4> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x2 <magic 0xcdeaba3b>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x2 <magic 0xcdeaba3b>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x3 <asyncmap 0x0> <magic 0xa4ea1177> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <magic 0xa4ea1177> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x3 <magic 0x4ff4f5fd>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x3 <magic 0x4ff4f5fd>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xbe279c3f> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xbe279c3f> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x4 <magic 0x4202edaf>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x4 <magic 0x4202edaf>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x5 <asyncmap 0x0> <magic 0x42be821a> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x5 <asyncmap 0x0> <magic 0x42be821a> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x5 <magic 0x8c1b2c5a>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x5 <magic 0x8c1b2c5a>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x6 <asyncmap 0x0> <magic 0x68d83f79> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x6 <asyncmap 0x0> <magic 0x68d83f79> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x6 <magic 0xffcab1f1>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x6 <magic 0xffcab1f1>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x7 <asyncmap 0x0> <magic 0xcf03368a> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x7 <asyncmap 0x0> <magic 0xcf03368a> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x7 <magic 0x9953e3e>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x7 <magic 0x9953e3e>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x8 <asyncmap 0x0> <magic 0x2832d3ee> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x8 <asyncmap 0x0> <magic 0x2832d3ee> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x8 <magic 0xbfbd0681>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x8 <magic 0xbfbd0681>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0x9 <asyncmap 0x0> <magic 0x7c19f3f4> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0x9 <asyncmap 0x0> <magic 0x7c19f3f4> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0x9 <magic 0x8ef0949b>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0x9 <magic 0x8ef0949b>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfReq id=0xa <asyncmap 0x0> <magic 0x86e736c> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfReq id=0xa <asyncmap 0x0> <magic 0x86e736c> <pcomp> <accomp>]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP ConfNak id=0xa <magic 0xbddedfbe>]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP ConfNak id=0xa <magic 0xbddedfbe>]
Apr  9 02:20:05 localhost pppd[9856]: Serial line is looped back.
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP TermReq id=0xb "Loopback detected"]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP TermReq id=0xb "Loopback detected"]
Apr  9 02:20:05 localhost pppd[9856]: sent [LCP TermAck id=0xb]
Apr  9 02:20:05 localhost pppd[9856]: rcvd [LCP TermAck id=0xb]
Apr  9 02:20:05 localhost pppd[9856]: Connection terminated.
Apr  9 02:20:06 localhost pppd[9856]: Exit.

WVDIAL LOG
michelle@mainframe:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT822-5473
--> Waiting for carrier.
ATDT822-5473
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Apr  9 01:53:44 2006
--> pid of pppd: 9086
******************************************
It just sits there after this; no new lines in the log, no new info.
*******************************************
TAIL -F /VAR/LOG/SYSLOG
michelle@mainframe:~$ tail -f /var/log/syslog
Apr  9 01:46:33 localhost pppd[8823]: sent [LCP ConfNak id=0xa <magic 0x4a0a3381 >]
Apr  9 01:46:33 localhost pppd[8823]: rcvd [LCP ConfNak id=0xa <magic 0x4a0a3381 >]
Apr  9 01:46:33 localhost pppd[8823]: Serial line is looped back.
Apr  9 01:46:33 localhost pppd[8823]: sent [LCP TermReq id=0xb "Loopback detecte d"]
Apr  9 01:46:33 localhost pppd[8823]: rcvd [LCP TermReq id=0xb "Loopback detecte d"]
Apr  9 01:46:33 localhost pppd[8823]: sent [LCP TermAck id=0xb]
Apr  9 01:46:33 localhost pppd[8823]: rcvd [LCP TermAck id=0xb]
Apr  9 01:46:33 localhost pppd[8823]: Connection terminated.
Apr  9 01:46:34 localhost pppd[8823]: Exit.
Apr  9 01:53:45 localhost pppd[9086]: pppd 2.4.3 started by root, uid 0


WVDIAL OPTIONS
michelle@mainframe:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT822-5473
--> Waiting for carrier.
ATDT822-5473
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Apr  9 02:15:06 2006
--> pid of pppd: 9726

I don't understand these results. it makes all the noise; the lights flash, but nothing happens, or it's terminated, if I'm reading this right. What is a "loopback" and all this "magic" stuff mentioned in the logs? I can't find anything on this in the forums so far.
Any help will be greatly appreciated. Thanks!!

---

