---
title: "Testing Hardware : CPU &amp; Motherboard"
date: 2014-09-14
forum: Hardware
---

### Post by Fabzil on 2014-09-14
Hello people!

I bought a **HP Elitebook 2540p** that was 3 years old and I use it for travelling around the world for a year.
It's now **4 years old**. The internal hard-drive died so my system is a Lubuntu flashdrive.

Three or four months before the end of my trip, I add to reinstall Lubuntu clean every 3 or 4 weeks because the system would become so **slow **it would be not usable anymore. At the very end of my trip, even a clean re-install of Lubuntu on a different formatted USB key would not solve the problem, and the system would be so freaking slow, especially firefox, at the very first boot.

Yet, very, very few crashes due to this slowness, and the system would always eventually catch up. So I think the RAM is fine. And it also can't be the USB drives because when I change them, I got the same problem.

I think my **CPU **or my **motherboard **is injured and now painfully limping, instead of running as a young stallion like in the old days.

_

In the Live CD of Ubuntu and Lubuntu, there is a tool for testing the RAM of a computer. **Is there something similar for a CPU and / or a motherboard?**


Thx you for your time and have a nice day!

---

### Post by varunendra on 2014-09-14
There is a tool called 'cpuburn' that tries to overload the cpu, and test its limit that way. I haven't tested it myself and so don't know if it stops at errors or even reports them or not. There is also a warning attached with its description -
> Description-en: Collection of programs to put heavy load on CPU
 CPUburn is a collection of programs to put heavy stress on CPU.
 These programs are designed to load CPUs as heavily as possible
 for the purposes of system testing.
 .
 Warning: The goal has been to maximize heat production from the CPU,
 putting stress on the CPU itself, cooling system, motherboard. This
 may cause data loss (filesystem corruption) [B][COLOR="#FF0000"]and possibly permanent
 damage to electronic components. Use at your own risk.[/COLOR][/B]

To install it -
```
sudo apt-get install cpuburn
```

But, have you tried using a new, fresh usb pen drive? It is the part that is most vulnerable to wear and tear. Besides, the OS gets heavier with each update. If your laptop's hardware is too old, it may not be able to handle newer versions at all.

What are the specs of your system? Maybe show us the full output of -
```
sudo lshw -sanitize
```

---

