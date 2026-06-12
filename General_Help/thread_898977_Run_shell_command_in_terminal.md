---
title: "Run shell command in terminal"
date: 2008-08-23
forum: General Help
---

### Post by Elcid247 on 2008-08-23
hi i wanted to creat a shell tht would cd to the current directory, run javac and java on the selected file_name.java the thing is, ofc i have to run java in terminal mode.

but when i try

```
gnome-terminal -e "Whatever Command"
```

it keeps telling me "There was an error creating child process for this terminal"

ive also tried

```
gnome-terminal --command="Whatever Command"
```

also gives me the same error

---

### Post by rossjman1 on 2008-08-23
How about a shell script?
```

#!/bin/bash
whatever command

```
Then make it executable
```
chmod ugo+x your_shell_script.sh
```

---

### Post by ad_267 on 2008-08-23
For more details: [http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

---

### Post by Elcid247 on 2008-08-24
thnx for tht guide ad_267


maybe i didnt clarify, i am making a shell, but when i tried using *gnome-terminal -e "command"* since the command MUST be run in terminal, it gave me tht error..

so this is exactly wht i need the shell to do:

1- open a new terminal
2- cd to current directory
3- execute javac
4- execute java

but this isnt just a shell problem, the *gnome-terminal -e "command"* gives me tht error even if i executed it in a terminal or run(alt+f2)

---

### Post by ad_267 on 2008-08-24
You mean you want to be able to see the command output in a terminal? Then you could just create a launcher (you can right click on the desktop and select create launcher) and choose application in terminal.

---

### Post by wdaniels on 2008-08-24
I'm not sure I understand what you're saying, but perhaps you need to create a shell script to do 2,3+4 and gnome-terminal -e "/path/to/shell/script" as the launch command rather than trying to open gnome-terminal from the shell script (or just use the run in terminal launcher option directly with the script as already suggested)?

---

### Post by p_quarles on 2008-08-24
> **Elcid247 said:**
> <snip>
so this is exactly wht i need the shell to do:

1- open a new terminal
2- cd to current directory
3- execute javac
4- execute java) 
<snip>
Just want to point out that a shell shortcut never requires you to change directory. The following two commands are equivalent:
```
cd /home/username/bin
./script.sh
```
and
```
/home/username/bin/script.sh
```
So, you can get rid of at least one step there. :)

---

### Post by Elcid247 on 2008-08-24
> **p_quarles said:**
> Just want to point out that a shell shortcut never requires you to change directory. The following two commands are equivalent:
```
cd /home/username/bin
./script.sh
```
and
```
/home/username/bin/script.sh
```
So, you can get rid of at least one step there. :)

thnx for the tip, but i actually need to change the directory for the javac and java not for the shell itself

eh again my fault, i shouldve clarified more, this is intended to be a Nautilus script to compile and run .java files and the output of the "java" command should be in a terminal.... i know it may sound a wierd idea but it just poped into my head lol.

anyway i got the terminal part to work, now working on the rest thnx for the help, and im gonna post again with the script.(hoping to make another 1 for c++ too)

o and thnx for ur help guys :D

---

### Post by ad_267 on 2008-08-24
Does it have to be in a terminal? I don't have much experience with java applications but possibly a better idea is to use zenity to show a text dialog box of the output.

A simple example just listing files would be:
```

ls | zenity --title "List of Files" --text-info

```

So maybe you could use something like:
```

output=`javac`+`java`
echo "$output" | zenity --title "Java" --text-info

```

---

