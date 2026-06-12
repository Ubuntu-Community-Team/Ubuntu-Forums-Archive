---
title: "SATA problems"
date: 2011-03-08
forum: Hardware
---

### Post by HandyGandy on 2011-03-08
First I know that there is some kind of problem my drive, my controller, cable or something else. So please don't give me generic advice like "replace the drive" etc. I am looking for some sense of what the actual problems with the systems are. I understand that this problem may be beyond what people here may know,
or that it may not, If it is so then I would greatly appreciate it if you could point me to a forum where they are more likely to help me.

Now on to the basics. I have two hard drives, the linux system is on sda and the second one is storage only, but I do a lot of stuff on it.  About six months ago I converted the whole system to mostly xfs pasrtitions. The first partition on sda was an NTFS partition. It contained two copies of XP, one dirty, one almost pristine for those times when I needed to use XP which were getting much rarer. The boot partition was ext4. The remaining partitions were all xfs or xfs converted from NTFS. In fact all the partitions on sda  were originally NTFs but then were converted to xfs.

About three months ago something flakey started happening on my first hard drive. I started to get some occasional rare sporadic errors on sda. Eventually the feeling I got was there was something wrong with the first partition on sda (NTFS formated). So I booted into Xp and did a chkdisk, It cleaned up some errors and that seemed to be it.

A month ago I started seeing errors again. Becoming more frequent. Most of these still seemed to be centered around the NTFS partition. One which was most glaring was that updatedb seemed to spend about 20 times as much time indexing the NTFS partition as it did all the rest of the partitions ( about 20G vs800G ). The system would crash due to drive errors which always seemed to happen when updatedb was indexing that NTFS partition.

I decided to boot again into XP and try chkdisk, but couldn't boot into either XP systems. Oh well. I could still see the stuff in that partition. I decided to remove that partition from fstab so it would not be mounted.
That day i tried to boot several times and got clean boots. I brought it up and it ran for a week with no problems. Yesterday, I was going to "bounce" the system because of a large package update--I think the who kde system was upgraded, I was going to be away for about four -six hours. So I shutdown the system. When i tried to bring it up again,sda would visible at start but vanish during boot. Now I can't gain any access to it.

The thing is that all the times I ran smartctl it seemed to be all clear. I'm certain that everime I ran smartcrl self tests they came out ckean. For that reason I suspected it was more of a software or hardware interacting with software problem then a straight hardware problem.

Now I try to run smartctl and here is what I get:
sudo smartctl -a  -T verypermissive /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

Device: /2:0:0:0  Version:
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
>> Terminate command early due to bad response to IEC mode page
Log Sense failed, IE page [scsi response fails sanity test]

Error Counter logging not supported
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
Device does not support Self Test logging

----------------------------------------------------

ATM I am running a liveCD with the 2.6.35 kernel,
and dmesg is report the following error message.


Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  153.453504] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 11 85 6f 39 00 00 01 00
[  153.453511] end_request: I/O error, dev sda, sector 293957433
[  153.453520] sd 2:0:0:0: [sda] Unhandled error code
[  153.453522] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  153.453525] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 11 85 6f 3a 00 00 07 00
[  153.453532] end_request: I/O error, dev sda, sector 293957434
[  153.453563] sd 2:0:0:0: [sda] Unhandled error code
[  153.453565] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

Now the reason that I was trying to nurse this drive along was that for a long time I was planning to get a new drive  to replace it on next Mon ( March 14 ).

If  at all possible I would like to nurse this drive till the 15th, Any suggestions?

---

