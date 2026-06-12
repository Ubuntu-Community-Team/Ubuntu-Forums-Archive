---
title: "How do I detect a user from script run as root?"
date: 2008-10-28
forum: General Help
---

### Post by foldor on 2008-10-28
I am creating a script that will be run by root. Not through a sudo command. I want it too copy files to the users home directory but I have no idea how. The environment variables all point to root as the user. These scripts are run from a .deb file if that matters.

I guess if someone could find a way to get the .deb file to install files to the users home directory that would work as well.

---

### Post by Portmanteaufu on 2008-10-28
If you're just going to put the files into *every* user's home folder, you could just do:
```

ls -1 /home

```
And loop through the folders listed. Note that that's a one, not a lower case L. Or, if you wanted to just get a listing of all users using bash or sh as their shell, you could do something like: 
```

cat /etc/passwd | grep -P '/bin/(?:ba)sh' | perl -e '@lines=<STDIN>;foreach $line (@lines){@line_items = split(/:/,$line); print $line_items[0]."\n";}'

```
Then you could just dump it into their respective folders.

---

### Post by bodhi.zazen on 2008-10-28
Or if it is going to a single user, just export the new home b4 you run the script.

export HOME='/home/user'

then run the script.

---

### Post by foldor on 2008-10-30
Thanks for the help. I ended up using this script to install all files to each users home directory.

```

#!/bin/sh
for i in `ls /home`; 
do 
  file /home/$i | cp -R /foo /home/$i;
done

```

---

