---
title: "Brother printer stopped filter failed error when printing on ubuntu-"
date: 2015-03-03
forum: Hardware
---

### Post by Boboci9 on 2015-03-03
Hi everyone,

I am trying to print with my new Brother printer 1610WE but I keep getting Stopped Filter failed messages. I have tried everything from similar posts but nothing solved my issue, I managed to get the scanner to work, so I can scan with the same machine but the printing still won' work.
I am totally new to ubuntu so please keep this in mind when you suggest solutions and if you can please give me the terminal commands not only the description of what I should try. Thanks :)
Solutions that I have tried:
  - I tried installing several packages suggested on different posts: cups-filters, foomatic-filters, [FONT=Courier 10 Pitch]printer-driver-hpijs[/FONT]
 - I gave chmod 0666 to my printer
 - tried cleaning the disk but I don't think this is the issue since I have a pretty new hardware with new ubuntu install 

```

Filesystem     1K-blocks     Used Available Use% Mounted on/dev/sda3       91899944  7794916  79413676   9% /
none                   4        0         4   0% /sys/fs/cgroup
udev             8143784        8   8143776   1% /dev
tmpfs            1630916     1188   1629728   1% /run
none                5120        0      5120   0% /run/lock
none             8154576    15956   8138620   1% /run/shm
none              102400       36    102364   1% /run/user
/dev/sdb5       93541312 15640900  73125656  18% /home

```

Thank you in advance

---

### Post by Li_Wu on 2015-03-03
why don't u copy the err msg in here. brother linux stuff usually works pretty well tho some quirks may happen

---

### Post by pdc on 2015-03-03
Hi bobo

I wonder what printer drivers you are using? If you can open a terminal ............ if you hold the control and alt and t keys down all at once, it will open the terminal and if you can copy this command and then paste it into the terminal; (to paste into a terminal click at the prompt and then hold the control and shift and v keys down all at once) ............ ```
dpkg -l | grep Brother
``` ........and if you can paste back the result please .............. to copy in a terminal, highlight the text and press shift and control and c keys all at once ..................

If I hadn't installed the drivers that Brother provide, I would delete any existing Brother setup in the PRINTERS section of the menu .......

then I would do as below .............

______________

If I was installing printer drivers for the DCP-1610W, I would 

1) go here and download and install the LPR debian package [http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp1610w_eu_as&os=128&dlid=dlf101533_000&flang=4&type3=559](http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp1610w_eu_as&os=128&dlid=dlf101533_000&flang=4&type3=559) ........ click on the big blue AGREE and DOWNLOAD button .......

2) then go here and get the CUPSWRAPPER package [http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp1610w_eu_as&os=128&dlid=dlf101532_000&flang=4&type3=561](http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp1610w_eu_as&os=128&dlid=dlf101532_000&flang=4&type3=561)

____________

then I would go back to the PRINTERS box and ADD A NEW PRINTER and the system should find the Brother DCP-1610 but with Brother drivers, it should set it all up and it should work well .....................

________________

---

