---
title: "keyboard repeat issue"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by f-bomb on 2006-06-01
I've been running the flights and beta on my test machine with no problems.  Did a final sudo apt-get dist-upgrade this morning, then restarted the box.  Now when GDM comes up, the keyboard now randomly repeats characters in the username and password fields, making it impossible to login.  I've swapped out a couple of different keyboards as well with no luck.  The box is an old HP Pavillion 6640C with the stock HP keyboard.  I've run into this before, but usually not until after I login and am on the desktop.

I"ve tried sshing in and changing the repeat and rate settings in /etc/gconf/gconf.xml.defaults/schemas/desktop/gnome/peripherals/keyboard/%gconf.xml with no luck....

ctrl-alt-f1 to a virt terminal does not exhibit this problem.

any ideas?

---

### Post by f-bomb on 2006-06-01
I've looked at all the other "keyboard repeat" threads in here, but none of those soultions seem to work.......

I can't be the only one who's having this problem....

---

### Post by f-bomb on 2006-06-01
ok, after a couple of reboots, its not happening anymore......

very strange

---

### Post by BrianT on 2006-10-09
I am glad to here your reboot worked.  I have had the same problem with Ubuntu 6.06 and Xandros 4.0 both.  It doesn't matter what setting I use for repeat, etc.  Every once in a while Xandros would have a normal keyboard behavior.  I have yet to get Ubuntu to work via a reboot.

Is there anyone who has a good understanding of the keyboard drivers out there?

UPDATE: For my hardware, the [solution by tseliot]("http://www.ubuntuforums.org/showthread.php?t=75281") worked great!  No more keyboard repeat problems.  For me option 2 in the 32bit section worked.

Now I am on to bigger fish...

---

