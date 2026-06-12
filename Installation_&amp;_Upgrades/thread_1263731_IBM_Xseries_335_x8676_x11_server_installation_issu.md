---
title: "IBM Xseries 335 x8676 x11 server installation issue"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by Tsu on 2009-09-11
Issue &#8211; 

When trying to install ubuntu 8.04 64-bit server edition. The following error is experienced.

Error message &#8211;
&#8220;This Kernel requires an x86-64 cpu, but only detected an i1586 cpu. Unable to boot &#8211; please use a kernel appropriate for your CPU.

Hardware &#8211;

IBM Xseries 335 x8676 x11 server
Two Xeon processors
2 GB memory
146 GB SCSI hard disks

Resolution &#8211; 

Download and use the 32 bit edition of 8.04 server edition.

Explanation &#8211;

This server only takes P4&#8217;s / xeons. They use two 32 bit processes in conjunction. It is not a 64 bit processor.
[http://en.wikipedia.org/wiki/Xeon](http://en.wikipedia.org/wiki/Xeon)
The majority of Xeon processors that go into this server are dual core 32 bit processors. You can cross reference the edition of the CPU you have with the list provided in the wiki link above.

Why have I created this thread?

To assist idiots like me in the future and to add to the knowledge base when searching for information on IBM servers using ubuntu.

Side note &#8211; Ubuntu Banzia!

---

