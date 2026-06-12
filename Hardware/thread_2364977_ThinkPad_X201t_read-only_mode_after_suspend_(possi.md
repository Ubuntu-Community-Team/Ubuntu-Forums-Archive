---
title: "ThinkPad X201t read-only mode after suspend (possibly SSD failure?)"
date: 2017-06-30
forum: Hardware
---

### Post by velotux on 2017-06-30
Hello,

I'm having an issue with my ThinkPad. It has a new (purchased less than 6 months ago) SSD, but from a somewhat lower-end brand. Recently my 16.10 install started having problems - following a a backup to an external hard drive (I ran Deja Dup to my automated folder, and then I manually copied the contents of /home/me to another  - I'm paranoid), it began behaving very poorly and multiple applications notified me that the entire filesystem was now read-only.

Reboots didn't help the first few times, but when I wiped the Hard Disk and installed 16.04 the system began behaving better. I restored my files from Deja Dup. I never got the chance to test this before the backup, but after the backup, every time I *suspend *(and only suspend), the system goes back into that read-only mode, and I have to have to shut the whole thing down. Since then I've noted that on boot, my system goes gray for a while, then displays the line: "Error: failure writing sector 0x42402 to 'hd0'".

I've performed several SMART tests, Disks says that "Disk is OK, 152 bad sectors". Total time the disk has been on is less than 11 days. Both the old 16.10 install and the new 16.04.2 have LVM set up automagically - nothing manually configured and no other OSes or partitions.

So, to summarize: My system goes into read-only mode on suspend and has problems with writing to the SSD on boot; even after a clean install to 16.04.2. Disk might be failing, but SMART says it isn't. I have two questions: 
[LIST=1]
[*]Is is possible that some program or configuration carried over from my home partition might be causing this issue? How would I go about finding it?
[*]If not, how will I go about verifying if my SSD is failing, since all the tests so far seem to indicate it isn't?
[/LIST]

---

### Post by Autodave on 2017-07-01
Is this a dual boot setup....are you also running Windows? Did you install in UEFI or legacy mode?

---

### Post by velotux on 2017-07-04
Nope, and I'm not sure - I didn't think the x201 had UEFI.

---

