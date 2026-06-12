---
title: "can't shutdown automatically"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by Isoss on 2006-07-02
I have LG intel centrino 1.7GHz laptop. it has windows xp and ubuntu ... when I shutdown from windows the power goes off, but when I shutdown from ubuntu it just freezes at "Will now halt" but never turns the power off!! 
What's the solution?

---

### Post by d3baser on 2006-07-02
I would appreciate help also, I am with the same problem.

---

### Post by xrchris on 2006-07-03
I reported this as a bug about a week before Dapper 6.06 was released and many more have done so since then. 

It appears to remain unresolved.

---

### Post by Isoss on 2006-07-03
Alright, the only way to turn the power of is to press the power button and hold for 5 seconds. It's not a problem cuz I do it once a day or every two days ... but my question is, would it cause a problem if done too much?

---

### Post by cracker on 2006-07-04
As long as you wait until the system is completely halted, it is perfectly fine to manually turn off the power. Data loss and errors will only result if you shut off the power during operation.

---

### Post by Isoss on 2006-07-05
Ok, this I know, but what I am worried about is the power supply! might there be a risk for the power supply if done too much? that's the question.

---

### Post by xrchris on 2006-07-05
It shouldn't make any difference to the power supply, after all its just 2 different types of switch for the same power source.

---

### Post by Zeratul7 on 2006-07-05
I am having the same problem on my Fujitsu Siemens S7020.
But after the "Will now halt" my monitor goes black but some indicators on mini display do not turn off and fan is still running.

---

### Post by zhoux on 2006-07-05
may be a problem with acpi or the power management software....

---

### Post by cracker on 2006-07-05
As far as the hardware is concerned, you can shut it off any time you please with no repercussions. Software corruption is the only reason the shutdown procedure was even created, and automatic power off was later added for convenience.

---

### Post by xrchris on 2006-07-06
This is the official bug report for those whose machines that freeze at "Will now halt" but never turns the power off!! 

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

---

