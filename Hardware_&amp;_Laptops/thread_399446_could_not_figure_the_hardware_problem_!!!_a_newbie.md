---
title: "could not figure the hardware problem !!! a newbie problem"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by ashokcz on 2007-04-02
hi , i m a newbie to ubuntu and this thread could be a long one sorry for that  i just tried to install ubuntu in my pc . but  installation never started and got struck @  the loading screen  but anyhow got it installed using alternate cd(text mode) . but during my first login after installtion it showed frequency out of range error .. so i thought of logging in recovery mode and expected to change my screen resolution in xconf settings but in recovery mode it never started while it  booting it showed me commands like this 
[B]
write protect is off
scsi device sda: drive cache : write back
<3> ata3:command 0xC8 timeout , stat 0x50 hoststat 0x64
ata3:status 0x50 <drive ready seek complete>
sda: correct : no sense : no sense : additional sense : no additional sense information :
info fld 0x71f4b8f
...........
...........
...........
...........
...........[/B]


like this it goes on 

wat i could sense is there could be some problem with respect to other hardware other than hard disk (coz i could install) and monitor(coz even i could install in text mode).,......
but i m not sure ... 
if someonme could give me any ans to come out of this .**..keeping  my machine idle for almost 2 weeks !!!!**:( 

**my pc specifiactions are **
Intel motherboard D102G gc2 
intel dual core processor 2.66 ghz 
SATA Seagate Hard Disk
FrontTech LCD Monitor
SamSung DVD R/W TS - H352

---

### Post by ashokcz on 2007-04-06
hi all  , 
is there somethin missing in my post  ......  its very much frustrating to have my machine off for  a  month

---

### Post by quirks on 2007-04-06
Hi ashokcz!

1. I am not a pro, but I don't think the "frequency out of range" error is related to the message concerning your hard disk, which you see when trying to boot in recovery mode.

2. Have I understood you correctly, that you are unable to boot into recovery mode due to the hard disk problem? Where does the error message appear? Doesn't it even get to the login prompt or don't you see the login prompt between loads of error messages? (However, as for this problem, I have currently no idea what to do :-/ )

3. Am I right when I assume that the "frequency out of range" error occurs, when you try to log in in graphical mode? Because if so, you might want to switch to another (text-based) terminal by pressing Ctrl+Alt+F1. Then you can log in and change the frequency settings.

quirks

---

