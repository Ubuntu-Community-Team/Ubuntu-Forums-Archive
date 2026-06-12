---
title: "Help!! Sata Raid Amd64 X2"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by nyteshade on 2005-12-20
Ok I have the following setup:

[HTML]
LANPARTY nF4 SLI-DR Mobo
AMD64 Athlon X2 4400+
2GB Dual Channel DDR PC3200+
2 x WD 250GB 2500KS SATA300 16MB 7200RPM HDDs
  RAID0: Si3114R Controller
    Partition 0: 430GB --> Windows XP Pro x64
    40GB Unpartitioned space remaining.
2 x eVGA nVidia 6800 Ultra PCIe SLI video cards
[/HTML]

I have Windows XP Pro x64 installed on the first partition and I would like to partition 20GB of the remaining space for a dual boot of Ubuntu 5.10. Problem is that the disk partionner doesn't correctly recognize the partitions. I don't really care to re-install (yet again; long story) WinXP Pro again. 

Any suggestions? Also, even were I to recompile the kernel, how do I put it back on a live bootable install DVD/CD as I have now?

Thanks in advance,
nyteschayde

---

### Post by Sutekh on 2005-12-21
[QUOTE=nyteshade]

I have Windows XP Pro x64 installed on the first partition and I would like to partition 20GB of the remaining space for a dual boot of Ubuntu 5.10. Problem is that the disk partionner doesn't correctly recognize the partitions. I don't really care to re-install (yet again; long story) WinXP Pro again. [/QUOTE]

What disc partitioner are you using?  The one from the Ubuntu install CD?  If so, what does it see exactly?

---

### Post by ytene on 2005-12-22
Hi Nyteshade,

I have some information for you, but I'm not sure if you'll like it. I have had exactly the same problem that you describe with my Thunder K8W Opteron Board, since that also has the Silicon Image Sil3114 SATA RAID Controller. 

To cut a long story short, this won't work in a hardware based RAID configuration under Linux... well, quite. It would be more accurate to describe this Silicon Image chipset as a WinRAID solution [as in the same sense as a WinModem] rather than a full hardware RAID. 

If you go to the Silicon Image web site you will find references there to a prebuilt solution [compliled code] for a variety of distributions, including SUSE and Red Hat. I tried and failed to get this to work and in the end gave up in disgust and split my RAID, removing the WindowsXP version. I did this because I did not want to risk discrepancies between Linux kernel RAID and the WinRAID solution. 

Let me know if you want more links to further details - I can trawl my mailbox and dig out links. Bottom line is that you'll struggle to get this to work.

Best Regards,

C

---

