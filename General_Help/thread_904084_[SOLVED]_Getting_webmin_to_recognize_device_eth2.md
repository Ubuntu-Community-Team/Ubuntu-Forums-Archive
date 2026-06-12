---
title: "[SOLVED] Getting webmin to recognize device eth2"
date: 2008-08-28
forum: General Help
---

### Post by Zeroangel on 2008-08-28
Hey all, i'm trying to configure Webmin, so that my computer will act as a router for my network.

I followed this guide:
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

Unfortunately, I cant start the DHCP server. 
> dave@icarus:/etc/init.d$ tail -n 30 /var/log/syslog
Aug 28 19:54:57 icarus postfix/tlsmgr[8937]: warning: redirecting the request to postfix-owned data_directory /var/lib/postfix
Aug 28 19:54:58 icarus postfix/smtpd[8935]: connect from 219-84-178-152-adsl-tpe.dynamic.so-net.net.tw[219.84.178.152]
Aug 28 19:54:58 icarus postfix/smtpd[8935]: NOQUEUE: reject: RCPT from 219-84-178-152-adsl-tpe.dynamic.so-net.net.tw[219.84.178.152]: 554 5.7.1 <ericoom@gmail.com>: Relay access denied; from=<all9988@gmail.com> to=<ericoom@gmail.com> proto=SMTP helo=<70.64.5.165>
Aug 28 19:54:59 icarus postfix/smtpd[8935]: lost connection after RCPT from 219-84-178-152-adsl-tpe.dynamic.so-net.net.tw[219.84.178.152]
Aug 28 19:54:59 icarus postfix/smtpd[8935]: disconnect from 219-84-178-152-adsl-tpe.dynamic.so-net.net.tw[219.84.178.152]
Aug 28 19:58:19 icarus postfix/anvil[8938]: statistics: max connection rate 1/60s for (smtp:219.84.178.152) at Aug 28 19:54:58
Aug 28 19:58:19 icarus postfix/anvil[8938]: statistics: max connection count 1 for (smtp:219.84.178.152) at Aug 28 19:54:58
Aug 28 19:58:19 icarus postfix/anvil[8938]: statistics: max cache size 1 at Aug 28 19:54:58
Aug 28 20:01:17 icarus dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Aug 28 20:01:17 icarus dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Aug 28 20:01:17 icarus dhcpd: All rights reserved.
Aug 28 20:01:17 icarus dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 28 20:01:17 icarus dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Aug 28 20:01:17 icarus dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Aug 28 20:01:17 icarus dhcpd: All rights reserved.
Aug 28 20:01:17 icarus dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 28 20:01:17 icarus dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Aug 28 20:01:17 icarus dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Aug 28 20:01:17 icarus dhcpd: All rights reserved.
Aug 28 20:01:17 icarus dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 28 20:01:17 icarus dhcpd: Wrote 0 leases to leases file.
Aug 28 20:01:17 icarus dhcpd:
Aug 28 20:01:17 icarus dhcpd: No subnet declaration for eth1 (70.64.5.165).
Aug 28 20:01:17 icarus dhcpd: ** Ignoring requests on eth1.  If this is not what
Aug 28 20:01:17 icarus dhcpd:    you want, please write a subnet declaration
Aug 28 20:01:17 icarus dhcpd:    in your dhcpd.conf file for the network segment
Aug 28 20:01:17 icarus dhcpd:    to which interface eth1 is attached. **
Aug 28 20:01:17 icarus dhcpd:
Aug 28 20:01:17 icarus dhcpd:
Aug 28 20:01:17 icarus dhcpd: Not configured to listen on any interfaces!

So I went into **Servers -> DHCP Server -> Edit Interfaces**. And eth2 is not listed (even though it shows up in ifconfig) The only interfaces that show up are
> eth1 (Internet)
(unknown)
lo (loopback)
(unknown)
How can I get eth2 to show up here?

Thanks.

---

### Post by Zeroangel on 2008-08-28
It turns out that I am, in fact, retarded.

I found the thing I was supposed to set by going into [FONT=Arial,Helvetica,Geneva,Swiss,SunSans-Regular,Sans-Serif][SIZE=2][COLOR=#5592ce]Networking[/COLOR] then [COLOR=#5592ce]Network Configuration[/COLOR] then [COLOR=#5592ce]Routing and Gateways[COLOR=Black] .

Setting up a new interface (eth2).

And then my computer was able to assign DHCP to the other computers on my network.

Success! :KS
[/COLOR][/COLOR] [/SIZE][/FONT]

---

