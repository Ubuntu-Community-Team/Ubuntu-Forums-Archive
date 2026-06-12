---
title: "[BASH/SH] Set a string's value to the output of a command"
date: 2008-10-07
forum: General Help
---

### Post by Dthdealer on 2008-10-07
I want to use the output of the command 'tty' in an if statement, so I used this line to set the output of that command as the value of the $tty string.
```
$tty='tty'
```
Unfortunately I get the error message that tty is not a command.
```
bash: =tty: command not found
```
How would I set the value of that string to the output of the tty command?

N.B. After that I use the information to see if the user has logged into TTY1 to TTY 6 (/dev/tty?) or is using a console window on TTY7 (/dev/pts/?).

---

### Post by lakris61 on 2008-10-07
Hi,
first use another name for clarity, second do not use the $ when You want to assign a value, third, I guess You want to be using back ticks, and not quotes. A recommendation is to use $(command) because it is easier to read, so try

curr_tty=$(tty)
echo $curr_tty

/Lakris

---

### Post by Dthdealer on 2008-10-07
Thanks, but now I get the error message
```
bash: [/dev/pts/0: No such file or directory
```
When using the conditional statement
```
if [$curr_tty = "/dev/pts/"?]
```
BASH for some reason thinks I'm checking if a directory exists, even though I haven't written any parameters to do so.

---

