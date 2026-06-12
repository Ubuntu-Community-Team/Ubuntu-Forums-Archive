---
title: "Ubuntu 9.04 - vpnc stopped working after upgrade"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Cold-Gin on 2009-04-26
Hi. I upgraded from Ubuntu 8.04 to 8.10, and then from 8.10 to 9.04. I've ran vpnc successfully in 8.04 before upgrading, but now I get the message:

> vpnc: authentication unsuccessful

after execution. My default.conf was not affected by the upgrade, and the only thing that I noticed in the example.conf, which is not present in my default.conf, is the line "IKE Authmode hybrid". I also have a "Domain" line specified in my default.conf file, which is not present in the example.conf file.

I also installed network-manager-vpnc, but no luck after installing it... I also rebooted, but that didn't help. Is there something else that I should re-install to get vpnc working again?

Thanks in advance.

---

### Post by Cold-Gin on 2009-04-27
I tried setting up a VPN connection through Preferences -> Network Connection, but that doesn't seem to work either. I get an "Invalid secrets" pop-up from the desktop. Plus, I need to be able to enter a FOB id.

Any insight on how I could go about debugging this would be greatly appreciated. 

Thanks.

---

### Post by Cold-Gin on 2009-04-28
Sorry, but this was a false alarm. Issue was caused by a password change. Everything is working fine with vpnc after upgrade to 9.04.

---

### Post by bryonak on 2009-04-29
Similar problem here: It was working last week with 8.10, after upgrading to 9.04 I get ```
vpnc: no response from target

```
I've tried the NAT traversal trick and also changing the port...
The VPN server responds to ping and it's VPN port is open.
It doesn't matter if I enter the correct password or not, it simply times out.

My current .conf looks like this:
```

Interface name tun0
IKE DH Group XXX
Perfect Forward Secrecy nopfs
IPSec gateway XXX
IPSec ID XXX
IPSec secret XXX
NAT Traversal Mode cisco-udp
Xauth username XXX

```

Commenting out the IKE, Forwarding or NAT lines doesn't help (as well as changing the port).

Could it be some permissions (AppArmor/SELinux) issue? I didn't fiddle with those, but read somewhere that allowing vpnc to communicate with dbus solved a similar problem, but that was about 3 years old...


[i]Edit: I don't use the nm-applet ;)
And I've tried vpnc 0.3.3 and some 0.4 without success...[/i]

---

### Post by jedi-penguin on 2009-05-29
I got the same problem. vpnc break my connection after every attenpt.

---

### Post by jonmcc on 2009-07-20
I'm having the same problem. I was using 8.04 & it worked fine. Then I upgraded to 8.10, and then 9.04 (in 2 steps over the net). Now, I'm getting "vpnc: authentication unsuccessful".

Is this a bug introduced in 9.04..?

To shed light on this, I installed VirtualBox (an excellent app) to run Windows XP as a virtual host. Then, using Cisco's Windows VPN client I managed to connect into work over the VPN! So, it would seem this is vpnc specific.

---

### Post by jonmcc on 2009-10-11
I notice there's been no comments / fixes since my post above :-(
Anyone out there fixed this, or is it still a bug in 9.04...? Thanks.

---

### Post by T3kG33k on 2009-11-05
> **jonmcc said:**
> I notice there's been no comments / fixes since my post above :-(
Anyone out there fixed this, or is it still a bug in 9.04...? Thanks.

It's still a bug and no one seems to be updating their posts.  Go figure.  There probably isn't an answer.  I've been looking for about a week now.

---

