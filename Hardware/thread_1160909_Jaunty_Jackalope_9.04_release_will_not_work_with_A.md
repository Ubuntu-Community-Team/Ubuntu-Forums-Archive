---
title: "Jaunty Jackalope 9.04 release will not work with AMD 780G SB700 chipset."
date: 2009-05-16
forum: Hardware
---

### Post by X00M on 2009-05-16
After running the install process, during which I had selected "AMD graphics" and after the install completed the system would not boot into Mythbuntu successfully, after the loader screen, everything corrupts and screen goes black.
[B]
It's [/B]Weird, I can boot off the live cd and run the "Try Ubuntu without making any changes to your system" option. This loads it fine and displays the regular desktop a long with Mythbuntu front-end etc.

But as soon as I do a full install it fails to boot into the fresh Ubuntu/Mythbuntu OS install. Declaring some Fatal errors, followed by some image corruption onscreen and freezes like that. Runs Vista just fine though, so it's not a hardware fault.

The freezing starts right after installation, when Install is complete it attempts to restart my system, ejecting my dvd-drive beforehand and freezing at this point with the ubuntu loader/process bar almost complete.

Can't get to the terminal or Dekstop, it simply refuses to work with my mobbo/chipset.

Using the new J&W MINIX 780G mini-itx board.

---

### Post by cozmicharlie on 2009-05-31
I have the same board and also have been experiencing problems with the video drivers.  I have Jaunty installed and it does work.  However, if I activate the restricted hardware (graphics driver) the system will not boot into the desktop (black screen).  When I leave the graphics driver deactivated it works fine.  Apparently from reading on the forums, this is a problem with amd/ati drivers.  Too bad - you might try using the open source drivers not the amd driver.  Hope this helps.

---

### Post by cozmicharlie on 2009-06-03
I think I got it figured out.  make sure you have the latest kernel installed.  In Synaptic (or whatever way you manage packages), go to repository, updates and check the jaunty proposed and backports.  Reload the packages.  Go to System>Administration>Hardware Drivers and activate the driver.  Close and restart.  This should install catalyst (Applications>Accessories) and the proprietary driver.  The first time I started it I got flickering but I simply restarted and all was well.  The drivers appear to work and the video was excellent.  Hope this helps.

---

### Post by gidsmyth on 2009-07-13
[[SIZE=5][COLOR=#000000]X00M[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=831609") , Mythbuntu may be installing fine or may have a (simple?) graphics problem. When you click 'restart' after installing, you said it ejects the disk and then stalls. Try pressing enter. I think it is supposed to pause there so you can remove the disk and allow it to restart without re-entering the install program.
 
You may then find that the rest of the install is ok, or there may be a graphics problem.

---

