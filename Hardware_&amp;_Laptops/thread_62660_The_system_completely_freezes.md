---
title: "The system completely freezes"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by tseliot on 2005-09-05
Hi, I have a problem which is really annoying: the system completely freezes randomly. 

I have tried to test my 2GB RAM (4x 512M DDR modules) in Memtest86 and after 2h 56min it was still running then I thought something was wrong and I stopped it.

No errors were reported:
I got number "7" under "Pass" 

How much should the test take? (I have an AMD 3500+)

And what that number 7 could mean?

Thanks in advance.

---

### Post by jouni on 2005-09-05
[QUOTE=tseliot]I have tried to test my 2GB RAM (4x 512M DDR modules) in Memtest86 and after 2h 56min it was still running then I thought something was wrong and I stopped it.

No errors were reported:
I got number "7" under "Pass" 

How much should the test take? (I have an AMD 3500+)

And what that number 7 could mean?[/QUOTE]

Memtest86 will run indefinitely long, repeating the tests over and over. I think Pass 7 means that the selected tests are being run for the 7th time, i.e., 6 complete passes have been run. What I would do is make sure all the tests are selected (I think not all of them are selected by default) and leave the program running overnight or for a weekend. However, according to the [Memtest instructions](http://www.memtest86.com/#timing), one pass should be enough to catch "all but the most obscure errors".

---

### Post by tseliot on 2005-09-05
[QUOTE=jouni]Memtest86 will run indefinitely long, repeating the tests over and over. I think Pass 7 means that the selected tests are being run for the 7th time, i.e., 6 complete passes have been run. What I would do is make sure all the tests are selected (I think not all of them are selected by default) and leave the program running overnight or for a weekend. However, according to the [Memtest instructions](http://www.memtest86.com/#timing), one pass should be enough to catch "all but the most obscure errors".[/QUOTE]
The problem is that I need my computer to run. I can't afford to keep it busy for such a long time.

However I noticed the system doesn't freeze in Windows.
Perhaps it because windows doesn't use all my RAM (I don't think it can use 2gb RAM).

If this is true perheps the faulty modules can be the modules in 4th and 5th position (which wouldn't be used by Windows)

Am I right?

---

### Post by jouni on 2005-09-05
[QUOTE=tseliot]However I noticed the system doesn't freeze in Windows.
Perhaps it because windows doesn't use all my RAM (I don't think it can use 2gb RAM).

If this is true perheps the faulty modules can be the modules in 4th and 5th position (which wouldn't be used by Windows)

Am I right?[/QUOTE]

I suppose it would be the last positions, if Windows really cannot use all of the RAM. However, there could be any number of other things that are different between Windows and Linux that can affect the problem. Perhaps Linux has some pattern of hardware usage that doesn't occur in Windows, and that triggers the error. It seems that many people only find out that they have faulty memory chips when they compile the Linux kernel: this exercises memory and disk I/O at the same time, and gcc is very sensitive to memory errors. This is described on the [SIG11](http://www.bitwizard.nl/sig11/) page.

Or, there could be a bug in a device driver in Linux (or X11). This can be very difficult to track down.

One way to narrow down the possibilities would be to remove half of your memory modules and run for a while (with enough load to really exercise the memory; try [this script](http://people.redhat.com/dledford/memtest.html)), then swap the modules and repeat. If the crashes only occur with one set of modules, it's definitely a memory problem.

---

### Post by tseliot on 2005-09-05
> **jouni]I suppose it would be the last positions, if Windows really cannot use all of the RAM. However, there could be any number of other things that are different between Windows and Linux that can affect the problem. Perhaps Linux has some pattern of hardware usage that doesn't occur in Windows, and that triggers the error. It seems that many people only find out that they have faulty memory chips when they compile the Linux kernel: this exercises memory and disk I/O at the same time, and gcc is very sensitive to memory errors. This is described on the [SIG11](http://www.bitwizard.nl/sig11/) page.

Or, there could be a bug in a device driver in Linux (or X11). This can be very difficult to track down.

One way to narrow down the possibilities would be to remove half of your memory modules and run for a while (with enough load to really exercise the memory said:**
> this script[/URL]), then swap the modules and repeat. If the crashes only occur with one set of modules, it's definitely a memory problem.
Thanks for the help I hope to find the problem

---

