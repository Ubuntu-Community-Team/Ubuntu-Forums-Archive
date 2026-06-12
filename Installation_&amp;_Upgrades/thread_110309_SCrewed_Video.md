---
title: "SCrewed Video"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by ThePerg on 2005-12-30
OK, I have made a mistake that I cannot seem to fix, I changed the video from 800x600 to 1024x768 now I get a black screen with purplish like scrible representing logon screen, mouse is all screwed up.. 

so i boot into recovery mode.. what file do i need to fix?

---

### Post by DoorGunner on 2005-12-30
su 
passwd

nano -w /etc/X11/xorg.conf

go down and edit 1024x768 back to 800x600

I suspect that you have a video card and no drivers installed?:D

---

### Post by ThePerg on 2005-12-30
[QUOTE=DoorGunner]su 
passwd

nano -w /etc/X11/xorg.conf

go down and edit 1024x768 back to 800x600

I suspect that you have a video card and no drivers installed?:D[/QUOTE]


well I looked at that file it has like 6 subsections of display depths 1,4,8,15,16,24 each one of them has 1024x768  800x600  600x400
the display depth is set for subsection depth 24 i have modified this for 1024x768 and 800x600 only.. still no change.

---

### Post by ThePerg on 2005-12-30
[QUOTE=ThePerg]well I looked at that file it has like 6 subsections of display depths 1,4,8,15,16,24 each one of them has 1024x768  800x600  600x400
the display depth is set for subsection depth 24 i have modified this for 1024x768 and 800x600 only.. still no change.[/QUOTE]

Here is screen shots of that file.

---

### Post by ThePerg on 2005-12-30
I got it.. I changed the "Section Device" .. "Driver" entry from s3 to vesa and left it 800x600 saved and rebooting.. going to try to step it up to 1024x768

---

