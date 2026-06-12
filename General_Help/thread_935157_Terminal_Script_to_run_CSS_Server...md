---
title: "Terminal Script to run CS:S Server.."
date: 2008-10-01
forum: General Help
---

### Post by GodsDead on 2008-10-01
Hey, i have looked around to try and find an answer to this, but i cant!!
I have a ubuntu server, with Counter strike source server installed, and it gets REALLY annoying to type out this all the time
```

cd /mnt/sdb1/srcds/
sudo ./srcds_run -console -game cstrike +map breakfloor -maxplayers 16 -autoupdate

```

So im looking into creating a script, im quite fluent in PHP, but would much prefer to use natural terminal scripting to make things work =p

this is my script (created in windows using notepadd++) and saved Via a samba folder share to my /home/tom.
The file is called csss.sh
im not sure about file extensions i guessed to save it as .sh from srcds.com tutorial on installing a CSS server..

```

#!/bin/bash
echo "Starting Counter-Strike:Source Server"
sleep 1
screen -A -m -d -S css-server /mnt/sdb1/srcds/srcds_run -console -game cstrike +map breakfloor +maxplayers 16 -autoupdate

```

I have screen installed..
but i have even tryed just having it echo out! and this is the error that i get!

```

tom@spicy:~$ sudo ./csss.sh
sudo: unable to execute ./csss.sh: No such file or directory

```

or without sudo

```

tom@spicy:~$ ./csss.sh
-bash: ./csss.sh: /bin/bash^M: bad interpreter: No such file or directory

```

And, i have chmodded the file with this;
```

tom@spicy:~$ sudo chown -R tom ./csss.sh
tom@spicy:~$ sudo chmod -R 777 ./csss.sh

```

please help im so confused!

---

### Post by Sycron on 2008-10-01
make it executable ```
sudo chmod +x csss.sh
```
and delete the **#!/bin/bash** line.

---

### Post by Peter09 on 2008-10-01
Hey I'm not a great command line person, but I believe you can create an alias to do what you want.
Does this help

[http://www.ss64.com/bash/alias.html](http://www.ss64.com/bash/alias.html)

---

### Post by alberto ferreira on 2008-10-01
I'm going to try to be as explicit as possible

Steps:
1-Choosing directory:
In a terminal go to the directory where you want to create your script

2-Create the file
write in the terminal "nano" and then the name of the script. It can be named with ".sh" extension or none at all
Example:
nano myscript

3-Write the script (you can just paste this in)
#! /bin/bash
echo "Starting Counter-Strike:Source Server"
sleep 1
screen -A -m -d -S css-server /mnt/sdb1/srcds/srcds_run -console -game cstrike +map breakfloor +maxplayers 16 -autoupdate

4-save the script
For this press Ctrl+o, then press Ctrl+x to leave the editor

5-Make the script executable
chmod +x myscript

6-Enjoy it :p

Anyways, I think the problem was the line #!/bin/bash, I believe it must have a space (#! /bin/bash)

If an error does occur it will be due to the third line of the script.
---------
Good luck

---

### Post by rainz0r on 2008-10-01
Yea, I ust to play CS:S competitively, Got myself to CEVOm and pretty much quit after that. Then I switched to linux! :)

---

### Post by GodsDead on 2008-10-04
Wicked, all running, thanks guys!!
Now to do some research on screen ==]

---

### Post by Sycron on 2008-10-04
Good luck then.

---

