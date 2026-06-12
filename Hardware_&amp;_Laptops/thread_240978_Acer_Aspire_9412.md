---
title: "Acer Aspire 9412"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by stubbe on 2006-08-21
Hi I'm new here, installing ubuntu on my Acer Aspire 9412 (it's a 9410 with NVidia graphic card I think). Installation went smooth but when I boot up ubuntu there's this slight error message before it entering the bootsplash. It's hex codes and said something about PCI and memory could not be read.

I've been using ubuntu on that laptop for about two weeks now, I experience some 3-5 seconds lockups. When I look into /var/log/messages this is the report :

```
Aug 18 03:19:27 stubbe kernel: [4298880.086000] ata1 is slow to respond, please be patient
Aug 18 03:19:56 stubbe kernel: [4298906.385000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 03:19:56 stubbe kernel: [4298906.419000] sda: Current: sense key: No Sense
Aug 18 03:19:56 stubbe kernel: [4298906.419000]     Additional sense: No additional sense information
Aug 18 03:20:22 stubbe kernel: [4298934.928000] ata1 is slow to respond, please be patient
Aug 18 03:20:51 stubbe kernel: [4298961.227000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 03:20:51 stubbe kernel: [4298961.261000] sda: Current: sense key: No Sense
Aug 18 03:20:51 stubbe kernel: [4298961.261000]     Additional sense: No additional sense information
Aug 18 03:20:51 stubbe kernel: [4298961.263000] sr: Current [descriptor]: sense key: Aborted Command
Aug 18 03:20:51 stubbe kernel: [4298961.263000]     Additional sense: Scsi parity error
Aug 18 03:26:37 stubbe kernel: [4299309.674000] ata1 is slow to respond, please be patient
Aug 18 03:27:06 stubbe kernel: [4299335.973000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 03:27:06 stubbe kernel: [4299336.007000] sda: Current: sense key: No Sense
Aug 18 03:27:06 stubbe kernel: [4299336.007000]     Additional sense: No additional sense information
Aug 18 03:27:06 stubbe kernel: [4299336.009000] sr: Current [descriptor]: sense key: Aborted Command
Aug 18 03:27:06 stubbe kernel: [4299336.009000]     Additional sense: Scsi parity error
Aug 18 03:38:06 stubbe kernel: [4299999.400000] ata1 is slow to respond, please be patient
Aug 18 03:38:35 stubbe kernel: [4300025.699000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 03:38:35 stubbe kernel: [4300025.732000] sda: Current: sense key: No Sense
Aug 18 03:38:35 stubbe kernel: [4300025.732000]     Additional sense: No additional sense information
Aug 18 03:59:13 stubbe kernel: [4301266.402000] ata1 is slow to respond, please be patient
Aug 18 03:59:42 stubbe kernel: [4301292.701000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 03:59:42 stubbe kernel: [4301292.735000] sda: Current: sense key: No Sense
Aug 18 03:59:42 stubbe kernel: [4301292.735000]     Additional sense: No additional sense information
Aug 18 04:14:38 stubbe kernel: [4302192.008000] ata1 is slow to respond, please be patient
Aug 18 04:14:45 stubbe kernel: [4302198.307000] sr 0:0:1:0: ioctl_internal_command return code = 8000002
Aug 18 04:14:45 stubbe kernel: [4302198.307000]    : Current [descriptor]: sense key: Aborted Command
Aug 18 04:14:45 stubbe kernel: [4302198.308000]     Additional sense: Scsi parity error
Aug 18 04:14:45 stubbe kernel: [4302198.358000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 04:14:48 stubbe kernel: [4302198.358000] sda: Current: sense key: No Sense
Aug 18 04:14:48 stubbe kernel: [4302198.358000]     Additional sense: No additional sense information
Aug 18 04:20:41 stubbe kernel: [4302554.722000] ata1 is slow to respond, please be patient
Aug 18 04:21:10 stubbe kernel: [4302581.021000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 04:21:10 stubbe kernel: [4302581.055000] sda: Current: sense key: No Sense
Aug 18 04:21:10 stubbe kernel: [4302581.055000]     Additional sense: No additional sense information
Aug 18 04:21:10 stubbe kernel: [4302581.056000] sr: Current [descriptor]: sense key: Aborted Command
Aug 18 04:21:10 stubbe kernel: [4302581.056000]     Additional sense: Scsi parity error
Aug 18 04:23:26 stubbe kernel: [4302719.152000] ata1 is slow to respond, please be patient
Aug 18 04:23:55 stubbe kernel: [4302745.451000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 04:23:55 stubbe kernel: [4302745.485000] sda: Current: sense key: No Sense
Aug 18 04:23:55 stubbe kernel: [4302745.485000]     Additional sense: No additional sense information
Aug 18 04:37:17 stubbe kernel: [4303550.711000] ata1 is slow to respond, please be patient
Aug 18 04:37:46 stubbe kernel: [4303577.010000] ata1: status=0x50 { DriveReady SeekComplete }
Aug 18 04:37:46 stubbe kernel: [4303577.044000] sda: Current: sense key: No Sense
Aug 18 04:37:46 stubbe kernel: [4303577.044000]     Additional sense: No additional sense information
```

and then one day out of nowhere when ubuntu is loading on the splash screen, somewhere in the middle the graphic screwed up. But after Nvidia logo appear it's okay again. Also booting up to windows it's fine.

I wonder if anybody have the solution in this, or have the same type of notebook as mine and running ubuntu without any problem?

---

### Post by Fire on 2006-10-02
I have the Acer Aspire 9410 intel based graphics and I have had the same problem with the 3 sec lock ups.  I have not yet figured out what that is all about.  But I was dual booting and I was getting errors through the linux load process.  I removed the partitions and  reformated the drive and currently I am only booting linux and I am not getting those errors any longer.  I also noticed that having the Partition in the front of the drive which was holding the image for re-installing windows seamed to give some problems.

Instead of dual booting I am trying to set up VMWare and see if I can get anything I may need from windows to run that way.  Sadly I do have a program for work that I need to run on this system, atleast for the next few weeks, and it will only run in windows.

---

### Post by RealG187 on 2007-05-28
I have Acer Aspire 9410 laptop intel graphics, its something like 945 GM, the sticer says 50, I will look at the exact text when I  get home.

I wanna run Kubuntu 7.04, will all my Laptop's built in hardware work [WLAN, Bluetooth, Card reader, Web Cam, Speakers, etc.]

I contacted Acer and they dont support Linux, do I need drivers??

---

