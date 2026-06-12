---
title: "How to add color in source code ?"
date: 2008-08-11
forum: General Help
---

### Post by kingkong22 on 2008-08-11
Hi,
  Does anyone know how to add colors in source code so that 
the sytax of key words are highlighted. (i.e. in c/c++ code).

Thanks !!!

---

### Post by jocko on 2008-08-11
In gedit, go to view --> syntax highlighting --> Sources --> C/C++/Obj C Header. That should do it. Don't know about other editors, but I guess there would be something similar.

**[COLOR=Red]EDIT:[/COLOR]** Actually my gedit automatically detects the syntax and uses the appropriate syntax highlighting.
I found a setting in gconf-editor where it can be enabled or disabled. Open up gconf-editor, browse to /apps/gedit-2/preferences/syntax_highlighting and make sure it's enabled.

---

### Post by kingkong22 on 2008-08-11
I want it done within vim ev. Thanks a lot!!!

---

### Post by jerome1232 on 2008-08-11
for vim it's :syntax enable

I edited my .vimrc file to have syntax enable in it so vim always does this when I open a file.

---

### Post by kingkong22 on 2008-08-11
Could you show me .vimrc file contents ? thank you !!!

---

### Post by jerome1232 on 2008-08-11
well mine just looks like this right now
```
syntax enable
```
it'll probably grow as I learn more commands in vim that make life easier for me.

---

### Post by kingkong22 on 2008-08-11
Error detected while processing /home/mjiang/.vimrc:
line    1:
E319: Sorry, the command is not available in this version: syntax enable
Press ENTER or type command to continue

above messages shows up after I made .vimrc with the following one line as you provided:
syntax enabe

How come I get the error ? Thanks !!!

---

### Post by jerome1232 on 2008-08-11
are you using vim-tiny??? It's what is installed by default on Ubuntu

Try sudo apt-get install vim to make sure you have the full version of vim

---

### Post by kingkong22 on 2008-08-11
After installing full vim, it does job ! great ! thank you so much !!!!!!

---

### Post by carolinason on 2008-09-23
I simply install vim-runtime, it allows for syntax highlighting and doesn't add a lot of extraneous files.

---

