---
title: "Does this sound like hard drive death?"
date: 2010-01-14
forum: Hardware
---

### Post by Pikestaff on 2010-01-14
I probably should have noticed the warning signs from the strange clanking noises emanating from my computer box but I ignored it and now both my Kubuntu and Windows XP partitions are quite fubar: taking ten times longer to boot than usual and not really letting me do anything once I'm in (trying to launch an application, for example, either does nothing or causes a random reboot).

A fsck seemed to momentarily fix the problem but things were acting up again within five minutes and now it just seems to be getting worse, with things like "ext3-fs error" getting thrown in my face when I shut down.

Before I squander my emergency funds on a new hard drive is there a possibility this might be another issue? I sort of doubt it :???: but you never know...

---

### Post by cascade9 on 2010-01-14
Running the drive manufacturers diagnostic software is a good idea. 

But that sounds like a drive, heading rapidly toward death to me. 

If you have any data on the drive you want to keep, stop using it until you can get a 2nd drive. Then, unplug the current drive, install your OSes, then plug the drive back in. Mount it and (hopefully) copy your data over.

---

### Post by Grenage on 2010-01-14
I'd backup before running the diagnostic tool, but it sounds toast.

---

### Post by pricetech on 2010-01-14
Most drive diagnostics will let you test the drive without disturbing the data on it, but backing it up is best anyway.

If you can get your hands on any other diagnostic tools, it wouldn't hurt to run them as well.

Boot from a live CD or put the drive in another computer to salvage everything you can before doing anything else with the drive.

---

### Post by Pikestaff on 2010-01-14
I've been backing up with a LiveCD and an external HD, so I've got that covered.

I ran smartmontools and got the following:

```
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       10%     30055         155092173

```

I'm assuming the "read failure" bit is a bad sign...

---

### Post by tgalati4 on 2010-01-14
30,000 hours is a lot for a consumer drive.  Reseat the connectors and cables.  Grab what data you can and get a newer drive.

You can try a low-level reformat using Ultimate Boot CD (using the manufacter's disk utility) and that might revive the drive.  Strange noise is usually a bearing failure or a loose head so don't expect too much.

---

### Post by Pikestaff on 2010-01-14
Hmm.  Well thanks for the tips, all.  I seem to be having luck backing everything up so I'll just pick up a new drive after work tomorrow.  I'll use it as an excuse to upgrade to the latest 'buntu. :)

---

