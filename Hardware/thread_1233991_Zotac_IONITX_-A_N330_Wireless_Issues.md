---
title: "Zotac IONITX -A N330 Wireless Issues"
date: 2009-08-07
forum: Hardware
---

### Post by nosaj070 on 2009-08-07
Hey All,

I am trying to get ubuntu up and running on my newly built HTPC running the Zotac ION board with the N330. 

I'm having no issues except that I cannot connect to my wireless n network. The machine can see it, but refuses to connect. Are there updated drivers I need to install in order to get this working properly?

Thanks,

P.S. I'm a linux newbie, so I'd appreciate relatively simple replies :D

---

### Post by SqRt7744 on 2009-08-16
If you open a terminal window: Applications->Accessories->Terminal and type:
```

lspci

```

what is the output? I need to know the wireless chipset to give you more specific instructions...

I'm actually thinking about getting this board myself :)

---

### Post by Alfiegerner on 2009-08-28
I'm having the same problem.  I can see the wireless network but I can't connect to it.

lspci shows: AR928X Wireless Network Adapter (PCI-Express) (rev 01)

lsmod result here [http://pastebin.com/m2a13c35b](http://pastebin.com/m2a13c35b)

Anybody know how to make this work?

Cheers.
Alex

---

### Post by falstaff on 2009-08-29
Hi,

I can definitely connect to a 802.11g Network with this Board... Do you try to connect to a 802.11n Network too? What says dmesg?

Bye
falstaff

---

### Post by Alfiegerner on 2009-08-30
> **falstaff said:**
> Hi,

I can definitely connect to a 802.11g Network with this Board... Do you try to connect to a 802.11n Network too? What says dmesg?

Bye
falstaff

Woops my bad - user error on authentication, thanks for the response though.

---

