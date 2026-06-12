---
title: "Root Partition Full"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by jonathonblake on 2007-08-30
All:

The root partition on my hard drive is full.
This is a 7 GB partition.   Way larger than the 250 MB that was suggested elsewhere.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920) would be useful, **if** I could start the programs that do the clean up described in it.   

I have to do the <CTRL><ALT<f1> thing, then  "sudo apt-get clean" to log in.

Thunderbird will retrieve email.  Sending email results in an error message of "error writing temporary files".
Firefox loads, and behaves normally.

I can't launch "System Monitor";
I can't launch Synaptic Package Manager;
I can't launch a terminal for the command line;
I can launch and navigate ">Start >Places >Computer";

I did find a couple of files that were 1GB in size, with a file name suffix of ".crash", and ".tmp", and other things that imply that they can be deleted without harming the system.  However, they all appear to require root access to delete.   
When I went to the command line using <alt><ctrl><F1> at startup, cd couldn't access those directories due to a permissions issue.   "sudo cd" doesn't work, because there it can't find the "cd" command!

I've got about 10 GB of data on this drive that I need to archive.   
Any suggestions on how to:
a) Delete those ".crash" files?
b) Delete some of the files on my root partition. I would have thought that 7 GB would be enough, but that doesn't appear to be the case.  :(
c) Archive that data to DVD.  I do have a free partition ( 9 GB) that was created for tossing files into,prior to burning to DVD.   DVD burner claims to have burned that material, but there is nothing on the DVD.  (Checked by examining the DVD on a Windows system.)

Ubuntu Christian Edition 2.2
1 GB RAM
80 GB hard drive.

Not sure what other data you want/need/would like to have.

Once that data has been archived, this drive will be reformatted, and Ubuntu 7.10 installed.

xan

jonathon

---

### Post by jackocleebrown on 2007-08-30
If you boot to a liveCD you should be able to mount the drive and archive things to DVD.

Do you have a seperate partition for /home? if not or you don't know what this means one option is to keep your install on the current partition and to move you /home to the new partition - you can do this while you are booted to the liveCD - ask for help if you need to know how.


hope this helps,
Jack

---

### Post by jonathonblake on 2007-08-30
[QUOTE=jackocleebrown]If you boot to a liveCD you should be able to mount the drive and archive things to DVD.[/quote]

I'll try that. 

Mount hard drive, and DVD burner.  

> 
Do you have a seperate partition for /home? 

Yes.  Roughly 20 G.  IIRC, it was 90% full. 

xan

jonathon

---

### Post by jackocleebrown on 2007-08-30
Ouch! that is full. so much for my /home suggestion.

My Feisty install uses 4gig (not including home) so it is not impossible to use 7 I guess.

You mention problems with accessing the directories.... use you need to use chmod to change the permissions of the directories so that you can cd to them: somthing like this "chmod a+rX <dirpath>".

Jack

---

