---
title: "Remounting External Hardrive"
date: 2008-10-07
forum: Hardware
---

### Post by Insomnautik on 2008-10-07
I have an external 500gig which i have mounted to home/Videos on start up. If the hard drive is somehow disconnected or, more annoying, a cell phone rings next to it an it spins down for a sec.. it will unmount itself from its location and remount as just a 500gig external. Is there any way to have it automatically remount its self back into the home/Videos folder in case of accidental disconnect.

---

### Post by jerome1232 on 2008-10-07
That's odd, mounting is usually based on the label on the drive, if there is no label it uses the size of the partition. Does simply unmounting, disconnecting, wait a few seconds then reconnecting it get the job done?

---

### Post by Insomnautik on 2008-10-07
I did what you said, but it did not mount it self automaticly.. although I was able to remount it to home/Videos through the terminal

is there a way to create a file which I could click on that runs certain commands (kind of like a .bat file in windows)?

---

### Post by jerome1232 on 2008-10-07
Well yeah you can create a script just pop open gedit or vim and start it off with the shebang, after that you can write terminal commands line by line.
```

#!/bin/bash
```

---

### Post by Insomnautik on 2008-10-07
alright, thanks for the help.

for the sake of checking... is there any way to make this process easier?

right now, if my hardrive spins down and comes back up mounted wrong, I have to do this.

sudo umount /dev/sdd5
sudo umount /home/Videos

Then I have to turn off and turn back on the hardrive and...

sudo mount /home/Videos

is there a way to do that without having to turn off the hardrive?

---

