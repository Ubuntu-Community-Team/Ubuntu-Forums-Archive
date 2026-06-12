---
title: "pwmconfig shows a regret message"
date: 2012-05-05
forum: Hardware
---

### Post by deepaknet on 2012-05-05
I am getting the following message on Ubuntu 12.04 (Dual boot Windows 7 is of no issue)


lavanyadeepak@lavanyadeepak:~$ sudo pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

---

