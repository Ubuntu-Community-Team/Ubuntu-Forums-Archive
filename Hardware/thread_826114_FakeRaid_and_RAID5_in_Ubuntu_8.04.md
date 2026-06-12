---
title: "FakeRaid and RAID5 in Ubuntu 8.04"
date: 2008-06-11
forum: Hardware
---

### Post by mattwynne on 2008-06-11
Hi,

I have a file server at home which has been running Windows, and I'm trying to move over to ubuntu.

The machine boots from an IDE hard-drive, but the data (photos, music etc) is stored on a SATA RAID5 array, which I built and used from Windows, unaware that it wasn't actually full on hardware RAID.

I'd like to keep the option to move back to Windows open for the time being.

The RAID array is the largest 'drive' I have, so I can't back it up right now, unless I spend on an external drive or wait three weeks while it uploads to S3.

I understand from the FakeRaidHowto article[1] on the wiki that dmraid and ubuntu don't support RAID5 out of the box.

I understand that there are some kernel patches[2] which should help this to work.

So I'm now trying to work out what to do.

As I see it, my options are (in no particular order):

1. give up, go back to Windows and wait for this to be built into a future version of ubuntu
2. buy a proper hardware RAID controller
3. buy an external drive, backup the data, wipe the array and build a linux-only software array
4. try to patch the kernel

So I guess my question for you guys is about option #4:

Is anyone willing to support me through this, or point me to a guide that does?

And how risky is it likely to be? I know there's a chance, but is there a significant chance I could lose my data?

And are there any other options I haven't considered?

Thanks in advance,
Matt

[1]https://help.ubuntu.com/community/FakeRaidHowto
[2]http://people.redhat.com/heinzm/sw/dm/dm-raid45/

---

### Post by mattwynne on 2008-06-12
Okay folks it looks like there is a fix coming up for this. There is more help here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220493](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220493)

---

### Post by Grafik on 2008-06-25
Oh, great, thanks. I'm in the same boat as you. I have a RAID 5 set up and I tried installing Ubuntu 8.04, but it won't recognize that I have a RAID. It sees each (4x300GB) drive individually, and if I try installing it on one, it will wipe my drives, therefore disabling my RAID. 

I'm currently dual-booting with XP and Vista, and wanted to add Ubuntu to my collection, but it seems that I'll have to wait a little while. And, I have an nVidia 8800 GTS to boot, so my problems have just multiplied. Hope to figure this out soon.

---

