---
title: "Slow write performance for SATA disk"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by jacktow on 2008-02-15
Hi,

I'm a newbie to linux, been working with it for a week. I got this new system for myself and since my 8GB RAM would be useless on XP I found the best opportunity to escape the M$ prison.
Anyways, the problem I have is a** slow write performance on my WD Caviar GP 1TB (WD10EACS)**. I came across this problem when I was formatting it for the first time use with TrueCrypt. It writes at 24.5MB/s max! At first I thought that was a TrueCrypt problem (or my Quad core Intel couldn't encrypt fast enough, silly aye, but then my old AMD Sempron encrypts the same algorithm (AES) at 40MB/s), so I tried 'dd' utility on the disk's block device, and that gave me similar results. Below's a summary of checks I did:

1. To see if the write performance was affected by TrueCrypt, I used 'dd' to write 512MB on the disk. It wasn't the case.
```
$ sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1000000

512000000 bytes (512 MB) copied, 21.0198 seconds, 24.4 MB/s
```

2. So out of curiosity I checked read rate and it gave me 70 MB/s. Now the problem seemed more specific that I initially thought.:(

3. I have two drives, one is a 250GB seagate which is home to my linux's root. It works as expected, both read and write (about 50 MB/s for both). Here's when the light bulb went on. I formatted my WD and put an XFS on it and then ran a file test on it.

```
$ sudo dd if=/dev/zero of=deleteme bs=512 count=1000000

512000000 bytes (512 MB) copied, 3.21664 seconds, 159 MB/s
```
*NOTE: I unmounted the disk and watched the HD LED to go off before deciding on how long it took. I'm sure 159 MB/s is because it's buffered.*
After stopwatching this which took about 6 or 7 seconds (= ~80MB/s), Woohoo,so putting an FS on the disk solves the problem!

However, that contradicted with my understanding that a raw sequential write on a block device is as fast as it is possible to write data on a disk. Am I wrong? Regardless, I need my disk to perform at its full speed. TrueCrypt tells me it'll take 12 hrs to format it all! Also, below is my system configuration:

M/B : Asus P5K-E WiFi AP
RAM: 8 GB Trancend
CPU: Intel Core 2 Quad Q6600
HD: WD Caviar GP 1TB (WD10EACS)
OS: Ubuntu 7.10
[COLOR="Red"]**Update:**
**TrueCrypt Version 5.0a (which I believe runs user space driver as opposed to previous versions)**[/COLOR]

It's worth mentioning that I did connect the disk to different SATA ports and played around with BIOS settings. No luck.

Would anyone have ideas as to what might be the problem?

Thanks
Mike

---

