---
title: "Toshiba 500 GB HDD Input/Output Read Error"
date: 2014-09-18
forum: Hardware
---

### Post by eruptionjoojo on 2014-09-18
Hello Everyone,

                 I have a Toshiba Satellite C850 i0013 Laptop, the main specifications are as under : -

Processor     Intel Core i3-3110M
Chipset Model     Intel HM76
RAM     6GB(DDR3) : 1600Mhz
HDD     500GB (5400 rpm)

[http://www.infibeam.com/Computers_Accessories/toshiba-satellite-c850-i0013-notebook/P-coac-86019414686-cat-z.html](http://www.infibeam.com/Computers_Accessories/toshiba-satellite-c850-i0013-notebook/P-coac-86019414686-cat-z.html)

I was having Windows 7 installed on my 500 GB HDD along with Ubuntu (Wubi install). But, somehow Windows 7 stopped to start and the screen would not move ahead of the cursor blinking after the initial BIOS screen. So, I formatted the HDD using Gparted and removed Windows 7 completely along with Ubuntu as neither was bootable. But, now my HDD is listed as unallocated under Gparted as well it lists that there is no partition table. So, while I try to create one I get an Input/Output read error. I can't install Windows 7 onto the HDD as Windows DVD gets stuck before the selection of the HDD partition for installation comes into play as well same is the case while I try to install Ubuntu.
                                                          So, please guide me as to what should be done in order to save my HDD.

Regards,
Joojo.

---

### Post by matt_symes on 2014-09-18
Hi

Run a SMART test on the drive from a LiveCD/USB as the disk or its controller may be failing.

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

Also you may want to post the output from dmseg. Start with this command to see where the timestamps for the disk are in dmesg and then look around the time stamps to see what error messages are displayed.

```
dmesg | grep sda
```

Kind regards

---

### Post by eruptionjoojo on 2014-09-18
Thanks a lot for your quick reply ...... really appreciate it ...... I would be posting the output of the commands in a short while ............ 

```
dmesg | grep sda
```

Output:

```

[    3.826674] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.826755] sd 0:0:0:0: [sda] Write Protect is off
[    3.826763] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.826801] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.342431] sd 0:0:0:0: [sda] Unhandled sense code
[   10.342434] sd 0:0:0:0: [sda]  
[   10.342439] sd 0:0:0:0: [sda]  
[   10.342462] sd 0:0:0:0: [sda]  
[   10.342468] sd 0:0:0:0: [sda] CDB: 
[   10.342479] end_request: I/O error, dev sda, sector 0
[   10.342538] Buffer I/O error on device sda, logical block 0
[   15.566799] sd 0:0:0:0: [sda] Unhandled sense code
[   15.566802] sd 0:0:0:0: [sda]  
[   15.566807] sd 0:0:0:0: [sda]  
[   15.566830] sd 0:0:0:0: [sda]  
[   15.566835] sd 0:0:0:0: [sda] CDB: 
[   15.566846] end_request: I/O error, dev sda, sector 0
[   15.566917] Buffer I/O error on device sda, logical block 0
[   20.483059] sd 0:0:0:0: [sda] Unhandled sense code
[   20.483062] sd 0:0:0:0: [sda]  
[   20.483067] sd 0:0:0:0: [sda]  
[   20.483090] sd 0:0:0:0: [sda]  
[   20.483095] sd 0:0:0:0: [sda] CDB: 
[   20.483105] end_request: I/O error, dev sda, sector 0
[   20.483177] Buffer I/O error on device sda, logical block 0
[   25.010978] sd 0:0:0:0: [sda] Unhandled sense code
[   25.010981] sd 0:0:0:0: [sda]  
[   25.010985] sd 0:0:0:0: [sda]  
[   25.011008] sd 0:0:0:0: [sda]  
[   25.011013] sd 0:0:0:0: [sda] CDB: 
[   25.011024] end_request: I/O error, dev sda, sector 0
[   25.011095] Buffer I/O error on device sda, logical block 0
[   30.815978] sd 0:0:0:0: [sda] Unhandled sense code
[   30.815982] sd 0:0:0:0: [sda]  
[   30.815986] sd 0:0:0:0: [sda]  
[   30.816009] sd 0:0:0:0: [sda]  
[   30.816014] sd 0:0:0:0: [sda] CDB: 
[   30.816025] end_request: I/O error, dev sda, sector 0
[   30.816096] Buffer I/O error on device sda, logical block 0
[   36.020268] sd 0:0:0:0: [sda] Unhandled sense code
[   36.020271] sd 0:0:0:0: [sda]  
[   36.020275] sd 0:0:0:0: [sda]  
[   36.020298] sd 0:0:0:0: [sda]  
[   36.020303] sd 0:0:0:0: [sda] CDB: 
[   36.020314] end_request: I/O error, dev sda, sector 0
[   36.020386] Buffer I/O error on device sda, logical block 0
[   40.848374] sd 0:0:0:0: [sda] Unhandled sense code
[   40.848377] sd 0:0:0:0: [sda]  
[   40.848382] sd 0:0:0:0: [sda]  
[   40.848405] sd 0:0:0:0: [sda]  
[   40.848410] sd 0:0:0:0: [sda] CDB: 
[   40.848420] end_request: I/O error, dev sda, sector 0
[   40.848493] Buffer I/O error on device sda, logical block 0
[   45.528371] sd 0:0:0:0: [sda] Unhandled sense code
[   45.528374] sd 0:0:0:0: [sda]  
[   45.528378] sd 0:0:0:0: [sda]  
[   45.528401] sd 0:0:0:0: [sda]  
[   45.528407] sd 0:0:0:0: [sda] CDB: 
[   45.528417] end_request: I/O error, dev sda, sector 0
[   45.528490] Buffer I/O error on device sda, logical block 0
[   50.668817] sd 0:0:0:0: [sda] Unhandled sense code
[   50.668821] sd 0:0:0:0: [sda]  
[   50.668825] sd 0:0:0:0: [sda]  
[   50.668848] sd 0:0:0:0: [sda]  
[   50.668854] sd 0:0:0:0: [sda] CDB: 
[   50.668864] end_request: I/O error, dev sda, sector 0
[   50.668936] Buffer I/O error on device sda, logical block 0
[   50.669045] Dev sda: unable to read RDB block 0
[   55.436797] sd 0:0:0:0: [sda] Unhandled sense code
[   55.436800] sd 0:0:0:0: [sda]  
[   55.436804] sd 0:0:0:0: [sda]  
[   55.436827] sd 0:0:0:0: [sda]  
[   55.436832] sd 0:0:0:0: [sda] CDB: 
[   55.436843] end_request: I/O error, dev sda, sector 0
[   55.436915] Buffer I/O error on device sda, logical block 0
[   59.608469] sd 0:0:0:0: [sda] Unhandled sense code
[   59.608472] sd 0:0:0:0: [sda]  
[   59.608476] sd 0:0:0:0: [sda]  
[   59.608499] sd 0:0:0:0: [sda]  
[   59.608505] sd 0:0:0:0: [sda] CDB: 
[   59.608515] end_request: I/O error, dev sda, sector 0
[   59.608587] Buffer I/O error on device sda, logical block 0
[   69.240598] sd 0:0:0:0: [sda] Unhandled sense code
[   69.240602] sd 0:0:0:0: [sda]  
[   69.240606] sd 0:0:0:0: [sda]  
[   69.240629] sd 0:0:0:0: [sda]  
[   69.240635] sd 0:0:0:0: [sda] CDB: 
[   69.240645] end_request: I/O error, dev sda, sector 24
[   69.240718] Buffer I/O error on device sda, logical block 3
[   78.192273] sd 0:0:0:0: [sda] Unhandled sense code
[   78.192276] sd 0:0:0:0: [sda]  
[   78.192280] sd 0:0:0:0: [sda]  
[   78.192303] sd 0:0:0:0: [sda]  
[   78.192309] sd 0:0:0:0: [sda] CDB: 
[   78.192319] end_request: I/O error, dev sda, sector 24
[   78.192392] Buffer I/O error on device sda, logical block 3
[   83.332613] sd 0:0:0:0: [sda] Unhandled sense code
[   83.332616] sd 0:0:0:0: [sda]  
[   83.332621] sd 0:0:0:0: [sda]  
[   83.332644] sd 0:0:0:0: [sda]  
[   83.332649] sd 0:0:0:0: [sda] CDB: 
[   83.332660] end_request: I/O error, dev sda, sector 0
[   83.332732] Buffer I/O error on device sda, logical block 0
[   83.332840]  sda: unable to read partition table
[   83.333064] sda: detected capacity change from 0 to 500107862016
[   83.333128] sd 0:0:0:0: [sda] Attached SCSI disk
[   88.537043] sd 0:0:0:0: [sda] Unhandled sense code
[   88.537046] sd 0:0:0:0: [sda]  
[   88.537051] sd 0:0:0:0: [sda]  
[   88.537075] sd 0:0:0:0: [sda]  
[   88.537081] sd 0:0:0:0: [sda] CDB: 
[   88.537092] end_request: I/O error, dev sda, sector 0
[   88.537164] Buffer I/O error on device sda, logical block 0
[   93.673429] sd 0:0:0:0: [sda] Unhandled sense code
[   93.673432] sd 0:0:0:0: [sda]  
[   93.673436] sd 0:0:0:0: [sda]  
[   93.673459] sd 0:0:0:0: [sda]  
[   93.673464] sd 0:0:0:0: [sda] CDB: 
[   93.673475] end_request: I/O error, dev sda, sector 0
[   93.673546] Buffer I/O error on device sda, logical block 0
[  102.617024] sd 0:0:0:0: [sda] Unhandled sense code
[  102.617027] sd 0:0:0:0: [sda]  
[  102.617032] sd 0:0:0:0: [sda]  
[  102.617055] sd 0:0:0:0: [sda]  
[  102.617060] sd 0:0:0:0: [sda] CDB: 
[  102.617070] end_request: I/O error, dev sda, sector 8
[  102.617142] Buffer I/O error on device sda, logical block 1
[  111.556625] sd 0:0:0:0: [sda] Unhandled sense code
[  111.556628] sd 0:0:0:0: [sda]  
[  111.556633] sd 0:0:0:0: [sda]  
[  111.556655] sd 0:0:0:0: [sda]  
[  111.556661] sd 0:0:0:0: [sda] CDB: 
[  111.556671] end_request: I/O error, dev sda, sector 8
[  111.556743] Buffer I/O error on device sda, logical block 1
[  120.556264] sd 0:0:0:0: [sda] Unhandled sense code
[  120.556267] sd 0:0:0:0: [sda]  
[  120.556272] sd 0:0:0:0: [sda]  
[  120.556295] sd 0:0:0:0: [sda]  
[  120.556300] sd 0:0:0:0: [sda] CDB: 
[  120.556311] end_request: I/O error, dev sda, sector 8
[  120.556383] Buffer I/O error on device sda, logical block 1
[  129.495876] sd 0:0:0:0: [sda] Unhandled sense code
[  129.495879] sd 0:0:0:0: [sda]  
[  129.495884] sd 0:0:0:0: [sda]  
[  129.495907] sd 0:0:0:0: [sda]  
[  129.495912] sd 0:0:0:0: [sda] CDB: 
[  129.495923] end_request: I/O error, dev sda, sector 8
[  129.495996] Buffer I/O error on device sda, logical block 1
[  134.636231] sd 0:0:0:0: [sda] Unhandled sense code
[  134.636234] sd 0:0:0:0: [sda]  
[  134.636239] sd 0:0:0:0: [sda]  
[  134.636261] sd 0:0:0:0: [sda]  
[  134.636267] sd 0:0:0:0: [sda] CDB: 
[  134.636277] end_request: I/O error, dev sda, sector 0
[  134.636349] Buffer I/O error on device sda, logical block 0
[  139.772637] sd 0:0:0:0: [sda] Unhandled sense code
[  139.772640] sd 0:0:0:0: [sda]  
[  139.772645] sd 0:0:0:0: [sda]  
[  139.772668] sd 0:0:0:0: [sda]  
[  139.772673] sd 0:0:0:0: [sda] CDB: 
[  139.772684] end_request: I/O error, dev sda, sector 0
[  139.772756] Buffer I/O error on device sda, logical block 0
[  144.908989] sd 0:0:0:0: [sda] Unhandled sense code
[  144.908992] sd 0:0:0:0: [sda]  
[  144.908997] sd 0:0:0:0: [sda]  
[  144.909019] sd 0:0:0:0: [sda]  
[  144.909025] sd 0:0:0:0: [sda] CDB: 
[  144.909035] end_request: I/O error, dev sda, sector 0
[  144.909106] Buffer I/O error on device sda, logical block 0
[  150.050897] sd 0:0:0:0: [sda] Unhandled sense code
[  150.050900] sd 0:0:0:0: [sda]  
[  150.050905] sd 0:0:0:0: [sda]  
[  150.050928] sd 0:0:0:0: [sda]  
[  150.050933] sd 0:0:0:0: [sda] CDB: 
[  150.050944] end_request: I/O error, dev sda, sector 0
[  150.051014] Buffer I/O error on device sda, logical block 0
[  156.778881] sd 0:0:0:0: [sda] Unhandled sense code
[  156.778884] sd 0:0:0:0: [sda]  
[  156.778889] sd 0:0:0:0: [sda]  
[  156.778913] sd 0:0:0:0: [sda]  
[  156.778919] sd 0:0:0:0: [sda] CDB: 
[  156.778930] end_request: I/O error, dev sda, sector 0
[  156.778981] Buffer I/O error on device sda, logical block 0
[  161.915605] sd 0:0:0:0: [sda] Unhandled sense code
[  161.915609] sd 0:0:0:0: [sda]  
[  161.915614] sd 0:0:0:0: [sda]  
[  161.915637] sd 0:0:0:0: [sda]  
[  161.915643] sd 0:0:0:0: [sda] CDB: 
[  161.915654] end_request: I/O error, dev sda, sector 0
[  161.915705] Buffer I/O error on device sda, logical block 0
[  170.860954] sd 0:0:0:0: [sda] Unhandled sense code
[  170.860957] sd 0:0:0:0: [sda]  
[  170.860962] sd 0:0:0:0: [sda]  
[  170.860986] sd 0:0:0:0: [sda]  
[  170.860992] sd 0:0:0:0: [sda] CDB: 
[  170.861003] end_request: I/O error, dev sda, sector 8
[  170.862024] Buffer I/O error on device sda, logical block 1
[  179.818735] sd 0:0:0:0: [sda] Unhandled sense code
[  179.818739] sd 0:0:0:0: [sda]  
[  179.818744] sd 0:0:0:0: [sda]  
[  179.818767] sd 0:0:0:0: [sda]  
[  179.818773] sd 0:0:0:0: [sda] CDB: 
[  179.818784] end_request: I/O error, dev sda, sector 8
[  179.820158] Buffer I/O error on device sda, logical block 1
[  188.828333] sd 0:0:0:0: [sda] Unhandled sense code
[  188.828336] sd 0:0:0:0: [sda]  
[  188.828341] sd 0:0:0:0: [sda]  
[  188.828364] sd 0:0:0:0: [sda]  
[  188.828370] sd 0:0:0:0: [sda] CDB: 
[  188.828381] end_request: I/O error, dev sda, sector 8
[  188.829991] Buffer I/O error on device sda, logical block 1
[  197.781623] sd 0:0:0:0: [sda] Unhandled sense code
[  197.781626] sd 0:0:0:0: [sda]  
[  197.781631] sd 0:0:0:0: [sda]  
[  197.781654] sd 0:0:0:0: [sda]  
[  197.781660] sd 0:0:0:0: [sda] CDB: 
[  197.781671] end_request: I/O error, dev sda, sector 8
[  197.783415] Buffer I/O error on device sda, logical block 1
[  202.609601] sd 0:0:0:0: [sda] Unhandled sense code
[  202.609604] sd 0:0:0:0: [sda]  
[  202.609609] sd 0:0:0:0: [sda]  
[  202.609633] sd 0:0:0:0: [sda]  
[  202.609639] sd 0:0:0:0: [sda] CDB: 
[  202.609650] end_request: I/O error, dev sda, sector 0
[  202.611363] Buffer I/O error on device sda, logical block 0
[  208.959097] sd 0:0:0:0: [sda] Unhandled sense code
[  208.959101] sd 0:0:0:0: [sda]  
[  208.959106] sd 0:0:0:0: [sda]  
[  208.959129] sd 0:0:0:0: [sda]  
[  208.959135] sd 0:0:0:0: [sda] CDB: 
[  208.959146] end_request: I/O error, dev sda, sector 0
[  208.960866] Buffer I/O error on device sda, logical block 0
[  214.107669] sd 0:0:0:0: [sda] Unhandled sense code
[  214.107672] sd 0:0:0:0: [sda]  
[  214.107677] sd 0:0:0:0: [sda]  
[  214.107698] sd 0:0:0:0: [sda]  
[  214.107703] sd 0:0:0:0: [sda] CDB: 
[  214.107714] end_request: I/O error, dev sda, sector 0
[  214.109325] Buffer I/O error on device sda, logical block 0
[  219.268521] sd 0:0:0:0: [sda] Unhandled sense code
[  219.268524] sd 0:0:0:0: [sda]  
[  219.268529] sd 0:0:0:0: [sda]  
[  219.268550] sd 0:0:0:0: [sda]  
[  219.268556] sd 0:0:0:0: [sda] CDB: 
[  219.268566] end_request: I/O error, dev sda, sector 0
[  219.270218] Buffer I/O error on device sda, logical block 0
[  225.665542] sd 0:0:0:0: [sda] Unhandled sense code
[  225.665545] sd 0:0:0:0: [sda]  
[  225.665550] sd 0:0:0:0: [sda]  
[  225.665573] sd 0:0:0:0: [sda]  
[  225.665579] sd 0:0:0:0: [sda] CDB: 
[  225.665590] end_request: I/O error, dev sda, sector 0
[  230.870303] sd 0:0:0:0: [sda] Unhandled sense code
[  230.870307] sd 0:0:0:0: [sda]  
[  230.870312] sd 0:0:0:0: [sda]  
[  230.870335] sd 0:0:0:0: [sda]  
[  230.870341] sd 0:0:0:0: [sda] CDB: 
[  230.870352] end_request: I/O error, dev sda, sector 0
[  239.821621] sd 0:0:0:0: [sda] Unhandled sense code
[  239.821624] sd 0:0:0:0: [sda]  
[  239.821628] sd 0:0:0:0: [sda]  
[  239.821650] sd 0:0:0:0: [sda]  
[  239.821655] sd 0:0:0:0: [sda] CDB: 
[  239.821666] end_request: I/O error, dev sda, sector 8
[  244.969871] sd 0:0:0:0: [sda] Unhandled sense code
[  244.969874] sd 0:0:0:0: [sda]  
[  244.969879] sd 0:0:0:0: [sda]  
[  244.969900] sd 0:0:0:0: [sda]  
[  244.969906] sd 0:0:0:0: [sda] CDB: 
[  244.969916] end_request: I/O error, dev sda, sector 0
[  250.342758] sd 0:0:0:0: [sda] Unhandled sense code
[  250.342761] sd 0:0:0:0: [sda]  
[  250.342766] sd 0:0:0:0: [sda]  
[  250.342789] sd 0:0:0:0: [sda]  
[  250.342795] sd 0:0:0:0: [sda] CDB: 
[  250.342806] end_request: I/O error, dev sda, sector 0
[  255.547278] sd 0:0:0:0: [sda] Unhandled sense code
[  255.547281] sd 0:0:0:0: [sda]  
[  255.547286] sd 0:0:0:0: [sda]  
[  255.547309] sd 0:0:0:0: [sda]  
[  255.547315] sd 0:0:0:0: [sda] CDB: 
[  255.547326] end_request: I/O error, dev sda, sector 0
[  264.498595] sd 0:0:0:0: [sda] Unhandled sense code
[  264.498599] sd 0:0:0:0: [sda]  
[  264.498605] sd 0:0:0:0: [sda]  
[  264.498628] sd 0:0:0:0: [sda]  
[  264.498634] sd 0:0:0:0: [sda] CDB: 
[  264.498645] end_request: I/O error, dev sda, sector 8
[  269.651074] sd 0:0:0:0: [sda] Unhandled sense code
[  269.651077] sd 0:0:0:0: [sda]  
[  269.651082] sd 0:0:0:0: [sda]  
[  269.651104] sd 0:0:0:0: [sda]  
[  269.651109] sd 0:0:0:0: [sda] CDB: 
[  269.651120] end_request: I/O error, dev sda, sector 0

```

---

### Post by whitesmith on 2014-09-18
You can run SMART tests from the Disks utility under Applications->Accessories. Nothing to install. Wubi may be your problem. It is no longer supported by Ubuntu. Regards.

---

### Post by eruptionjoojo on 2014-09-18
Thanks a lot for your reply ................ but unfortunately, SMART tests are Not supported under Disk Utility ...............

---

### Post by eruptionjoojo on 2014-09-18
```

sudo smartctl -t long /dev/sda

```

Output :
```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.14-kali1-amd64] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MK5075GSX
Serial Number:    72CGFV0OS
LU WWN Device Id: 5 000039 426f030ea
Firmware Version: GT001M
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Sep 19 08:20:57 2014 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (  89)	The previous self-test completed having
					the electrical element of the test
					failed.
Total time to complete Offline 
data collection: 		(  120) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 194) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       2126
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       1202
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       3536
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1025
 10 Spin_Retry_Count        0x0033   124   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1198
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       35
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       97
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       2391
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       39 (Min/Max 14/58)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       259
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       832
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   253   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       34
222 Loaded_Hours            0x0032   099   099   000    Old_age   Always       -       767
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       260
240 Head_Flying_Hours       0x0001   001   001   001    Pre-fail  Offline  FAILING_NOW 1

SMART Error Log Version: 1
ATA Error Count: 10351 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 10351 occurred at disk power-on lifetime: 1016 hours (42 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 0a 00 00 00 60  Error: UNC at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 08 00 00 00 40 00      00:06:14.628  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:06:14.625  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      00:06:14.625  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:06:14.624  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:06:14.624  SET FEATURES [Set transfer mode]

Error 10350 occurred at disk power-on lifetime: 1016 hours (42 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 02 08 00 00 60  Error: UNC at LBA = 0x00000008 = 8

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 08 00 00 40 00      00:06:05.684  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:06:05.682  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      00:06:05.682  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:06:05.681  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:06:05.681  SET FEATURES [Set transfer mode]

Error 10349 occurred at disk power-on lifetime: 1016 hours (42 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 f2 00 00 00 60  Error: UNC at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 f0 00 00 00 40 00      00:06:00.512  READ FPDMA QUEUED
  60 08 e8 20 60 38 40 00      00:06:00.508  READ FPDMA QUEUED
  60 08 e0 80 5f 38 40 00      00:06:00.484  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:06:00.482  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      00:06:00.482  READ NATIVE MAX ADDRESS EXT

Error 10348 occurred at disk power-on lifetime: 1016 hours (42 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 da 00 00 00 60  Error: UNC at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 d8 00 00 00 40 00      00:05:55.310  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:05:55.114  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      00:05:55.114  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:05:55.114  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:05:55.113  SET FEATURES [Set transfer mode]

Error 10347 occurred at disk power-on lifetime: 1016 hours (42 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 d2 00 00 00 60  Error: UNC at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 d0 00 00 00 40 00      00:05:49.973  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:05:49.971  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      00:05:49.970  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:05:49.970  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:05:49.970  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: electrical failure 90%      1017         0
# 2  Short offline       Completed without error       00%         3         -
# 3  Short offline       Completed without error       00%         3         -
# 4  Short offline       Completed without error       00%         3         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by eruptionjoojo on 2014-09-20
Since it seems my HDD has gone bad ............ left with no options I have ordered a new one ..................

---

