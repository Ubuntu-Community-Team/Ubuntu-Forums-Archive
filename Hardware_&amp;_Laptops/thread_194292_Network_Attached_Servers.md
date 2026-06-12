---
title: "Network Attached Servers"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by bohboh on 2006-06-11
Are there any NAS devices that work under ubuntu?

I looked into Netgears sc101 but there are no linux drivers/support.

Does anyone know of any alternatives around the same price that work with ubuntu?

---

### Post by manutremo on 2006-06-11
As far as i know, any NAS that exposes its shares with Samba (most of them) or NFS (almost none), should be capable of working with ubuntu.

In my case, I'm using 2 Linksys NSLU2, a Freecom FSG and a DLINK DSM-G600. All of them show up in ubuntu with no problems.

---

### Post by bohboh on 2006-06-11
[QUOTE=manutremo]As far as i know, any NAS that exposes its shares with Samba (most of them) or NFS (almost none), should be capable of working with ubuntu.

In my case, I'm using 2 Linksys NSLU2, a Freecom FSG and a DLINK DSM-G600. All of them show up in ubuntu with no problems.[/QUOTE]

The thing i like about the netgear sc101 is that you can add ide drives to it rather than having them plugged in via the usb ports. So it essentially acts as a file server. I know i could just get another machine and use that, but due to limited space in my office, having a smaller device like the netgear seems like a neater solution.

---

### Post by manutremo on 2006-06-11
I apologize for not completely reading your message. I'm afraid that there is no way to use the netgear sc101 from a linux machine, at least that i know of. These devices use a proprietary protocol for communication, not standard NFS or smb, so you must install a program in every machine to access them. The problem is that this software is only available for the windows SO.

Anyway they are said to be extremely slow devices, although they are really small and cheap...

---

### Post by bohboh on 2006-06-11
I wonder if they will work under wine/crossover?

Would like to try but may end up stuck with it in case it doesnt. :D 

Oh well, may end up building a shuttle case pc.

---

### Post by CyBuzz on 2007-03-19
we will never see this happen will we :-(

---

### Post by red_five on 2007-03-22
Yeah, these NetGear things use some form of ZSCSI IIRC, and the software is only available on Windoze. It shows up like a local drive, rather than a net device. It looks like they may be working on a Linux driver, but the device is pretty slow.

---

### Post by magicfab on 2008-06-13
I know this thread is really old, but I now own one of these and it works fine in Hardy for me with the nbd module. That software is around since late 2007. See:
[http://ubuntuforums.org/showpost.php?p=4151832&postcount=15](http://ubuntuforums.org/showpost.php?p=4151832&postcount=15)

If you'd like to know if/when this makes it into Ubuntu, please subscribe to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/213744](https://bugs.edge.launchpad.net/ubuntu/+bug/213744)

Cheers,

---

