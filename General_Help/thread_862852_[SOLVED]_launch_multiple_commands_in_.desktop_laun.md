---
title: "[SOLVED] launch multiple commands in .desktop launchers"
date: 2008-07-17
forum: General Help
---

### Post by joshsmith on 2008-07-17
say if i do: right click on panel, add to panel, custom application launcher. then choose:
type: application
name: my app
command: totem && gedit
comment: 

then clicking on it doesnt work. clicking on the launcher produces no visible output. it doesnt run either of the commands.

running
```

totem && gedit

```
in a terminal does exactly what i would like. ie runs totem, then gedit when totem closes.

so, what do i need to do to make it work in the launchers? 

i note that launchers can have arguments, so i could make my own script which parses arguments and turn them into a command, much like how
```

`echo totem && gedit`

```
(` included) works in the terminal [again doesnt work for launcher files] 

the command would then be in the form
```

myscript totem AND gedit

```
where myscript read the arguments and runs the command
```
 
totem && gedit

```
i feel this would have a chance of working

i would rather not have to use this kind of script, as it is not as portable as it should be, and as i am probably missing something. so any ideas?

---

### Post by mc4man on 2008-07-17
> say if i do: right click on panel, add to panel, custom application launcher. then choose:
type: application
name: my app
command: gnome-terminal && gedit
comment: 
for what you first mentioned choose under type - Application in terminal and just use gedit as command or
use type - application and again just use gedit or use command  gksudo gedit

---

### Post by joshsmith on 2008-07-17
ok poor choice of example applications. what i really meant was just two distinct applications. say running
```

gedit && totem

```
to run one after the other
or 
```

gedit & totem

```
to run them together.

ill change my original post

---

### Post by mc4man on 2008-07-17
Well, create a shell script and use it's paths  as command in the launcher, the type set as you prefer

or make 2 scripts and 2 launchers for both ways

---

### Post by joshsmith on 2008-07-18
yeah i could do that, but its a messy way to do things. surely there is a simpler way. if desktop launchers can run my script from a text file, surely it can just run the contents of my script

i should just be able to write
gedit && totem
in the command box

if there is no way to do that directly, i should be making a bug report, unless you know why that shouldnt be possible

i have often wanted to make lots of items start up from the sessions menu that run something like
sleep 4m && {programname}
its very messy to have to make 4 scripts and give the path of each rather than just typing in this very simple command

---

### Post by cross157 on 2008-11-26
This is precisely what I want, so i'm bumping this thread. I want to create a custom launcher for four program to run independently.

Example, ```
vlc & skype
``` that works from a command line but not a custom launcher, wtf? Any help is appreciated thanks in advance.

---

### Post by joshsmith on 2009-01-11
i made a script called hackexec with contents:

echo $@ > /tmp/hackyrunscript
chmod +x /tmp/hackyrunscript
/tmp/hackyrunscript

and put it into a folder in my PATH. Then from gnome launchers i can do

```

hackexec "totem; gedit"

```

and it will run whatever is in the speech marks, properly

---

### Post by staticsage on 2009-09-07
Sorry for bumping an old post, but instead of creating the hackexec script, you can just do:

```
sh -c "gedit && gcalctool"
```

---

### Post by DaithiF on 2009-09-07
just to add the reason why && doesn't work in a launcher -- its because && is a feature of the shell, and the launcher isn't a shell, its a much simpler environment for running commands.  Other shell features don't work either, so for example, creating a launcher with the command:
```
echo hello > ~/hello.out
```
it might be expected that this would write out 'hello' to the file 'hello.out' in your home directory, but the expansion of ~ into your home directory is a shell feature, so won't work.  This version will work as expected.
```
sh -c "echo hello > ~/hello.out"
``` 
so the bottom line is that if want to use shell constructs in a launcher command (joining commands, expanding variables, etc), then make sure your launcher actually invokes a shell to run that command!

---

