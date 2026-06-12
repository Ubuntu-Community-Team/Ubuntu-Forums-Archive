---
title: "1215n Ion Solution?"
date: 2010-12-05
forum: Hardware
---

### Post by hudsong on 2010-12-05
Hello,

So, I am aware that there are multiple threads on this laptop, but I can't find the answer that I'm looking for, namely: Has the graphics switching been fixed in 10.10?

I have found these two things:

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

So it looks like it's possible to switch between the two GPUs in those ways. Has anyone tried those methods with a 1215n?

I have seen that some people were complaining about the Ion 2 being "stuck on." In the early days of hacking this, ACPI calls were used to disable the other card completely... but does this mean that the card was actually *working*? Or was it just using battery life? Does this card simply *not work at all*? Or was/is the problem the inability to switch it off?

Thanks for any information!
;)

---

### Post by ch3rryc0ke on 2010-12-13
> **hudsong said:**
> Hello,

So, I am aware that there are multiple threads on this laptop, but I can't find the answer that I'm looking for, namely: Has the graphics switching been fixed in 10.10?

I have found these two things:

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

So it looks like it's possible to switch between the two GPUs in those ways. Has anyone tried those methods with a 1215n?

I have seen that some people were complaining about the Ion 2 being "stuck on." In the early days of hacking this, ACPI calls were used to disable the other card completely... but does this mean that the card was actually *working*? Or was it just using battery life? Does this card simply *not work at all*? Or was/is the problem the inability to switch it off?

Thanks for any information!
;)


I have the 1215N with 10.10 installed and I don't believe the graphics card has been fixed. I previously tried installing the nVidia driver with 10.04 but that hosed the machine, so I have not tried with 10.10.

In regards to the ACPI calls-- I've used the script that people suggest, but I can't get it to work. It seems to shut off the nVidia card (The battery meter immediately shows more available time), but then about 1 minute after I make the ACPI call, the machine hangs-- without fail.

I believe that card stays on unless you use the ACPI calls.

---

### Post by tuahaa on 2010-12-14
I will be getting one of these machines soon so I'll let you know.

---

### Post by ckmccoy on 2011-01-08
same problem. i've had no luck getting it working.  hopefully a fix comes soon

---

