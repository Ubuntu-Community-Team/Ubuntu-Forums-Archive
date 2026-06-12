---
title: "crashed - voltage levels during system sleep/idle?"
date: 2015-02-05
forum: Hardware
---

### Post by D0natell0 on 2015-02-05
Hi,
What happens by default to motherboard/SATA voltage levels during system sleep/idle? 
Has anyone had problems with either system crashes, HDD or SSD failures, due to voltage drops during system sleep/idle?

Thanks in advance.

---

### Post by D0natell0 on 2015-02-05
After some research, here's what I've found: Windows has states such as hibernate, standby, etc., all of which will involve the SATA powering down. You can control power down of the SATA in the Power Options in the Windows Control Panel. You can set how many minutes pass until power is removed and they spin down.

So, next question is how does this get enforced in Linux?
Thanks.

---

### Post by D0natell0 on 2015-02-05
Here's the relevant documentation page. Seems you can't be too careful with power settings! Check out relevant device drivers are upto date too!
Seems I need to do further investigation...

[https://help.ubuntu.com/12.04/ubuntu-help/power-suspendfail.html](https://help.ubuntu.com/12.04/ubuntu-help/power-suspendfail.html)

---

### Post by tgalati4 on 2015-02-06
You can control (somewhat) what parts of the computer bus remained powered during sleep.

Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

Typically a computer will leave 5VDC on during sleep to certain parts of the motherboard to allow it to resume.  You can check 5VDC with a voltmeter by probing the motherboard power connector.  The issue with not coming back after sleep can be caused by many, many issues.  It requires some reading and some understanding of how Ubuntu handles sleep and hibernation.

First, you cannot hibernate if your swap size is smaller than your RAM.

What is the output of:

```
free
```

---

