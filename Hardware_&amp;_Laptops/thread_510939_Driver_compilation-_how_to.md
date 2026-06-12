---
title: "Driver compilation- how to?"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by hissingshark on 2007-07-27
Hey,

I've been trying to get my hardware fully up and running under Feisty.
My SATA and Audio are all on the nForce2 motherboard.
I've gone direct to the manufacturers and found they provide Linux drivers and install guides.
Great to see.

[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)

Unfortunately these are pre-compiled for various distributions other than Ubuntu (see link above).
However,
The individual folders in the download package contain the C source (see directory tree below)

[IMG]http://hissingshark.com/forum/1.png[/IMG]

[IMG]http://hissingshark.com/forum/2.png[/IMG]

[IMG]http://hissingshark.com/forum/3.png[/IMG]

So is it possible to compile these for use in Ubuntu?
And if so, can anyone point me in the right direction?
I'm quite a Linux newbie, but a quick learner!
(I mean hey, I just managed to find the commandline FTP client via the package manager and upload the above .png's to my site via the terminal whilst writing this thread... well I'm pleased anyway!)

Thank folks,

---

### Post by hissingshark on 2007-07-29
Still got nothing more concrete on this subject.

I'm all for reading up on it but everything has been so specific to one driver etc.  
There don't seem to be any books out there in the real world that help either.
The "guru's" must learn this somewhere.
But where?

I wanted to learn CGI, Perl, XHTML, CSS- I bought books, followed online tutorials and I was sorted.

All I've found so far is a guide for kernel compilation that said I don't actually need to do that and to stop reading...  

Apparently a custom driver just needs custom header compilation.
But again, how does one go about this, and do I have the required source code to begin with?

---

### Post by zabien1970 on 2007-07-29
You should copy this over to the 'Programming Talk' forum, alot of members there are familiar with C which is what I think drivers are written in.

---

### Post by bogolisk on 2007-07-29
I think all those drivers are already part of Ubuntu. No need to DIY. Unless you want to learn, of course.

---

