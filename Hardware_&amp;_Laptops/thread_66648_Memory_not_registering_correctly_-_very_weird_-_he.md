---
title: "Memory not registering correctly - very weird - help!"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by AgenT on 2005-09-17
Laptop: X31 
OS: Ubuntu (Hoary) 
Bought a 1GB memory stick, had 2 256 sticks installed. Here is the problem: 
 
When adding a 1GB stick, whether with another stick or by itself (socket placement does not matter), the memory is always 906656 kB. Now here is the strange part: the memory registers correctly in the BIOS, and memtest86 gives no errors. Also, different Linux distributions give different results. Some give the correct size (like an old kernel 2.4 Gentoo), while others (like Ubuntu Hoary, Knoppix and Mandrake) give the same wrong amount mentioned above. Also, Windows 2000 seems to be registering the memory correctly. At least the IBM Rescue & Recovery program that is based on Windows 2000 does. Can anyone help? What can be wrong? 
 
My guess would be that it's either a strange memory module, a kernel problem or something strange with the BIOS. Looking at the BIOS changelog for the X31, nothing has been fixed in terms of memory issues so updating the BIOS seems pointless and not worth the risk. 
 
I still have a few days to return the memory just in case. Help me, fellow Ubuntu users! ](*,)

---

### Post by doclivingston on 2005-09-18
The 386 kernel (which is installed by default) can access more memory than that. To fix the problem, install either the 686 (intel) or k7 (amd) kernel - the package names are linux-686 and linux-k7.

---

### Post by AgenT on 2005-09-18
You mean that "it **cannot** access more memory than that", correct? What is the reason for this? And just so you know, your tip worked. The memory is now registered correctly with the system. Thank you! \\:D/

---

### Post by doclivingston on 2005-09-19
Yeah, I meant "... cannot access memory memory than that".

The reason is that the 386 kernel can't access more memory is that it isn't compiled with "large memory" support. The 686 and k7 kernels are, but they aren't included on the cd because they would take up too much space.

---

