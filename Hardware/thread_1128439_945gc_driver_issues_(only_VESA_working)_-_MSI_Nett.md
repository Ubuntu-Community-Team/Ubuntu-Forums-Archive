---
title: "945gc driver issues (only VESA working) - MSI Nettop 100 w/ Intel Atom 330"
date: 2009-04-17
forum: Hardware
---

### Post by number1pete on 2009-04-17
I have put together a MSI nettop 100 build.  I am running Ubuntu 8.10.  The problem is that non of the intel display drivers work on this system.  

The MSI nettop 100 barebone is running a intel 945GC chipset.  I have tried the intel, i810, and 915resolution based drivers and nothing works. It always says no displays found when loading Ubuntu then reverts to the VESA driver.  

I have a feeling that the 945GC does not get along with the previous intel drivers made for all the other versions of the 945 chipset.  This is an Atom 330 based barebone so the 945GC chipset is slightly different then most 945chipsets that have been used with Ubuntu before.

I have tried new drivers from intel's website but nothing specifically says it supports the GC variant of the 945 chipset.  Also I think i read somewhere that someone tried Ubuntu 9.04 with no luck.

Basically I need an expert to reply to this becaseu i have tried most of the basic to moderate steps.  

Thanks for the help guys.

Here is a link to a video of my build:
[http://www.l337tech.com/how_to_videos/how_to_build_nettop_100_msi_wind_pc_an_intel_atom_barebone_build/]("http://www.l337tech.com/how_to_videos/how_to_build_nettop_100_msi_wind_pc_an_intel_atom_barebone_build/")

---

### Post by qIsFree on 2009-05-05
I too have the nettop 100.
 First, I upgraded to ubuntu 9.04.

 Then I fixed it by editing xorg.conf (sudo gedit /etc/X11/xorg.conf) and adding in the intel driver like this:
 

  make this section:
  Section "Device"
        Identifier "Configured Video Device"
EndSection
 

  read like this:
 

  Section "Device"
            Identifier "Configured Video Device"
         Driver "intel"
EndSection
 
If you have a line in that section that reads> Driver "vesa" 
   put a # in front of it.

Then save and reboot.

(thanks to Guy Smith on launchpad.net for the pointer)
I also talked to the guys on intel's Linux driver IRC chan, and they confirmed accelerated support for our chipset as of rhel4 (a ways back). :smile:

cheers.

---

### Post by number1pete on 2009-05-05
okay i just updated to jaunty (9.04) and then wrote in "intel" into my xorg.conf file (like i have done before many times) and again it fails to work and reverts back to the vesa driver.  The error i consistently get with the "intel" driver is something like "found screen but no valid modes detected".   

At this point i have basically given up and just use the vesa drivers.  But if there is a pro out there that may know how to fix this, please respond.

thanks,

---

### Post by webbsm on 2009-07-14
Did you - or has anyone else - had any luck getting this to work? 
 
I've got the same problem - only vesa appears to work and I can't select the appropriate resolutions for my monitor.....

---

### Post by number1pete on 2009-07-21
tried every driver ever made for intel graphics.  Even the new ones that have come out recently.  No matter what i do i always get the "found monitor but no known modes" error or something like that.  Then it reverts to vesa.  I have even tried writing my own modes and that did not work either.  What we need is somebody that is really good at writting modes in xorg.conf file and share that file with us.

so basically no progress has been made.

---

