---
title: "Gparted - how long to format new 1TB with NTFS"
date: 2009-06-10
forum: Hardware
---

### Post by CapeCodKiter on 2009-06-10
I just got a new 1TB drive and I used gparted to put the partition table on it and format it with NTFS. The whole process took about 5 minutes. I thought (based on my experience formatting drives with windows) that it would take a really long time since its a 1TB drive. I was skeptical that it even worked, but I can read/write files to it and even after rebooting, my files are accessible. 

Why was the process much quicker with gparted/ubuntu then what I remember when I did it with windows?

I'm running a dual core 2.7ghz AMD and the drive is a 3gb/s SATA drive. Is that really the difference?

---

### Post by iponeverything on 2009-06-10
You did a quick format. This does not check for bad sectors or zero out the drive.  If you did the full format on 1 TB drive, you might be waiting for a couple of days.

---

### Post by CapeCodKiter on 2009-06-10
So is a quick format a good or bad thing? Should I have done a full format?

---

### Post by H2SO_four on 2009-06-10
I prefer full format, but I haven't tried it on a drive as large as you have.  It will take a long, long time.  :(

---

### Post by CapeCodKiter on 2009-06-10
1TB is nothing these days! It was only $80 so I couldn't turn that down. You almost cant get any drive cheaper then that :)

---

### Post by iponeverything on 2009-06-10
I don't think that its a bad thing. I would have done a quick format as well.. As I am not that patient a person.

---

### Post by yaroto98 on 2009-06-10
Did you "Apply" the changes after making them?

---

### Post by CapeCodKiter on 2009-06-10
Yes, I believe I did "apply" them. That's the only time I saw anything take any time. If I didnt apply it, then I wouldnt be able to mount the drive and write to it, right?

---

