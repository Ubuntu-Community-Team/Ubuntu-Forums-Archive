---
title: "USB stopped working after a BSOD in a dual-boot Windows. (It still works in Windows)"
date: 2016-12-28
forum: Hardware
---

### Post by lvrma on 2016-12-28
Hey guys!

So, this a bizarre one, I honestly have no idea what's going on, LOL.

My laptop (an Alienware 17) has 3 USB ports, 2 on the left side and 1 on the right. When I installed Ubuntu on it, all 3 ports worked perfectly.

Now, originally the Windows that came with the computer was slightly bugged, it would freeze over out of nowhere and the CPU/GPU fans would go crazy. The more demanding was usage (as in for example, gaming), the more it would freeze. I thought maybe it was some programs doing first time setups or something weird like that, and that it would go away after I used Windows for a while. It didn't though, and during a Starcraft 2 game (in which I was using all 3 USB ports for peripheral devices), the computer froze, fans went crazy, and I got a BSOD.

After the BSOD, I booted on Ubuntu and realized one of the ports on the left side wasn't working (to be fair, it does work, but at veeeery low power, as in, anything more than a USB printer cable won't work, and even this one is unstable. Something like a headset won't work *at all*). 

I then did a bit of research and found that it was some Dell adware that was interfering with the Alienware software in Windows, causing this freezing behavior. I deleted it and Windows stopped freezing, it worked perfectly from then on!!

The bizarre part is, when I booted on Windows to delete the adware, all USB ports were working perfectly, and still are. So something that caused the fans to go crazy and give me a BSOD, also caused Ubuntu to stop recognizing one of the ports properly, although I can't even fathom how.
Any ideas?

Thanks in advance!
Lucas.

---

### Post by ajgreeny on 2016-12-29
Is that USB port also dead using a live Ubuntu OS?

---

### Post by lvrma on 2016-12-29
> **ajgreeny said:**
> Is that USB port also dead using a live Ubuntu OS? 

Actually yes, it's also dead in the live Ubuntu, just tried it. What could that mean?

I'd also like to add that **lsusb** doesn't recognize the stuff connected to the port in question, and yet, just for emphasis, it works perfectly on Windows 10, so it's not a dead port.

---

