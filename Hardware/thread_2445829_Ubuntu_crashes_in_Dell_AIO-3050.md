---
title: "Ubuntu crashes in Dell AIO-3050"
date: 2020-06-20
forum: Hardware
---

### Post by pranitchuri on 2020-06-20
I have tried installing ubuntu 16.04, 18.04 and also 20.04 in dell AIO-3050 machine. on this perticular machine after installing ubuntu OS, updating and upgrading it works well but after some count of restart, this machine doest boot. stuck at  

 pceiport 0000:00:1c.6: AER: PCIe Bus Error: severity=Corrected, type=physical Layer, (Receiver ID) 
 pceiport 0000:00:1c.6: AER:     device [8086:a296]  error status/mask=00000001/00002000
 pceiport 0000:00:1c.6: AER:        [  0]  RxErr

with above error boot process stucks. this has occured so many times even after installing new ubuntu distributions in same machine. 
i have also performed system check using Dell dignostinc. resulting test report to be passed every time. so found no physical issue with machine. when finally after installing windows 10 on same machine, it works fine. but i'm still confused with Why Ubuntu doenst work well with this perticular Dell machine.

---

### Post by CelticWarrior on 2020-06-20
Welcome.

Update UEFI ("BIOS") (you'll find this is actually marked as "urgent").
Make sure you're booting in UEFI mode - how it boots is how it installs - the Ubuntu 20.04 installation media. Do not use older releases.

---

### Post by pranitchuri on 2020-06-22
i have already updated BIOS. and also tried with UEFI mode. also i tried duel booting via Legacy mode and installed ubuntu 20.04 after installing windows 10. but eventually end up facing same issue.

---

### Post by pranitchuri on 2020-06-22
now after installing only windows 10 in legacy, works great. pls suggest what to do, to have ubuntu.

---

### Post by CelticWarrior on 2020-06-22
You're doing the opposite of what you should be doing, for Windows and Ubuntu.
I won't help with legacy installations that are done for no reason whatsoever.

---

### Post by pranitchuri on 2020-06-23
Ok im trying in UEFI mode now. Will let u know the result

---

