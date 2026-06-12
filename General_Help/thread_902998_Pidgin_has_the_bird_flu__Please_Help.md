---
title: "Pidgin has the bird flu  Please Help"
date: 2008-08-27
forum: General Help
---

### Post by dh04000 on 2008-08-27
My copy of Pidgin isn't working anymore. I have already used the package manager to reinstall it, but it still doesn't work.

I can get it to start up, but when I sign in, it crashes just as the screen with all of the people online show up.

I ran the debug window and got this:

(20:49:56) account: Connecting to account Hinatarockz
(20:49:56) account: Connecting to account Hinatarockz
(20:49:56) Session Management: Received first save_yourself
(20:49:56) Session Management: Received save_complete
(20:49:56) docklet: embedded
(20:49:56) network: Entering nm_callback_func!
(20:49:56) autorecon: do_signon called
(20:49:56) autorecon: calling purple_account_connect
(20:49:56) account: Connecting to account Hinatarockz
(20:49:56) autorecon: done calling purple_account_connect
(20:50:01) util: Writing file prefs.xml to directory /home/devin/.purple
(20:50:01) util: Writing file /home/devin/.purple/prefs.xml
(20:50:01) util: Writing file accounts.xml to directory /home/devin/.purple
(20:50:01) util: Writing file /home/devin/.purple/accounts.xml
(20:50:01) util: Writing file blist.xml to directory /home/devin/.purple
(20:50:01) util: Writing file /home/devin/.purple/blist.xml
(21:09:21) connection: Connecting. gc = 0x865d7c8
(21:09:21) oscar: registered module misc (family 0xffff, version = 0x0000, tool 0x0000, tool version 0x0000)
(21:09:21) oscar: registered module oservice (family 0x0001, version = 0x0003, tool 0x0110, tool version 0x0629)
(21:09:21) oscar: registered module locate (family 0x0002, version = 0x0001, tool 0x0110, tool version 0x0629)
(21:09:21) oscar: registered module buddy (family 0x0003, version = 0x0001, tool 0x0110, tool version 0x0629)
(21:09:21) oscar: registered module messaging (family 0x0004, version = 0x0001, tool 0x0110, tool version 0x0629)
(21:09:21) oscar: registered module admin (family 0x0007, version = 0x0001, tool 0x0010, tool version 0x0629)
(21:09:21) oscar: registered module popup (family 0x0008, version = 0x0001, tool 0x0104, tool version 0x0001)
(21:09:21) oscar: registered module bos (family 0x0009, version = 0x0001, tool 0x0110, tool version 0x0629)
(21:09:21) oscar: registered module userlookup (family 0x000a, version = 0x0001, tool 0x0110, tool version 0x0629)
(21:09:21) oscar: registered module stats (family 0x000b, version = 0x0001, tool 0x0104, tool version 0x0001)
(21:09:21) oscar: registered module chatnav (family 0x000d, version = 0x0001, tool 0x0010, tool version 0x0629)
(21:09:21) oscar: registered module chat (family 0x000e, version = 0x0001, tool 0x0010, tool version 0x0629)
(21:09:21) oscar: registered module odir (family 0x000f, version = 0x0001, tool 0x0010, tool version 0x0629)
(21:09:21) oscar: registered module bart (family 0x0010, version = 0x0001, tool 0x0010, tool version 0x0629)
(21:09:21) oscar: registered module feedbag (family 0x0013, version = 0x0004, tool 0x0110, tool version 0x0629)
(21:09:21) oscar: registered module icq (family 0x0015, version = 0x0001, tool 0x0110, tool version 0x047c)
(21:09:21) oscar: registered module auth (family 0x0017, version = 0x0000, tool 0x0000, tool version 0x0000)
(21:09:21) oscar: registered module alert (family 0x0018, version = 0x0001, tool 0x0010, tool version 0x0629)
(21:09:21) oscar: Adding handler for ffff/0003
(21:09:21) oscar: Adding handler for ffff/0006
(21:09:21) oscar: Adding handler for 0007/0003
(21:09:21) oscar: Adding handler for 0007/0005
(21:09:21) oscar: Adding handler for 0007/0007
(21:09:21) oscar: Adding handler for 0018/0001
(21:09:21) oscar: Adding handler for 0018/0007
(21:09:21) oscar: Adding handler for 0017/0003
(21:09:21) oscar: Adding handler for 0017/0007
(21:09:21) oscar: Adding handler for 0017/000a
(21:09:21) oscar: Adding handler for 0010/0005
(21:09:21) oscar: Adding handler for 0009/0001
(21:09:21) oscar: Adding handler for 0009/0003
(21:09:21) oscar: Adding handler for 0003/0001
(21:09:21) oscar: Adding handler for 0003/0003
(21:09:21) oscar: Adding handler for 0003/000b
(21:09:21) oscar: Adding handler for 0003/000c
(21:09:21) oscar: Adding handler for 000e/0001
(21:09:21) oscar: Adding handler for 000e/0003
(21:09:21) oscar: Adding handler for 000e/0004
(21:09:21) oscar: Adding handler for 000e/0002
(21:09:21) oscar: Adding handler for 000e/0006
(21:09:21) oscar: Adding handler for 000d/0001
(21:09:21) oscar: Adding handler for 000d/0009
(21:09:21) oscar: Adding handler for 0013/0001
(21:09:21) oscar: Adding handler for 0013/0003
(21:09:21) oscar: Adding handler for 0013/0006
(21:09:21) oscar: Adding handler for 0013/000e
(21:09:21) oscar: Adding handler for 0013/0008
(21:09:21) oscar: Adding handler for 0013/0009
(21:09:21) oscar: Adding handler for 0013/0015
(21:09:21) oscar: Adding handler for 0013/0019
(21:09:21) oscar: Adding handler for 0013/001b
(21:09:21) oscar: Adding handler for 0013/001c
(21:09:21) oscar: Adding handler for 0004/0007
(21:09:21) oscar: Adding handler for 0004/000a
(21:09:21) oscar: Adding handler for 0004/000b
(21:09:21) oscar: Adding handler for 0004/0001
(21:09:21) oscar: Adding handler for 0004/0014
(21:09:21) oscar: Adding handler for 0004/000c
(21:09:21) oscar: Adding handler for 0015/00f3
(21:09:21) oscar: Adding handler for 0015/00f2
(21:09:21) oscar: Adding handler for 0002/0003
(21:09:21) oscar: Adding handler for 0002/0006
(21:09:21) oscar: Adding handler for 0002/0001
(21:09:21) oscar: Adding handler for 0002/fffd
(21:09:21) oscar: Adding handler for 0001/0001
(21:09:21) oscar: Adding handler for 0001/000f
(21:09:21) oscar: Adding handler for 0001/001f
(21:09:21) oscar: Adding handler for 0001/0021
(21:09:21) oscar: Adding handler for 0001/000a
(21:09:21) oscar: Adding handler for 0001/0005
(21:09:21) oscar: Adding handler for 0001/0013
(21:09:21) oscar: Adding handler for 0001/0010
(21:09:21) oscar: Adding handler for 0008/0002
(21:09:21) oscar: Adding handler for 000a/0001
(21:09:21) oscar: Adding handler for 000a/0003
(21:09:21) oscar: oscar_login: gc = 0x865d7c8
(21:09:21) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified.  Using Pidgin's proxy settings instead.
(21:09:21) dns: DNS query for 'login.messaging.aol.com' queued
(21:09:21) dns: Created new DNS child 6995, there are now 1 children.
(21:09:21) dns: Successfully sent DNS request to child 6995
(21:09:21) dns: Got response for 'login.messaging.aol.com'
(21:09:21) dnsquery: IP resolved for login.messaging.aol.com
(21:09:21) proxy: Attempting connection to 64.12.200.89
(21:09:21) proxy: Connecting to login.messaging.aol.com:5190 with no proxy
(21:09:21) proxy: Connection in progress
(21:09:21) proxy: Connected to login.messaging.aol.com:5190.
(21:09:21) oscar: connected to FLAP server of type 0x0017
(21:09:21) oscar: Username sent, waiting for response
(21:09:22) oscar: inside auth_resp (Username: Hinatarockz)
(21:09:22) oscar: Login Error Code 0x0005
(21:09:22) oscar: Error URL: [http://www.aim.com/errors/MISMATCH_PASSWD.html?ccode=us&lang=en](http://www.aim.com/errors/MISMATCH_PASSWD.html?ccode=us&lang=en)
(21:09:22) account: Disconnecting account 0x817dc20
(21:09:22) connection: Disconnecting connection 0x865d7c8
(21:09:22) oscar: Destroying oscar connection of type 0x0017.  Disconnect reason is 0
(21:09:22) oscar: Disconnected.  Code is 0x0000 and msg is 
(21:09:22) oscar: Signed off.
(21:09:22) connection: Destroying connection 0x865d7c8
(21:09:26) util: Writing file accounts.xml to directory /home/devin/.purple
(21:09:26) util: Writing file /home/devin/.purple/accounts.xml

Can anybody help? (I recently tried to install Tor and Privoxy, but failed and uninstalled them using the package manager, maybe that will help)

---

### Post by tuxxy on 2008-08-27
Try this [latest version]("http://www.getdeb.net/app/Pidgin")

---

### Post by dh04000 on 2008-08-27
Thanks it worked. Any idea what I did to it in the first place so I don't do it again?

---

### Post by Sudh on 2009-02-06
Until now, the spread of the virus from one person to another has been very rare and it is thought that it cannot spread beyond one person. However, some scientists are concerned that in the future the H5N1 virus could easily spread from one person to another due to the fact that all types of influenza viruses are known for the increased ability to mutate. If this happens, the consequences will be horrifying as the H5N1 virus is foreign to humans and our bodies cannot begin to offer us a reliable immune protection against it.

[Bird Flu]("http://www.drugdelivery.ca/bird-flu.aspx")

---

### Post by a1ygator on 2009-02-06
The same thing happened to me except even after I installed the new version it still crashed. So I installed Kopete and I haven't had any problems yet.

---

