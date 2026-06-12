---
title: "Software to overclock CPU in Linux"
date: 2010-03-06
forum: Hardware
---

### Post by sandy8925 on 2010-03-06
Hi, I want to know if there's any software to overclock the CPU in Linux ? 

Yes I know it can be dangerous and blablabla , so on and so forth . I'm well aware of the risks and have done it before. I'm using a laptop(a Fujitsu C1321) and the BIOS doesn't allow me to overclock so please don't tell me that's the recommended way and all that . Just tell me is there any program I can use and where I can get it from.

Thanks in advance.

---

### Post by MelDJ on 2010-03-06
[http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/](http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/)

---

### Post by cascade9 on 2010-03-06
As far as I know there is not software tools for overclocking CPUs in linux...seems that the software devs agree with the general 'if you want to overclcock, do it right, from the BIOS' idea (which is my personal opinion as well)

I wouldnt mind being proved wrong though ;)

---

### Post by SpawnHappyJake on 2012-03-31
I know this thread is a little old, but it's one of the first that come up when one Googles "overclock cpu Linux".

So I feel a little obligated to debunk some very common myths, at least if they show up as the first search result.

Overclocking of modern CPUs is done by writing to a certain spot in the MSR (model/machine specific register).

It is my current understanding that the CPU sends whatever is at that spot in the MSR to a PLL chip. Using a crystal and other PLL systems, the PLL chip that the CPU sent the code to creates the requested frequency. The CPU is connected to this and goes that frequency.

If the BIOS is setting the CPU clock speed, it is writing to the MSR.

If software running under your operating system is setting the CPU clock speed, it is writing to the MSR.

Either way, you're overclocking via writing to the MSR. The two techniques (if you can even call them two _different_ techniques; more like one technique) do the same thing, and thus one's not better than the other, contrary to common belief (myth).


Another fallacy, though usually very subtly implied, is that the BIOS isn't software. The BIOS (or any firmware for that matter) is just as much 1s and 0s scurrying across your processor as FireFox is. There's not even a gray area. It can't be "partially software". It's either hardware or software.


There is an MSR kernel module for Linux that allows you to overclock the CPU from within Linux. And c2ctl and k10ctl use the MSR kernel module for you in your overclocking endeavors (both are Linux-native programs, of course).

See this thread: [http://www.overclock.net/t/1205257/overclock-cpu-in-linux-necessary-program-names-given]("http://www.overclock.net/t/1205257/overclock-cpu-in-linux-necessary-program-names-given")

---

