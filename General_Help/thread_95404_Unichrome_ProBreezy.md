---
title: "Unichrome Pro/Breezy"
date: 2005-11-26
forum: General Help
---

### Post by at_a_loss on 2005-11-26
Hi Everyone,

Anyone know how to get my Unichrome Pro video card working in Breezy?  I have an averatec 3715.

I've seen explanations on how to build the drivers in hoary, but I can't seem to get that to work for Breezy.  Any suggestions would be appreciated!

---

### Post by ivor on 2005-11-28
Hi,
Initial breezy debs can be found at: [http://www.openchrome.org](http://www.openchrome.org)

---

### Post by at_a_loss on 2005-12-02
Hey Thanks!  Any chance you could give slightly more detailed install instructions?

Seems like I should just download those three files?  Do I just use dpkg to install the .deb files?

Should I manually replace the xserver-xorg and the libxvmc packages, or will that happen automatically?

Thanks in advance!!

---

### Post by xmorg on 2005-12-14
[QUOTE=ivor]Hi,
Initial breezy debs can be found at: [http://www.openchrome.org](http://www.openchrome.org)[/QUOTE]

I couldnt get these to work.  Basicly the screened turned sort of "Chromish" then hung.  I found on the openchrome.org site that the  Averatec 3715 was added on the 18th, and teh packages were released on the 16th.  I didnt want to mess with source

I found a way to get driver support from the via Arena.

Download this package from the suse drivers
cn-cle-pmxf40056-kernel-bin-suse9.1_20050124.tgz

Untar it
tar -xzvf cn-cle-pmxf40056-kernel-bin-suse9.1_20050124.tgz

Because you aren't using SUSE, the install script will not work.  You will have to copy the files manually.

Most important:
sudo cp CN-CLE-PMXF40056-kernel-bin-SuSE9.1_20050124/CN-CLE-PMXF40056-kernel/SuSE/9.1/pentium/XServer/via_drv.o/ /usr/X11R6/lib/modules/drivers/  (you will be overwriting the current via_drv.o

Follow the other paths and copy the files as the script would (make backups if you are scared)

The kernel device doesnt work, but thats ok.
When you restart X you will be in a minimum Resolution.  You can fix this by adding refresh rates to your xorg.conf file.
$  vi /etc/X11/xorg.conf
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30.0 - 60.0
        VertRefresh     50.0 - 75.0
EndSection

Now X starts with MAX resolution and you should be able to play videos at a normal speed.  GL also seems to work (at least better than in VESA lol)

something else, 
you will also have to install the files in the DRI folder....

---

