---
title: "3ware 9550SX"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by AlexBligh on 2005-10-30
Does anyone have a 3Ware 9550SX working in Ubuntu (preferably on an AMD64 Opteron with SMP).

So far I've run into the following problems:
* Support not present in 2.6.12 as shipped
* Cannot patch kernel sources as advertised (i.e. dpatch) to drop in new drivers (complains about a /tmp/ file for the ABI for the flavour I selected not being present) - got around this by patching sources directly
* On backporting the 2.6.14 driver, startup reports all sorts of bad LUN messages (see the end)
* mkfs INCREDIBLY slow (like so slow I had to give up) - appeared to be writing one inode a minute.
This is attached to a SATA-3 array (1.5Tb RAID 5)

Can it really be this hard?

Help!?

Alex

Oct 30 20:09:09 localhost kernel: [  138.688249]  /dev/scsi/host4/bus0/target0/lun0: p1 < p5 >
Oct 30 20:09:09 localhost kernel: [  138.712496] Attached scsi disk sdb at scsi4, channel 0, id 0, lun 0
Oct 30 20:09:09 localhost kernel: [  138.712814] scsi: On host 4 channel 0 id 0
only 511 (max_scsi_report_luns) of 214715501 luns reported, try increasing max_scsi_report_luns.
Oct 30 20:09:09 localhost kernel: [  138.712817] scsi: host 4 channel 0 id 0 lun 0x383438203636202d has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712822] scsi: host 4 channel 0 id 0 lun 0x204c697665203078 has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712826] scsi: host 4 channel 0 id 0 lun 0x6666666666666666 has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712830] scsi: host 4 channel 0 id 0 lun 0x3838303039303030 has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712835] scsi: host 4 channel 0 id 0 lun 0x0a74696c65626c69 has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712839] scsi: host 4 channel 0 id 0 lun 0x7420333332382031 has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712843] scsi: host 4 channel 0 id 0 lun 0x206662636f6e2c20 has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712848] scsi: host 4 channel 0 id 0 lun 0x4c69766520307866 has a LUN larger than currently supported.
Oct 30 20:09:09 localhost kernel: [  138.712852] scsi: host 4 channel 0 id 0 lun 0x6666666666666638 has a LUN larger than currently supported.

---

### Post by skylark on 2005-11-11
Did you ever find a fix for this? I imagine you could install a custom 2.6.14 kernel which might help. I thought 3ware stuff was meant to be linux friendly, so this is a little surprising.

---

### Post by HS-L on 2006-02-02
Still no fix?

I'm trying to install ubuntu server on a raid1 system,
but I've had no luck sofar.

HS-L

---

### Post by cylaris on 2006-04-25
Hi Guys,


Just FYI in case your still awaiting updates.

I have the 9550SX in a Dual Opteron 265 machine with 8x500GB HDs and it runs great using the latest kernel 2.15.20. I had problems with 2.15.19 but 2.15.20 fixed it. 

Cylaris

---

### Post by gcb on 2006-05-15
Pardon my ignorance, but I'm trying to install Ubuntu on a machine with a RAID-5 off the 9550SX.  Is there a way to get an install ISO with the necessary kernel version?

Thanks for any advice,
gcb

---

### Post by TJInc. on 2006-06-23
Hi All,

Can anyone help this person out as I'm about to face the same issue. I contemplating purchasing a true hardware based raid controller like a 3ware SATA-II 4 port controller and want to know whether is exercise will work or not. especially on the 64bit version using an AMD64 X2 (AM2) 4200+ machine

Somebody please respond.

Thanks.

---

### Post by dean123 on 2006-08-04
> **TJInc. said:**
> Hi All,

Can anyone help this person out as I'm about to face the same issue. I contemplating purchasing a true hardware based raid controller like a 3ware SATA-II 4 port controller and want to know whether is exercise will work or not. especially on the 64bit version using an AMD64 X2 (AM2) 4200+ machine

Somebody please respond.

Thanks.

ie LUN messages: 

You need to update the driver if your system has 4G RAM or more and is running kernel x86_64. 

# uname -a (check your kernel)
# dmesg | grep 3w (check 3ware driver version) 

3ware posts 2 different driver sources for upstream kernels ie kernels from [www.kernel.org](www.kernel.org) and supported kernels/distros ie Fedora4, Redhat AS4 etc...

Use driver sources from latest release 9.3.0.4. You may have to recompile their driver source against your existing kernel. Send an email to 3ware support, they have best linux support staff among raid vendors. 3ware don't specifically support Ubuntu but they will help linux users. Good luck :)

---

