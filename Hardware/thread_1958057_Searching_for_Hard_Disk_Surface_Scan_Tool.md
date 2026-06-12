---
title: "Searching for Hard Disk Surface Scan Tool"
date: 2012-04-13
forum: Hardware
---

### Post by rickatnight11 on 2012-04-13
I recently inherited 9 x 2TB from a friend's failed array.  As I don't know which disk(s) is/are bad, I'd like to perform a surface scan of the sectors on each disk.

Most of the tools I've found either merely check SMART or perform a block check on an existing filesystem.  I don't need to check a filesystem, since there isn't one, and there's no need to preserve any existing data.  I just want to scan the drives in the most thorough manner possible.

Is there an existing tool to do this, or is creating an ext3/4 partition on each drive and running **badblocks** sufficient?

---

### Post by winh8r on 2012-04-13
try this:

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")


it has a full suite of diagnostic utilities on it. I have used the MHDD utility and found it to be reliable.

Hope this helps.

---

### Post by rickatnight11 on 2012-04-13
> **winh8r said:**
> try this:

I'd like to do this without power-cycling the server (I have hot swap drive bays), ergo I'd prefer a Linux tool.  Thanks, though!

---

### Post by efflandt on 2012-04-14
Some drive manufacturers (like wdc.com for WD and seagate.com for Seagate and Maxtor) have a utility that can run a destructive test on drives by alternately writing all zeros and all 1's to them and then random data to see if they read what they wrote during each test.  Destructive does not mean that it destroys the drive, just data on it.

I imagine you could do something similar with dd in a script (or binary if so inclined), to write and read blocks of data, and compare.  Don't expect that to be quick (long time).  I would write all zeros to it last, so a drive that passes would appear to be a fresh drive for ease of partitioning and formatting.  Once when I accidentally formatted a floppy as a Mac floppy in Linux, I could not format as a DOS floppy (for minix) until I dd'd some zeros to the beginning of the floppy.

Drives normally reserve space to transparently automatically replace bad sectors with good sectors.  So if you actually see bad sectors on a drive, that is a bad sign that all of the error sites are used up, and the drive should not be trusted because it can only get worse.

---

### Post by recluce on 2012-04-14
The following assumes that you have installed smartmontools.

Your first step should be to evaluate the SMART report of each drive using smartctl. "smartctl -a /dev/sdX" assuming a standard SATA controller, with X being the actual drive identifier 

Your second step should be an extended drive self-test, smartctl is the way to go here as well: "smartctl --test=long /dev/sdX" and after the test time has passed (between 60 and 240 minutes for most drives), read the results with the command in step 1.

Your third step should be a drive conveyance test, if supported by your drive. You get an error from the following command if it is not supported: "smartctl --test=conveyance /dev/sdX". Results: see step 1.

Up to this point, simply writing the whole drive would have been a bad idea, since bad sector remappings are done during write operations. In other words, the evidence of the drive failure might have been covered up.

Assuming that all steps above fail to find a problem, you should now use "badblocks" to scan your drives for write errors:

badblocks -nvs /dev/sdX

The above is a nondestructive test, use -wvs is the destructive alternative, may be a bit faster.

---

### Post by rickatnight11 on 2012-04-15
> **efflandt said:**
> Some drive manufacturers..

I imagine you could do something similar with dd in a script...

Drives normally reserve space to...

Good information, thanks!  I'm not sure if I'd trust my scripting skills enough to accurately test the whole disk.  Any recommendations?

> **recluce said:**
> The following assumes that you have installed smartmontools.

Your first step should be to evaluate the SMART report...

Your second step should be an extended drive self-test...

Your third step should be a drive conveyance test...

Up to this point, simply writing the whole drive...

Assuming that all steps above fail to find a problem, you should now use "badblocks" to scan your drives for write errors:

badblocks -nvs /dev/sdX

The above is a nondestructive test, use -wvs is the destructive alternative, may be a bit faster.
This sounds like what I need.  I thought badblocks could only be run on a partition, not the drive itself (as the name contains "block", a filesystem term.)

---

### Post by rickatnight11 on 2012-04-18
Thanks again for the advice.  After mapping the tests to a spreadsheet I've determined that 4 out of 9 disks should probably be RMA'd.  Thankfully Western Digital has a nice RMA process.

---

