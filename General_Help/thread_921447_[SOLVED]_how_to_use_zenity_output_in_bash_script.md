---
title: "[SOLVED] how to use zenity output in bash script?"
date: 2008-09-16
forum: General Help
---

### Post by jakonj on 2008-09-16
Hello,

I love zenty and i would like to use it in some of my scripts but how to use it`s uotput?

Example:
I would like to open file, that i selected in zenity, in nano. Zeniti output is like this:
```
krak@ubuntu:~$ zenity --file-selection
/home/krak/.asunder
krak@ubuntu:~$ 
```

WHat to use this output in script?
tnx

---

### Post by loell on 2008-09-16
try 

```
ans=$(zenity --file-selection); echo $ans
```

---

### Post by jakonj on 2008-09-16
it works. I used:
```
ans=$(zenity --file-selection);
```
So now i can manuipulate with it :)

tnx

---

### Post by jjpcexpert on 2010-02-22
Another issue to raise (this thread is related)

How do I run commands like this

If we let ```
$runcommand=xfce4-panel
``` (just an example), then how do I run it? Do it run it like ```
This:
$runcommand
``` or what? As in I need this for a shell script for a Zenity-based run dialog which displays some options to run a program.
(I'm a scot :) )

---

### Post by bodhi.zazen on 2010-02-22
runcommand='/full/path/to/command'

$runcommand

---

### Post by jjpcexpert on 2010-02-22
I understand what you mean here. What if it can be run with just its name? eg runcommand=xterm
$runcommand

Oh and you obviously were the first to spot it.

---

### Post by bodhi.zazen on 2010-02-22
You can use xterm, but scripts often run with a minimal $PATH , so, IMO best to specify the full path.

---

### Post by Jose Catre-Vandis on 2010-02-22
> **loell said:**
> try 

```
ans=$(zenity --file-selection); echo $ans
```

Also, put the output in double quotes, just in case you have spaces in the file name

```
ans=$(zenity --file-selection); xfce4-terminal -x nano "$ans"
```

---

