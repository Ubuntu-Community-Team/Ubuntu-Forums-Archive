---
title: "Removed external HDD from case. Now it doesn't work."
date: 2008-09-19
forum: Hardware
---

### Post by oxboood on 2008-09-19
Alright I didn't know where to look online for this answer, but I have been searching. I have Maxtor 200gb external HDD. I took it out of the case to use in my modded xbox, and formatted it(I knew this might have repercussions later).

 Now I need it back as an external drive, I tried plugging it in to my desktop and formatting it to FAT32, in hopes that the external HDD controller would recognize it... to no avail. Do you think I need to re image it somehow with some proprietary Maxtor utility?

Anything will help, Thanks.

-Max

---

### Post by cariboo on 2008-09-19
You could try writing zeros to the disk using dd. to do this open up a terminal and type:

```
dd if=/dev/zero of=/dev/sdx
``` 

where /dev/sdx is your hard drive. This command will overwrite all the information on your hard drive. It will take several hours so you might as well go out and see a movie or something while you are waiting.

Jim

---

