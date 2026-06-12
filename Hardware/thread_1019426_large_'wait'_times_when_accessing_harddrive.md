---
title: "large 'wait' times when accessing harddrive"
date: 2008-12-23
forum: Hardware
---

### Post by oliverthered on 2008-12-23
Hi,
I get a lot of wait time when accessing the hard drive and things like file copies or starting applications that I haven't run before in the session seem to be a lot slower then I would expect.

This is especially true when I run vmware with a windows xp vm. wait time saturates the processor and it really slows things down.

the strange thing is that hdparm -tT seems to report that the hard drive is performing quite well.

 Timing cached reads:   8312 MB in  2.00 seconds = 4161.26 MB/sec
 Timing buffered disk reads:  204 MB in  3.01 seconds =  67.80 MB/sec

Is this high wait time usual or is it something stange. Is there anything I can do about it, I don't mind hacking the kernel or could it be user space.

Thanks in advance.

---

