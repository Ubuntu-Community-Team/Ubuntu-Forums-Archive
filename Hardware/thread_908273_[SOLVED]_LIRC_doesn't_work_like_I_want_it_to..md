---
title: "[SOLVED] LIRC doesn't work like I want it to."
date: 2008-09-02
forum: Hardware
---

### Post by Machtin on 2008-09-02
Hey guys!

I got an Asus P5W DH Deluxe mobo which ships with an IR-remote.. now i'd like to use that one - but I don't really get it working.

I downloaded the lirc file and chose the Asus-remote in the setup. Then i created several files (which i have from here: 
[http://www.hentges.net/misc/howtos/p5wdh/p5w_remote.shtml](http://www.hentges.net/misc/howtos/p5wdh/p5w_remote.shtml))

Then i installed IRkick (found it via aptitude.. called "kdelirc")
When i now run lircd it gives the following output:

lircd: WARNING: invalid code found for aaaaaaa: SUSPEND


However, when I do "cat /dev/usb/hiddev0" as root and press some buttons on the remote it does show some strange chars.. but that's the only effect.. these commands are not interpreted to do what they should.

Could someone help me to solve that one, please?

edit: managed it via reinstall and some things i can't remember.

---

