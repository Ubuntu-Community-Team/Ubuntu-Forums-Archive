---
title: "hp tx2 1050el:  reversed mouse"
date: 2010-08-12
forum: Hardware
---

### Post by Francesco1980 on 2010-08-12
Hello:)

I have installed Lynx on hp tx2 1050el. All ok, but after the rotation screen, mouse is reversed
I use Ati radeon graphics and  fglrx  ...  I tried to enter the string: aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"


This is the output: 
root@francesco-laptop:~# aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE" 
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.


What could I do to fix this problem?

---

