---
title: "Moving folders containing certain file types"
date: 2008-07-27
forum: General Help
---

### Post by Udaho on 2008-07-27
I've been searching the net for the last couple hours for the best way to consolidate my backed up pictures, music, and video into single directories. Right now they're scattered across my backup drive in a bunch of different folders. I was able to move all my .avi files into a single directory with this command:

```
find . -iname "*.avi" -exec mv '{}' /media/Backup/Movies/ \;
```

This works fine for movies because there aren't a ton of them and they aren't really related to any other files, but if I do that for my .jpg's or .mp3's they won't be organized by date or by album anymore.

I know I can just find directories by using find and specifying -type d, but I don't know how to tell it to:

1. find directories containing files that end in a certain file type, and
2. Move all those directories to a new location.

Thanks for taking a look at this, any light you can shed on this is much appreciated.

---

### Post by ryanhaigh on 2008-07-27
This will only copy those files with the given extestion, you can however change the extension and run it again (if for example you have .mov files in with your pictures).
```

#find all jpgs copy them maintaining the directory structure
find ./ -iname '*.jpg' -exec cp -b --parents {} ~/Desktop/ \;

```

---

### Post by Udaho on 2008-08-02
Thanks for the point in the right direction. One thing I discovered while testing the command you suggested is that if your destination directory is contained in the directory you are searching it will create an infinite loop. I'm sure you knew that but since I am new to bash commands I'm glad I tested it.

I'm still searching for a way to move the directories instead of copy them but I have posted this question on several boards and this was the best answer so far.

---

### Post by pauper on 2008-08-03
> **Udaho said:**
> ...if your destination directory is contained in the directory you are
searching it will create an infinite loop.

[list][*] Move the files to some parent or sibling directory of that you do the
search in, i.e. if you're running search for /home move the files to /tmp.

[*] Use "-prune" with "find" to exclude some sub-directories below.
Note: There is a drawback though. If the name of directory, you have excluded,
is common, "find" will disregard any occurrence of it in sub-directories as
well.

An example:

```
:~$ **mkdir -p ~/{foo/{dir_1/{dir_2/{new,dir_3},new},new},foo_2}**
:~$ **touch ./foo/new/file_1.txt ./foo/dir_1/new/file_2.txt \**
> **./foo/dir_1/dir_2/new/file_3.txt ./foo/file_4.txt \**
> **./foo/dir_1/file_5.txt ./foo/dir_1/dir_2/file_6.txt \**
> **./foo/dir_1/dir_2/dir_3/file_7.txt**
:~$ **ls**
[color=blue]foo[/color] [color=blue]foo_2[/color]
:~$ **ls -FR ~/foo**
$HOME/foo:
[color=blue]dir_1/[/color]  file_4.txt  [color=blue]new/[/color]

$HOME/foo/dir_1:
[color=blue]dir_2/[/color]  file_5.txt  [color=blue]new/[/color]

$HOME/foo/dir_1/dir_2:
[color=blue]dir_3/[/color]  file_6.txt  [color=blue]new/[/color]

$HOME/foo/dir_1/dir_2/dir_3:
file_7.txt

$HOME/foo/dir_1/dir_2/new:
file_3.txt

$HOME/foo/dir_1/new:
file_2.txt

$HOME/foo/new:
file_1.txt

[color=green]# Move all *.txt files from ~/foo and all its sub-directories to ~/foo_2:
# omit from search any */new directory, prompt before executing (type either
# y or n, Enter):[/color]

:~$ **[highlight]find[/highlight] ~/foo -name new -prune -o -name "*.txt" -print0 \**
> **| [highlight]xargs[/highlight] -0p [highlight]mv[/highlight] -t ~/foo_2**
mv -t $HOME/foo_2 $HOME/foo/file_4.txt $HOME/foo/dir_1/dir_2/dir_3/file_7.txt
$HOME/foo/dir_1/dir_2/file_6.txt $HOME/foo/dir_1/file_5.txt ?...y

[color=green]# If you want to combine *.odt, *.txt, *.bak ->[/color] **-name "*[.odt,.txt,.bak]"**
[highlight]# !!! Before moving any essential data practice with some foo files.[/highlight]

:~$ **ls ~/foo_2**
file_4.txt  file_5.txt  file_6.txt  file_7.txt
:~$ **ls -FR ~/foo**
$HOME/foo:
[color=blue]dir_1/[/color]  [color=blue]new/[/color]

$HOME/foo/dir_1:
[color=blue]dir_2/[/color]  [color=blue]new/[/color]

$HOME/foo/dir_1/dir_2:
[color=blue]dir_3/[/color]  [color=blue]new/[/color]

$HOME/foo/dir_1/dir_2/dir_3:

$HOME/foo/dir_1/dir_2/new:
file_3.txt

$HOME/foo/dir_1/new:
file_2.txt

$HOME/foo/new:
file_1.txt
```

[*] Use "-maxdepth n, -mindepth n" with "find". See "man find".[/list]

By the way, "-exec...'{}' **\;**" will start a program for each file it finds, which
is more resource and time consuming; better use "-exec...'{}' **\+**" or "xargs",
it will queue all matches and execute them in order.

---

