---
title: "Using the terminal to copy &amp; paste files &amp; directories"
date: 2008-08-23
forum: General Help
---

### Post by bigdee973 on 2008-08-23
how do i copy and paste directories but eliminate some sub directories..for instance i have My Documents that have directories My Pictures My Videos My music plus more that i do not want to be copied and pasted onto my external...how do i go about copying and pasting My Documents without having those folders/directories. i just want the mountain of .doc's pdfs i have stored in My documents to be backed up thanks 

and also how would i go about excluding not just subdirectories but files as well from being copied and pasted...i need to know for future reference just in case thank you in advanced

also how would you copy and paste individual files in a batch..say 3 pdfs and paste them to destination folder all at once..is it possible? if not then how would u do it just one by one..im a noob please please help thanks

---

### Post by sdennie on 2008-08-23
In general, I think you can probably just use:

```

cp -R /path/to/source /path/to/destination

```

That will recursively copy files but not maintain the directory structure.

However, if you are looking for a backup solution, it may be easier to use Simple Backup:

```

sudo apt-get install sbackup

```

Then look for it in System->Administration.

---

### Post by Cheesehead on 2008-08-23
To copy a directory:
```
cp -r /home/USER/folder /media/usb_stick/backup/folder
```
Repeat for the folders you do want to copy.

You can also script the sequence, and simply run the script from an icon, launcher, command line, cron, or another script.

You can also use any of the many synchronize or backup apps in the repositories.

You can also use tar or zip commands to build an *archive*, then use one command to *refresh* the archive.

You can also...well, you get the idea.

---

### Post by bigdee973 on 2008-08-23
> **Cheesehead said:**
> To copy a directory:
```
cp -r /home/USER/folder /media/usb_stick/backup/folder
```
Repeat for the folders you do want to copy.

You can also script the sequence, and simply run the script from an icon, launcher, command line, cron, or another script.

You can also use any of the many synchronize or backup apps in the repositories.

You can also use tar or zip commands to build an *archive*, then use one command to *refresh* the archive.

You can also...well, you get the idea.

okay so how do i exclude a subfolder/subdirectory from being copied and pasted..for example folder "documents" has a folder within it called "SPAM" how do i copy everything in Documents without including "SPAM" i have about 5,000 pdf files floating around in documents and a folder called "SPAM" with 200gb.... Deleting SPAM folder is not an option because i do not want to delete it please help

and also, how do i copy and paste individual files???

---

### Post by bigdee973 on 2008-08-23
> **bigdee973 said:**
> okay so how do i exclude a subfolder/subdirectory from being copied and pasted..for example folder "documents" has a folder within it called "SPAM" how do i copy everything in Documents without including "SPAM" i have about 5,000 pdf files floating around in documents and a folder called "SPAM" with 200gb.... Deleting SPAM folder is not an option because i do not want to delete it please help

and also, how do i copy and paste individual files???

i found out how to copy and paste the individual file one by one.  just cp /path/to/file /path/to/destination, i figured also if i just mv the folder into another directory it would get it out the way for now.  which i think is best solution for now but if there is a simple command to just exclude or GROUP individual files together to be transfered than i would love to know but for now that would do thank you

---

### Post by Cheesehead on 2008-08-23
Your question was: 'What command do I use to copy?'. We answered it.

It's NOT the backup solution I would choose, since it's long and laborious.

'cp' doesn't have an exclude function. It simply copies.

If the question you *meant* to ask was 'How can I set up a one-click backup solution using bash commands', that's a different question, and has a different answer. (We did answer that, also - you use a *script* or group files in an *archive*).

---

### Post by Cheesehead on 2008-08-23
Your question was: 'What command do I use to copy?'. We answered it.

It's NOT the backup solution I would choose, since it's long and laborious.

'cp' doesn't have an exclude function. It simply copies.

If the question you *meant* to ask was 'How can I set up a one-click backup solution using bash commands', that's a different question, and has a different answer. (We did answer that, also - you use a *script* or group files in an *archive*).

---

### Post by linux_tech on 2008-08-23
cp(1) - link to Linux man page for cp
[http://linux.die.net/man/1/cp](http://linux.die.net/man/1/cp)

Copy SOURCE to DEST
cp from /path to file to /where you want file to go

change directory to the folder where the files are then issue a command 
like: 
cp -r file1.css file2.pdf file3.php /media/usb_stick/backup/folder

You can also use wild card characters-
*.* = all files
ie.#1 (if you are in dir where files are)- cp *.* /usr/bin
this would copy all files to /usr/bin

#2
cp *.txt newdir
would copy all files ending in .txt into the newdir directory

It is also handy to learn shortcut keys for terminal, up arrow -recalls last command.  
 other keyboard shortcuts that work within the terminal-

    ctrl-insert : copy

    shift-insert : paste

    shift-delete : cut

    shift-ctrl-C : copy

    shift-ctrl-V : paste

---

### Post by bigdee973 on 2008-08-23
yes of course guys u did and i thank you for your help and i have contributed a thanks to you thank you again

---

### Post by bigdee973 on 2008-08-23
> **linux_tech said:**
> cp(1) - link to Linux man page for cp
[http://linux.die.net/man/1/cp](http://linux.die.net/man/1/cp)

Copy SOURCE to DEST
cp from /path to file to /where you want file to go

change directory to the folder where the files are then issue a command 
like: 
cp -r file1.css file2.pdf file3.php /media/usb_stick/backup/folder

You can also use wild card characters-
*.* = all files
ie.#1 (if you are in dir where files are)- cp *.* /usr/bin
this would copy all files to /usr/bin

#2
cp *.txt newdir
would copy all files ending in .txt into the newdir directory

It is also handy to learn shortcut keys for terminal, up arrow -recalls last command.  
 other keyboard shortcuts that work within the terminal-

    ctrl-insert : copy

    shift-insert : paste

    shift-delete : cut

    shift-ctrl-C : copy

    shift-ctrl-V : paste

Awesome Dude,  thats something i was looking for.  very very helpful especially number 2 :guitar: thank you man

---

### Post by ghostdog74 on 2008-08-23
in bash you can use extended globbing, say you want to copy all files except text files
```

shopt -s extglob
cp !(*.txt) /destination

```

---

### Post by bigdee973 on 2008-08-23
> **ghostdog74 said:**
> in bash you can use extended globbing, say you want to copy all files except text files
```

shopt -s extglob
cp !(*.txt) /destination

```

cool, how would i go about excluding folders?  that would be really really good thing to know... and what do u mean in bash? im a bit of a noob... i think its a file i have to edit right?

---

### Post by ghostdog74 on 2008-08-23
> **bigdee973 said:**
> cool, how would i go about excluding folders?  that would be really really good thing to know... and what do u mean in bash? im a bit of a noob... i think its a file i have to edit right?

bash is the shell , you know, command line?? (terminal ?? )
if you want to exclude folders, you can use find
```

find /path -type d ! -name "*exclude*" -exec cp -r "{}" /destination \;

```
the above says find all directory names not having word "exclude" and copy recursively to destination

---

### Post by bigdee973 on 2008-08-23
> **ghostdog74 said:**
> bash is the shell , you know, command line?? (terminal ?? )
if you want to exclude folders, you can use find
```

find /path -type d ! -name "*exclude*" -exec cp -r "{}" /destination \;

```
the above says find all directory names not having word "exclude" and copy recursively to destination

im a little confused, im sorry, im a real noob rewrite that whole thing to suite me...for instance in bash im in /home/ubuntu/documents ... in there i have a folder called junk and i want to copy and paste everything in documents except junk folder and move it to /media/MyBook/Documents  how would U input the command? step by step... sorry for being such a noob

---

### Post by ghostdog74 on 2008-08-23
```

find /home/ubuntu/documents -type d ! -name "junk" -exec mv "{}" /media/MyBook/Documents \;

```

---

### Post by bigdee973 on 2008-08-23
> **ghostdog74 said:**
> ```

find /home/ubuntu/documents -type d ! -name "junk" -exec mv "{}" /media/MyBook/Documents \;

```

unfortunately, all that did was basically CUT and PASTE the folder.  i tried it on 4 different folders... and they cut and pasted everything within the folders...it did not exclude the JUNK folder..the junk folder and everything in it was transfered into the external hard drive... sorry im 100% sure that i did not make a typo

---

### Post by jerome1232 on 2008-08-23
Yeah it's missing a -maxdepth 0 option to keep it from recursing into subdirectories.

---

### Post by bigdee973 on 2008-08-23
> **jerome1232 said:**
> Yeah it's missing a -maxdepth 0 option to keep it from recursing into subdirectories.

where would i put -maxdepth 0 ? inbetween where? do i need to include the the word option with -maxdepth 0? (i.e. -maxdepth 0 option)

---

### Post by jerome1232 on 2008-08-23
```
find /home/ubuntu/documents -maxdepth 0 -type d ! -name "junk" -exec mv "{}" /media/MyBook/Documents \
```

maybe maxdepth 1 instead I haven't tested it.

---

### Post by bigdee973 on 2008-08-24
> **jerome1232 said:**
> ```
find /home/ubuntu/documents -maxdepth 0 -type d ! -name "junk" -exec mv "{}" /media/MyBook/Documents \
```

maybe maxdepth 1 instead I haven't tested it.

well i tried both -maxdepth 1 and 0 and all i get is a > symbol with the cursor blinking... i checked my external hard drive and the files have not been transfered any ideas?

---

### Post by Cheesehead on 2008-08-24
I recommend keeping your commands simple.

Sure, it's fun to see how extravagant you can make a singe line.
But six months from now, you're gonna change a folder name or a backup location or *something*...

...and then you'll need to *remember* what it all means so you can fix it.

If you're new, keep the commands short and simple. Script it, and just run the script.
---
#!/bin/sh
# This is my backup script. I'm so great.
cp -ur /home/USER/Music /media/stick/backup/Music
cp -ur /home/USER/Porn  /media/stick/backup/Porn
cp -ur /home/USER/.mail /media/stick/backup/.mail
---

---

### Post by bigdee973 on 2008-08-24
> **Cheesehead said:**
> I recommend keeping your commands simple.

Sure, it's fun to see how extravagant you can make a singe line.
But six months from now, you're gonna change a folder name or a backup location or *something*...

...and then you'll need to *remember* what it all means so you can fix it.

If you're new, keep the commands short and simple. Script it, and just run the script.
---
#!/bin/sh
# This is my backup script. I'm so great.
cp -ur /home/USER/Music /media/stick/backup/Music
cp -ur /home/USER/Porn  /media/stick/backup/Porn
cp -ur /home/USER/.mail /media/stick/backup/.mail
---

thats pretty awesome right there.  what does the -ur mean? whats its function? and i never wrote a script or did nothing with script so far, so how would that work?  do i have to open up a text editor, copy and paste what you wrote but customize it to my directories, Save it as an .sh file and then after words just ./back.sh and it will do itself or what? give me an idea this is real cool.  this would be awesome to do automatically because i could back up all my files even bookmarks etc this way...plus more stuff i guess

---

### Post by linux_tech on 2008-08-24
2 different switches for cp
-u = (update) copy only when source file is newer than  the  destination file or when the destination file is missing
-r = copy directories recursively

---

### Post by bigdee973 on 2008-08-24
> **linux_tech said:**
> 2 different switches for cp
-u = (update) copy only when source file is newer than  the  destination file or when the destination file is missing
-r = copy directories recursively

hmm the -u command sounds nice.  very smart function i would say.  saves alot of time and processing power by preventing it from overwriting for command. thanks.

---

