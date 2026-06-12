---
title: "[SOLVED] PTP filesystem driver found - needs improvement"
date: 2008-06-11
forum: Hardware
---

### Post by summersab on 2008-06-11
This is mainly to all of the coders out there. I know how to write in C++ and  such to a certain degree, but I think this might be out of my ballpark since I don't know enough kernel details.

A lot of people are frustrated in Ubuntu that when you plug in a camera that only supports PTP and not MTP (most new Canon cameras) that they can only transfer pictures using a host program such as gThumb or Picasa - there is no way to mount the camera as a mass storage device and drag/drop photos off of the camera using a graphical file browser (Nautilus, Konqueror, etc). This is a serious drawback, and users have to purchase card readers or use Windows to get their photos off. Completely NOT ideal.

Today while looking for a solution, I came across a partial one at the following url: [http://www.dankulp.com/ptpfs/](http://www.dankulp.com/ptpfs/) - it is essentially the basics for solving the problem described above. However, there are some fairly major issues with this driver as described on the website. Also, it was made for a 2.4 kernel, and I, as someone who is still cutting teeth, cannot seem to get it to install.

Is there anyone willing to help with this project? Is there any way to get this post into the right hands so that the project will be adopted into Ubuntu? This is one of the small pieces that will help Ubuntu to be taken more seriously as a viable option. Can we make this happen?

---

### Post by pingpongboss on 2008-06-28
Another way to mount PTP cameras is to use gphotofs. It is too cumbersome though.

+1 for better PTP support.

---

### Post by summersab on 2008-07-03
Solved. I found out about gphotofs and it is great. It's a little buggy at times, but it let me get to my pictures. Check out this link to figure out how to install it:

[http://gentoo-wiki.com/Gphoto2#Automount_with_gphotofs_and_autofs](http://gentoo-wiki.com/Gphoto2#Automount_with_gphotofs_and_autofs)

Now, when the command says "emerge," it is Gentoo code for "apt-get install." Also, the files for autofs are not in the folders shown. I think they are just in /etc. That, and they are named differently. It's pretty easy to figure out what they meant by context, though.

Give it a whirl, PTP stuck camera owners!

---

