---
title: "What device in /dev is for PC printer port?"
date: 2019-06-24
forum: Hardware
---

### Post by scharkalvin on 2019-06-24
I'm running Kubuntu 18.04.  My computer has a legacy LP port on it, and is enabled in the bios.  I don't see any corresponding device in /dev for the printer.  
I want to write a program to interface an old style eprom burner to the computer using the printer port.  What device would I need to open?  

$ lsmod | grep lp
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev

$ ls /dev/lp*
ls: cannot access '/dev/lp*': No such file or directory

$ ls /dev/par*
ls: cannot access '/dev/par*': No such file or directory

---

