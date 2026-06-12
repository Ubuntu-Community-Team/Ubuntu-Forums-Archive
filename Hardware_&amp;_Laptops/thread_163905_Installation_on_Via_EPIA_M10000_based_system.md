---
title: "Installation on Via EPIA M10000 based system"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by Michael Grabbe on 2006-04-21
I "lost" my Mini-Q system, which ran Ubuntu 5.04 quite nicely, due to a failure of the Jetaway 650DF motherboard, so I have built a new system based on the VIA EPIA M10000 (Nehemiah) motherboard.  This motherboard uses a CLE266 Northbridge chip with integrated Unichrome graphics. This is a Mini-ITX motherboard. When I tried to load Ubuntu V 5.10 all I could see on the screen was a mess that looked like severe sync missmatch. So at the moment I am running Mandriva Free - this required a bit of trial and error choosing a driver to work with this system, but I was able to get it to work. Has anyone been able to sucessfuly load Ubuntu on this series of VIA motherboard and if so, how were you able to get it to work? Any information would be appreciated. Thanks.

---

### Post by Bonifacius on 2006-04-29
Try this:
boot: linux debian-installer/framebuffer=false

Bonifacius

---

### Post by Michael Grabbe on 2006-05-06
Thanks for the tip. My experience with Linux has been to throw in the CD and  let it go install. I assume the command is from a blank screen, or should I do this from the command line with the current distro runnnig and the Ubuntu CD in the drive?

---

### Post by ElectusUnum on 2006-06-06
In the bios settings you need to switch the display from "CRT+TV" to plain "CRT"

This should resolve all the issues, and passing framebuffer=false won't be needed.  But be advised, the Server install of dapper doesn't seem to be working with the EPIA boards.

---

### Post by Quartus on 2006-06-17
[QUOTE=ElectusUnum]But be advised, the Server install of dapper doesn't seem to be working with the EPIA boards.[/QUOTE]
Someone that knows more about this? I'm considering buying an EPIA board and would like to know if there is any problem related to them when installing Ubuntu.

---

### Post by Nunzio on 2006-06-19
If it doesnt work with a Server Install cd, will it work with a Xubuntu install cd?

Will test tonight and let people know.

---

### Post by s_g_robertson on 2006-06-19
[QUOTE=Quartus]Someone that knows more about this? I'm considering buying an EPIA board and would like to know if there is any problem related to them when installing Ubuntu.[/QUOTE]
I've got 6.06 running on an M10000 board.  I'm pretty much a linux novice and I got it going using the Live CD install no problem. 

 I only have one outstanding issue and that is the the TV-out(composite)occasionaly "disappears".  If I connect using VNC everything is still running ok.  If I then change the screen resolution then the TV output reappears.  Even if I select to keep the previous resolution the tv output remains on. 

BTW I'm using this mainly as a MythTV box, but as far as I can tell it's not connected to Myth, but I may be wrong!!

---

### Post by markba on 2006-06-25
[QUOTE=Quartus]Someone that knows more about this? I'm considering buying an EPIA board and would like to know if there is any problem related to them when installing Ubuntu.[/QUOTE]
See my post on this thread:
[http://ubuntuforums.org/showthread.php?p=1179363#post1179363](http://ubuntuforums.org/showthread.php?p=1179363#post1179363)
Bottom line: this issue can be solved, either by installing 5.10 and upgrading to 6.06 or by using another install-iso (though I have not tried the last solution).

---

