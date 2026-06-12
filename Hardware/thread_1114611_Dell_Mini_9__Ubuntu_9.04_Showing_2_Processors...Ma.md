---
title: "Dell Mini 9 / Ubuntu 9.04 Showing 2 Processors...Maybe due to hyper-threading?"
date: 2009-04-02
forum: Hardware
---

### Post by damage84 on 2009-04-02
Okay so I've searched all over the net and all over the Ubuntu forums however I am not able to figure out what is going on with my Dell Mini 9.

I installed Ubuntu 9.04 Beta on my Mini and when I check the system monitor it shows my Mini as having two processors when I am pretty sure the N270 for laptops only has a single core and not dual cores. A friend of mine said it was showing two due to hyper-threading, but I did not think hyper-threading was even enabled by default.

So does anyone have any experience with the Mini 9 + Ubuntu 9.04 and if so do you have any idea what is going on? Is this hyper-threading? Do I actually have a dual core atom processor? Any help would be greatly appreciated. Thanks.

---

### Post by devnull73 on 2009-04-03
Yup, you're 100% right.

From memory the Dell has a hyperthreading atom? My Aspire One runs an Atom too, and the two processors that appear in /proc/cpuinfo are due to the hyperthreading.

---

### Post by Barry Carroll on 2009-04-03
Yes, that's correct.  I'm almost certain that all Atoms have hyper-threading so you'll see 2 processors for your one physical atom cpu.

---

### Post by weaver4 on 2009-04-10
I have a dual core 330 and it shows up as 4 processors.  

So let me add a question...If processor one is 40% busy, processor two is 20%, processor three is 10% busy and four is 10% busy then how busy are my processors?  Is core one 60% busy or 30% busy?  Is core two 20% busy or 10% busy?

---

