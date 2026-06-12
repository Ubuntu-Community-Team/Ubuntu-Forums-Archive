---
title: "Installed a new DVD burner and now I can't burn anything"
date: 2010-02-12
forum: Hardware
---

### Post by Nugar on 2010-02-12
Hi all,

Recently, I changed the DVD-RW unit on my Ubuntu 9.10 64-bit box. I was using an IDE unit and changed to a SATA drive.

Now, whenever I try to burn anything, with any application, I just get a coaster. I've found some threads and pages confirming this behavior, but I've failed to find a solution.

Does anyone know how to fix this?

I'm using Ubuntu 9.10 Karmic Koala 64-bit and the drive is an LG Supermulti HL-DT-ST DVDRAM GH22NS50. 

Thanks in advance for any guidance here,

---

### Post by gordintoronto on 2010-02-12
Try this: reboot, don't start other programs, run Brasero, change the settings in Brasero to slow down the burning.

How fast is your computer?

---

### Post by Nugar on 2010-02-13
Thanks, gordintoronto, I'll try that, although this box burned with no problems with the IDE drive.

I have an AMD Phenom II Quad core running at 3.2ghz with 4gb ram. So I don't think that's the issue.

Cheers,

---

### Post by carlosbellino on 2010-03-26
Hi, try cheking that you DVD-writer have "pata_atiixp driver" with
command "[FONT=monospace]dmesg | grep scsi[0-7]"[/FONT]
__________________________________________________  _______________________
[FONT=monospace]kaname@kaname-desktop:~$ dmesg | grep scsi[0-7]
[    1.274677] scsi0 : ahci
[    1.274727] scsi1 : ahci
[    1.274757] scsi2 : ahci
[    1.274785] scsi3 : ahci
[COLOR=Red][    1.275092] scsi4 : pata_atiixp
[    1.275120] scsi5 : pata_atiixp[/COLOR]
[    2.079988] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.379864] scsi6 : SCSI emulation for USB Mass Storage devices
__________________________________________________  ________________________

Sata Channels 4 and 5 have it,
Verify where is your burner:
"dmesg | grep scsi | grep GH22NS50"

[/FONT][FONT=monospace]__________________________________________________  ________________________

kaname@kaname-desktop:~$ dmesg | grep scsi | grep GH22NS50
[    2.058836] [COLOR=Red]scsi 2[/COLOR]:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[/FONT][FONT=monospace]__________________________________________________  ________________________
[/FONT]
[FONT=monospace]and [/FONT]then at the mobo plug the SATA cable on 4th or 5th sata channel..

---

### Post by Nugar on 2010-03-26
Hi carlos,

Thanks, but what I ultimately did, out of lack of time, was reinstall the IDE drive and it works again :)

Cheers!

---

