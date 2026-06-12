---
title: "DLT Tape Drive not recognized"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by ovig on 2007-05-21
Hi,

I have a Compaq DL380 server on which I've installed Ubuntu 6.06 LTS Server Edition.
The server comes with a SCSI RAID Controller (Compaq Smart Array 5i) on which I've plugged a DLT tape drive after having completed the installation - the problem is that despite the tape drive being seen by the BIOS, Ubuntu does not see it at all.

Below are the details of the tests I've carried out and things I've noticed...

When booting the server, it sees the tape drive at "SCSI port 1 - SCSI id 6" - i.e. target 6 on the external SCSI port which matches how it's connected. If I use the Compaq Diagnostics CD, the tape drive is recognised, and the model number / make / etc are displayed properly - so I am confident that the drive can be "spoken to" over the SCSI bus.

/dev does not show any st/sg device
I have rebooted after adding sg and st to /etc/modules - to no avail
I know that the driver for the SCSI controller has been loaded OK - I can see it in dmesg- and the fact that the server boots is proof enough as the hhard drives are connected to the same controller
all HDD paritions are matches by devices in /dev/cciss/c0d0p* and /dev/cciss/c0d1p* (I have two HDDs) - there is no /dev/cciss/st* or /dev/cciss/c0* that would match the tape drive

I am quite confident that all's working & that the only missing thing is for me to configure the tape drive correctly - but I just cannot figure out how. 

Thanks in advance for any help,

---

### Post by houston.hemi on 2008-03-03
I'm having a very similar problem with my Quantum DLT 8000 series drive.  The SCSI device is listed in the bios, I also see the DLT listed when i use the following command:

#cat /proc/scsi/scsi | less

Still, I can't access the drive.  I get a permissions error:

tar: /dev/st0: Cannot open: Permission denied
tar: Error is not recoverable: exiting now

Can someone please help...

---

### Post by sn00kst3r on 2008-03-26
1.Have you tried SUDO in front of this tar command?

2. If you would like an excellent guide to working this then check out this PDF at the Quantum website. It worked for me with my DLT7000.

[http://downloads.quantum.com/dlt4000/6464215011.pdf](http://downloads.quantum.com/dlt4000/6464215011.pdf)

There are several other excellent articles there as well.

Good Luck

---

### Post by Slim Backwater on 2008-04-05
I know it's an old post, but I just ran into this problem myself and later found a solution:

From: Using a tape drive on a CCISS controller
[http://www.cpqlinux.com/cciss-tape.html](http://www.cpqlinux.com/cciss-tape.html)

for x in /proc/driver/cciss/cciss[0-9]*
        do
                echo "engage scsi" > $x
        done

Should take care of it.  My /proc/scsi/scsi was empty before this, and populated with the tape drive (and library) afterwards.

You could also just do echo "engage scsi" > /proc/driver/cciss/cciss0 if you only had the one controller.

---

