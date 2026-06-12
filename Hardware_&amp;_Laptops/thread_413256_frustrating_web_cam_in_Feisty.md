---
title: "frustrating web cam in Feisty"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by bran on 2007-04-19
this cam did work under Dapper

:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:08f5 Logitech, Inc. 


:~$ lsmod | grep pcw
:~$ lsmod | grep spca

both show no output

lsdev does not show any video devices

Camorama outputs the cannot connect error

easycam generates piles of errors and fails on make (error 2)

Very frustrating given this is reported as on of the cams that just works.

Have tried manual install of the spca5xx which also declines to work.

Any help/ideas

---

### Post by bran on 2007-04-24
bump

Is it possible that its an error in the choice of compiler?

---

### Post by kev000 on 2007-04-26
i'm also getting errors in feisty trying to get my webcam to work...

anyone?

---

### Post by bran on 2007-05-10
bump

---

