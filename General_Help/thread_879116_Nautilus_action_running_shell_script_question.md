---
title: "Nautilus action running shell script question"
date: 2008-08-03
forum: General Help
---

### Post by bbqsandwich on 2008-08-03
Hello,

I would like to use nautilus actions to add a new right-click menu item - "Backup files in this folder." When clicked, it would execute a shell script that makes a folder called Backup in whatever folder it is run in, then copies all the contents of that folder into the Backup folder.

I tried this by making backup.sh in ~/Documents/Scripts with:

```

#!/bin/bash
mkdir Backup
cp * Backup

```

and having a nautilus action, "Backup files in this folder," with the path:

```
sh /home/[username]/Documents/Scripts/backup.sh
```

Yet this does not work. Any help would be much appreciated!

---

### Post by mc4man on 2008-08-03
atm nevermind

---

### Post by kaibob on 2008-08-03
It worked for me with the following:

```
#!/bin/bash
cd $1
mkdir Backup
cp * Backup
```

I used %M as the parameter in Nautilus Actions.

Is your Scripts directory in your path? Perhaps try the script in ~/bin without the sh.

---

### Post by bbqsandwich on 2008-08-05
I tried your suggestions, kaibob...

1. put it in ./bin as backup.sh
2. set Path in nautilus-actions-config to "backup.sh" (no quotes)
3. set Parameter in nautilus-actions-config to "%M" (no quotes)

Still does not work. Any other suggestions? I wonder what you are doing differently that I am not doing...

---

### Post by caljohnsmith on 2008-08-05
Just in case you haven't checked all ready, bbqsandwich, is that script executable? (chmod +x script.sh) If that isn't it, then I would put something in the script that doesn't require input, for example:
```
echo "this script executed successfully" > /home/<username>/Desktop/script_executed.txt
```
That would tell you for sure whether the script is run or not.

---

### Post by dexter.deepak on 2008-08-05
try this solution :
```
#!/bin/bash
cd $1
mkdir /home/dpak/exp/backup
cp * /home/dpak/exp/backup

```

in the nautilus config menu, i gave the path as "/home/dpak/exp/naut" (without qoutes...and this is path to my script)

in the parameters i passed %d

in the conditions tab, i applied it for both files and folders.
you will have your backup of the parent of the selected file/folder in   the /home/dpak/exp/backup

---

### Post by mc4man on 2008-08-05
@ bbqsandwich
works fine as the script by kaibob (won't back up sub folders if present)
Just put your script in home dir. (and make sure you had done a chmod +x on it)
see screen (named script backup)

I'm not good at scripts but if there are subfolders in the folder your backing up this worked (probably could be written better)
```

#!/bin/bash
cd $1
mkdir Backup
cp -r * Backup 
cd Backup 
rm -r Backup
```

---

### Post by mb_webguy on 2008-08-05
> **kaibob said:**
> It worked for me with the following:

```
#!/bin/bash
cd $1
mkdir Backup
cp * Backup
```

I used %M as the parameter in Nautilus Actions.

Is your Scripts directory in your path? Perhaps try the script in ~/bin without the sh.

I put this script in my ~/bin directory, chmod'ed it to 774, and added it to the Nautilus actions with the %d parameter and it successfully made a Backup directory containing the contents of the current directory in the current directory.

Note that this will only backup files in the current directory, and not subdirectories.  If you want it to grab all subdirectories as well, you'll need to change the last line of the script to "cp -r * Backup" (which I tested to make sure it doesn't create an infinite loop).  The only problem with this is that if you use the script to backup a directory several times, you'll end up with recursive backup directories.  This might actually be a feature rather than a bug, since each sub-Backup directory will be from an earlier backup.  On the other hand, you might eat up your drive space rather quickly if you're not careful...

---

### Post by kaibob on 2008-08-05
I agree with the advice given above. Also, just to check that the script itself is OK, I would suggest that you open a terminal window and type the following:

```
backup.sh /path/to/folder
```

In the above, insert the full path to the folder to be backed up (e.g. /home/kaibob/documents/). If the script works OK, then let us know exactly what you have in the Nautilus Actions configuration dialog (or better yet post screenshots).

---

### Post by bbqsandwich on 2008-08-07
I was still unable to get the exact original solution I wanted, but I have done something else that works just as well for me. I hesitate to mark this [SOLVED], however, because technically the original problem has not been solved.

What I did was install nautilus-open-terminal, so I can right-click in a folder to open a terminal there. I then made a bash alias:

```
alias bak='mkdir backup && cp * backup'
```

So I just type "bak" into the terminal and it accomplishes the same task. Also, this prevents using a right-click menu item for a single, limited function, and I can accomplish other things while the terminal is open.

Thanks everyone for all of your help!!

---

