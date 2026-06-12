---
title: "External drives changes permission by themselves!!!"
date: 2008-10-16
forum: General Help
---

### Post by hananias on 2008-10-16
Every external drive I have (3 different ones)  all got changed to read only permission by themselves after I just plug them in ubuntu.  What's da deal?  In os x (macbook) they plug in fine, and I can read and write!  

Actually one of them work after I reinstall ubuntu...but after the second time (after second boot)  again the permission change, making this impossible to back up ubuntu!
so it's very important for me to fix this.

I did try to change the permission in os x, which works, but as soon as I plug em in ubuntu it changes.

---

### Post by penguinpi.com on 2008-10-16
This has happened to me before with flash drives. Did you format it with ext3? Try this: after Ubuntu auto mounts the drive unmount it and mount in manually from the Command Line as root then do a chmod -R 777 or something to the whole drive.

---

### Post by hananias on 2008-10-17
thanks for the reply!  But I'm such a noob :confused: I need more detail instructions what to do...sorry...I went to terminal as root...and then what?  I tried going to the 'media' or 'mnt'...I don't know how to mount a drive from the terminal.  
I don't know if this is the same thing, but I've tried to change the permission via 'gtksu (something like that) nautilus' and change it there...still nothing happens!

---

### Post by hananias on 2008-10-17
Well, I think I was able to try to mount the external drive via terminal, but I get the error that
 'mount: mount point /media/UNTITLED does not exist'
Any clues???  this is such a mystery...I never had any permission problems before the upgrade.  I'm thinking of going back to Hardy...there some features I like in intrepid, but it's still too buggy. Well, if my option is to revert to Hardy, then I'll loose a lot of new files!!!
I'm stuck between the sword and the wall...

---

