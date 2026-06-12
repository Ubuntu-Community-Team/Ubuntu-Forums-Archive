---
title: "xserver test config"
date: 2008-08-29
forum: General Help
---

### Post by bfuzze on 2008-08-29
Does xserver (Gnome) have a test config mode/option comparable to apachectl configtest?

I'm recently installed U 8.04 x86_64.  The install went smoothly, but then I started adding programs and messing with network configurations and now U freezes after the graphical login.  
I tried using the Recovery mode at boot:
   dpkg - repair broken packages
   xfix - fix xserver
No change.

I need to be able to see where during the xserver init is hanging.
The last things I did before I encountered the init problem:
   Installed vmware 1.0.6 (i386)
   Installed Centos 4.6 (i386) virtually
   Network configuration

The problem is most likely with vmware, but it is at least conceivably related to a networking conflict of some kind because I'm trying to give the Centos instance static ips on a host with both DHCP and/or static connection.  

Any help would be appreciated.

My background:
I recently transitioned from Windows platform, so my experience with Ubuntu and Linux in general is limited, but I have fully committed for the last couple of months so I'm not completely raw (I've rebuilt this machine 4 times in the last month or so, 2 more installs and dual boot at home). In addition, my background is PHP web development and am trying to climb the ladder into web server administration so my networking skills are akin to a toddler driving a stick shift, meaning: small words, step-by-step instructions please 8-[ . Don't assume I know anything, I won't take offense.

TIA

---

