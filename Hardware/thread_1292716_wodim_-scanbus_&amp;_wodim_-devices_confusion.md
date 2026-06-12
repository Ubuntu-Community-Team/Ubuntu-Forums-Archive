---
title: "wodim -scanbus &amp; wodim -devices confusion"
date: 2009-10-16
forum: Hardware
---

### Post by texas.chef94 on 2009-10-16
My notebook lacked DVD capability and while its old and 32 bit afford ability issues dictated I take path least resistance, purchase of external.
I had a previously downloaded DVD image on HD choose k3b and image plus the burn DVD option. It recognized the image, but not the DVD in the drive.
So as a further test proving (I have not a clue) I inserted a blank CD choose a CD image and it recognized the image and burned the CD
Is this a k3b issue an external DVD issue or what. Please advise after reading the terminal output below


allen@ubuntu:~$ wodim -devices
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'SONY' 'CD-RW  CRX830E'
 1  dev='/dev/scd1'	rwrw-- : 'SONY' 'DVD RW DRU-500A'
-------------------------------------------------------------------------
allen@ubuntu:~$ wodim -scanbus
scsibus1:
	1,0,0	100) 'SONY    ' 'CD-RW  CRX830E  ' 'JPK4' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
scsibus2:
	2,0,0	200) 'SONY    ' 'DVD RW DRU-500A ' '2.1a' Removable CD-ROM
	2,1,0	201) *
	2,2,0	202) *
	2,3,0	203) *
	2,4,0	204) *
	2,5,0	205) *
	2,6,0	206) *
	2,7,0	207) *
allen@ubuntu:~$

---

