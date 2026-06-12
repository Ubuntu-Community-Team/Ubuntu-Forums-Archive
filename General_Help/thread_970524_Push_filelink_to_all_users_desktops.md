---
title: "Push file/link to all users desktops"
date: 2008-11-04
forum: General Help
---

### Post by jodgi on 2008-11-04
Does anyone know of a quick and easy way to push a file/link to the desktop of all users?

I'm not creative enough with the command line to figure it out.

---

### Post by jodgi on 2008-11-07
*bump*

Any bash jedi-tricks out there?

---

### Post by scragar on 2008-11-07
```
cd /home
sudo -i
for X in `ls`; do
  cd $X
  **WHAT YOU WANT TO DO HERE**
  cd ..
done
```
I'll want to more about what you want to do to offer any more advice.

---

### Post by geirha on 2008-11-07
When you create a new user, the contents of /etc/skel is copied to the new user's homedir, so if you add /etc/skel/Desktop and add those files there, all new users will get those files. That does not give allready existing users those files of course.

Putting files on users' Desktop is a bit of an intrusion of privacy in my opinion. Some user's may prefer to not have any icons on their desktop. At the least you should ask the users if it's ok first. I'd recommend you rather create a menu entry that you put in /usr/share/applications (use one of the allready existing ones to figure out which fields to set) and if you have an icon for it, put the icon in /usr/share/icons.

With a menu-entry, users can right-click it and put it on the desktop if they want.

---

### Post by jodgi on 2008-11-07
Thanks scragar and geirha!

First a little background so you understand what I want to do:
I run (or try to) a 8.04 LTSP terminal server on a school. There are about 120 user accounts on the server and about 50 terminals around the little school.

On request I've made a dir (/home/teachers/) for sharing among the teachers and one for the students (/home/students/). 

If I tell people they will find their share folder in the /home folder they will just return an empty stare ;) They want a nice little icon sitting on their desktop, for them to click on that takes them to the share folder.

So I made links for those two dirs but hated the idea of manually pushing the student link to 100 desktops... and didn't know the things you just told me.

I reckon geirha's advice will keep it covered for future accounts and scragar's will take care of those 100 existing student desktops.

Could you send the links based on group membership? The teacher share to the members of the teacher group...? Am I pushing it now? ;)

---

### Post by scragar on 2008-11-07
```
LOOKINGFOR=teacher
cd /home
sudo -i
for X in `ls`; do
  cd /home/$X
  if [ "`ls -dl ./ | grep "$X $LOOKINGFOR"`" ]; then
    cd Desktop
    **stuff to do here.**
  fi
done
```but I'd be a little scared of this making the same file on the /home/teachers directory as for all the teachers, something like this would cancel that out though:
```

LOOKINGFOR=teacher
cd /home
sudo -i
for X in `ls`; do
  cd /home/$X
  if [ "$X" != "$LOOKINGFOR" ]; then
    if [ "`ls -dl ./ | grep "$X $LOOKINGFOR"`" ]; then
      cd Desktop
      **stuff to do here.**
    fi
  fi
done

```

EDIT:
ooh, I'd just noticed, I'm not dropping out of sudo, might want to add an exit to the very end of that code, to avoid passing root perms on anywhere else.
```
.......
  fi
done
**exit**
```

---

### Post by geirha on 2008-11-07
In that case, I think adding a bookmark would be a nicer thing to do. Then you'd just go to "Places -> Students" or "Places -> Teacher".

Assuming the teacher group is called *teacher*, and that the teachers are regular members of this group, and does not have it as the gid (primary group). Then you should get a comma-separated list of all teachers with this command:
```
getent group *teacher* | cut -d: -f4
```

We can loop through each of those users with a while loop, and add a bookmark
```

#!/bin/bash

bookmark="file:///home/teacher"

getent group *teacher* | cut -d: -f4 | while read -d, user; do
  # Get the homedir
  homedir=`su $user -c "xdg-user-dir"`
  
  # If the bookmark already exists we skip. We don't want to add it twice
  grep -q "^$bookmark$" "$homedir/.gtk-bookmarks" && continue
  
  # Append it to the end of the bookmark list
  echo "$bookmark" >> "$homedir/.gtk-bookmarks"

  # Alternatively, add a symlink on the desktop
  #ln -vs "/home/teacher" "`su $user -c "xdg-user-dir DESKTOP"`/teacher"
done

```

EDIT: Read your post again and changed teachers to teacher
Adding a bookmark like that only works if the users are using gnome though. I made that assumption without thinking.

---

### Post by jodgi on 2008-11-08
Thanks guys!

---

