---
title: "The best file type to format pen drives?"
date: 2009-05-31
forum: Hardware
---

### Post by Rytron on 2009-05-31
Hi.
What file system types does Windows read?
I have two pen drives. They are 2gb & 256mb in size. They are both currently formatted as fat16. Ubuntu reads it perfectly. What is the best file type to formate pen drives of these sizes that both Windows and Ubuntu will both read? Is fat16 the best option?

---

### Post by squaregoldfish on 2009-05-31
For USB pen access where universal access is required, I tend to leave them as they are. They tend to be formatted with the lowest common denominator file system that everything will understand. You may be able to reformat them with FAT32 and keep the same level of compatibility, but if a pen's working as required, why mess with it?

I forget the exact differences between FAT32 and FAT16 - mainly to allow file systems of >4Gb and to reduce the minimum block size, I think, but I'm not sure it's important enough to worry about.

Steve.

---

### Post by Rytron on 2009-05-31
I was just checking whether formating them to another filesystem would make the pen drives more efficient. Perhaps leaving them as fat16 is best.

---

### Post by Rytron on 2009-05-31
More info [here]("http://en.wikipedia.org/wiki/Comparison_of_file_systems"). Under the heading 'OS support' it shows what file systems each OS can handle.

---

### Post by squaregoldfish on 2009-05-31
> **Rytron said:**
> I was just checking whether formating them to another filesystem would make the pen drives more efficient. Perhaps leaving them as fat16 is best.

I'd be surprised if you saw any efficiency gains. The limiting factor will be the hardware rather than the partition type.

Steve.

---

