---
title: "Performance of USB type-c pen drive"
date: 2022-01-13
forum: Hardware
---

### Post by satimis on 2022-01-13
Hi all,

USB type-c pen drive
vs
SATA3 6G/s SSD

Please advise which drive has better performance.

USB type-c pen drive is quite convenient in changing drive. It can be booted.  But SATA3 6G/s SSD needs to open the PC case.

Please advice. Thanks

Regards

---

### Post by sudodus on 2022-01-14
Most USB pendrives have cheaper memory hardware and simpler built-in systems to distribute the wear compared to SSDs. typically USB pendrives are slower and degrade faster than SSDs (getting even slower and losing memory cells due to wear).

But there are a few USB pendrives with hardware that matches SSDs.

See for example [this link](https://www.pcgamer.com/whats-the-difference-between-flash-and-ssd-storage/).

---

### Post by satimis on 2022-01-14
> **sudodus said:**
> Most USB pendrives have cheaper memory hardware and simpler built-in systems to distribute the wear compared to SSDs. typically USB pendrives are slower and degrade faster than SSDs (getting even slower and losing memory cells due to wear).

But there are a few USB pendrives with hardware that matches SSDs.

See for example [this link](https://www.pcgamer.com/whats-the-difference-between-flash-and-ssd-storage/).
Thanks for your advice.

My idea is sharing HDD between PCs.  OS installed on USB type-c pen drive can be booted.  But in another thought my PCs have different hardware configuration.  Sharing HDD btw PCs seems not working for me.

Regards

---

### Post by sudodus on 2022-01-14
If you connect the HDD or SATA-SSD via a USB3 to SATA adapter, only the software (the operating system) makes a difference concerning bootability and portability. I think it is the same case if the HDD or SSD is connected directly via SATA or eSATA.

If you have problems to boot an external drive in different computers, you should use only built-in hardware drivers and stay away from proprietary drivers in order to preserve portability.

---

### Post by satimis on 2022-01-14
> **sudodus said:**
> If you connect the HDD or SATA-SSD via a USB3 to SATA adapter, only the software (the operating system) makes a difference concerning bootability and portability. I think it is the same case if the HDD or SSD is connected directly via SATA or eSATA.

If you have problems to boot an external drive in different computers, you should use only built-in hardware drivers and stay away from proprietary drivers in order to preserve portability.
My attempt is to share SSD-HD amongst PCs having different hardware configuration, such as mobo, display card etc.

Now I can change SSD-HD on a PC from outside without opening the PC case, with a long data cable and a long power cable.  It is NOT a good house-keeping.  The SSD-HD is just lying on the table.  The OS of all SSD-HDs was installed on the same PC.  It can be booted.

Now I wonder whether SSD-HDs with OS installed on different PCs can be shared in this way?

Regards

---

### Post by oldfred on 2022-01-14
I built system in 2006 with M.2 SATA SSD as NVMe drives were very expensive, then.
I recently wanted newer larger drive and NVMe drives are still a bit more but not as expensive. So moved M.2 SATA SSD to external USB adapter.

My not scientific speed test is a full install of Kubuntu. 
Full install to internal NVMe SSD, about 10 to 12 min.
Full install to internal HDD about 14 min.
And external SSD was about the same as internal HDD.

I have seen USB-c ports with same speeds as USB-a and others at the faster speed.
Even cables can make a difference.
[https://en.wikipedia.org/wiki/USB-C](https://en.wikipedia.org/wiki/USB-C)

---

### Post by sudodus on 2022-01-14
> **satimis said:**
> My attempt is to share SSD-HD amongst PCs having different hardware configuration, such as mobo, display card etc.

Now I can change SSD-HD on a PC from outside without opening the PC case, with a long data cable and a long power cable.  It is NOT a good house-keeping.  The SSD-HD is just lying on the table.  The OS of all SSD-HDs was installed on the same PC.  It can be booted.

Now I wonder whether SSD-HDs with OS installed on different PCs can be shared in this way?

Regards

***Yes***, I have done it several times (tested in several computers). There are some limits though, for example, some computers need a proprietary driver for graphics and/or wifi, and this can make it impossible to share a system with a computer that cannot run with that particular proprietary driver.

See [this link](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step) with detailed instructions and also [this link](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) about portable installed systems.

An alternative is a persistent live system (in an SSD or HDD), which might work in some cases where an installed system does not work, but there are no big differences in portability. It is easy to make a persistent live system with [mkusb](https://help.ubuntu.com/community/mkusb). A problem with a persistent live system is that you cannot upgrade the kernel (and its drivers), but you can backup the home directory and reuse it in a fresh persistent live system.

---

