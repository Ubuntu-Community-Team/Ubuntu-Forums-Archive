---
title: "Programs only run from /usr/bin/ not from Home"
date: 2005-11-24
forum: General Help
---

### Post by Roobert on 2005-11-24
Hi,

I downloaded teTeX via Synaptic (tetex base, bin, doc, and extra packages) and I can't get it to process my text file unless I cd to /usr/bin and run the commands from there. How do I set up Ubuntu to run teTeX (or any other program, for that matter) from any directory on my system?

Thanks!

---

### Post by oskude on 2005-11-24
that sounds like a bug or something, isnt "/usr/bin" in```
echo $PATH
```
?

---

### Post by Roobert on 2005-11-24
[QUOTE=oskude]that sounds like a bug or something, isnt "/usr/bin" in```
echo $PATH
```
?[/QUOTE]

Here's my $PATH:

$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:***/usr/bin***:/usr/bin/X11:/usr/games

---

### Post by oskude on 2005-11-24
ok, looks good. 
please post exactly what you typed and the error message you got...
(and please use CODE tag to post console stuff)

---

### Post by Roobert on 2005-11-24
Ok, I've overcome that problem....I was using "tetex" on the command line, and nothing was happening. Once I started using "tex test.tex" or "latex test.tex" as my command instead, the program seemed to work fine. I thought that installing tetex packages meant that typing "tetex" plus other commands would run the program....but it seems I need to use latex instead. Is this normal?

---

### Post by oskude on 2005-11-24
yeah, its sometimes litte hard to know how to run the program if its not the same name as used with synaptic or apt-get install...

me wonders if theres a way to look what (runnable) program names where installed with a package...

i know that when i do like "apt-get install puredata" that i have to use "pd" instead of "puredata" to run the program... but how should a newbie know this ?

---

