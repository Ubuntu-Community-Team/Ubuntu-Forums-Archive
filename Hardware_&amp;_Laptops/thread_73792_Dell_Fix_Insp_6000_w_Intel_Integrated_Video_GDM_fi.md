---
title: "Dell Fix: Insp 6000 w/ Intel Integrated Video GDM fix"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by Ab3 on 2005-10-10
I had to set up a Dell inspiron 6000 laptop w/ integrated intel graphics. unfortunately, GDM and X just would not work. Finally, after reading the forums and googling, i managed to get it working - so i am posting the instructions, maybe it will save someone else all the headache it caused me.

-----------------------------------------------------
Getting the GDM to work in DELL inspiron 6000
-------------------------------------------------------------------------
This is compiled from various posts on this forum and others, this config is what did the trick for me. I am posting it here for others who might encounter the same problem, but i can not take credit for coming up with the solution.
-------------------------------------------------------------------------

download: [http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb](http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb)
[http://www.fairlite.demon.co.uk/i810_drv.o](http://www.fairlite.demon.co.uk/i810_drv.o)

run 'dpkg -i 855resolution_0.3-4_i386.deb'
run 'sudo vi /etc/default/855resolution'
add config from modes list

MODE=54
XRESO=1024
YRESO=768

run 'sudo /etc/init.d/855resolution start'

check xorg.conf
run 'sudo vi /etc/X11/xorg.conf'
make sure i810 drive is selected under devices

-Update Driver-

cd /usr/X11R6/lib/modules/drivers/
sudo mv i810_drv.o i810_drv.o.old
copy the downloaded i810 driver in this directory 

restart gdm 
sudo /etc/init.d/gdm restart

You should be getting the GDM gui now. 

-anubhav

---

### Post by Pumpino on 2005-10-13
Or you could download the new BIOS released a couple of days ago.  I just upgraded mine to A09 after installing Kubuntu 5.10, and X still boots fine.

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094)

---

### Post by denvervp on 2005-10-28
[QUOTE=Pumpino]Or you could download the new BIOS released a couple of days ago.  I just upgraded mine to A09 after installing Kubuntu 5.10, and X still boots fine.

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094)[/QUOTE]

Can you play DVD ? By using VESA driver (generic), I boot fine with A05 but cannot watch DVD or play any 3D game.

---

