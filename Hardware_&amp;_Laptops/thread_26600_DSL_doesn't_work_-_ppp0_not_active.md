---
title: "DSL doesn't work - ppp0 not active"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by falke on 2005-04-13
Hey there. I have the following problem:

I have a Devolo network at home (dLAN). My computer is connected to my ADSL Modem via this network. The modems ip is 10.0.0.138.
When i send a ping, it answers with 4ms.

My Internet provider is AON and uses pptp.
When i want to connect to the internet, ppp0 doesn't activate. I have set the following configurations:

_ /etc/ppp/pap-secrets and /etc/ppp/chap-secrets:_

*username * usercode  **
-----

_/etc/ppp/options_

[I]noipdefault
name username
noauth
defaultroute
replacedefaultroute
lcp-echo-failure 10
lcp-echo-interval 10[/I]
-----

_/etc/hosts :_

*10.0.0.138 alcatel *
-----

_/etc/resolv.conf_
[I]
nameserver 195.3.96.67
nameserver 195.3.96.68 [/I]
-----

when i log in as root, i should connect by typing
*/usr/sbin/pptp 1.0.0.138*


But it doesn't. What have i done wrong ?
best regards, Daniel

---

