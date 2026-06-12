---
title: "Linux Ubuntu 13.04 freezes while booting, hard drive hard resets"
date: 2013-06-02
forum: Hardware
---

### Post by user_of_gnomes on 2013-06-02
From time to time, Linux Ubuntu freezes for well over 5 minutes before it'll let me log in. Nothing responds during that time.

It seems the below log entry indicates the problem:

```
[  651.996722] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  651.996728] ata1.00: failed command: IDENTIFY PACKET DEVICE
[  651.996733] ata1.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[  651.996733]          res 50/00:03:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  651.996735] ata1.00: status: { DRDY }
[  651.996739] ata1: hard resetting link
[  652.488662] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  653.290989] ata1.00: configured for UDMA/100
[  654.104194] ata1: EH complete

```

The [Hard Drive S.M.A.R.T read-out tells me ]("http://paste.ubuntu.com/5726818/")that the drive is healthy. 
This did not happen under Windows 7.

It's a WDC WD1002FAEX-00Z3A0 (05.01D50)

Any ideas?

---

### Post by gordintoronto on 2013-06-02
According to this: [http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device](http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device)

it's actually the optical drive, and two solutions are offered.

---

### Post by user_of_gnomes on 2013-06-03
> **gordintoronto said:**
> According to this: [http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device](http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device)

it's actually the optical drive, and two solutions are offered.

Invoking the command ```
/lib/udev/ata_id --export /dev/sr0
``` doesn't seem to make the system freeze. 
However, I have seen something along the lines of dev/sr0 freezing just before the system does finally start. 

I suppose I could try solution number one regardless. Are there any downsides to doing so?

---

### Post by gordintoronto on 2013-06-03
I don't see any downside. Then again, I'm not always right.

---

### Post by user_of_gnomes on 2013-06-14
> **gordintoronto said:**
> I don't see any downside. Then again, I'm not always right.

It seems that commenting out the line as described earlier on does make the problem less frequent but it still returns from time to time. 

The bootlog no longer indicates a hard reset from what I can tell.

Any idea what to do next?

---

### Post by gordintoronto on 2013-06-14
Switching to a different optical drive? I've got a couple lying around, salvaged out of computers which have gone to the big network in the sky.

---

### Post by user_of_gnomes on 2013-06-16
> **gordintoronto said:**
> Switching to a different optical drive? I've got a couple lying around, salvaged out of computers which have gone to the big network in the sky.

It used to work fine under Windows and it works under Ubuntu. Evoking the command that should have frozen the system did not yield any such result.
What makes you think it is the optical drive?

I'll have to do some more research, I do not know how to interpret these boot logs ..

---

### Post by gordintoronto on 2013-06-16
The link I provided to Askubuntu seemed to be a similar problem, and it was the optical drive in that case.

Your hard drive is well-reviewed on Newegg, except for the small number of DOA drives. There was one review which indicated a drive freezing -- out of 2647 reviews. Perhaps you have the same problem.

---

### Post by user_of_gnomes on 2013-06-17
> **gordintoronto said:**
> The link I provided to Askubuntu seemed to be a similar problem, and it was the optical drive in that case.

Your hard drive is well-reviewed on Newegg, except for the small number of DOA drives. There was one review which indicated a drive freezing -- out of 2647 reviews. Perhaps you have the same problem.

Yes, I picked this one with care. It comes with a 5-year-warranty.

What if I tried to invoke the /lib/udev/ata_id --export /dev/sr0 command on the hard drive to see if that causes the problem somehow?
How would I go about doing that and could it be considered harmful?

---

### Post by gordintoronto on 2013-06-17
Sorry, that's way above my pay grade.

---

