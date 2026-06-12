---
title: "Laptop has 64-bit, what do I do?"
date: 2011-06-29
forum: Hardware
---

### Post by MG&amp;TL on 2011-06-29
A question-did try googling it but it was like wallowing through mud, people debating the pros and cons of 64bit.:confused:

Currently I'm running something that most people would call a junkheap of a desktop, it's seven years old. However, a generous family member has said that they'll buy me a laptop, however, said laptop is scarily marked "64bit". I'm not asking about performance pros and cons, I don't care, it'll be faster regardless, but a) does ubuntu run reliably, and b) do most programs run on 64bit, I'm into programming, so it'll be things like Code::Blocks, graphics libraries, Wine and that sort of thing.

Hope you generous people can either point me to a thread, or provide an answer.

---

### Post by Yellow Pasque on 2011-06-29
I don't think there's any right answer, just more opinions. Here's mine: if you're worried about compatibility, just use 32-bit. The important components (kernel, libc6) are i686-optimized (take advantage of SSE2 and such). Some of the tasks that still see significant performance gains from 64-bit are virtualization, video encoding, and using programs that take up enormous amounts of RAM (GIMP).

---

### Post by haqking on 2011-06-29
> **MG&TL said:**
> A question-did try googling it but it was like wallowing through mud, people debating the pros and cons of 64bit.:confused:

Currently I'm running something that most people would call a junkheap of a desktop, it's seven years old. However, a generous family member has said that they'll buy me a laptop, however, said laptop is scarily marked "64bit". I'm not asking about performance pros and cons, I don't care, it'll be faster regardless, but a) does ubuntu run reliably, and b) do most programs run on 64bit, I'm into programming, so it'll be things like Code::Blocks, graphics libraries, Wine and that sort of thing.

Hope you generous people can either point me to a thread, or provide an answer.


Just cause it says 64 bit does not mean it will be faster it just infers that ;-)

what is the spec of the hardware ? and only things that can take advantage of 64 bit will perform better and some wont.

Also if you plan to use 64 bit there is somewhat less support from a development perspective in so much as working product, i still think 32 bit development is superceding 64 bit currently so it really depends on your goals.

I personally run 64 bit but not for any particular app, more a case of cause i can type thing ;-)

---

### Post by MG&amp;TL on 2011-06-29
> **haqking said:**
> Just cause it says 64 bit does not mean it will be faster it just infers that ;-)



I know that, it's just that the thing WILL be faster than the thing I'm running currently. It still prefers to use floppy disks.:D

I don't know what the spec is exactly, said kindly relative just quoted some stuff over the phone, "4gb RAM, i3 processor, 2.something Ghz, 64bit. I guess she just quoted the techie-sounding bits...**I mean honestly, some people just don't think about linux compatibility, do they? It's atrocious;)**

As long as I can just download the 32bit iso, put it on with a partition, run programs, I don't really care, I was just thinking, hmmm...now does 'buntu support 64bit, whatever that strange and mystical architecture is?

---

