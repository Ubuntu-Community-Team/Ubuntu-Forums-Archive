---
title: "invalid mount message"
date: 2008-07-23
forum: Hardware
---

### Post by eyes_of_set on 2008-07-23
I own an acer aspire 5720z notebook that i converted from vista to xp. i had some issues recently and a virus made it crash where i couldnt boot to windows so i decided to give ubuntu a whirl yesterday.
So far everything works fine except ( and this is a big except) none of my external hard drives will work on this computer.
"invalid mount option when attempting to mount the volume "724" "
ive opened my hard drive on other linux based systems on friends computers with no issues at all.
what can i do without formatting my hard drives? i cant lose all my stuff and i cant access it now which really sucks.
much gracias
The Logan

---

### Post by ilrudie on 2008-07-23
Make sure your user is in the plugdev group.  If that does not work when do you receive the error?  When you plug it in?  When you try to navigate to it?  When you attempt to mount from the command line?  The error to me sounds like its getting a very funky umask or permissions but I'm not really sure why that would happen.  Have you made any modifications to your base install that might mess this up?  What version of the os are you running?  Also check for any messages that seem important in the logs (System>Administration>System Logs) and post them if they seem relevent.

---

### Post by eyes_of_set on 2008-07-23
went into admin and looked for "plugdev" and couldnt find it. what happend is i just straight up plug the hard drive in and it doesnt recognize it. as far as i know this is not an altered version of ubuntu. ill ask the guy who installed it and find out.

---

### Post by eyes_of_set on 2008-07-23
actually he installed eeebuntu .he also says this is probably what caused the error. any advice where to go from here?

---

### Post by ilrudie on 2008-07-23
Install a standard version of Ubuntu?  I'm not familiar with that distribution.  I really don't know what they changed when they made it.  The plugdev group controls who can use USB devices.

You can try mounting the drive as root to see if maybe its just not auto-mounting properly.  Type 'man mount' in the console to learn about mounting drives.

---

### Post by dl7und on 2008-08-31
Don't know if this has already been solved. If not, the solution is to comment out the /dev/cdrom line in /etc/fstab...

---

