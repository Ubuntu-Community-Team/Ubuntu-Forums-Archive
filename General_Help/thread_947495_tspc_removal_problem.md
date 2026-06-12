---
title: "tspc removal problem"
date: 2008-10-14
forum: General Help
---

### Post by hittudiv on 2008-10-14
i actually installed a package tspc that is supposed to be a ipv6 tunnel.
power went off before i could configure it..

and now...if i install any softie frm synaptic (apt-get and dpkg also)..it gets installed..but an error msg comes and synaptic is freezed..i hav to foce it to close..

the error msg is

"Shutting down IPv6 tunnel: invoke-rc.d: initscript tspc, action "stop" failed.

dpkg: error processing tspc (--remove):

 subprocess pre-removal script returned error exit status 1

Setting up IPv6 tunnel: tspGetCapabilities error 2: SOCKET_ERROR

if you are using udp, there is probably no udp listener at anon.freenet6.net

"
and even if i try to remove the software ..same error comesup..

i tried this.."sudo invoke-rc.d tspc stop"
it worked with admin privilages..
i guess synaptic was running it w/o root privilages..
is there a way i can uninstall the program??

thanks
Bad_Sector

---

### Post by Mr Roboto on 2008-11-03
I had exactly the same problem. Here's how I fixed it - it's actually pretty easy.  You just delete the init.d script that keeps failing.

```

cd /etc/init.d
sudo rm tspc
sudo apt-get remove tspc

```

Sweet as a nut!

---

### Post by hittudiv on 2008-11-06
:)
thanks..it worked

---

### Post by unhot on 2009-03-26
This was driving me crazy in Intrepid as well - thanks.

---

### Post by tixetsal on 2009-04-15
Me too.  Thanks!

---

