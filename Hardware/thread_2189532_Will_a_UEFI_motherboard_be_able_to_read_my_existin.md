---
title: "Will a UEFI motherboard be able to read my existing HDDs?"
date: 2013-11-22
forum: Hardware
---

### Post by nstgc379 on 2013-11-22
After about a year of using a hard drive I will remove it as a back up. Its a convient way to make sure that you have absolutely **everything** backed up. However I read somewhere that you can't read these drives on the new motherboards? Is this true? If so what voodoo will I need to work in order to get the drivers to read?

For refference, I have an[Asus X79 Deluxe]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813132047") and an i7-4930k. I'm waiting for the semester to be over to put everything together, and am hoping for a heads up.

---

### Post by electrohandyman501 on 2013-11-22
When I changed PC's that didn't use IDE interface anymore I bought a USB3.0 external HDD box to plug in my extra HD for access. I use it for extra storage now.

Not sure in your case if you could boot from it, but it may work.

---

### Post by oldfred on 2013-11-23
New UEFI systems will boot from gpt partitioned drives but read MBR or even if UEFI turned off boot from MBR(msdos) drives as they have a compatibility mode. But once you start booting in one mode you cannot switch as they boot differently and are not really compatible. So best if all systems are UEFi or all are BIOS.

Windows XP will not read gpt partitioned drives. And Windows 32 bit will not boot with UEFI.
BIOS boot from Windows will read gpt partitioned drives.
If drive is gpt Windows will only boot in UEFI mode, but Ubuntu can boot in either BIOS or UEFI.
IF drive is MBR both systems will only boot in BIOS mode.

---

### Post by nstgc379 on 2013-12-19
So, you're saying, there is no issue with retrieving data. That the only issue is booting from Windows.

---

### Post by oldfred on 2013-12-19
You should be able to boot Windows if installed to match partitioning. New UEFI motherboards work as UEFI or BIOS.
Some USB caddies do not support very large drives and some do not work well with USB3 ports. Best to make sure drive caddy will work first, it you decide to use that.

I now prefer gpt partitioning for all Ubuntu drives whether BIOS or UEFI. Windows booting just must be in UEFI if boot drive is gpt. Windows would not read Linux formatted partitions anyway. But if you have a NTFS partition on another gpt drive Windows 7 or later will read it.

---

