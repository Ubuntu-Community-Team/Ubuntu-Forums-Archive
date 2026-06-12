---
title: "Checking specs of computer in Ubuntu question"
date: 2009-10-31
forum: Hardware
---

### Post by mjp29 on 2009-10-31
I now have 3 Pentium 4 desktop computers that Ubuntu will go on.

I would like to know the easiest way to check the specs of each computer so I know which computer is the best (like has the most ram, best video card, dvd or cd drive, dvd or cd write/burn drives, etc...)

Use terminal or click something on desktop to find out?

---

### Post by fancypiper on 2009-10-31
I think you are looking for the System Monitor, an aplet you can add to the panel.

For the command line:
sudo lshw | less

---

### Post by mjp29 on 2009-10-31
> **fancypiper said:**
> I think you are looking for the System Monitor, an aplet you can add to the panel.

For the command line:
sudo lshw | less

I think the sudo command will be better for me than adding an applet because some of these computers have not been set up yet and i will be booting them from a live cd and checking before any install (some have a bad hard drive)

---

### Post by fancypiper on 2009-10-31
It's a shifted \

You can scroll up and down to see all the hardware that is detected.

You could also send the output to a text file:
sudo lshw > hardware.txt

Then you could use gedit to see your hardware.

---

### Post by mjp29 on 2009-10-31
ok I figured it out - thanks

some questions:

1) where does it tell how good the video card (under multimedia?  and where specifically can I look to write down how good each video card is in each computer)

2) one of the computers has memory slot that is: unclaimed memory 512k that is flash (non-volatile flash) and there is another one like it in a slot that it does  not specify it's size).  Is this memory soldered onto the motherboard?  for what reason?  cache or something or is it ram soldered on like in a laptop

---

