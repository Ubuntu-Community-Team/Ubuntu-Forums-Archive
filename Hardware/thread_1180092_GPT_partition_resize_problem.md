---
title: "GPT partition resize problem"
date: 2009-06-06
forum: Hardware
---

### Post by ripken204 on 2009-06-06
I have a 3ware 9650SE-8LPML.
I just expanded my 7x1.5TB raid6 array to a 8x1.5TB raid6 array.
I am using the GUID partition table. 
The entire disk I want as one partition, currently it's 6.82TB and I want it to be 1.36TB.
So I used gparted to resize my partition..

When I resize it I get this error:
"Not all of the space available to /dev/sdb appears to be used, you can fix the GPT to use all of the space (an extra 2929666048 blocks) or continue with the current setting? "

When I try to make the unallocated space its own partition I get this:
"unable to satisfy all constraints on the partition gpt"

---

