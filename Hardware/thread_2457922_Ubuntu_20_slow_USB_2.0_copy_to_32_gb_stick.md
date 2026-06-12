---
title: "Ubuntu 20 slow USB 2.0 copy to 32 gb stick"
date: 2021-02-12
forum: Hardware
---

### Post by deepakdeshp on 2021-02-12
Hello,
I observed very slow writing of the USB stick on my 32 gb stick.It starts with 36 MBPS and at the end crawls to a very slow rate. I searched but haven't found any definitive solution. I should be getting a 132 gb stick soon.
Does anybody know a solution?

---

### Post by Autodave on 2021-02-12
What file format is the USB stick using?

---

### Post by TheFu on 2021-02-12
Flash storage wears out as the number of write cycles grow.  There's no way to "fix" that.  In general, cheaper flash has much fewer write cycles before failure. As the write cycle count increases, it takes longer and longer to actually write the data.

The initial speed is because writes are cached in RAM buffers. When the buffers are full, the speed slows to the performance possible by the physical media, the file system, and the interface.  In general, the fastest I've ever seen expensive USB2 flash media work is 22 MBps.  USB2 bus theoretical limit is 480 Mbps (60MBps) [https://en.wikipedia.org/wiki/USB#USB_2.0](https://en.wikipedia.org/wiki/USB#USB_2.0).

If you want the best possible performance and don't need to share the flash drive with other OSes, then use f2fs as the file system.  f2fs is almost as fast as ext4 in testing and sometime faster.  exFAT would be the next choice, then ext4, then NTFS, then last choice is FAT32.  FAT32 is slow for a number of reasons.

132GB is an odd size for any storage.  128GB would be more likely.  With that size, you cannot use FAT32 (according to Microsoft), though from Linux you can format anything as FAT32. That won't fix the underlying design issues with that file system.  FAT32 was made for smaller storage partitions and loses efficiency with every size increase over about 16G.  In theory, exFAT will be getting faster and faster, since Microsoft opened the patents on it and has been working to create a solid kernel driver for it. Last time I checked FAT32, NTFS, f2fs and exFAT all used FUSE file system drivers.
[https://en.wikipedia.org/wiki/Comparison_of_file_systems](https://en.wikipedia.org/wiki/Comparison_of_file_systems)  Note which support POSIX permissions without any footnotes.

---

### Post by deepakdeshp on 2021-02-22
> **TheFu said:**
> Flash storage wears out as the number of write cycles grow.  There's no way to "fix" that.  In general, cheaper flash has much fewer write cycles before failure. As the write cycle count increases, it takes longer and longer to actually write the data.

The initial speed is because writes are cached in RAM buffers. When the buffers are full, the speed slows to the performance possible by the physical media, the file system, and the interface.  In general, the fastest I've ever seen expensive USB2 flash media work is 22 MBps.  USB2 bus theoretical limit is 480 Mbps (60MBps) [https://en.wikipedia.org/wiki/USB#USB_2.0](https://en.wikipedia.org/wiki/USB#USB_2.0).

If you want the best possible performance and don't need to share the flash drive with other OSes, then use f2fs as the file system.  f2fs is almost as fast as ext4 in testing and sometime faster.  exFAT would be the next choice, then ext4, then NTFS, then last choice is FAT32.  FAT32 is slow for a number of reasons.

132GB is an odd size for any storage.  128GB would be more likely.  With that size, you cannot use FAT32 (according to Microsoft), though from Linux you can format anything as FAT32. That won't fix the underlying design issues with that file system.  FAT32 was made for smaller storage partitions and loses efficiency with every size increase over about 16G.  In theory, exFAT will be getting faster and faster, since Microsoft opened the patents on it and has been working to create a solid kernel driver for it. Last time I checked FAT32, NTFS, f2fs and exFAT all used FUSE file system drivers.
[https://en.wikipedia.org/wiki/Comparison_of_file_systems](https://en.wikipedia.org/wiki/Comparison_of_file_systems)  Note which support POSIX permissions without any footnotes.

Thank you for your detailed reply. The stick has to be connected to an Android TV box hence I don't think the file systems like ext4 would work. I used the default already created FS fat32 and things worked. The speed was also ok, not that bad at all to copy on to 128 fb USB stick.

---

### Post by TheFu on 2021-02-22
Android supports ext4 and some versions support f2fs.

No way did a USB flash drive over 64G come pre-formatted FAT32. It came with exFAT.

---

### Post by deepakdeshp on 2021-02-23
> **TheFu said:**
> Android supports ext4 and some versions support f2fs.

No way did a USB flash drive over 64G come pre-formatted FAT32. It came with exFAT.
Looks like it can be done.
[https://www.diskpart.com/articles/format-128gb-usb-fat32-0310.html](https://www.diskpart.com/articles/format-128gb-usb-fat32-0310.html)

---

### Post by TheFu on 2021-02-23
> **deepakdeshp said:**
> Looks like it can be done.
[https://www.diskpart.com/articles/format-128gb-usb-fat32-0310.html](https://www.diskpart.com/articles/format-128gb-usb-fat32-0310.html)
 I said that it wouldn't be delivered from the manufacturer that way.

There are thousands of things that CAN be done on Linux. Almost always, using fat32 on storage over 32G is a really bad idea. Learn mode about fat32 to understand why.

---

