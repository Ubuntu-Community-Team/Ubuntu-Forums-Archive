---
title: "Resetting Terminal title (from shell script)"
date: 2008-09-23
forum: General Help
---

### Post by rwigle on 2008-09-23
I have tried to change the terminal title a number of times in a (bash) shell script and I can't get it to work. 

I run a program that generates a lot of screen output and I'd like to see what stage the processing is at. In a Windows batch file I used to do:

title "Solving the baseline"
gams baseline
title "Solving the first experiment"
gams first

I tried the following in a shell script, but it seems to do nothing.

PS1="\[\033]2; Solving baseline $sc\007\] \h: "

If I type that (literally) in terminal it works as I expect. (sc has been set)

Thanks in advance.

This is bash under Hardy Heron.

---

### Post by tCarls on 2008-09-24
I don't think any environment variables set in a shell script will stick unless you source it.

Try running "source script.sh" instead of "./script.sh". (alternatively you can try ". script.sh")

---

### Post by spibou on 2008-09-24
> **rwigle said:**
> I have tried to change the terminal title a number of times in a (bash) shell script and I can't get it to work. 

I run a program that generates a lot of screen output and I'd like to see what stage the processing is at. In a Windows batch file I used to do:

title "Solving the baseline"
gams baseline
title "Solving the first experiment"
gams first

I tried the following in a shell script, but it seems to do nothing.

PS1="\[\033]2; Solving baseline $sc\007\] \h: "


What you're trying to do depends, if possible, on which terminal emulator you're using. In any case, based on what you posted, doing ```
echo "\[\033]2; Solving baseline $sc\007\] \h: "
```will probably work.

---

### Post by rwigle on 2008-09-26
Thanks to both of you for trying, but what you suggested also doesn't work.

(As asked this is gnome-terminal.)

What I can't figure out is why my original attempt works if I type it in at an open gnome terminal, but not if I run a script with the exact same text in it. (Quoting, something?)

---

### Post by spibou on 2008-09-26
```
printf '\033]2;%s\007' "your_string"
```
will work.

The reason that setting PS1 works from the command line but not from a script is that BASH prints the output of PS1 as part of prompting. On the other hand when running a script BASH doesn't print PS1 at all so the content of PS1 is irrelevant. But that's not the full story. BASH interprets certain sequences of characters specially when they appear as part of PS1. I had forgotten about that in my previous reply. Have a look inside the BASH man page in the section titled "PROMPTING". So when prompting, BASH prints the output of the PS1 variable *after* interpreting those sequences. The end result is equivalent to the printf statement I gave above.

Another thing to know is that gnome-terminal emulates the behaviour of xterm so for similar questions Google for "xterm escape sequences".

---

### Post by rwigle on 2008-09-26
That does it......

I am just trying to port a bunch of batch files to shell files and learn as I go. So it's still a bit of greek to me....

Also thanks re gnome-terminal=xterm (I thought so, but wasn't sure.)

---

### Post by sapn on 2008-12-19
> **spibou said:**
> ```
printf '\033]2;%s\007' "your_string"
```
will work.

Thanks for the tip, very useful :D

---

