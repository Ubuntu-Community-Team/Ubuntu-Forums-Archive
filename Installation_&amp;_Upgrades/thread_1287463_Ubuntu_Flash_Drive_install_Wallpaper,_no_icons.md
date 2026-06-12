---
title: "Ubuntu Flash Drive install: Wallpaper, no icons"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by corysnyder28 on 2009-10-10
Hi everybody,
   I'm trying to create a persistent USB Flash-drive installation of Ubuntu 9.04 and having a strange problem.


I've used two methods -- Ubuntu's USB Startup Disk Creator AND uNetboot-Linux -- and had the same issue. After installing from an iso file (ubuntu-9.04-desktop-i386.iso) unto my Flash drive, I boot into Ubuntu and I see only a wallpaper.I have a mouse cursor, but no icons or top/bottom toolbar. 

Is this a monitor resolution issue? Is it to do with the .iso I'm using? I'm baffled!

That's my first question. My second question -- is Ubuntu's USB Startup Disk Creator my best bet for creating this USB install? I want persistence, and I want to be able to boot into the OS from the Flash drive.

Thanks very much for your help,
 CS

---

### Post by Meow27 on 2009-10-10
yes the ubuntu built- in version is the oen you want, just make sure that you make the paging file big enough for your own needs.

does the liveCD of the image not work as well? did you try downloading it again?

---

### Post by corysnyder28 on 2009-10-10
Thanks for the note.

I just used Sun VirtualBox to run the ISO I downloaded of Ubuntu 9.04 and...had the same issue! Within the virtual machine. So I'm guessing the issue is with the ISO I downloaded -- can this be possible (i.e., a distro that would include any sort of UI beyond the desktop)?

I'm using UNetbootin to download the ISO again and re-install. Think this is my best bet?

Thanks,
  CS

---

### Post by Meow27 on 2009-10-10
yeah, if virtualbox is having problems with that, its the iso. 

it could be a problem with the ISP on your end or thiers

unetbootin works... the built-in one for ubuntu works better (though you dont have access to it)

---

