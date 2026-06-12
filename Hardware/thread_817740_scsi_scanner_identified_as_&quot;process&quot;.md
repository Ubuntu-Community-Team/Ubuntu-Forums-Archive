---
title: "scsi scanner identified as &quot;process&quot;"
date: 2008-06-03
forum: Hardware
---

### Post by eddarl on 2008-06-03
I am running Unbuntu Hardy and I have a scsi scnner an HP 4p. I have looked at all the documents that I could find and I keep running into a wall. (once and a while the scanner is recognized and works). I have started and restarted turned the scanner on and off. 
As Root I have reloaded the sg module and the aic7xxx driver.
Nothing seems to help.

The scanner is recognized but not as a scanner. It is a "process" and no matter what I have done I have not been able to change this.

Here is the output of lsscsi on my machine.
[0:0:0:0]    disk    ATA      ST380011A        3.06  /dev/sda
[0:0:1:0]    disk    ATA      IC35L060AVV207-0 V22O  /dev/sdb
[1:0:0:0]    cd/dvd  HL-DT-ST DVDRAM GSA-4081B A100  /dev/scd0
[1:0:1:0]    cd/dvd  HL-DT-ST CD-RW GCE-8520B  1.00  /dev/scd1
[2:0:0:0]    disk    ATA      Hitachi HDT72505 V56O  /dev/sdc
[5:0:0:0]    disk    HP       Photosmart A510  1.00  /dev/sdi
[6:0:0:0]    disk    CBM      Flash Disk       4.00  /dev/sdd
[7:0:0:0]    disk    Generic  USB SD Reader    1.00  /dev/sde
[7:0:0:1]    disk    Generic  USB CF Reader    1.01  /dev/sdf
[7:0:0:2]    disk    Generic  USB SM Reader    1.02  /dev/sdg
[7:0:0:3]    disk    Generic  USB MS Reader    1.03  /dev/sdh
[8:0:2:0]    process HP       C1130A           3540  -       

The last line is my scanner. Note there is no /dev associated with it
and it is consider a process.

I have seen similar posts but the solutions have not worked yet.

thanks in advance.

---

### Post by eddarl on 2008-06-04
I have solved the problem for now.
In /etc/sane.d/dll.conf, I added C1130A in the Hp section.
Now when I do "sudo sane-find-scanner" it finds my scsi scanner.

Also after this add

sudo ln /dev/sg?  /dev/scanner

And for me as a user to use the scanner

sudo chmod 666 /dev/sg?

where sg? is port scsi scanner is attached. Shown with "sane-find-scanner'

---

### Post by eddarl on 2008-06-06
I have spent a frustrating couple of days. It seems my solution above works only so so. Sometimes scanner is recognized. More often not.

However, I stumbled on this work around when reading man page of lsscsi.

If I run lsscsi with -g option. I get that my scanner is connected to /dev/sg11. If I then run sudo ln /dev/sg11 /dev/scanner and change the permissions sudo chmod 666 /dev/sg11. I am able to run the sanner as user.
I hope this is userfull to others.

---

