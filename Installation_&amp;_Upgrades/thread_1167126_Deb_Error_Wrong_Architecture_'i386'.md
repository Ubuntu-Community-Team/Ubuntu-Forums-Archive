---
title: "Deb Error: Wrong Architecture 'i386'"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by robinlouis on 2009-05-22
Hi,

I have installed a Wubi 8.04 Ubuntu on my Dell Vostro 1510 which is a 32bit machine. 

When I try and open any .deb files, I get the error message "Error: Wrong Architecture 'i386'". I read somewhere that this could be if the wrong version of Ubuntu was installed (32bit/64 bit). So I ran the 'uname -m' command, and it says x86_64. Does that mean the version of Ubuntu I've installed is a 64bit one? How do I fix this? 

I'm new to Ubuntu/Linux, but keen to switch from Windows. Would appreciate any help I can get.

Robin

---

### Post by oldos2er on 2009-05-22
Wubi automatically detects whether your processor is 32- or 64-bit, and installs the appropriate kernel. Your machine must be 64-bit, because 64-bit can't run on a 32-bit processor.

   You should look for 64-bit version of whatever deb file you're installing; or, you can force the installation of a 32-bit deb with
```
sudo dpkg -i --force-architecture filename.deb

``` If you stick to the repositories, 64-bit packages will automatically be installed.

---

### Post by robinlouis on 2009-05-23
Hi,

Thanks for the response. But, could you tell me just how accurate Wubi is? The reason I ask is because I was pretty sure I had bought a 32 bit machine since a 64 bit one was more expensive. Also I checked the system info through windows and its a 32 bit windows installation. So, either Dell gave me a 64 bit machine by mistake or Wubi might have gotten it wrong. I'm really confused now. Your thoughts?

Robin

---

### Post by mcduck on 2009-05-23
> **robinlouis said:**
> Hi,

Thanks for the response. But, could you tell me just how accurate Wubi is? The reason I ask is because I was pretty sure I had bought a 32 bit machine since a 64 bit one was more expensive. Also I checked the system info through windows and its a 32 bit windows installation. So, either Dell gave me a 64 bit machine by mistake or Wubi might have gotten it wrong. I'm really confused now. Your thoughts?

Robin

If the 64-bit Ubuntu works at all, you definitely *do* have a 64-bit CPU. Running 64-bit operating system on a 32-bit processor is simply not possible.

---

### Post by lisati on 2009-05-23
If uname shows x86_64 then your machine is a 64-bit machine, not 32-bit. I recently discovered that one of my machines was 64-bit, and that was after having the thing nearly four years!

---

### Post by Sef on 2009-05-23
> Thanks for the response. But, could you tell me just how accurate Wubi is? The reason I ask is because I was pretty sure I had bought a 32 bit machine since a 64 bit one was more expensive. Also I checked the system info through windows and its a 32 bit windows installation. So, either Dell gave me a 64 bit machine by mistake or Wubi might have gotten it wrong. I'm really confused now. Your thoughts?


Almost all computers sold now have 64-bit hardware.  However, the operating system can be either 64-bit or 32-bit.   If you got a Windows machine, then likely you got a 32-bit operating system working on 64-bit hardware.   

Wubi works just fine.  It's a good way to check out how Ubuntu works on your machine without installing it.

---

### Post by robinlouis on 2009-05-23
Thanks for all the responses. This is a real eye opener! Why in the world would they sell me a 64bit machine as a 32bit machine? 

Anyway... thanks once again everyone.

Best regards,
Robin

---

