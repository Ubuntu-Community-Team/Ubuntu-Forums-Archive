---
title: "problem with laptop video card"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by devin0 on 2007-11-25
I recently bought a laptop and put ubuntu on it. everything is working fine, except for the s-video out port (lets me use a tv as a monitor) this port was working when i had windows running on it but isn't hasn't worked scince i put ubunu on. the laptop is a compaq presario 2100. can anyone tell me how to get the s video out port working again?

---

### Post by jcsteele on 2007-11-25
Can you run the command "lspci" and post its output below for us to see...it will greatly help in diagnosing the problem.

//jcs

---

### Post by devin0 on 2007-11-25
ok i did that and this is what i got-

0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBu s Controller
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (Ma cPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

-now what should i do?

---

### Post by jcsteele on 2007-11-26
Can you post the output to the command "xrandr --verbose" to the forum?  You can enter this command from the Terminal.


I just googled, assuming you do NOT have the closed-source ATI driver installed...if this is the case, you can follow the guide below to  get S-Video working.

[http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1)

Its worth a shot....but lets see what xrandr comes up with first.

//jcs

---

### Post by devin0 on 2007-11-26
SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60
 1    640 x 350    ( 347mm x 260mm )   60
 2    640 x 400    ( 347mm x 260mm )   60
 3    720 x 400    ( 347mm x 260mm )   60
 4    640 x 480    ( 347mm x 260mm )   60
 5    800 x 600    ( 347mm x 260mm )   60
 6    832 x 624    ( 347mm x 260mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
Setting size to 0, rotation to normal
Setting reflection on neither axis



-now what should i do?

---

### Post by jcsteele on 2007-11-26
Is that with or without the s-video port plugged in?  Try plugging the s-video into the television, and run the following commands....were trying to see if xrandr is recognizing the television as a possible output...

xrandr
xrandr --verbose
xrandr -q

//jcs

---

### Post by Yellow Pasque on 2007-11-26
EDIT: Nevermind

---

### Post by devin0 on 2007-11-26
i didn't get anything on my tv screen, when i typed in the commands you gave me this is what i got :
lyokoboy@lyoko:~$
lyokoboy@lyoko:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60
 1    640 x 350    ( 347mm x 260mm )   60
 2    640 x 400    ( 347mm x 260mm )   60
 3    720 x 400    ( 347mm x 260mm )   60
 4    640 x 480    ( 347mm x 260mm )   60
 5    800 x 600    ( 347mm x 260mm )   60
 6    832 x 624    ( 347mm x 260mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
lyokoboy@lyoko:~$ xrandr --verbose
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60
 1    640 x 350    ( 347mm x 260mm )   60
 2    640 x 400    ( 347mm x 260mm )   60
 3    720 x 400    ( 347mm x 260mm )   60
 4    640 x 480    ( 347mm x 260mm )   60
 5    800 x 600    ( 347mm x 260mm )   60
 6    832 x 624    ( 347mm x 260mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
Setting size to 0, rotation to normal
Setting reflection on neither axis
lyokoboy@lyoko:~$ xrandr -q
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60
 1    640 x 350    ( 347mm x 260mm )   60
 2    640 x 400    ( 347mm x 260mm )   60
 3    720 x 400    ( 347mm x 260mm )   60
 4    640 x 480    ( 347mm x 260mm )   60
 5    800 x 600    ( 347mm x 260mm )   60
 6    832 x 624    ( 347mm x 260mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
lyokoboy@lyoko:~$

---

### Post by jcsteele on 2007-11-28
It doesn't look like its even recognizing the s-video port....you might try install the ATI driver, which might help...its worth a try.

Take a look at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and setup the ATI driver.....then try again.

I am going to try to get my s-video working on my new laptop and get back with you as well....

//jcs

---

### Post by devin0 on 2007-12-03
ok thanks so much for the help :)
i will post back with my results from that toutorial you gave me :)

---

### Post by www.rzr.online.fr on 2008-03-19
same issue, tvout is not detected on my card radeon igp :


 # rzr@nrv:tmp/ # :( # xrandr  --output S-video --set load_detection 1
 X Error of failed request:  173
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  14
  Current serial number in output stream:  14


--
[http://rzr.online.fr/q/vbe](http://rzr.online.fr/q/vbe)

---

