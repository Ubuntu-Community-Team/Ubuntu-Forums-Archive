---
title: "Dead External Hardrive!"
date: 2008-04-26
forum: Hardware
---

### Post by HermanChess on 2008-04-26
[ 7618.998524] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 7618.998533] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 7619.956158] sd 5:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 7619.956168] sd 5:0:0:0: [sdc] Device not ready: Add. Sense: Logical unit not ready, cause not reportable
[SIZE="4"]**[ 7619.956175] end_request: I/O error, dev sdc, sector 0**[/SIZE]
[ 7619.956179] printk: 14 messages suppressed.
[ 7619.956182] Buffer I/O error on device sdc, logical block 0
[ 7620.322922] sd 5:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 7620.322932] sd 5:0:0:0: [sdc] Device not ready: Add. Sense: Logical unit not ready, cause not reportable
**[ 7620.322939] end_request: I/O error, dev sdc, sector 0**

----

I would say it's dead. I was using it just hours ago, someone asked for it to use it in another ubnuntu machine, I unmounted it, and it never worked again. :(  

I tried using dd_recue but it was saving an average of 0.0% it seems ...  What can I do? Is there some good linux app to recover my files or even better... fix it?

It is a fujitsu 80gb usb external drive. Formatted in ntfs.

Please help! :(

---

### Post by Rocket2DMn on 2008-04-26
That certainly does look like a bad problem.  It's not even mentioning partitions on the drive, just the device itself.  Since the drive is formatted with ntfs, I suggest plugging it into a windows machine since windows handles ntfs natively.  There is a metapackage called "ntfsprogs" in the Ubuntu repos, but they wouldn't do as good of a job as a windows machine could with that drive, especially since we don't even see partitions at this point.

If you do get the drive to work somewhere, get as much off it as you can since it could die forever at any time.

---

### Post by tamoneya on 2008-04-26
I would suggest using [The Ultimate Boot CD]("http://www.ultimatebootcd.com/").  Use this to clone the drive first.  This will prevent you from doing any more damage than you already have.  You can then try to mount and extract data from the clone.  You can also do some hardware integrity checks with the built in tools on UBCD

---

### Post by HermanChess on 2008-04-26
Thanks for the responses. I don't have windows in my house right now, so I can't check that. I'm downloading the Super Boot CD right not, I'll let you know how that goes.  There are 60gb of music I don't wish to lose. :popcorn:

---

