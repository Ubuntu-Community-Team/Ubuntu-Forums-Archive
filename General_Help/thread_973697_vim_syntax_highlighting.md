---
title: "vim syntax highlighting"
date: 2008-11-06
forum: General Help
---

### Post by fedex1993 on 2008-11-06
okay i just started C++ and i was using borland c++ on windows but on ubuntu i use vim alot for editing. Is there a possible way that i can get vim C++ syntax highlighting?

---

### Post by ad_267 on 2008-11-06
Create a file in your home directory called ".vimrc" and put this in it:
```
syntax on
```

My .vimrc looks like this:
```
syntax on
set cindent
set hlsearch
set tabstop=4
set shiftwidth=4
set expandtab
set smarttab
set softtabstop=4
set showmatch
```

---

### Post by fedex1993 on 2008-11-06
> **ad_267 said:**
> Create a file in your home directory called ".vimrc" and put this in it:
```
syntax on
```

My .vimrc looks like this:
```
syntax on
set cindent
set hlsearch
set tabstop=4
set shiftwidth=4
set expandtab
set smarttab
set softtabstop=4
set showmatch
```

can i see a screenshot of your vim setup?

---

### Post by fornix on 2008-11-06
You can put in those commands even inside vim by using Esc and then entering the commands after :
example :
:syntax on
:set cindent
:set tabstop=4
:set shiftwidth=4

These 4 commands would suffice for your C++ needs.

---

### Post by kdcoetzee on 2008-11-06
I usually just edit 

```

vi /etc/vim/vimrc

```

the stuff is already there. so just remove the hashes.
of the lines the previous people posted...

---

### Post by pansz on 2008-11-07
```

sudo apt-get install vim-full
cp /usr/share/vim/vim71/vimrc_example.vim ~/.vimrc
vi .vimrc

```

then you should get your syntax highlight.

please note the first line, ubuntu does not install a full version of vim by default, so you will not get syntax highlighting out-of-box.

---

### Post by kdcoetzee on 2008-11-07
> **pansz said:**
> ```

sudo apt-get install vim-full
cp /usr/share/vim/vim71/vimrc_example.vim ~/.vimrc
vi .vimrc

```

then you should get your syntax highlight.

please note the first line, ubuntu does not install a full version of vim by default, so you will not get syntax highlighting out-of-box.


Damn, I forgot about that.
That is the first package I install on a fresh install. And can't live without it.

---

