---
title: "Vim Mess up - How to fix?"
date: 2008-11-03
forum: General Help
---

### Post by paulsjv on 2008-11-03
I was wondering if any knew how to reset vim from command line?  Mine got royally screwed up (see attachment) and nothing I try to do seems to fix it.  Any thoughts?

---

### Post by taurus on 2008-11-03
Did you install the vim-full package?

```
sudo apt-get update
sudo apt-get install vim-full
```

---

### Post by paulsjv on 2008-11-03
yep it's the full package.

---

### Post by taurus on 2008-11-03
I assume you are talking about the yellow highlights.  Do you get the same yellow highlights when you are in vim from a console since I see that you are remotely connecting to your machine using PuTTY?

Have you looked in ~/.vimrc?

---

### Post by paulsjv on 2008-11-03
> **taurus said:**
> I assume you are talking about the yellow highlights.  Do you get the same yellow highlights when you are in vim from a console since I see that you are remotely connecting to your machine using PuTTY?

Have you looked in ~/.vimrc?

The behavior started when I copied something from a browser and went to my PuTTY session and pasted (Ctrl+v) into my vim session without first hitting "i" for --INSERT--.  Ever since I can't seem to revert vim back to the way it was.  Thanks for your help so far and any help in the future! :)

Below is my ~/.vimrc

```
syntax on       " turn on syntax highlighting

" Auto indent files
filetype indent on
set autoindent

set nu          " turn on line numbers
set hls         " highlight search
set ruler       " show the position of the cursor
set showmatch   " show matching parenthese
"set mouse=a    " use mouse everywhere

set wrap      " don't wrap lines
set smarttab    " use tabs at the start of a line, spaces elsewhere

" Setting colors for ebl files
au BufRead,BufNewFile *.ebl set filetype=ebl
au! Syntax ebl source ~${EXUSER}/.vim/ebl.vim

```

---

### Post by paulsjv on 2008-11-03
bump

---

### Post by geirha on 2008-11-03
Looks like you've searched for something that matches the entire file. What happens if you search for something else with ```
/something
``` ?

---

### Post by nnamdi on 2008-11-03
you could use gedit to edit your configurations

---

### Post by paulsjv on 2008-11-03
> **nnamdi said:**
> you could use gedit to edit your configurations

Unfortunately all I have is command line access. :(

---

### Post by paulsjv on 2008-11-03
> **geirha said:**
> Looks like you've searched for something that matches the entire file. What happens if you search for something else with ```
/something
``` ?
Woohoo! that worked!  The thing is I tried that and it didn't work. hm... Well none the less thanks a ton! :)

---

