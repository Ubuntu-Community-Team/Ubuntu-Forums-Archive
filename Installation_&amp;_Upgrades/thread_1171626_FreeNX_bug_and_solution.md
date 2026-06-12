---
title: "FreeNX bug and solution"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by marstonstudio on 2009-05-27
Here's something I ran into while installing FreeNX on Jaunty and a quick solution. Following the instructions here:  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

apt would fail to fully configure nxserver and would throw error messages whenever i did anything using apt

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up freenx-server (0.7.3+teambzr104-0freenxteam1) ...
chown: invalid group: `nx:nx'
dpkg: error processing freenx-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of freenx-rdp:
 freenx-rdp depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-rdp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx-media:
 freenx-media depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx:
 freenx depends on freenx-server; however:
  Package freenx-server is not configured yet.
 freenx depends on freenx-media; however:
  Package freenx-media is not configured yet.
 freenx depends on freenx-rdp; however:
  Package freenx-rdp is not configured yet.
dpkg: error processing freenx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx-vnc:
 freenx-vnc depends on frNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                     No apport report written because MaxReports is reached already
                                                                                   No apport report written because MaxReports is reached already
                                                                                                                                                 eenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-vnc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 freenx-server
 freenx-rdp
 freenx-media
 freenx
 freenx-vnc
E: Sub-process /usr/bin/dpkg returned an error code (1)






The solution?  

groupadd nx
apt-get upgrade 

and everything is hunk dory again

---

### Post by ricojonah on 2009-10-14
Thanks for this info. I was having the same issue--this fixed it for me!

---

