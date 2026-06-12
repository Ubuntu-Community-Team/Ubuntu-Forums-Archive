---
title: "[SOLVED] pen drive not mounting"
date: 2008-10-05
forum: General Help
---

### Post by suhaib1thariq on 2008-10-05
i am posting this thread second time .............since i can't get clear reason and solution.
i had installed hardy.....in hardy ..it doesn't detect any pen drives ...when i plug the pen drive it shows
                   "cannot mount volume
Invalid mount option when attempting to mount the volume 'kingston".
why hardy can't mount pen drive suggest me a solution

---

### Post by Julius1988 on 2008-10-05
i am having the same issue to,did some extensive search but did not find a solution to this, is this resolvable in hardy?:confused:

---

### Post by earthpigg on 2008-10-05
do either of you NOT have a cd rom drive?

if this is the case:

```
sudo gedit /etc/fstab
```

change the line:

```
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

too:

```
# /dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

and restart for good measure.

if that does not work, undo what i just told you to do :)

---

### Post by Julius1988 on 2008-10-05
i am having.

---

### Post by earthpigg on 2008-10-05
> **Julius1988 said:**
> i am having.

well... i dunno then. people smarter then me trying to solve the problem may want to see the output of

```
cat /etc/fstab
```

from the terminal.

---

### Post by suhaib1thariq on 2008-10-05
i am also having cd rom drive

---

### Post by earthpigg on 2008-10-05
> i am having.

> i am also having cd rom drive 

both of you do not speak english as your first language. 

what language do you guys have ubuntu set to? and the people smarter than me may want the results of 

```
cat /etc/fstab
```

PEOPLE SMARTER THAN ME: is there any way this could be a language localization issue...? shot in the dark, but finding patterns is where you start when you want to replicate a problem :)

---

### Post by Julius1988 on 2008-10-05
why do u think it will be an issue regarding the language we speak?

---

### Post by suhaib1thariq on 2008-10-05
what do u think about u? r u english teacher? no right ........if u understand my questions reply......from this i understand that u don't have answer

---

### Post by earthpigg on 2008-10-05
> **Julius1988 said:**
> why do u think it will be an issue regarding the language we speak?

not the language you **speak**, but the language you have **ubuntu** set to.

and i have no idea if that even makes sense... probably not, but you said you did an extensive search and couldn't find anything that worked... 

as Arthur Conan Doyle [said]("http://www.brainyquote.com/quotes/authors/a/arthur_conan_doyle.html"):

> When you have eliminated the impossible, whatever remains, however improbable, must be the truth.

:)

---

### Post by earthpigg on 2008-10-05
> **suhaib1thariq said:**
> what do u think about u? r u english teacher? no right ........if u understand my questions reply......

i am not making fun of your english at all - you speak english much better than i speak any other language.

---

### Post by suhaib1thariq on 2008-10-05
k..ya ...it's nt my first language.....do u had answer for that...please refer and tell me

---

### Post by earthpigg on 2008-10-05
no, i do not have an answer for that. i am not that good with linux.

i am merely hypothesizing:

**if** you both have ubuntu set to a second language, and
**if** you both are having the exact same problem, and
**if** no other solution exists, then
maybe ubuntu needs to fix its support for your language.

what language do you have ubuntu set to?

what does putting this in the terminal show?

```
cat /etc/fstab
```

i probably do not have the solution based on that, but whoever comes along that is smarter than me will ask you to do show your /etc/fstab :)

---

### Post by Julius1988 on 2008-10-05
I am not here for a debate......i am here to find a solution to the problem...i have distributed ubuntu at least to 10 of my friends they are all reporting this issue to me, i take responsibility in addressing their issue so rely on forums for effective solution.

Here is  the output of fstab file.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=f72d3d79-a4aa-4825-82dd-8b0c7bf79c04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
/dev/sda5 /media/sda5 ntfs defaults,umask=007,gid=46 0 0 
/dev/sda6 /media/sda6 ext3 defaults 0 1
/dev/sda7 /media/sda7 vfat defaults,umask=007,gid=46 0 0 
/dev/sda8 /media/sda8 ntfs defaults,umask=007,gid=46 0 0
/dev/sda1 /media/sda1 ntfs defaults,umask=007,gid=46 0 0
UUID=d2973430-107b-468d-9eb2-93267f184bb4 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



---

### Post by suhaib1thariq on 2008-10-05
my fstab file is...
 

suhaib@suhaib-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda8 :
UUID=1b5bae7b-b3c2-4266-83a7-0680463f6549 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda9 :
UUID=4de4a5d3-06b6-475c-8db9-711dd1a15515 none swap sw 0 0
/dev/sdf1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda7 /media/sda7 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/SUHAIB ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by Teefs on 2008-10-10
> do either of you NOT have a cd rom drive?

if this is the case:

Code:

sudo gedit /etc/fstab

change the line:

Code:

/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

too:

Code:

# /dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

and restart for good measure.

if that does not work, undo what i just told you to do 


I don't have a cd-rom drive and the fix worked for me.:) Thanks

---

