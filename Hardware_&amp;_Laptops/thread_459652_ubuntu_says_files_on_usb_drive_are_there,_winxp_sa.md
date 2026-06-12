---
title: "ubuntu says files on usb drive are there, winxp says its not"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by ghmercado on 2007-05-30
hi. I have no problems getting my [Kingston 1gb USB]("http://www.kingston.com/flash/dt_mf.asp") drive from getting detected my xubuntu 7.04 laptop.

And when i copy it:

[INDENT]cp /home/Desktop/name_of_file.doc /media/KINGSTON[/INDENT]

it says it's there. I then pull it out, take it to a Windows XP PC and it's empty!

I take the usb drive back to my xubuntu machine again, and true enough, it's empty. I try cut and pasting again and again, I take it to my Win machine, it's not there again!

I tried **umount**ing the drive before I removed it, and it worked. But do I have to do that each time I need to pull it out? How can I be sure a file is in my USB drive if xubuntu says it's really there? ](*,)

---

### Post by ryanVickers on 2007-05-30
> I tried umounting the drive before I removed it, and it worked. But do I have to do that each time I need to pull it out?
Um, yeah, that's kind of important :p :lolflag:

You can be sure it's there because if it shows up and is the same file size as the source.

~ Of course, on windows, you can't really be sure any of your files are there ~ 0_o
I wouldn't trust a micro$oft file system if my life depended on it!

there is an easier way though, on the desktop icon it makes for the drive, right click it and pick unmount/eject and that can save you trouble of commands.  The reason for this is that it may still be copying thigs to it.

---

### Post by ghmercado on 2007-05-30
well im glad you found it amusing, ryanvickers. Thanks a lot though.

---

