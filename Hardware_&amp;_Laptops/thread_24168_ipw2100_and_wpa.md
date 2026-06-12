---
title: "ipw2100 and wpa"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by kermy on 2005-04-05
I'm having trouble getting ipw2100 working with wpa. This could be because wpa is not compiled into the kernel module i read somewhere... This is what I get when running wpa_supplicant after modprobing the ipw2100 module:
> sax@orion:~ $ sudo /usr/sbin/wpa_supplicant -B -c/etc/wpa_supplicant.conf -ieth1 -Dipw2100
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW2100_IOCTL_WPA_SUPPLICANT]: Operation not supported
I can get wpa working using ndiswrapper, but I'd rather use the open source driver for some reason ...  8-[

---

### Post by bkuhn on 2005-04-23
I had quite a bit of trouble myself.  I spent hours on it.  In the end, I
was not able to make WEP work, but I was able do get it working.

First, I used the latest Free Software drivers from [the sourceforge ipw2100 site](http://ipw2100.sourceforge.net)
I used version 1.1.0.

However, there is some sort of bug, [which is described in a post on ipw2100.devel](http://article.gmane.org/gmane.linux.drivers.ipw2100.devel/4662) .  I used the patch at that
link there (and I included that patch here.  The patch seems to only
"pretend" to the drivers that they are compiled in-kernel as opposed to as
modules.

I then compiled these drivers seperately, by running ```
make
``` in
the unpacked directory where the patch was applied.  I then loaded them by
doing the following in that same directory:

```

./load; insmod ieee80211.ko; insmod ipw2100.ko

```

In other words, their load commands don't do the right thing so you
have to load two of the many modules by hand.

After they are loaded, ```
wpa_supplicant -dd -K -ieth1
-c/etc/wpa_supplicant.conf -Dipw
``` seems to stop giving the
```
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
```
error.  I was then, with the right configuration posted elsewhere in this
firms, able to get WPA-PSK working.  The reason plain WEP won't work
remains a mystery, but I don't really need it so I didn't investigate
further.  I have a theory that WEP may be broken on my Gateway 7001 in the
first place, and it has nothing to do with the laptop with the ipw2100 in
it.

Hope this helps, and saves someone else from burning 7 hours on this
problem as I did.

---

### Post by kermy on 2005-04-25
Well, I'll just wait until the latest ipw2100 drivers appear in the linux kernel. Too much trouble to get it working and I'd have to use other drivers when roaming into a WEP network...

---

### Post by Archalien on 2005-06-17
> **bkuhn]I had quite a bit of trouble myself.  I spent hours on it.  In the end, I
was not able to make WEP work, but I was able do get it working.

First, I used the latest Free Software drivers from [the sourceforge ipw2100 site](http://ipw2100.sourceforge.net)
I used version 1.1.0.

However, there is some sort of bug, [which is described in a post on ipw2100.devel](http://article.gmane.org/gmane.linux.drivers.ipw2100.devel/4662) .  I used the patch at that
link there (and I included that patch here.  The patch seems to only
"pretend" to the drivers that they are compiled in-kernel as opposed to as
modules.

I then compiled these drivers seperately, by running ```
make
``` in
the unpacked directory where the patch was applied.  I then loaded them by
doing the following in that same directory:

```

./load said:**
> : Operation not supported
```
error.  I was then, with the right configuration posted elsewhere in this
firms, able to get WPA-PSK working.  The reason plain WEP won't work
remains a mystery, but I don't really need it so I didn't investigate
further.  I have a theory that WEP may be broken on my Gateway 7001 in the
first place, and it has nothing to do with the laptop with the ipw2100 in
it.

Hope this helps, and saves someone else from burning 7 hours on this
problem as I did.
 OH GOD please someone help! Ive had this patch for sometime, I apply it to the source, use make, and have followed several different procedures following this with no success, Im not a complete noob, nor a veteran.  I need every step spelled out.

When I follow bkuhns load command I get errors.

Ive tried unistalling original ipw2100 and replcaeing w/ patched one and still no good.

---

### Post by Archalien on 2005-06-18
Dont ask me how, its still a mystery to me, but I actually got it connected- sorta
It will connect but the connection keeps dropping then reconnecting making surfing almost impossible, but Im closer this is the first distro Ive been able to get ipw2100 working w/ wpasupplicant at all!!!

I did instructions as above, but when I did the "load" I got errors so I dont know that it made any difference??

Anyhelp on getting this stable would be appreciated!

---

