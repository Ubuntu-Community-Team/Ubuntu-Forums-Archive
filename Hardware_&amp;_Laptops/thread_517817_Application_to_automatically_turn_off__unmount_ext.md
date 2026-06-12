---
title: "Application to automatically turn off / unmount external hard drive?"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by tak1150 on 2007-08-05
Does anybody know of an application that can automatically turn off / unmount (thereby turning off) an external hard drive? I want something to turn off the external HD after certain amount of time of idling so that it does not wear out. I also want the same app to turn it on (or mount it) when I call for the stuff on it via ssh.

I realize I can just have an entry in fstab and do "sudo mount -a" and "sudo umount /dev/xxx"
but I am curious to find such an app, because when I used to use Windows XP, there was such an application that came with the external HD.

---

### Post by tak1150 on 2007-08-08
After this post I realized that unmounting the external HD does not turn it off. So I really need a solution like the software I mentioned above. Help!

---

### Post by racyrefinedraj on 2007-08-09
I really don't think that you have anything to worry about as far as wearing out your hard drive goes. Is the hard drive spinning while the computer is idle? Having it sit there plugged in won't cause anything to wear out any quicker.

---

### Post by tak1150 on 2007-08-09
Thanks for the reply.
Yes. I can feel the vibration and hear the spinning sound even when the computer is idle.

---

### Post by hoboken on 2008-06-09
Well, I know this comes nearly a year late but this is how I did it: 

1. Create a file named eject.sh with the following contents:

#!/bin/bash
exec 2>&1
pumount $1 || umount $1
sdparm --command=sync $1
sdparm --command=stop $1

2. copy it into root folder

cd Desktop
sudo cp ~/Desktop/eject.sh /eject.sh

3. Create a launcher, which you can either dump on you desktop or have as an option in your main menu. When clicked, your drive will eject and turn off:

Option: run in terminal
command: sudo /./eject.sh /dev/sd* (mountpoint of your drive)




There, lovely. Curiously enough in xubuntu my disk was switched off automatically after unmounting the regular way. I wonder how the devs did it?

---

