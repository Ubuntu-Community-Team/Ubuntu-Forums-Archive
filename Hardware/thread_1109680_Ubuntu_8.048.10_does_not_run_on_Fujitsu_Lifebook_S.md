---
title: "Ubuntu 8.04/8.10 does not run on Fujitsu Lifebook S6110?"
date: 2009-03-29
forum: Hardware
---

### Post by Hilleri8 on 2009-03-29
My problem is simple and I have a picture to help.  I attempt to load a test version of Ubuntu and the graphics do not display properly then fade to black.
[IMG]http://1.media.tumblr.com/04pshNSShlmt04xedcXS2HOSo1_500.jpg[/IMG]

Info about machine:
Fujitsu Lifebook S6110
Pentium 3m 1.2ghz
512mb ram
Intel 830m graphics chip (eats upto a max of 48mb of system memory)

What I have tried so far:
[LIST]
[*]Downloaded the CD for 8.10 and the DVD for 8.04 each time doing md5checksum.
[*]When I load up the CD/DVD I checked the CD/DVD for errors and it reported that there were none.
[*]I have scanned the memory of the system for problems using the memory scan tool on the CD/DVD
[*]I have tried to run ubuntu off the CD/DVD in graphic safe mode.
[*]I have tried to run ubuntu off the CD/DVD with each possible combination of special options (aspc = off), etc.
[/LIST]

Each time that I have tried I end up with the same results: the above screen shot.  Ohh, and also if I wait for a little bit the computer plays some sort of noise, I am guessing the is the noise of booting into Ubuntu.  So Ubuntu seems to be running ok, just nothing gets output to my laptop's display.

Thanks for any help.

---

### Post by Hilleri8 on 2009-03-29
Ok, well I think that I fixed my problem.  I can boot into the ubuntu gui no problem now.

For anyone who may be interested I did this by adding the following line to my xorg.conf file in the Device section:
Driver "i810"

---

### Post by cosmicmonkey on 2009-06-01
do you mind sharing your xorg.conf file.  Mine doesn't work at all.

---

