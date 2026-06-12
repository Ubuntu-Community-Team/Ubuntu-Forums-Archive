---
title: "MythTV crashed my package managers.  Help?"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by mscyber07 on 2009-04-14
MythTV has crashed all of my package managers.  I can no longer get aptitude, apt-get or Synaptic to work correctly.  The Command Line Output when I try to download and install GParted is as such:

> mscyber07@MyTallest:~$ sudo aptitude install gparted
[sudo] password for mscyber07: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  mythtv-common mythtv-frontend mythtv-theme-blootube 
  mythtv-theme-blootube-osd mythtv-theme-blootube-wide 
  mythtv-theme-blootubelite-wide mythtv-theme-glass-wide 
  mythtv-theme-gray-osd mythtv-theme-isthmus mythtv-theme-iulius 
  mythtv-theme-iulius-osd mythtv-theme-minimalist-wide 
  mythtv-theme-mythbuntu mythtv-theme-mythcenter 
  mythtv-theme-mythcenter-wide mythtv-theme-neon-wide 
  mythtv-theme-projectgrayhem mythtv-theme-projectgrayhem-osd 
  mythtv-theme-projectgrayhem-wide mythtv-theme-retro 
  mythtv-theme-retro-osd mythtv-theme-titivillus 
  mythtv-theme-titivillus-osd 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up mythtv-common (0.21.0+fixes18722-0ubuntu1) ...
cat: /usr/share/mythtv/mysql.txt.dist: No such file or directory
sed: -e expression #1, char 40: unknown option to `s'
dpkg: error processing mythtv-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common (= 0.21.0+fixes18722-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootube:
 mythtv-theme-blootube depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootube (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootube-osd:
 mythtv-theme-blootube-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootube-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootube-wide:
 mythtv-theme-blootube-wide depends on mythtv-common; hNo apport report written because the error message indicates its a followup error from a previous failure.
 No apport report written because the error message indicates its a followup error from a previous failure.
                           No apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
       owever:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootube-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootubelite-wide:
 mythtv-theme-blootubelite-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootubelite-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-glass-wide:
 mythtv-theme-glass-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-glass-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-gray-osd:
 mythtv-theme-gray-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-gray-osd (--configure):
 depNo apport report written because MaxReports is reached already
                                                                  endency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-isthmus:
 mythtv-theme-isthmus depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-isthmus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-iulius:
 mythtv-theme-iulius depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-iulius (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-iulius-osd:
 mythtv-theme-iulius-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-iulius-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-minimalist-wide:
 mythtv-theme-minimalist-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-minimalist-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-projectgrayhem:
 mythtv-theme-projectgrayhem depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-projectgrayhem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-projectgrayhem-wide:
 mythtv-theme-projectgrayhem-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-projectgrayhem-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-mythbuntu:
 mythtv-theme-mythbuntu depends on mythtv-frontend; however:
  Package mythtv-frontend is not configured yet.
 mythtv-theme-mythbuntu depends on mythtv-theme-projectgrayhem; however:
  Package mythtv-theme-projectgrayhem is not configured yet.
 mythtv-theme-mythbuntu depends on mythtv-theme-projectgrayhem-wide; however:
  Package mythtv-theme-projectgrayhem-wide is not configured yet.
dpkg: error processing mythtv-theme-mythbuntu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-mythcenter:
 mythtv-theme-mythcenter depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-mythcenter (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of mythtv-theme-mythcenter-wide:
 mythtv-theme-mythcenter-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-mythcenter-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-neon-wide:
 mythtv-theme-neon-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-neon-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-projectgrayhem-osd:
 mythtv-theme-projectgrayhem-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-projectgrayhem-osd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: dependency problems prevent configuration of mythtv-theme-retro:
 mythtv-theme-retro depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-retro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-retro-osd:
 mythtv-theme-retro-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-retro-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-titivillus:
 mythtv-theme-titivillus depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-titivillus (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: dependency problems prevent configuration of mythtv-theme-titivillus-osd:
 mythtv-theme-titivillus-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-titivillus-osd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mythtv-common
 mythtv-frontend
 mythtv-theme-blootube
 mythtv-theme-blootube-osd
 mythtv-theme-blootube-wide
 mythtv-theme-blootubelite-wide
 mythtv-theme-glass-wide
 mythtv-theme-gray-osd
 mythtv-theme-isthmus
 mythtv-theme-iulius
 mythtv-theme-iulius-osd
 mythtv-theme-minimalist-wide
 mythtv-theme-projectgrayhem
 mythtv-theme-projectgrayhem-wide
 mythtv-theme-mythbuntu
 mythtv-theme-mythcenter
 mythtv-theme-mythcenter-wide
 mythtv-theme-neon-wide
 mythtv-theme-projectgrayhem-osd
 mythtv-theme-retro
 mythtv-theme-retro-osd
 mythtv-theme-titivillus
 mythtv-theme-titivillus-osd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mythtv-common (0.21.0+fixes18722-0ubuntu1) ...
sed: -e expression #1, char 40: unknown option to `s'
cat: /usr/share/mythtv/mysql.txt.dist: No such file or directory
dpkg: error processing mythtv-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv-theme-glass-wide:
 mythtv-theme-glass-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-glass-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-projectgrayhem-osd:
 mythtv-theme-projectgrayhem-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-projectgrayhem-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-iulius-osd:
 mythtv-theme-iulius-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-iulius-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-gray-osd:
 mythtv-theme-gray-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-gray-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootube:
 mythtv-theme-blootube depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootube (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-iulius:
 mythtv-theme-iulius depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-iulius (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootubelite-wide:
 mythtv-theme-blootubelite-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootubelite-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-titivillus-osd:
 mythtv-theme-titivillus-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-titivillus-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootube-osd:
 mythtv-theme-blootube-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootube-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-titivillus:
 mythtv-theme-titivillus depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-titivillus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-projectgrayhem:
 mythtv-theme-projectgrayhem depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-projectgrayhem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-mythcenter-wide:
 mythtv-theme-mythcenter-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-mythcenter-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-mythcenter:
 mythtv-theme-mythcenter depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-mythcenter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-retro-osd:
 mythtv-theme-retro-osd depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-retro-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common (= 0.21.0+fixes18722-0ubuntu1); however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-minimalist-wide:
 mythtv-theme-minimalist-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-minimalist-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-blootube-wide:
 mythtv-theme-blootube-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-blootube-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-retro:
 mythtv-theme-retro depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-retro (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-neon-wide:
 mythtv-theme-neon-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-neon-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-projectgrayhem-wide:
 mythtv-theme-projectgrayhem-wide depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-projectgrayhem-wide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-isthmus:
 mythtv-theme-isthmus depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-theme-isthmus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-theme-mythbuntu:
 mythtv-theme-mythbuntu depends on mythtv-frontend; however:
  Package mythtv-frontend is not configured yet.
 mythtv-theme-mythbuntu depends on mythtv-theme-projectgrayhem; however:
  Package mythtv-theme-projectgrayhem is not configured yet.
 mythtv-theme-mythbuntu depends on mythtv-theme-projectgrayhem-wide; however:
  Package mythtv-theme-projectgrayhem-wide is not configured yet.
dpkg: error processing mythtv-theme-mythbuntu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-common
 mythtv-theme-glass-wide
 mythtv-theme-projectgrayhem-osd
 mythtv-theme-iulius-osd
 mythtv-theme-gray-osd
 mythtv-theme-blootube
 mythtv-theme-iulius
 mythtv-theme-blootubelite-wide
 mythtv-theme-titivillus-osd
 mythtv-theme-blootube-osd
 mythtv-theme-titivillus
 mythtv-theme-projectgrayhem
 mythtv-theme-mythcenter-wide
 mythtv-theme-mythcenter
 mythtv-theme-retro-osd
 mythtv-frontend
 mythtv-theme-minimalist-wide
 mythtv-theme-blootube-wide
 mythtv-theme-retro
 mythtv-theme-neon-wide
 mythtv-theme-projectgrayhem-wide
 mythtv-theme-isthmus
 mythtv-theme-mythbuntu
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

I very well could have simply missed a similar article, and I'm thinking it might be worth my time to just wait until Ubuntu 9.04 is released.  Thoughts?

            Thanks,
                 mscyber07

---

### Post by mscyber07 on 2009-04-15
Update:  now my update manager isn't functioning correctly either.  a similar error message displays when it crashes.

---

### Post by mscyber07 on 2009-04-20
Problem solved.  Sorry to waste nobody's time, but all I needed to do was purge the broken packages.

I used:
> sudo dpkg -P #insert broken package names here#

Now everything works great.

---

