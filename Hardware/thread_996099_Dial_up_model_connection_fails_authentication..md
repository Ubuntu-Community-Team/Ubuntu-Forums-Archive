---
title: "Dial up model connection fails authentication."
date: 2008-11-28
forum: Hardware
---

### Post by MyFathersSon on 2008-11-28
Hi,

I looked for help in the General forum to no avail, so I'm hoping I can solve my problem here.

I'm running 8.10 using a 3com (USR) internal modem. Ubuntu detects the modem, I can dial the ISP, negotiation appears to be successful (i.e., no errors reported in the log), but authentication fails.  I’ve tried different methods of connecting (Gnome-ppp, kppp, Kermit, pppconfig/pon) but all fail at the authentication stage.

I’ve tested the modem using Windows and was able to connect with out any problem.  Windows reports the following on the connection:
============
Device Name: U.S. Robotics 56K Fax PCI
Device Type: modem
Server Type: PPP
Transports: TCP/IP
Authentication: PAP
Compression: (none)
PPP multilink framing: Off
Server IP address: <removed>
Client IP address: <removed>
=============

I don’t know what certain of these settings are set to in Ubuntu.  I use PAP, so that should not be a problem unless there is a problem in the Linux PAP routine.  I don’t know if things like compression and multilink framing will make a difference and are set differently in Ubuntu.

For your edification and reading enjoyment, the following is the output of plog; I don’t see any clue as to what the problem might be:
===============
mrl@mrl-desktop:~$ pon <name removed>
mrl@mrl-desktop:~$ plog
Nov 24 11:01:34 mrl-desktop chat[5626]: ATZ^M^M
Nov 24 11:01:34 mrl-desktop chat[5626]: OK
Nov 24 11:01:34 mrl-desktop chat[5626]: -- got it 
Nov 24 11:01:34 mrl-desktop chat[5626]: send (ATDT<number removed>^M)
Nov 24 11:01:34 mrl-desktop chat[5626]: expect (CONNECT)
Nov 24 11:01:34 mrl-desktop chat[5626]: ^M
Nov 24 11:02:01 mrl-desktop chat[5626]: ATDT<number removed>^M^M
Nov 24 11:02:01 mrl-desktop chat[5626]: CONNECT
Nov 24 11:02:01 mrl-desktop chat[5626]: -- got it 
Nov 24 11:02:01 mrl-desktop chat[5626]: send (\d)
mrl@mrl-desktop:~$ plog
Nov 24 11:02:02 mrl-desktop pppd[5624]: using channel 2
Nov 24 11:02:02 mrl-desktop pppd[5624]: Using interface ppp0
Nov 24 11:02:02 mrl-desktop pppd[5624]: Connect: ppp0 <--> /dev/ttyS1
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa1a7c35d> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: rcvd [LCP ConfReq id=0xf0 <asyncmap 0xa0000> <auth pap> <magic 0xbfc8f45f> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [LCP ConfAck id=0xf0 <asyncmap 0xa0000> <auth pap> <magic 0xbfc8f45f> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xa1a7c35d> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [LCP EchoReq id=0x0 magic=0xa1a7c35d]
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [PAP AuthReq id=0x1 user="<name removed>" password=<hidden>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: rcvd [LCP EchoRep id=0x0 magic=0xbfc8f45f]
mrl@mrl-desktop:~$ plog
Nov 24 11:02:02 mrl-desktop pppd[5624]: Using interface ppp0
Nov 24 11:02:02 mrl-desktop pppd[5624]: Connect: ppp0 <--> /dev/ttyS1
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa1a7c35d> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: rcvd [LCP ConfReq id=0xf0 <asyncmap 0xa0000> <auth pap> <magic 0xbfc8f45f> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [LCP ConfAck id=0xf0 <asyncmap 0xa0000> <auth pap> <magic 0xbfc8f45f> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xa1a7c35d> <pcomp> <accomp>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [LCP EchoReq id=0x0 magic=0xa1a7c35d]
Nov 24 11:02:03 mrl-desktop pppd[5624]: sent [PAP AuthReq id=0x1 user="<name removed>" password=<hidden>]
Nov 24 11:02:03 mrl-desktop pppd[5624]: rcvd [LCP EchoRep id=0x0 magic=0xbfc8f45f]
Nov 24 11:02:06 mrl-desktop pppd[5624]: sent [PAP AuthReq id=0x2 user="<name removed" password=<hidden>]
mrl@mrl-desktop:~$ plog
Nov 24 11:02:09 mrl-desktop pppd[5624]: sent [PAP AuthReq id=0x3 user=",name removed>" password=<hidden>]
Nov 24 11:02:12 mrl-desktop pppd[5624]: rcvd [PAP AuthNak id=0x3 "Authentication failed"]
Nov 24 11:02:12 mrl-desktop pppd[5624]: Remote message: Authentication failed
Nov 24 11:02:12 mrl-desktop pppd[5624]: PAP authentication failed
Nov 24 11:02:12 mrl-desktop pppd[5624]: sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
Nov 24 11:02:12 mrl-desktop pppd[5624]: rcvd [LCP TermReq id=0xf1]
Nov 24 11:02:12 mrl-desktop pppd[5624]: sent [LCP TermAck id=0xf1]
Nov 24 11:02:12 mrl-desktop pppd[5624]: rcvd [LCP TermAck id=0x2]
Nov 24 11:02:12 mrl-desktop pppd[5624]: Connection terminated.
Nov 24 11:02:12 mrl-desktop pppd[5624]: Exit.
====================

Hope someone can give me a clue.  A friend of mine recommended using Suse or Fedora instead because they are better with hardware than Ubuntu.  I like Ubuntu and would prefer to stick with it, but I have to get the modem working.  I’m not a Microsoft or a Windows fan, in fact one of my favourite pastimes is to rant on them, but you have to admit, Windows works well with most hardware.  I know, I know, hardware manufactures build their products for Windows and not Linux, but still…  

That being said, except for the modem and my newer Samsung printer (which, buy the way includes a linux driver on the CD…I just haven’t installed it yet), Ubuntu did a pretty good job of seeing and configuring my hardware, including the wireless network.  Vastly improved.  Nearly there guys.

---

