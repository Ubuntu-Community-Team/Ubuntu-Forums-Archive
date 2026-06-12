---
title: "software raid 0 on brand new seagates 500 gb"
date: 2008-08-03
forum: General Help
---

### Post by brw02005 on 2008-08-03
Well am setting up a computer just for spead.  First thing I did was set up a 250 mb boot partition on first hard drive because without that the system wouldn't even boot.  I then created three raid drives a 46 gig section for root a 10 gig section for swap and a 868 gig section for home.  I became curious when I copied music one the home drive  from one folder to another and hardy rated it at 44 MB/s.  I then ran bonnie and got the following outputs.

Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
3po              6G 44154  96 138415  55 63486  19 52127  97 193807  23 311.3   1
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
3po,6G,44154,96,138415,55,63486,19,52127,97,193807,23,311.3,1,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

This means my system will only do 43 MB/s under putc() macro invocations but with efficient block writes will do 135 MB/s.   I just looking for some advice as to why this is.  This system is noticeably faster though so I probably shouldn't care.  Just looking to get the most out of my hardware.

---

### Post by fjgaude on 2008-08-05
If the controller for the drives is running off the PCI bus and not PCI-E then your speed is limited to about 115MB/sec because of bus I/O. If not, then likely the CPU and memory may be an issue.

What's your hardware?

---

