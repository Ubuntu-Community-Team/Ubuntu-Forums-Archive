---
title: "Clean Install Questions"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by tachyon4 on 2009-05-26
Long story short, I upgraded to 9.10 and had trouble with booting and suspending, so I tried a clean install.

Before installing 9.10 from the CD, I made a copy of my home folder on another partition.  (I had trouble with permissions at first, but I was able to copy all of the "visible" files and folders and nothing else.)

Then I performed a clean install.

When I copied my old files back into the new home folder, they all gained irremovable "no read" and "no write" emblems.  Technically, I can use these files to an extent, but it becomes a real pain typing "sudo" every time I want to perform a basic task.  Also, some tasks (such as installing applications from a list in one of these text files) are not possible to my knowledge with these restrictions.

What can I do to return these files to their normal state, in which I can read and write freely?

And ultimately, what can I do to my computer to give me more authority over my files?  I am not afraid of accidentally giving full permissions to someone who shares my computer because I am the sole user.  A change here would likely preclude many redundant questions in the future.

Thanks as usual.

---

### Post by donato roque on 2009-05-26
Hi
You should change your file ownership.  Open a terminal and type:
~$sudo chown -R yourname:yourgroupname <enter>.

~ means you should be in your /home/yourname folder.  You can
    also check your files by typing $ls, ok?

"chown"  means change ownership of files

-R  means recursive; applying the command on all folders

yourname  means the name of your desktop

if you open nautilus to /home/yourname you can observe the change in
real time.

Good luck!

---

### Post by donato roque on 2009-05-26
Hi
I would like to corrent myself.  The command should be:
~$sudo chown -R yourname:yourgroupname /home/yourname <enter>

All the files/folders ownership in your home directory will
revert back to you.  All the restrictions stems from these 
folders "root" ownership.

Good luck!

---

