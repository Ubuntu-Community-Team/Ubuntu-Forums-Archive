---
title: "Laptop Not Booting up Goes to Busy Box"
date: 2012-03-07
forum: Hardware
---

### Post by clbaines on 2012-03-07
My laptop will not boot up 11.10. Goes to Busy Box. Not exactly the same as some other posts. I booted up from a Linux Format CD with 11.10 on it. Booted up. When I went to the Home directory and tried to mount my Hard Drive, shown as a device it won't mount it. 

The message says:  Can't mount 117GB files.....
Unable to mount 117 GB filesystem.
Error mounting: Mount: Wrong FS Type, Bad option, Bad Superblock on
/dev/sda1, missing codepage or helper program, or other error.
In some cases useful info is found in Syslog- try dmesg | tail.

Output of dmesg | tail:
[sda] Result: hostbyte=DID_ok
driverbyte=driver_sens
[sda] Sense Key: mediu,m error
[current] [descriptor
Descriptor Sense Data with Sense Descriptions(in hex):
72 03 11 04 00 08 0c 00 oa 80 00 00 00 00
[Sda] Add.Sense: Unrecovered read error auto real sd 0:0:0:0 
[Sda] CDB: Read(10): 25 00 06 C7 46 F8 00 00 00 70 00  end_request
sector 113273128
ata1: EH Complete

Don't know if I have a bad disk or grub is messed up. Any help will be greatly appreciated. I don't want to re-install.

This has happened after some system updates a couple of days ago. 
I had a message that said some files could not be removed. Did say system was up to date. Left the laptop running until today when I tried to restart.

---

### Post by ajgreeny on 2012-03-07
From the live CD try running the terminal command ```
sudo e2fsck /dev/sda1
```I am assuming that the error message related to your ubuntu partition;  correct?
That may solve the problem in one go, but if it is not successful come back again.

---

### Post by clbaines on 2012-03-07
*t has never been dual boot. Came with Ubuntu from Dell. I have upgraded several times. Latest was to 11.10*

---

### Post by clbaines on 2012-03-08
Thanks for the tip. It is now booting up.

Did the e2fsck /dev/sda1
   Results:  recovering journal
   error reading block 14215134
     ignore error  (Yes)
     force rewrite (yes)

Thanks again ejgreeny.

First thing I did was do a complete backup. I am now on Ubuntu One.
I promise to do backups. Close call.

---

### Post by ajgreeny on 2012-03-08
Great!  It happened to me once a long time ago, and I've never forgotten the solution, even though I have not needed it since.

Can you mark as Solved from the Thread Tools menu at the top of the thread.

---

