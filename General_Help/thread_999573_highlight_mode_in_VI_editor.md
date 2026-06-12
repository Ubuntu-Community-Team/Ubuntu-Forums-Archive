---
title: "highlight mode in VI editor?"
date: 2008-12-02
forum: General Help
---

### Post by abhilashm86 on 2008-12-02
whenever i do program using vi editor i am unable to get keywords and other functions highlightned,so sometimes linking and debugging becomes complicated,so pls help to highlight keywords.........:)

---

### Post by sdennie on 2008-12-02
Many people find the vim-full package (which contains the syntax highlighting among other things) the most productive way to use vim.  Try:

```

sudo apt-get install vim-full

```

---

### Post by king_lear on 2008-12-02
You can use ":syntax on" to turn the syntax on everytime you use vim
else open /etc/vim/vimrc
find the line "syntax off"
and change it to "syntax on" to turn on syntax highlighting by default

---

### Post by abhilashm86 on 2008-12-02
so according to u,should we use vim instead of vi,so to open a new file of c program,i need to
vim matrix.c

is this right?

---

### Post by abhilashm86 on 2008-12-02
hey king_lear where is that option
Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
"syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark


what should be status of set background?

---

### Post by sdennie on 2008-12-02
You can use either vi or vim.  On some flavors of unix they may be different commands but, on linux, they will generally point to the same thing.  To get syntax highlighting to work, you will need the vim-full package (or at the very least vim-common and vim-runtime).

---

