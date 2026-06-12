---
title: "need help with tape transfers"
date: 2008-08-29
forum: General Help
---

### Post by speedwayusher on 2008-08-29
Hi guys, i'm new to linux and need some help so please bear with me.

I recently acquired the task of transferring/archiving approx. 200 backup tapes onto a hard drive. These are DDS backup tapes created on various digital UNIX systems. i don't need to read the tapes, i just need to be able to copy them onto a hard drive, and if needed be able to copy back onto tape for machine recovery. there are 2 savesets on each tape (partition a and partition g)

My first attempt was to copy onto a linux machine and FTP to and from WinXP but the files changed somewhere in the transfer. 
Next I tried copy to UNIX ( dd bs=10240 if=/dev/nrmt0h of=test) FTP to/from Linux then create a tape. This was successful, however i am adding approx 60 minutes for FTP time, and have to delete each entry from the UNIX machine afterwards.

I am using UBUNTU 7.04 (Feisty Fawn) and a SCSI external tape drive.
I would like to be able to be able to copy directly to the linux machine, but when i use the exact same command (dd bs=10240 if=/dev/st0 of=test) I get the following error.

root@UNIX-RAID:~# dd bs=10240 if=/dev/nst0 of=test
dd: reading `/dev/st0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0289983 seconds, 0.0 kB/s

someone told me i have to mount the device first which resulted in

root@UNIX-RAID:~# mount st0
mount: can't find /root/st0 in /etc/fstab or /etc/mtab

Here is where I get lost. ..... what does this mean? 

The mt status command gives me the following  

root@UNIX-RAID:~# mt -f /dev/st0 status
drive type = Generic SCSI-2 tape
drive status = 318767616
sense key error = 0
residue count = 0
file number = 0
block number = 0
Tape block size 512 bytes. Density code 0x13 (DDS (61000 bpi)).
Soft error count since last status=0
General status bits on (45010000):
 BOT WR_PROT ONLINE IM_REP_EN

lost again .....](*,)

Any help is greatly appreciated,

---

