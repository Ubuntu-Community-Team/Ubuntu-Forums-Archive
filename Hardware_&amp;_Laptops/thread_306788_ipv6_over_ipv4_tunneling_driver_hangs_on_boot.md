---
title: "ipv6 over ipv4 tunneling driver hangs on boot"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by walding on 2006-11-25
HI,

I have an Asus A6VM laptop running Edgy (I normally use KDE).
I have a problem with booting - the laptop hangs on "ipv6 over ipv4 tunneling driver" for a few minutes each time.  A fresh install hasn't helped.

Any ideas?  I don't even know what that driver does!

Thanks

AW

---

### Post by hernad on 2006-12-19
I had the same problem with my inspiron 8000.

I have found this blog [http://oviedos.com.mx/?blog/category/13](http://oviedos.com.mx/?blog/category/13). 


/etc/modprobe.d/aliases
-----------------------------
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off

With these changes ipv6 were disabled.

After that, my boot was as fast as possible :).

I hope it will help you also.
Regards,
Ernad

---

### Post by walding on 2007-01-09
Hi,

I finally got round to trying this, but it still hangs for a good while at the same point.
Anyone else have any ideas?

AW

---

### Post by TrinitronX on 2007-01-27
Getting this too as well, tried the modprobe.d/aliases edit, but no luck either.
After an insanely long hang, it finally boots, but it's quite unusable like that.

EDIT:
I have found that my problem was due to udev and madwifi fighting over an interface name "ath0" on boot.  Fixed it by editing the /etc/iftab file, and putting: "arp 1" on the end of each line.  If yours is the same problem, try doing the same to see if it fixes it.
See these links for more info:
[https://launchpad.net/ubuntu/+source/udev/+bug/46048](https://launchpad.net/ubuntu/+source/udev/+bug/46048)
[http://www.mail-archive.com/madwifi-tickets@lists.sourceforge.net/msg03389.html](http://www.mail-archive.com/madwifi-tickets@lists.sourceforge.net/msg03389.html)

---

