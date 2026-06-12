---
title: "Useful Shell Scripts"
date: 2008-10-20
forum: General Help
---

### Post by dennismoore1 on 2008-10-20
Hello, these are a collection of shell scripts I have created and found very useful.

**install-script** - installs a shell script

mv $1 /usr/local/sbin/$1
chmod a+rwx /usr/local/sbin/$1

use:
install-script *file*

**alph** - alphabetizes a file

cat "$1" | sort > "$1"

use:
alph *file*

**clndir** - gets rid of pesky "file~" files

rm *~

use:
clndir *directory/name*

**empty-trash** - empties the trash bin

rm -rf ~/.local/share/Trash/

use:
empty-trash

**delinux-disk** - gets rid of .Trash directories on jump drive

sudo mv /media/$1/.* ~/.local/share/Trash/files/
empty-trash

use:
delinux-disk *drive name*

**vidget** - downloads youtube videos and names them
!IMPORTANT!
use the following code before using this script:

sudo apt-get youtube-dl

youtube-dl http://www.youtube.com/watch?v=$1
mv ~/$1.flv ~/Videos/$2.flv

use:
vidget *video-roster-number* *desired name*

for clarification or amendments on any of these just reply to this post.
Thanks Guys!

---

### Post by shaggy999 on 2008-10-20
Here's a useful shell script I use:

```

#!/bin/bash
/etc/init.d/ntp stop
ntpdate ntp.ubuntu.com
/etc/init.d ntp start
hwclock --systohc

```

Just drop this in a file, name it whatever and set the execute bit and run it. I use a commandline-only system so this is pretty handy. Took me FOREVER to figure out that I need to shut off the ntp server to update manually.

---

### Post by WRDN on 2008-10-20
Good scripts. My only comment is that, in the "empty-trash" script, you only need to remove the Trash folder, and unless there are some files you do not own in your Trash folder, "sudo" is not required. When you next delete a file, the Trash folder is recreated.

---

### Post by dennismoore1 on 2008-10-20
Could you please clarify WRDN?
I did not quite understand that.
I have tinkered with the script quite a bit.
And I am the only user on my system so I almost never include security.
Of course, I am deffinitly no master.
I am open to your suggestions.

---

### Post by WRDN on 2008-10-20
> **dennismoore1 said:**
> Could you please clarify WRDN?
I did not quite understand that.
I have tinkered with the script quite a bit.
And I am the only user on my system so I almost never include security.
Of course, I am deffinitly no master.
I am open to your suggestions.

Sure.

To quote from the original post:

```
empty-trash - empties the trash bin

sudo rm -rf ~/.local/share/Trash/
mkdir ~/.local/share/Trash/
mkdir ~/.local/share/Trash/info
mkdir ~/.local/share/Trash/files

use:
empty-trash
```

This can be reduced to a single line:

```
rm -rf ~/.local/share/Trash
```

Regarding the use of "sudo", in the context of Trash removal, it is OK to use, but if you don't need the higher privileges, there is no point asking for them. The user should own all the files in the Trash folder (which is located in their own home folder), so "sudo" is not needed.

---

### Post by dennismoore1 on 2008-10-20
very very true
however,
are you sure that when you delete a file the trash bin directories are recreated on their own?

---

### Post by dennismoore1 on 2008-10-20
oh yes
it is
i just tested it
ill make an amendment
thank you

---

### Post by jyaan on 2008-10-20
here's one i made (actually a python script, if you use it make sure to chmod +x it so you dont have to type python every time) that fixes screen resolution. useful when wine games mess it up and you want to fix it quickly without bothering with all the menus. change the res to whatever you like to use, mine is 1440x900.

```

jyaan@ubuntu:~$ cat /usr/local/bin/fixres.py 
#!/usr/bin/python

import pygame
from pygame.locals import *

pygame.display.set_mode((1440,900), FULLSCREEN)
pygame.quit()
exit()

```

i use this one below a lot

```

jyaan@ubuntu:~$ cat /usr/local/bin/sapt 
#!/bin/bash
# a simple script to lessen the amount of typing
# required to search with apt-cache.
# jyaan bresy 13.09.2008.

args=$1
echo searching through apt\'s cache for \"$args\"
exec apt-cache search $1

```

---

### Post by bodhi.zazen on 2008-10-20
good start, but can be simplified.

Take a look at pipes and redirects.

cat "$1" | sort > "$1"

*Note also using quotes " " allows file names with spaces :twisted:

Also you will like this one

look at man mkdir

mkdir -p ~/.local/share/Trash/{info,files}

You should likely use /usr/local/bin for scripts (rather then sbin)

Most of these "one liners" can be set as an alias or function in ~/.bashrc

---

### Post by Sam on 2008-10-20
> **jyaan said:**
> here's one i made (actually a python script, if you use it make sure to chmod +x it so you dont have to type python every time) that fixes screen resolution. useful when wine games mess it up and you want to fix it quickly without bothering with all the menus. change the res to whatever you like to use, mine is 1440x900.

```

jyaan@ubuntu:~$ cat /usr/local/bin/fixres.py 
#!/usr/bin/python

import pygame
from pygame.locals import *

pygame.display.set_mode((1440,900), FULLSCREEN)
pygame.quit()
exit()

```

This does not work ?
```
xrandr -s 1440x900
```

---

### Post by DGortze380 on 2008-10-20
Use this one twice a day.

Just one a threw together for myself so there isn't much error checking or anything. Simple enough to modify for other systems, PM me with any questions. Could automatically check for a mounted drive easily enough, I just ask the user to remind myself to check, don't need the script to check for me.

```

#!/bin/ksh

# The backup created is of /Users (all users home and shared directories) not
# system files. Add any other directories below.

# This script will sync the backup located on /Volumes/My_External using
# the rsync command with options archive and one file system.

begin=no
run=0

while [[ $run -eq 0 ]] do

echo "Is the drive mounted and ready for the backup to begin?" 
echo "(yes|no|exit)"
read begin

if [[ $begin = "yes" ]]
then
run=1
sudo rsync -ax --delete /Users /Volumes/My_External
# -a  archive mode (recursive, links, perms, times, groups, owner, devices)
# -x  one file system

# ADD ADDITIONAL DIRECTORIES HERE USING ABOVE RSYNC COMMAND

else
if [[ $begin = "no" ]]
then
clear
echo "Please Connect and Mount the drive and type yes to continue." 
else
if [[ $begin = "exit" ]]
then
run=1
clear
else
echo "Please enter valid input (yes|no|exit)"
fi
fi
fi
done

```

---

### Post by jyaan on 2008-10-20
yea thats better, i was just messing w/ python recently. ive also found that mien is not 100% reliable after certain types of win32 crashes =0.

id still put the code in a script for easy autocomplete tho =P

---

### Post by rectifiercc on 2011-09-27
In regards to this script, some youtube videos are not flv files. How can you modify this script to give the proper extension to the downloaded file?

```
vidget - downloads youtube videos and names them
!IMPORTANT!
use the following code before using this script:

sudo apt-get youtube-dl

youtube-dl http://www.youtube.com/watch?v=$1
mv ~/$1.flv ~/Videos/$2.flv

use:
vidget video-roster-number desired name
```

---

### Post by rectifiercc on 2011-09-27
I ended up doing this:

```
youtube-dl http://www.youtube.com/watch?v=$1
if [ -f $HOME/$1.flv ]
  then
    mv ~/$1.flv ~/Desktop/$2.flv
    echo "$2.flv copied to the desktop"

fi

if [ -f $HOME/$1.mp4 ]
  then
   mv ~/$1.mp4 ~/Desktop/$2.mp4
   echo "$2.mp4 copied to the desktop"
fi


```

---

### Post by debd on 2011-09-27
> **install-script** - installs a shell script

mv $1 /usr/local/sbin/$1
chmod a+rwx /usr/local/sbin/$1
I have a objection with this one.
The line ```
chmod a+rwx /usr/local/sbin/$1
``` gives read, write and execution permission on the file to everybody i.e the owner, group and others, which is undesirable most of the time.
Better would be ```
chmod u+rwx /usr/local/sbin/$1
``` that gives rwx perms for only the owner of the file.

---

### Post by nothingspecial on 2011-09-27
Downloading videos from youtube is not supported here.

Closed.

---

