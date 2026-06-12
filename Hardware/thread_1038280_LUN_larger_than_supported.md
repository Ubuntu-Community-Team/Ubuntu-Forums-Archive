---
title: "LUN larger than supported"
date: 2009-01-12
forum: Hardware
---

### Post by Kuea on 2009-01-12
Hello!

I recently salvaged a scsi disk array from the junk pile at work (with permission and much paperwork) and hooked it up to my Ubuntu 8.10 box.  The only problem is, it only sees half of the storage space (should be 4TB) and I get odd messages at boot:

[    3.046622] scsi: waiting for bus probes to complete ...
[    5.692931] scsi 0:0:0:0: Direct-Access     RS3160sa  UD100           0001 PQ: 0 ANSI: 3
[    5.692943] scsi target0:0:0: tagged command queuing enabled, command queue depth 16.
[    5.692958] scsi target0:0:0: Beginning Domain Validation
[    5.693102] scsi target0:0:0: asynchronous
[    5.694007] scsi target0:0:0: wide asynchronous
[    5.694363] scsi target0:0:0: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 31)
[    5.706612] scsi target0:0:0: Domain Validation skipping write tests
[    5.706615] scsi target0:0:0: Ending Domain Validation
[    5.706760] scsi: host 0 channel 0 id 0 **lun 0x0000000029000000 has a LUN larger than currently supported.**
[    9.890291] Driver 'sd' needs updating - please use bus_type methods
[    9.890631] sd 0:0:0:0: [sda] 4294950912 512-byte hardware sectors (**2199015 MB**)

I'm guessing that LUN message is the problem.  Do I need to split it up into two 2TB sections, or is there something else going on here?

Thanks,

---

### Post by electrogeist on 2009-01-12
Nice score!  That looks like a nice piece of fairly recent equipment!

First off I would find documentation for the RS3160sa.  And you did not say what controller you are using...become familiar with that as well.

You may try adding, in a file under /etc/modprobe.d/ for whatever your controller is, something like:

	options scsi_mod max_luns=128 default_dev_flags=0x40000

The default_dev_flags=0x40000 may change the way the LUNs are scanned, some devices report them oddly or incorrectly.
 
 
PS can I come raid your junkpile too?  ;)

---

