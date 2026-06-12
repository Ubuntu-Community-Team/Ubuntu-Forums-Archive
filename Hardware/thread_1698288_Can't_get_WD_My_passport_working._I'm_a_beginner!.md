---
title: "Can't get WD My passport working. I'm a beginner!"
date: 2011-03-02
forum: Hardware
---

### Post by carega on 2011-03-02
Hi, i'm migrating from windows to ubuntu. I have aprox 80gb worth of files in my windows laptop and copied the information to a external HDD, my passport WD.

However I'm unable to open it on ubuntu. I downloaded wine and all but it can't run the unlocker file. When I try to run it gives me the following message:

"the application has encountered an unexpected error and is now exiting."

Ok, so I've read that you need to click somewhere and allow the file to be executed as a program in order to run it through wine. I tried doing that but I couldn't because the system is read-only (whatever that means).

What do I do? Help please I'm a beginner with ubuntu and linux in general! It's my first time using an OS other than Windows.

EDIT: found this link with help: [http://community.wdc.com/t5/My-Passport-for-PC/Running-My-Passport-Essential-on-Linux-Ubuntu/m-p/54576](http://community.wdc.com/t5/My-Passport-for-PC/Running-My-Passport-Essential-on-Linux-Ubuntu/m-p/54576)

Tiped the command there but got the following message:

carega@amaterasu:~$ sudo mount -t ntfs-3g /dev/sr1 /mnt/ -o force
[sudo] password for carega: 
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

carega@amaterasu:~$ sudo mount -t ntfs-3g /dev/sdb /mnt/ -o force
Error reading bootsector: Error de entrada/salida
Failed to mount '/dev/sdb': Error de entrada/salida
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Any ideas?

---

