---
title: "dpkg error"
date: 2005-12-04
forum: General Help
---

### Post by yohan on 2005-12-04
I installed fuse-utils then removed it because I realized I dont need it...I installed it with apt-get install and nothing seemed odd when i removed it. 

Just now i tried to install xboard and i get this error:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  xaw3dg
Suggested packages:
  gnuchess crafty phalanx
The following NEW packages will be installed:
  xaw3dg xboard
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/537kB of archives.
After unpacking 2163kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
dpkg: syntax error: unknown group `fuse' in statusoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)   

What does that mean? Is there anything Ive done wrong? Im not really sure on how dpkg works...

thanks!

---

### Post by teaker1s on 2005-12-04
try removing with synaptic if it fails then check synaptic help and limitations

---

