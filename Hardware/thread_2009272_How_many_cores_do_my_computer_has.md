---
title: "How many cores do my computer has?"
date: 2012-06-24
forum: Hardware
---

### Post by gozlemci on 2012-06-24
Hi There;
I've brought a new lenovo laptop. The seller said it is triple core computer. Windows 7 was installed at that computer and, according to bios, system diagnosis programs and computer properties , the computer has one dual core cpu.
On the other hand, during the Win7 era according to device manager and according to System settings -> Details (now ubuntu 12.04 is installed) the processor status is:
"AMD Athlon(tm) II P340 Dual-Core Processor × 2 "

How many cores do I have? How can I understand it?

---

### Post by drpjkurian on 2012-06-24
you have two
Just google your 'AMD Athlon(tm) II P340 Dual-Core Processor × 2'

---

### Post by hansdown on 2012-06-24
Hi gozlemci.

Four cores.

It has two dual core processors, so it is a quad core.

[http://www.notebookcheck.net/AMD-Athlon-II-P340-Notebook-Processor.37883.0.html](http://www.notebookcheck.net/AMD-Athlon-II-P340-Notebook-Processor.37883.0.html)

If you open ststem monitor>resources, you should see how many cpus are there.

---

### Post by m_duck on 2012-06-24
What is the model of the laptop? I'm fairly sure that CPU is a dual core.

---

### Post by raja.genupula on 2012-06-24
Dual core means already two cores , and the last thing "x2"  . i am thinking it has totally 4 cores .

---

### Post by gozlemci on 2012-06-24
My computer is lenovo g565.
Here are the snapshots:

It seems I've been betrayed.

---

### Post by m_duck on 2012-06-24
I assume the X2 (though appearing more as a multiplication sign in the screenshot) is part of AMDs product line as it appears as part of the name in a number of their CPUs.

See [here on Play.com's](http://www.play.com/PC/PCs/4-/17587683/856552316/Lenovo-G565-AMD-Athlon-II-X2-P320-2-1GHz-2GB-250GB-DVD-SM-15-6-inch-Windows-7-Home-Premium-Laptop-Notebook/ListingDetails.html?_$ja=tsid%3a11518%7ccat%3a17587683%7cprd%3a17587683) description for this laptop mentioning "Lenovo G565 15.6 inch Laptop (AMD Athlon II X2 **Dual-Core** P320 2.1GHz, 2GB RAM, 250GB HDD, DVDRW, Windows 7 Home Premium)". I couldn't seem to find the computer on Lenovo's website.

---

### Post by hansdown on 2012-06-24
> **gozlemci said:**
> My computer is lenovo g565.
Here are the snapshots:

It seems I've been betrayed.

It appears to be a single dual core processor.

---

### Post by raja.genupula on 2012-06-24
hi do this 

```
sudo apt-get install sysinfo ;sysinfo
``` and click at CPU .

---

