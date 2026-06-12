---
title: "Not sure how to set up Conky"
date: 2008-07-17
forum: General Help
---

### Post by Het Irv on 2008-07-17
I just downloaded the Conky source, ./configure && sudo make && sudo make install and all that jazz.

Then I put in a .conkyrc that I liked and added a script to get part of it to work, but when I start Conky parts will not work.

TERMINAL OUTPUT:
```
hetirv@hetirv-laptop:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: /home/hetirv/.conkyrc: 32: no such configuration: 'maximum_size'
Conky: unknown variable wireless_link_bar
Conky: unknown variable wireless_link_qual
Conky: unknown variable wireless_essid
Conky: unknown variable wireless_bitrate
Conky: desktop window (10000bc) is subwindow of root window (59)
Conky: window type - normal
Conky: drawing to created window (3800001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT1/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT1/state: No such file or directory
Conky: can't open /proc/apm: No such file or directory
--12:44:21--  http://whatismyip.org/
           => `-'
Resolving whatismyip.org... 206.176.224.3
Connecting to whatismyip.org|206.176.224.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12 [text/plain]

100%[====================================>] 12            --.--K/s             

12:44:21 (958.28 KB/s) - `-' saved [12/12]

sh: /home/hetirv/.conky/amarok: Permission denied
sh: /home/hetirv/.conky/amarok: Permission denied
sh: /home/hetirv/.conky/amarok: Permission denied
Conky: your execibar value is not between 0 and 100, therefore it will be ignored

```

Attached are the conkyrc file and the amarok script.

---

### Post by RealPSL on 2008-07-19
You might be running an older version of conky against a .conkyrc with new variables. Your best bet is just to start simple with the sample .conkyrc file. Or you edit the .conkyrc file you want to use and remove those variables it is complaining about. You can get the sample .conkyrc file by running

```
gunzip -c /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

Just remember to backup the one you are replacing first.

---

### Post by Lord DarkPat on 2008-07-19
try the conkyrc thread in the Cafe. I found mine there

---

### Post by Kevbert on 2008-07-19
What version of conky are you using ? (it looks like 1.49 or before that). If you have Hardy, you can get conky 1.51 via Synaptic, which looks like it will work with your conky.txt file.  With regards to the battery error you need to see if you can browse to the directory using Nautilus.

---

