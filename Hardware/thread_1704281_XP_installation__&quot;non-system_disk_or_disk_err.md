---
title: "XP installation  &quot;non-system disk or disk error&quot;"
date: 2011-03-10
forum: Hardware
---

### Post by TCMGO on 2011-03-10
[FONT=Times New Roman][SIZE=3]You guys have been a great in helping me work through a very frustrating dual boot set up with my Abit NF7-S V2 mobo. Thank you. I made it to first base only to hit another wall at second. I was able to finally install the XP OS on a SATA drive, but when it went to boot up (to finish installation) it hit this error: “non-system disk or disk error.” Here are the steps I took:[/SIZE][/FONT]

[LIST]
[*][FONT=Times New Roman][SIZE=3]Booted up with XP install CD, hit F6 and successfully loaded the SATA drivers, which this mobo needs to see SATA drives.[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]XP sees the SATA drive. Being a used drive (WD 800 – Serial ATA) and wanting a clean slate, I low-level formatted prior to installation, wherein I had XP format it in NTFS.[/SIZE][/FONT]
[*][FONT=Times New Roman][SIZE=3]After formatting, it then proceeded to finish loading the Windows files with no errors and then hit the error above when it went into reboot.[/SIZE][/FONT]
[/LIST][FONT=Times New Roman][SIZE=3]I took the drive to another computer and it checks out as healthy and active. The Windows file with all its sub folders is accessible. Solutions I have tried:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]In bios, I tried a number of boot order options to no avail:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Boot CD first, SATA second[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Boot CD first, SCSI second[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Under Integrated peripherals, I tried both enabling and disabling the Serial ATA controller and X-SATA Raid Rom to no avail. I believe the drive and XP installation is good, but have no way to absolutely verify this. Somehow, in boot up when it comes to selecting the boot/system disk it doesn’t see the SATA drive, even though the mobo saw it during the XP installation. Any suggestions?[/SIZE] [/FONT]

---

