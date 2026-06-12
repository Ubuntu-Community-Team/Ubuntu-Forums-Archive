---
title: "Dell Vostro 1510 problems"
date: 2009-05-08
forum: Hardware
---

### Post by lvshankar on 2009-05-08
Hey,

I have a Dell Vostro 1510 running Intrepid. Recently, I upgraded to Jaunty through Update Manager. Ever since, I am facing the following problems:

[LIST]
[*]my desktop effects have been disabled (am not able to enable it again, I get "Desktop effects could not be enabled")
[*]My keyboard doesn't work sometimes. Just whatever key I press gets no response. Even alphanumeric keys in a text area. This gets fixed on restart but not on logoff
[*]I think my screen looks different though the resolution is the same
[*]I had settings to run Transmission client in the Taskbar when the window is closed, that too was reset.
[/LIST]

I haven't had time to explore for other problems, but right now I need to get these fixed. Is it a known bug, or did I do something wrong?

---

### Post by durand on 2009-05-08
This thread might help you:
[http://ubuntuforums.org/showthread.php?t=829525](http://ubuntuforums.org/showthread.php?t=829525)

It's for the vostro 1710 but it should have similar hardware to yours.

---

### Post by lvshankar on 2009-05-09
This helped.
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

According to [another post]("http://webupd8.blogspot.com/2009/05/ubuntu-intel-graphic-card-driver-news.html") I was supposed to get the recently whitelisted Intel drivers for my card from PPA repos. I got that but it didn't work still. And then I did the Ubuntu forums link above.

It says video playing would be bad, but video playback is pretty fine for me. Maybe its the PPA drivers.

Thanks.

Of course, my keyboard problem is still on :(

---

### Post by MrGabrielGray on 2009-05-28
Hi, i have the same laptop, the problem is not in the xorg per se, the problem is in the load of the video module (Assuming you have installed).

check this out $ sudo lshw -C display

unfortunately i dont know how to fix it =(, but its a tip!

---

### Post by lvshankar on 2009-05-28
this is my output for lshw -C display

```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

---

### Post by MrGabrielGray on 2009-05-28
Yeap, same as mine, have you seen this ? 

[http://ubuntuforums.org/showthread.php?t=1131978](http://ubuntuforums.org/showthread.php?t=1131978)

---

