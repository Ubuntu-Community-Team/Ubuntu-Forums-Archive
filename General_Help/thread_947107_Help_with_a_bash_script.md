---
title: "Help with a bash script"
date: 2008-10-14
forum: General Help
---

### Post by sauce345 on 2008-10-14
I wrote a bash script to mount a bunch of media shares that i have on a windows system.  I have 1 problem that i would like to overcome.  The script uses the sudo command and so obviously requires a password to continue, because i have like 6 sudo commands in a row.  Any here is the script:

#!/bin/sh
sudo mount.cifs //192.168.1.101/Movies /mnt/Movies cifs user=root
sudo mount.cifs //192.168.1.101/"High Def Movies" /mnt/HighDefMovies cifs user=root
sudo mount.cifs //192.168.1.101/"TV Shows" /mnt/"TV Shows" cifs user=root
sudo mount.cifs //192.168.1.101/Music /mnt/"Music" cifs user=root

It is also weird because it asks for a password from the user then the root?  But anyway how do get it so that it doesn't ask me to type a password after every line?

Also any other types to making it more efficient/better?  I have only written simple scripts that just execute consecutive commands.

I wish i didn't even have to do this, but i could not get the samba stuff working properly to see the share in Nautulis.  I can browse and see the computer with the shares fine, but none of the shares show up.

Thank you in advance.

---

### Post by Saint Angeles on 2008-10-14
try removing those sudos

i just made script that uses apt get and i didnt use sudo in it once. when i run it, it asks me for sudo once then im set for the other 4 commands:

[http://ubuntuforums.org/showthread.php?t=943131&]("http://ubuntuforums.org/showthread.php?t=943131&highlight=all4")

---

