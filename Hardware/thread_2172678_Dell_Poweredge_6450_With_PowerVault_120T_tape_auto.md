---
title: "Dell Poweredge 6450 With PowerVault 120T tape autoloader Issues"
date: 2013-09-06
forum: Hardware
---

### Post by mrbill2 on 2013-09-06
Hello I am running a fresh install of Ubuntu 12.04 on my Dell PowerEdge 6450. I am attempting to get my Dell powervault 120T autoloader working, but am not having any luck.
It is a  scsi device, and shows up as two separate devices, the quantum DLT 4000 drive inside, and the autoloader picker. No scsi conflicts.

The install would lock up if the device was attached. Its activity indicator would flash, but nothing would happen for a long duration of time, so i did the install with it disconnected.
Im assuming the device is /dev/st0. Ive tried dumping a small tar archive to the device with no luck. Any help on the subject is appreciated.

---

### Post by tgalati4 on 2013-09-06
Was the device working?  Perhaps the tape drive has a short and that is why the install locked up when attached.  Do you have any other devices or other machines to swap?  

Dell has a diagnostic CD for their servers.  Burn that and boot the server with it.  Then run through the tape diagnostics--and all the other diagnostics as well.  See if there are any hardware faults.  Tape drives are simple devices.  They either work or they don't.  Not much in between.

A quick search:  [http://dell.driversdown.com/dell-drivers-downloads/Dell-CD-ISO-Service-and-Diagnostics_17379.shtml](http://dell.driversdown.com/dell-drivers-downloads/Dell-CD-ISO-Service-and-Diagnostics_17379.shtml)

Check the BIOS version and upgrade that while you are at it.  You want the latest BIOS on these older machines.

---

### Post by mrbill2 on 2013-09-06
Ive actually just recently replaced the entire tape drive in it, as the Device was not passing its POST before. Now however it powers up, i can set the scsi id, and i can load a tape, so it seems unlikely that the device is bad, however ill burn the dell diagnostic cd and give it a shot.

This is a HVD SCSI drive, and i dont have any other HVD scsi controllers to test it with, however the controller im using is also what my hardware raid array is on and ubuntu is booting off that just fine so I don't think that is the problem either.

---

### Post by mrbill2 on 2013-09-06
Im not seeing any bootable diagnostic utility for the Tape autoloader. 

I found the driver/application for windows server 2003 called "Dell Library and Tape Tools", Ill boot windows server 2003 and see if there are any diagnostics in there.

---

### Post by tgalati4 on 2013-09-06
It's possible that the tape mechanism works, but the SCSI backend is messed up.  That would cause a bus freeze.  Is there a terminator that must be set on the SCSI chain?  Perhaps changing ID's or moving devices around.  I would first find a diagnostic or verify that the tape works with WinServer, before trying to troubleshoot in linux.  Nothing more frustrating than chasing hardware problems.

---

