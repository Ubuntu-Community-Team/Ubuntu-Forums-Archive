---
title: "New laptop best Hardware ubuntu compatibilty"
date: 2016-04-28
forum: Hardware
---

### Post by iokara08 on 2016-04-28
Hi all Linux users,

I have decided to buy a new laptop since it has been a lot of time from my last buy...2007 Acer Aspire 5052. To be honest my laptop even if it is almost 10 years old, for office work it is still useful and that thanx to Ubuntu.
Based on personal experience in installing Linux software in several PC's, Desktops, Laptops and netbooks (I am my best in spreading the word...) I have noticed that some hardware is usually harder to make a proper installation than others.
For example is it better to buy a laptop which will include an ATI radeon graphic card instead of Nvidia? Similarly, speaking always about compatibility,  what is your opinion about AMD vs Intel cpu?
My current laptop includes AMD processor and ATI radeon graphic card and I never experienced any compatibility issues with all the Linux flavours that I have used the last 10 years.
Conversely, whenever I used Linux softwares in machines including Nvidia card I was experiencing compatibility issues and I had to search along the internet for a solution.

If you also have any suggestion regading some particular laptops you are free to propose. Below you can find my needs:
-Not a gaming laptop.
-LCD: 15.6
-RAM: 4GB DDR3 is ok
-CPU: ?
-Storage: HDD or SSD dont mind

Thank you in advance for your time.

---

### Post by ajgreeny on 2016-04-28
The most recent Ubuntu version 16.04 seems to be causing some problems for some users, not all, with AMD graphics cards.

I suspect this is related to the specific card and how new it is; for the newer cards I think AMD now has its own open source amdgpu driver instead of the older radeon driver, and regrettably at present the fglrx proprietary driver is a no-no with 16.04.

If you go the Intel route you will probably have fewer problems; that is the way I moved when my old AMD sempron machine finally died 3 years ago, and so far all the *ubuntu OSs I've tried have worked brilliantly in every respect, with all hardware supported.

---

### Post by Bucky Ball on 2016-04-28
*Thread moved to **Hardware**.*

99% of problems come from either graphics and/or wireless. The other 1% manufacturer BIOS or config issues (which can usually be worked around one way or the other). 

If you're more fine-grained and research those things and get them right, you're there. Sure you're going to get plenty of suggestions here, though. :)

---

### Post by iokara08 on 2016-04-28
Hi ajgreeny,

Thanks for the fast reply. There are plenty of laptops on the market that include Ubuntu as the default OS so probably such a laptop could be what I need since the possibility to run into compatibility issues will be too small.

---

### Post by iokara08 on 2016-04-28
Hi Bucky ball, I am not in rush and thus I have plenty of time to wait for the ideas of the forum :cool: but as I also wrote previously I believe that the best is to consider a laptop which has been designed for Linux OS. Likely there are many manufacturers nowadays that design machines for Ubuntu :biggrin:

---

### Post by weatherman2 on 2016-04-28
If you are not gaming and you go for an Intel CPU, you can just use integrated graphics and not get ether an Nvidia or Radeon (AMD) graphics card.  Intel integrated graphics performance is much better nowadays since the graphics controller has been integrated into the CPU itself.  I really haven't found any need for an extra graphics card, and in a laptop it only uses more power and reduces your battery life, anyway, but I don't play games, either.

If you ever want to upgrade your laptop's wireless card, avoid an HP or Lenovo laptop, because they "whitelist" their wireless cards and don't allow you to install non-approved wireless cards - something I have done many times on my laptops.  I prefer Intel wireless cards in part because they usually work out-of-the-box in Ubuntu whereas other cards (e.g. Broadcom) seem to require additional drivers and techniques that change with each new release just to get them working.

If you ever think you'll upgrade the hard drive to an SSD, make sure any new laptop allows that fairly easily.  Some laptops are designed to allow easy access to the drive while others may require a lot of disassembly just to get to the drive.

---

### Post by iokara08 on 2016-04-30
Weatherman2 thank your for your reply,
A cpu with integrated graphics sounds a smart choice and to be honest since I quite following the development of laptop parts I wasn't aware of such a possibility. Anyway thank you a lot for your useful reply which covered all critical parts of a laptop, cpu, wireless and graphics.

---

### Post by mörgæs on 2016-04-30
I think you should try a fresh install of Lubuntu (not Ubuntu) on the Acer Aspire 5052 before deciding. Chances are that you don't need to buy anything at all.

---

