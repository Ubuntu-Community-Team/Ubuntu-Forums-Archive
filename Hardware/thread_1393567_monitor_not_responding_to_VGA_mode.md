---
title: "monitor not responding to VGA mode"
date: 2010-01-29
forum: Hardware
---

### Post by orientalware on 2010-01-29
Hi,

I use Ubuntu 9.10 in on my desktop computer (graphical mode)
I use CentOS 5.3 on my server computer (text mode)
I use a single mouse, keyboard, and CRT monitor
They are shared with the 2 computers using a KDM switch (Keyboard, Display, Mouse). I can alternate between the computers by hitting the scroll-lock key twice. 
Things were perfect for 6 months. The server and KDM switch were removed and kept away. The desktop computer had direct connections to the CRT monitor, keyboard and mouse.

Last week i reconnected the KDM switch and the server.
The server display in text mode remains blank though the led indicator of the CRT monitor shows yellow indicating signal.
Ubuntu desktop computer continued working perfectly through the bios boot-up (text mode) and the entire boot sequence of Ubuntu.
In 2 days the Ubuntu desktop computer also stopped working in the text mode during the bios boot and then ubuntu boot sequence. It would get back working when the graphical login screen of Ubuntu would reappear. The led indicator of the monitor shows yellow indicating signal.

The text mode display stay blank in both the computers even if I remove the KDM switch and attached the monitor, keyboard and mouse directly for each.
While this does not seem to be a Ubuntu specific issue, i'm unable to find out if problem is in monitor or video cards of both the computers are damaged to not support text mode
Can you provide me pointers to know what has happened or how to resolve it.

Thanks

---

### Post by orientalware on 2010-02-07
> **orientalware said:**
> Hi,

I use Ubuntu 9.10 in on my desktop computer (graphical mode)
I use CentOS 5.3 on my server computer (text mode)
I use a single mouse, keyboard, and CRT monitor
They are shared with the 2 computers using a KDM switch (Keyboard, Display, Mouse). I can alternate between the computers by hitting the scroll-lock key twice. 
Things were perfect for 6 months. The server and KDM switch were removed and kept away. The desktop computer had direct connections to the CRT monitor, keyboard and mouse.

Last week i reconnected the KDM switch and the server.
The server display in text mode remains blank though the led indicator of the CRT monitor shows yellow indicating signal.
Ubuntu desktop computer continued working perfectly through the bios boot-up (text mode) and the entire boot sequence of Ubuntu.
In 2 days the Ubuntu desktop computer also stopped working in the text mode during the bios boot and then ubuntu boot sequence. It would get back working when the graphical login screen of Ubuntu would reappear. The led indicator of the monitor shows yellow indicating signal.

The text mode display stay blank in both the computers even if I remove the KDM switch and attached the monitor, keyboard and mouse directly for each.
While this does not seem to be a Ubuntu specific issue, i'm unable to find out if problem is in monitor or video cards of both the computers are damaged to not support text mode
Can you provide me pointers to know what has happened or how to resolve it.

Thanks
Thanks, Problem identified & solved!. 
CRT Monitor was damaged. Culprit could be KDM switch or wear&tear of monitor

Solution: replaced old monitor with new crt monitor

---

