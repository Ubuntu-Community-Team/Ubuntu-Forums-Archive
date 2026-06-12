---
title: "Failed HDD"
date: 2012-06-13
forum: Hardware
---

### Post by Jonny87 on 2012-06-13
I have a Hard Drive that appears to have failed that I'm trying to sort out for a friend. I'm looking to see if it's recoverable. I've tried placing it in two different Hard Drive enclosures and the result is slightly different each time. In one enclosure it comes up in Disk Utility as a something rather brand with no capacity what so ever. It won't mount and doesn't seem to show up elsewhere (i.e. sudo fdisk -l). In the other enclosure it appares to have a different brand and shows up as 4 GB. And still no mount etc.
With the second enclosure that is currently mounted, I get this under lsusb;
```
Bus 002 Device 018: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
```

I was going to try rebuild the partition table and format the drive etc in case it's that simple (I've been able to get drives going in the past by doing something similar to this), but I'm concerned that what I'm seeing is in fact somehow the enclosure and not the Hard Drive. And I don't want to damage the enclosure.

Any ideas or insight anyone?

---

### Post by roelforg on 2012-06-13
If you have a working hdd that is larger then the one you're repairing, you could make some free room on that one and make a raw hdd image.
An example of how i did that once with a 40GB drive. (/dev/sdb and used my external hdd (1tb, 900gb free, /dev/sdc).
```

sudo mkdir /media/external
sudo mount /dev/sdc1 /media/external
sudo dd if=/dev/sdb of=/media/external/image.img

```
dd then went on to crunch on the drive for a few houres.
 
I then used fdisk to check the partition offsets on the image and used those to link the partitions to a /dev/loop[0,1,2,3,4,5,etc] device. Fsck didn't mind running on the loop devices. Worked pretty darn good.
You could launch gparted like this:
```

sudo gparted /media/external/image.img

```
 
Good luck!

---

### Post by Jonny87 on 2012-06-13
I'll give it ago, I'm not sure on that second part though, could you please re-clarify that and possibly give me some example commands? in the mean time I'll start on the dd imaging.

[I]*SIDE NOTE*
Also how can I report spam? I noticed some sort of nonses spam on another post but when I clicked Report it came up saying that I was allowed to perform this action.[/I]

---

### Post by Jonny87 on 2012-06-13
OK... the dd command took not even one second and made the image file that was 0 bytes in size. Command output also said that it 0 bytes were copied.

Your thoughts?

---

### Post by roelforg on 2012-06-13
Check if the paths were ok (the /dev/sdX i gave were examples)
Does the drive make any sound or signs of life?
Did dd output anything, anything at all?
Make sure that the if= param is the whole drive (partition: /dev/sdXN drive: /dev/sdX).

---

### Post by Jonny87 on 2012-06-13
Yep the paths were fine, the Drive made no sign of being active, and yes a file was created as specified in the path, but it was 0 bytes in size.

Here is the commands and the output;

```
jonny@jonny-laptop:~$ sudo dd if=/dev/sdb of=/media/WD\ External\ Hard\ Drive/image.img
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0771885 s, 0.0 kB/s
jonny@jonny-laptop:~$ ls -l /media/WD\ External\ Hard\ Drive/
total 0
-rw------- 1 jonny jonny 0 Jun 13 21:11 image.img
```

As I said earlier though, I'm worried that what I'm seeing for the supposed /dev/sdb (the drive in question) isn't actually the drive but the Hard Drive enclosure. Is this possible? 

Unfortunately I only have a laptop to work off, I don't have a Desktop that I can plug it into directly as I'd prefer. The Hard Drive enclosures are all I have.

---

### Post by trundlenut on 2012-06-13
Try physically moving the drive around and see if it works better in any particular orientation.

I had a laptop in which the hard drive died but it worked with the laptop stood up on end rather than sitting flat.  The drive lasted long enough like this to let me image it.

Does the drive make any noise when it is in the enclosure and connected?

---

### Post by ahallubuntu on 2012-06-13
Check the drive's S.M.A.R.T. status first before doing anything else.  Use SmartMonTools - just install that in Ubuntu.

Then in a terminal type

sudo smartctl -a /dev/sdb

Replace "/dev/sdb" with your drive's device path.

Look for Attributes that have non-zero RAW values like Pending Sector Count.

Sometimes SmartMonTools can't access data from a drive attached via an enclosure without giving it a hint about the enclosure controller's chipset.  Here's a list of controller options:

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices)

So for your JMicron chipset enclosure, try

smartctl -a -d usbjmicron /dev/sdb

Note that it may be easier to view S.M.A.R.T. results in a GUI instead of a terminal.  So you can try GSmartControl for that (it calls smartctl and highlights Attributes in Red if the are obviously failing).  There's an option to set -d usbjmicron there  too.

---

### Post by Jonny87 on 2012-06-14
> **trundlenut said:**
> Try physically moving the drive around and see if it works better in any particular orientation.

I had a laptop in which the hard drive died but it worked with the laptop stood up on end rather than sitting flat.  The drive lasted long enough like this to let me image it.

Does the drive make any noise when it is in the enclosure and connected?

OK just tried lying it on its side, still no better. There is only very slight noise coming from it when I try to do something with it, though it beeps when I turn it on which I know can't be good.

---

### Post by Jonny87 on 2012-06-14
> **ahallubuntu said:**
> Check the drive's S.M.A.R.T. status first before doing anything else.  Use SmartMonTools - just install that in Ubuntu.

Then in a terminal type

sudo smartctl -a /dev/sdb

Replace "/dev/sdb" with your drive's device path.

Look for Attributes that have non-zero RAW values like Pending Sector Count.

Sometimes SmartMonTools can't access data from a drive attached via an enclosure without giving it a hint about the enclosure controller's chipset.  Here's a list of controller options:

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices)

So for your JMicron chipset enclosure, try

smartctl -a -d usbjmicron /dev/sdb

Note that it may be easier to view S.M.A.R.T. results in a GUI instead of a terminal.  So you can try GSmartControl for that (it calls smartctl and highlights Attributes in Red if the are obviously failing).  There's an option to set -d usbjmicron there  too.

Working on this at the moment and will get back to you with what I come up with.

---

### Post by roelforg on 2012-06-14
> **Jonny87 said:**
> OK just tried lying it on its side, still no better. There is only very slight noise coming from it when I try to do something with it, though it beeps when I turn it on which I know can't be good.
 
Wait, you never mentioned the beeps...
Take note of the pattern and look it up, i bet they're POST-error codes.
Power On Self Test (POST) is a test that the motherboard firmware does to check for broken components, the beeping means something (there should be a list for your system to help id the beeps)
 
Slight noise is normal (the disk is spinning and the R/W-heads are moving).

---

### Post by Jonny87 on 2012-06-14
> **roelforg said:**
> Wait, you never mentioned the beeps...
Take note of the pattern and look it up, i bet they're POST-error codes.
Power On Self Test (POST) is a test that the motherboard firmware does to check for broken components, the beeping means something (there should be a list for your system to help id the beeps)
 
Slight noise is normal (the disk is spinning and the R/W-heads are moving).

Yea I'd consider it being POST if it was happening during the early stages of boot up when the computer performs the POST. But the my laptop is already running and the beep is coming from the hard drive in the external enclosure, when the enclosure is turned on. I've tried the HDD in two different external enclosure and it beeps in both which suggests that its coming from the actual HDD and that it's seriously stuffed. I already thought that it was, but I like a challenge and I know that sometimes a failed HDD can be recovered, if only long enough to backup data. I'm hoping I can at least do that for my friend if its possible.

Any more ideas?

---

### Post by pooper on 2012-07-16
it would seem ubuntu doesn't like hd enclosures?

I have just got hold of one and on first go it worked fine I could see everything on hd and since then its basically got worse each time I connect the drive!? To the point where no files or folders are visible, just incorrect partition sizes, for example reporting 12.5gb when really there is 60gb?

Also another drive just fails to boot at all.

and since reformatting the drive that did work it does all sorts of weird things, such as continuous rebooting as in physically i can hear the drive powering up and down...

any ideas?

---

