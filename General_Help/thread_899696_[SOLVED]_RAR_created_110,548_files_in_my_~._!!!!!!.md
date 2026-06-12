---
title: "[SOLVED] RAR created 110,548 files in my ~./ !!!!!!"
date: 2008-08-24
forum: General Help
---

### Post by linuxisevolution on 2008-08-24
I just wanted to make a .rar archive. . . i ended up with several hundered thousand ncaaplaybook.part.234234.rar's! how do i get rid of them? just using the file browser on a amd 5000+ overclocked takes it to 100% cputime! i can hardly move teh mouse around the screen. Howdo i delete them?

---

### Post by bthoward on 2008-08-24
Open a terminal (Applications > Accessories > Terminal) then type "rm ~/ncaaplaybook.part.*"  I usually hesitate to mention this last part but since you have so many.  Simply typing that above command will require verification on each file.  You can either press y for each file (just hold it down) or you can add -f to the end after the file name and that will force it to remove them all.  It should get the job done for you right quick.

---

### Post by linuxisevolution on 2008-08-24
> **bthoward said:**
> Open a terminal (Applications > Accessories > Terminal) then type "rm ~/ncaaplaybook.part.*"  I usually hesitate to mention this last part but since you have so many.  Simply typing that above command will require verification on each file.  You can either press y for each file (just hold it down) or you can add -f to the end after the file name and that will force it to remove them all.  It should get the job done for you right quick.
THANKS! im am sad to say it did not work. . . i got this::


-bash: /bin/rm: Argument list too long

---

### Post by linuxisevolution on 2008-08-24
> **linuxisevolution said:**
> THANKS! im am sad to say it did not work. . . i got this::


-bash: /bin/rm: Argument list too long
what now?

---

### Post by bthoward on 2008-08-24
Add more of the files before putting the *.   The * means anything here...  So if you put rm -f ~/ncaaplaybook.part.12*  then do 13 and so on.  Put in as little information as you can and not get the too long of a list so that you get it done faster.  Once you get it to work make sure to mark the thread as solved and click thanks and what not if you would.

---

### Post by cariboo on 2008-08-24
Give this a try:

```
find . -name '~/ncaaplaybook.part.*' | xargs rm
```

This will delete the files one at a time, but it should work.

Jim

---

### Post by linuxisevolution on 2008-08-24
> **bthoward said:**
> Add more of the files before putting the *.   The * means anything here...  So if you put rm -f ~/ncaaplaybook.part.12*  then do 13 and so on.  Put in as little information as you can and not get the too long of a list so that you get it done faster.  Once you get it to work make sure to mark the thread as solved and click thanks and what not if you would.
Thanks man!! i *thanked* you. . I just typed sudo rm /home/nothinghere/NCAAplaybook.part.004* and so on. All the times i have used the terminal. . never knew that. . .Well i guess that sudo rm window* if you know what i mean ;)

---

### Post by linuxisevolution on 2008-08-24
> **bthoward said:**
> Add more of the files before putting the *.   The * means anything here...  So if you put rm -f ~/ncaaplaybook.part.12*  then do 13 and so on.  Put in as little information as you can and not get the too long of a list so that you get it done faster.  Once you get it to work make sure to mark the thread as solved and click thanks and what not if you would.
Well i would like to mark thethread as solved.. and i did but i changed it back! :(

I can type: sudo rm /home/afile/NCAAplaybook.part00* and the output is::

-bash: /bin/rm: Argument list too long

TADA!

if i try to shorten it by doing, sudo rm/home/afile/NCAAplaybook.part000*, i get

rm: cannot remove `/home/home/NCAAplaybook.part00*': No such file or directory

what now?? back to the beginning .. .cariboo's command did not work. It would find the files, but rm would not delete them::

rm: missing operand

---

### Post by panayk on 2008-08-24
The files are in you home directory?

find ~ -name 'ncaaplaybook.part.*' | xargs -n 100 rm

The value after the -n parameter controls how many arguments to process per command execution. The more the faster.

---

### Post by bthoward on 2008-08-24
Wouldn't the command:
ls ~/ncaaplaybook.part.* | xargs -n 100 rm 

go a lot faster?

Edit:  That is providing that they are all in your home directory and not spread through out the folders below it...  But that is how I understand things are setup for you.

---

### Post by panayk on 2008-08-24
```
$ seq 1 110548 | sed 's/^/ncaaplaybook.part./' | xargs touch
$ time bash -c 'find ~ -name "ncaaplaybook.part.*" | xargs -n 100 rm'

real	1m18.067s
user	0m0.772s
sys	0m5.012s
```
```
$ seq 1 110548 | sed 's/^/ncaaplaybook.part./' | xargs touch
$ time bash -c 'find ~ -name "ncaaplaybook.part.*" | xargs rm'

real	1m14.515s
user	0m0.376s
sys	0m3.620s
```
```
$ seq 1 110548 | sed 's/^/ncaaplaybook.part./' | xargs touch
$ time bash -c 'ls ncaaplaybook.part.* | xargs rm'
[COLOR="Red"]bash: /bin/ls: Argument list too long[/COLOR]
rm: missing operand
Try `rm --help' for more information.

real	0m7.987s
user	0m3.664s
sys	0m0.284s

```

So it seems globbing doesn't work for this many arguments.

---

### Post by mssever on 2008-08-24
A couple notes: First, you should never parse the output of ls. It's human-readable, but it's not designed to be machine-parseable, and it can sometimes do the wrong thing.

Try this: ```
for i in ncaaplaybook.part*; do
  rm -f "$i"
done
```
You can't list that many files on the command line, but you can loop over them. This script considers them all one at a time, so it might not be the fastest, but it's guaranteed to work.

---

### Post by panayk on 2008-08-24
> A couple notes: First, you should never parse the output of ls. It's human-readable, but it's not designed to be machine-parseable, and it can sometimes do the wrong thing.

Agreed, the safest thing to do, if possible, is something like:

```
find path expression -print0 | xargs -0 command
```

---

### Post by mssever on 2008-08-24
> **panayk said:**
> Agreed, the safest thing to do, if possible, is something like:

```
find path expression -print0 | xargs -0 command
```
Yes, but I should point out that shell globbing (such as in the for loop I gave) is equally safe. However, a properly-crafted [FONT=Courier New]find[/FONT] command is more efficient. I'm just too lazy to learn the ins and outs of [FONT=Courier New]find[/FONT]. :)

---

### Post by linuxisevolution on 2008-08-25
> **mssever said:**
> Yes, but I should point out that shell globbing (such as in the for loop I gave) is equally safe. However, a properly-crafted [FONT=Courier New]find[/FONT] command is more efficient. I'm just too lazy to learn the ins and outs of [FONT=Courier New]find[/FONT]. :)
Thanks guys i fixed it! i used the find command and used xargs+rm to delete the results. rm was giving an error becuase i had already deleted the files! please respond to my other post. thanks you guys for your help ;)

---

