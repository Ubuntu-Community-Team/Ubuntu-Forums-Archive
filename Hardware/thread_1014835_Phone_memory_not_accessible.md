---
title: "Phone memory not accessible"
date: 2008-12-18
forum: Hardware
---

### Post by rajenpn on 2008-12-18
I've got Sony Ericsson W700i Mobile. It has, around **32 MB of Phone memory** in addition to the **Memory Stick** Pro Duo.

When I connect it through the USB Datacable, Ubuntu is showing up only the Memory Stick and **not the Phone Memory**.

How to access this "Phone Memory"? Please help me.

Thank you.

---

### Post by rajenpn on 2009-01-01
Is there any one who can answer my above question?

---

### Post by el_chupacabra on 2009-05-22
> **rajenpn said:**
> Is there any one who can answer my above question?

I just ran into the same problem. It looks to me that it is not possible to access the phone memory using Linux.

See here: [https://help.ubuntu.com/community/PortableDevices/SonyEricsson](https://help.ubuntu.com/community/PortableDevices/SonyEricsson)

---

### Post by el_chupacabra on 2009-05-23
Good news. With the help of my brother I found a solution for my Sony Ericsson S302.

When you connect the phone via the USB cable, enter the following into a shell:

```
dmesg|tail
```

That command contained the following line for me:

```
[10869.025104] sd 8:0:0:1: [sdc] Attached SCSI removable disk
```

Now, I simply mounted the device/phone using:

```
sudo mount -t vfat /dev/sdc /media/phone
```

That way it is possible to access all files on the internal phone memory.

I hope this helps. ;)

---

### Post by jamste on 2010-02-01
Does anyone know how to access the internal memory of a Samsung Tocco Via USB?

---

