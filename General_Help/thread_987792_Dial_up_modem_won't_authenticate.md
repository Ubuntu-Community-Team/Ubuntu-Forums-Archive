---
title: "Dial up modem won't authenticate"
date: 2008-11-19
forum: General Help
---

### Post by MyFathersSon on 2008-11-19
Hi!

I'm running 8.10 using a 3com internal modem.  I'm mostly using Gnome-ppp to connect, but tried wvdialconf with the same results.  Gnome-ppp was able to detect the modem and was able to dial, handshake, wait for and receive a response, but when it tried to authenticate the connection was dropped with "Authentication failed" put in the log (yes, I made sure I put in the correct user and pw).  I'm running a dual boot and was able to connect properly using Windows, so I know the modem is working.

I can't find anything in the documentation that deals specifically with this situation nor have I found anything in forums yet.  Any suggestions?

---

### Post by plucky on 2008-11-20
Not sure if this will help,but when I was using dial up,I had to have "stupid mode" ticked in Gnome-ppp.I think it is on the third tag.
Not sure why ,but that worked for me.


Good Luck

---

### Post by MyFathersSon on 2008-11-20
> **plucky said:**
> Not sure if this will help,but when I was using dial up,I had to have "stupid mode" ticked in Gnome-ppp.I think it is on the third tag.
Not sure why ,but that worked for me.


Good Luck

Thanks for responding, though I think I tried that.  But I'll give it a try.

Follow up: I tried the suggestion but it did not work.  Same problem.  I hope someone can help me.

---

### Post by editrix on 2008-11-21
Shot in the dark, but does your ISP require authentication? Mine doesn't, and with that option ticked in KPPP, the authentication fails.

Took me a while to figure out that username & password are something different from authentication.

---

### Post by MyFathersSon on 2008-11-21
Thanks.  I'll try it.

Editrix: I loaded kppp, but I can't find the place to deselect authentication.  When I connect to the ISP using windows, the Authentication Method is PAP.  I'm not sure but I believe this forces client side authentication (i.e., I have to authenticate myself to the server, but the server doesn't have to authenticate to me).  But even with PAP selected, authentication still fails.  Does the option you refer to indicate no authentication on either side?

---

### Post by plucky on 2008-11-22
According to this [Howto setup Dialup modem](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?highlight=(howto)|(modem)) you
> If you have problems with Authentification, you might want to edit /etc/ppp/peers/kppp-options and activate the line noauth by removing the comment sign. 


Hope this helps.

---

### Post by editrix on 2008-11-22
> **MyFathersSon said:**
> I loaded kppp, but I can't find the place to deselect authentication.

Whoops! I can't find it either. Might have been an older version, or maybe an halucination. Sorry about that.

In any case, here's the *entire* contents of my /etc/ppp/peers/kppp-options:

```
noauth
```

That's it, one line.

And, if this may help:

> /etc/ppp/peers/ppp0:

connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"
defaultroute

/dev/ttyS0
115200
user "myloginname" [replace with your login name]

> /etc/ppp/peers/provider
# example configuration for a dialup connection authenticated with PAP or CHAP
#
# This is the default configuration used by pon(1) and poff(1).
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "myusername@realm"

# MUST CHANGE: replace ******** with the phone number of your provider.
# The /etc/chatscripts/pap chat script may be modified to change the
# modem initialization string.
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T ********"

# Serial device to which the modem is connected.
/dev/modem

# Speed of the serial line.
115200

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth

You'll note that "myusername@realm" has NOT been changed to my real login name. How odd, it still works.

BTW, I configured none of this, with the possible exception of the "noauth" by editing files. It was all set up with KPPP.

And here's my /etc/ppp/peers/wvdial--not that I ever configured wvdial.

> noauth
name wvdial
usepeerdns

Edit: I discovered I have a wvdial.conf too:
> Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
Init = ATZ
Phone = XXXXXXXXXXX
Username = myloginname
Password = mypassword
New PPPD = yes

Dial Command = ATDP

Needless to say, change 
Phone = XXXXXXXXXXX
Username = myloginname
Password = mypassword

to what's appropriate for you.

I suggest you use something gui to configure, then check these files against your own.

Oh, and if you decide to use KPPP, and you're using Gnome, don't let it dock in the panel--I find it gets confused, because it's not the KDE panel it's docking into.

---

### Post by MyFathersSon on 2008-11-22
Editrix: Thanks again for the info.  I'll check it out.  I'm beginning to think that it is a issue of prompt/response.  I don't know how PAP works but if the server is prompting and the modem is looking for something from the server that the server is not supplying then confusion reigns and a timeout is reached.  I don't see anything in the logs that gives me a clue.  Maybe my ISP can help me.  From what I've seen in the various files I've looked at, everything looks similar to what you have provided.  But I'll take a closer look.  Thanks very much.

Followup: I checked everything out and all looks correct.  I checked other info sources on setting up dialup in linux and arrived at the same conclusion.  The following is the output of plog (I used pon):
===============
mrl@mrl-desktop:~$ pon <name removed>
mrl@mrl-desktop:~$ plog
Nov 24 11:01:34 mrl-desktop chat[5626]: ATZ^M^M
Nov 24 11:01:34 mrl-desktop chat[5626]: OK
Nov 24 11:01:34 mrl-desktop chat[5626]:  -- got it 
Nov 24 11:01:34 mrl-desktop chat[5626]: send (ATDT<number removed>^M)
Nov 24 11:01:34 mrl-desktop chat[5626]: expect (CONNECT)
Nov 24 11:01:34 mrl-desktop chat[5626]: ^M
Nov 24 11:02:01 mrl-desktop chat[5626]: ATDT<number removed>^M^M
Nov 24 11:02:01 mrl-desktop chat[5626]: CONNECT
Nov 24 11:02:01 mrl-desktop chat[5626]:  -- got it 
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

I can't see any clue as to why authentication has failed.  Hope someone else can see something.

---

### Post by MyFathersSon on 2008-11-24
Does anyone know how to open a modem terminal session where I can communicate directly with the modem to enter AT commands?

---

