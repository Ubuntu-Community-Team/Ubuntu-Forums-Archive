---
title: "Help with creating launchers"
date: 2008-07-25
forum: General Help
---

### Post by chad2408m on 2008-07-25
Okay, I have been at this for days, Im about out of my mind.  Ive been trying to create a launcher to this program: 

/home/chad/Games/Phun/Phun (4.13)/phun

The program is a Shell Script which does this:

#!/bin/sh
LD_LIBRARY_PATH=".:${LD_LIBRARY_PATH}" ./phun.bin $@

I need help making a launcher to this.  The problem is that I need to 'cd' to the directory.  I did this in a terminal with no problems, and the application worked fine.  Now Im trying to make a launcher, and nothing seems to work.  Please give some suggestions as to what I should do next.

---

### Post by chad2408m on 2008-07-25
Okay, I have been at this for days, Im about out of my mind.  Ive been trying to create a launcher to this program: 

/home/chad/Games/Phun/Phun (4.13)/phun

The program is a Shell Script which does this:

#!/bin/sh
LD_LIBRARY_PATH=".:${LD_LIBRARY_PATH}" ./phun.bin $@

I need help making a launcher to this.  The problem is that I need to 'cd' to the directory.  I did this in a terminal with no problems, and the application worked fine.  Now Im trying to make a launcher, and nothing seems to work.  Please give some suggestions as to what I should do next.

---

### Post by chilinski on 2008-07-25
What part of creating the launcher is the problem? What do you have as the command? One of the things I would do is remove the parenthesis from the file path...on a Redhat system a few hours ago, I couldn't do certain commands on a file that had a ( in it. Once I changed the name, it worked fine.

I think the command should be:
/home/chad/Games/Phun/Phun_4.13/phun

assuming you change the name of Phun (4.13) to Phun_4.13.

If you need to cd to the directory, why not do that as the first line in the script? Maybe I don't understand your problem well enough.

---

### Post by silkstone on 2008-07-25
You can't use spaces in file or folder names unless you put the whole path in quotes. It's best to rename without the space, but otherwise...

"/home/chad/Games/Phun/Phun (4.13)/phun"

i.e. you need quotes around the whole path. But I'm not sure if the ( ) are allowed.

---

### Post by geirha on 2008-07-25
Try adding the cd to your script:
[php]
#!/bin/sh
cd $(dirname $0)
LD_LIBRARY_PATH=".:${LD_LIBRARY_PATH}" ./phun.bin "$@"
[/php]

---

### Post by rune0077 on 2008-07-25
If it's a shellscript I think you'll need to give it the .sh extension. 

So the path should be: /home/chad/Games/Phun/Phun (4.13)/phun.sh

Now add a launcher (right-click on desktop and select "add launcher"), and under the "Command" click browse and point it to your shell script. That works for me.

---

### Post by sdennie on 2008-07-25
Threads merged.  Please try not to double post.

---

