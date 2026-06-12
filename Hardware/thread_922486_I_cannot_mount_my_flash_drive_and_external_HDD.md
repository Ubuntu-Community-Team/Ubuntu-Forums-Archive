---
title: "I cannot mount my flash drive and external HDD"
date: 2008-09-17
forum: Hardware
---

### Post by jlvandal on 2008-09-17
I don´t understand, but, I cannot mount my external HDD and my flashdrive. What can be done to correct that? I tried to format them but I can´t find the format command. Then, I can´t see the microsoft office suite in the wine menu. How can I do that? Thank you.:(

---

### Post by vanadium on 2008-09-17
An external HD and USB mount automatically when you plug them in. A frequent instance where that does not happen is when the drive is ntfs formatted, and the ntfs volume is not "clean", i.e. it has not been properly disconnected from Windows. In the latter case connecting the drive to windows and safely disconnecting it there usually does the job. In a worse case, you might need to check and repair the ntfs volume using the Windows tools.

However, I do know nothing about your particular devices, and thus the above might not apply for you.

---

### Post by Missdevilla on 2008-09-17
I have the same problem. Oddly, although it WAS once connected to Windows, the last OS it was connected to was Mandriva! Mandriva had no problem seeing it. I just plugged it in and there it was. I'm confused. :confused:

I prefer Ubuntu, but what does Mandriva have that Ubuntu doesn't that makes this particular plug and play issue so simple?

---

