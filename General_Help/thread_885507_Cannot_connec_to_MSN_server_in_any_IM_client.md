---
title: "Cannot connec to MSN server in any IM client"
date: 2008-08-10
forum: General Help
---

### Post by JCoster on 2008-08-10
Hi there.

I've recently come back to Ubuntu and installed 8.04.

However, I cannot connect to MSN on any client I have tried; aMSN, Kopete, Mercury nor Pidgin.

I have no software firewall and I just have a basic Netgear router.  

This problem has been occurring for over a week and so I do not think it is a problem with the MSN servers.  

The errors I'm getting refer to not being able to connect to messenger.hotmail.com:1863

I can connect to webmessenger.msn.com and I'm at a loss of what to do to fix this problem.

The Pidgin error log is as follows:
```
Pidgin Debug Log : Sun 10 Aug 2008 11:29:32 BST
(11:29:21) account: Connecting to account james@*********.net
(11:29:21) connection: Connecting. gc = 0x8670f50
(11:29:21) msn: new httpconn (0x8672af0)
(11:29:21) dns: DNS query for 'messenger.hotmail.com' queued
(11:29:21) util: requested to fetch (http://192.168.0.1:49153/gateway.xml), full=1, user_agent=((null)), http11=1
(11:29:21) dns: DNS query for '192.168.0.1' queued
(11:29:21) Session Management: Received first save_yourself
(11:29:21) dns: Created new DNS child 10903, there are now 1 children.
(11:29:21) dns: Successfully sent DNS request to child 10903
(11:29:21) Session Management: Received save_complete
(11:29:21) dns: Created new DNS child 10904, there are now 2 children.
(11:29:21) dns: Successfully sent DNS request to child 10904
(11:29:21) dns: Got response for '192.168.0.1'
(11:29:21) dnsquery: IP resolved for 192.168.0.1
(11:29:21) proxy: Attempting connection to 192.168.0.1
(11:29:21) proxy: Connecting to 192.168.0.1:49153 with no proxy
(11:29:21) proxy: Connection in progress
(11:29:21) proxy: Connected to 192.168.0.1:49153.
(11:29:21) util: Request: 'GET /gateway.xml HTTP/1.1

Connection: close

Host: 192.168.0.1:49153



'
(11:29:21) docklet: embedded
(11:29:21) prefs: /pidgin/blist/width changed, scheduling save.
(11:29:21) prefs: /pidgin/blist/height changed, scheduling save.
(11:29:21) util: Response headers: 'HTTP/1.1 200 OK

CONTENT-LENGTH: 3124

CONTENT-TYPE: text/xml

DATE: Sun, 10 Aug 2008 10:29:24 GMT

LAST-MODIFIED: Sat, 01 Jan 2000 00:00:31 GMT

SERVER: Linux/2.6.8.1, UPnP/1.0, Intel SDK for UPnP devices /1.2

CONNECTION: close



'
(11:29:21) util: parsed 3124
(11:29:21) prefs: /pidgin/blist/width changed, scheduling save.
(11:29:21) prefs: /pidgin/blist/height changed, scheduling save.
(11:29:21) util: requested to fetch (http://192.168.0.1:49152/upnp/control/WANIPConnection), full=0, user_agent=((null)), http11=1
(11:29:21) dns: DNS query for '192.168.0.1' queued
(11:29:21) dns: DNS query for '192.168.0.1' queued
(11:29:21) dns: Got response for 'messenger.hotmail.com'
(11:29:21) dnsquery: IP resolved for messenger.hotmail.com
(11:29:21) proxy: Attempting connection to 65.54.239.20
(11:29:21) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(11:29:21) proxy: Connection in progress
(11:29:21) dns: Created new DNS child 10907, there are now 1 children.
(11:29:21) dns: Successfully sent DNS request to child 10907
(11:29:21) dns: Created new DNS child 10908, there are now 2 children.
(11:29:21) dns: Successfully sent DNS request to child 10908
(11:29:21) proxy: Connected to messenger.hotmail.com:1863.
(11:29:21) proxy: Error connecting to messenger.hotmail.com:1863 (Connection refused).
(11:29:21) proxy: Connection attempt failed: Connection refused
(11:29:21) msn: Connection error: Connection refused
(11:29:21) msn: Connection error from Notification server (messenger.hotmail.com): Unable to connect
(11:29:21) dns: Got response for '192.168.0.1'
(11:29:21) dnsquery: IP resolved for 192.168.0.1
(11:29:21) proxy: Attempting connection to 192.168.0.1
(11:29:21) proxy: Connecting to 192.168.0.1:49152 with no proxy
(11:29:21) proxy: Connection in progress
(11:29:21) dns: Got response for '192.168.0.1'
(11:29:21) dnsquery: IP resolved for 192.168.0.1
(11:29:21) proxy: Attempting connection to 192.168.0.1
(11:29:21) proxy: Connecting to 192.168.0.1:49152 with no proxy
(11:29:21) proxy: Connection in progress
(11:29:21) account: Disconnecting account 0x817f7a8
(11:29:21) connection: Disconnecting connection 0x8670f50
(11:29:21) msn: destroy httpconn (0x8672af0)
(11:29:21) connection: Destroying connection 0x8670f50
(11:29:21) proxy: Connected to 192.168.0.1:49152.
(11:29:21) proxy: Error connecting to 192.168.0.1:49152 (Connection refused).
(11:29:21) proxy: Connection attempt failed: Connection refused
(11:29:21) proxy: Connected to 192.168.0.1:49152.
(11:29:21) proxy: Error connecting to 192.168.0.1:49152 (Connection refused).
(11:29:21) proxy: Connection attempt failed: Connection refused
(11:29:21) upnp: Local IP: 192.168.0.9
(11:29:21) network: Entering nm_callback_func!
(11:29:21) autorecon: do_signon called
(11:29:21) autorecon: calling purple_account_connect
(11:29:21) account: Connecting to account james@******.net
(11:29:21) connection: Connecting. gc = 0x86abd00
(11:29:21) msn: new httpconn (0x867e148)
(11:29:21) dns: DNS query for 'messenger.hotmail.com' queued
(11:29:21) autorecon: done calling purple_account_connect
(11:29:21) dns: Created new DNS child 10909, there are now 1 children.
(11:29:21) dns: Successfully sent DNS request to child 10909
(11:29:21) dns: Got response for 'messenger.hotmail.com'
(11:29:21) dnsquery: IP resolved for messenger.hotmail.com
(11:29:21) proxy: Attempting connection to 65.54.239.20
(11:29:21) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(11:29:21) proxy: Connection in progress
(11:29:21) proxy: Connected to messenger.hotmail.com:1863.
(11:29:21) proxy: Error connecting to messenger.hotmail.com:1863 (Connection refused).
(11:29:21) proxy: Connection attempt failed: Connection refused
(11:29:21) msn: Connection error: Connection refused
(11:29:21) msn: Connection error from Notification server (messenger.hotmail.com): Unable to connect
(11:29:21) account: Disconnecting account 0x817f7a8
(11:29:21) connection: Disconnecting connection 0x86abd00
(11:29:21) msn: destroy httpconn (0x867e148)
(11:29:22) connection: Destroying connection 0x86abd00
(11:29:26) util: Writing file prefs.xml to directory /home/jcoster/.purple
(11:29:26) util: Writing file /home/jcoster/.purple/prefs.xml
(11:29:26) util: Writing file accounts.xml to directory /home/jcoster/.purple
(11:29:26) util: Writing file /home/jcoster/.purple/accounts.xml
(11:29:26) util: Writing file blist.xml to directory /home/jcoster/.purple
(11:29:26) util: Writing file /home/jcoster/.purple/blist.xml
(11:29:32) prefs: /pidgin/filelocations/last_save_folder changed, scheduling save.
```

Any ideas?

Thanks in advance.

---

### Post by jimv on 2008-08-10
"Error connecting to messenger.hotmail.com:1863 (Connection refused)."

It's not you, MSN changed something on their end.  You'll see updates for you IM clients soon.

---

### Post by JCoster on 2008-08-10
Ok thanks, so is everyone having this problem at the moment then?

---

### Post by diffuze on 2008-08-10
I am connected to msn through Pidgin without any problems.

---

### Post by ragflan on 2008-08-10
I personally love Pidgin. But I've been using Emesene for a month or so now and I couldn't be happier.

Try Emesene. I'm running it without any problems, and best of all it looks better than Pidgin to me and it looks more like Windows Live Messenger (which is not the best messenger around, but I like the way it looks). [http://www.emesene.org/](http://www.emesene.org/) It's also available in the repositories. So, open up Synaptic Package Manager and search for Emesene. 

Also, the current version sometimes does not load up the contact list. So, try the SVN version on this page: [http://emesene.org/trac/](http://emesene.org/trac/) Installation steps are easy to follow. 

Let me know if it works!

---

### Post by JCoster on 2008-08-10
Ok, thanks for that.

I've got Emesene running but only by using 'HTTP Method'.  Without this I just got a connection failed error.

I think there's something screwed up in my network somewhere.  Any ideas what it could be?

---

### Post by impy1980 on 2008-09-08
Great help thanks, got it working for me! Also good to know MSN has changed it's login system or whatever was said, I forget now and it's nothing to do with me, tried using Pidgin and aMSN with no sucess, although the first ever time I did get my *@hotmail.com account to work with Pidgin under openSUSE but then I decided to change to Ubuntu. Emesene also lets me log into my *@hotmail.co.uk, sweet! Now all I'd like on first use is webcam capabilities and maybe Yahoo, contrary to belief there are UK users of Yahoo.

I'm a Linux newbie, although I think I like openSUSE's interface a bit more, Ubuntu is much easier when installing programs and finding more readily compatible programs.

Now all I need to find is a browser and/or plugin that will play/run Flash/Java type videos and chat room.

I'm looking for an excuse to ditch Windows now, a year ago I played with the idea of Linux, partitioned my hard drive slightly wrong before I had downloaded Linux and I couldn't install it how I wanted, so left it. But 2 weeks ago got a devastating virus that really messed up Windows so had to re-install it, giving me the perfect opportunity to install Linux, and I really like it, once I know it'll do everything I do under Windows then it'll be my primary OS.

> **JCoster said:**
> Ok, thanks for that.

I've got Emesene running but only by using 'HTTP Method'.  Without this I just got a connection failed error.

I think there's something screwed up in my network somewhere.  Any ideas what it could be?

---

### Post by kol on 2008-09-08
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by TheLions on 2008-09-08
new version of aMSN (0.97.2) is working now...

[http://packages.ubuntu.com/intrepid/amsn-data](http://packages.ubuntu.com/intrepid/amsn-data)
[http://packages.ubuntu.com/intrepid/tcl-tls](http://packages.ubuntu.com/intrepid/tcl-tls)
[http://packages.ubuntu.com/intrepid/amsn](http://packages.ubuntu.com/intrepid/amsn)

---

### Post by connorh123 on 2008-09-27
Hey guys. Pidgin works perfectly for me, just messenger is something I can't get running. I've tried putting it in winecfg, but still nothing ](*,)

---

