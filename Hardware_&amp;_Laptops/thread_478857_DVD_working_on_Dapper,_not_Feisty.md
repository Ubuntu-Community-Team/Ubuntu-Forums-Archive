---
title: "DVD working on Dapper, not Feisty"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by Lary Grant on 2007-06-19
I have a Sony DVD RW on a multi-boot system. It is working for both playback and burning in Dapper, but not when I boot from my fresh Feisty partition. I forget what all I had done in Dapper to get it working.

The symptoms in Feisty are:

K3B displays the spash screen then freezes the whole machine. I have to do a hard reboot.

A DVD that I have previously burned in Dapper shows up in Feisty but it looks like all the files are empty and does not play back.

In Feisty, the automatic DVD burning thang that comes up when I insert a blank DVD (I have no idea what DVD burning software it is running automatically... it is not K3B) seems to work, but the DVD ends up being blank at the end of the process.

I tried accessing the DVD through the shell. I tried doing an "ls" on one of the directories on the DVD and got:

    ls: video_ts: Input/output error

I'm seeing these errors in "dmesg":

    [ 625.671092] sr 1:0:1:0: SCSI error: return code = 0x08000002
    [ 625.671100] sr1: Current: sense key: Hardware Error
    [ 625.671103] Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
    [ 625.671112] end_request: I/O error, dev sr1, sector 1108

---

### Post by chele on 2007-06-28
Can you see the files on the DVD using "sudo ls"? If so, it may be related to this issue:  [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550)

---

### Post by Lary Grant on 2007-07-30
It seems like the root cause of this is a kernel issue.  Is there any plan to update the kernel in Feisty to address this?

---

### Post by Lary Grant on 2007-08-07
I am really bummed about this... I'm glad I kept my old Dapper partition while I tried out Feisty, because I am forced to go back to Dapper now due to this issue.   I read somewhere that upgrading Feisty to the latest Gutsy hurd may fix it, because that way I'd get the latest kernel, but that did not work.  Unfortunately not only did that fix my DVD issue, it made some other things break, and I can't go back to Feisty (which was running fine except for the DVD issue).

Are there any other options for me to get Feisty running with my DVD?

---

### Post by rykel on 2007-08-07
Hi,

Just offhand... could it be that your DVD RW has reached its End Of Life (EOL)?

---

### Post by Lary Grant on 2007-08-07
You mean, no longer supported?  Is there a list of those?

---

