---
title: "Getting rid of VIM"
date: 2008-10-05
forum: General Help
---

### Post by maxorator on 2008-10-05
I was wondering about what VIM is like. Downloaded, compiled, installed, piece of cake. But then, I couldn't find out how to launch it. It didn't appear on any application lists (except the package manager) and when I did "vim test.c" then it only showed me the contents of the file in terminal, nothing else (not much of an IDE). So I thought it wasn't worth the mess. I went to package manager and tried to remove VIM. When I selected the package, it also told me that it needs to remove "ubuntu-minimal", which of course is out of question. Now I'm thinking of manually deleting all files associated with it, but how would it affect the package manager?

---

### Post by p_quarles on 2008-10-05
Vim is a basic part of the Ubuntu installation, and you already had the pre-installed version before you compiled your own copy. To remove the copy you installed, you should be able to cd to the directory in which you compiled the program and run:
```
make uninstall
```
Removing the copy that is installed by default is not recommended. If I recall correctly, vi is part of the UNIX specification. 

As for it not being "much of an IDE" -- it's a modal editor, and therefore very unlike the visual editors which are shipped with Windows and OS X machines (though OS X, of course, complies with the Single UNIX Specification, so ships with vim). There are many good tutorials that can guide you through the basics if you ever decide to give it another shot.

---

### Post by oblidor on 2008-10-05
> **maxorator said:**
> I was wondering about what VIM is like. Downloaded, compiled, installed, piece of cake. 

Don't download software and compile yourself. First go to your System menu and start Synaptic Package Manager and check if the software is there. If it is, then install it. It will be much less painful and things will work. Vim is in there and you can easily check it out. Then afterwards if you want to uninstall you can do that easily too.

---

### Post by kdcoetzee on 2008-10-05
And if you decide to use Vim install the full package of it.

```
 sudo apt-get install vim-full 
```

Then open up /etc/vim/vimrc, and remove all the commits that is in front of these:

```

syntax on

set background=dark

if has("autocmd")
  filetype indent on
endif

set showcmd		" Show (partial) command in status line.
set showmatch		" Show matching brackets.
set ignorecase		" Do case insensitive matching
set smartcase		" Do smart case matching
set incsearch		" Incremental search
set autowrite		" Automatically save before commands like :next and :make
set hidden              " Hide buffers when they are abandoned
set mouse=a	

```

Vim is a brilliant text editor. don't "throw" it away because it is in a terminal.

---

### Post by maxorator on 2008-10-07
> **Juggernaut_KDC said:**
> Vim is a brilliant text editor. don't "throw" it away because it is in a terminal.
So... it's true? It IS in a terminal? :|

I mean, I never imagined an IDE can be non-graphical. I've been using Code::Blocks and GEdit, but was looking for something more. To be honest, Vim sounds more like a source code analyzer than an editor. :)

---

### Post by bodhi.zazen on 2008-10-07
LOL

If you wish to run vim in X, try gvim

```
sudo apt-get install vim-full
```

Then launch it from your menu or 

```
gvim
```

---

### Post by sdennie on 2008-10-07
> **maxorator said:**
> So... it's true? It IS in a terminal? :|

I mean, I never imagined an IDE can be non-graphical. I've been using Code::Blocks and GEdit, but was looking for something more. To be honest, Vim sounds more like a source code analyzer than an editor. :)

I think it depends on your definition of an editor.  Some people are more comfortable with lots of buttons and using the mouse to do things.  Vim has a lot of IDE-like functionality but, as you've noticed, it's not accessed with the mouse but by typing (though, you get menus if you use gvim).  There is a fairly steep learning curve when you first start using vim but, once you understand how it works and get your fingers trained to use it, for many people, it's difficult to imagine using anything else.

---

### Post by maxorator on 2008-10-07
So, does Vim manage projects too or do I have to mess with the files manually?

Do I have to create the makefile manually? :?

Err... one more thing - how do I actually edit a file in terminal?

---

### Post by bodhi.zazen on 2008-10-07
> **maxorator said:**
> So, does Vim manage projects too or do I have to mess with the files manually?

Do I have to create the makefile manually? :?

Err... one more thing - how do I actually edit a file in terminal?

To edit files in a terminal you can use nano or vim.

To learn vim , if you so desire, I suggest you start with any of the many tutorials :

[http://blog.interlinked.org/tutorials/vim_tutorial.html](http://blog.interlinked.org/tutorials/vim_tutorial.html)

======

What do you mean by "manage projects"?

---

### Post by Tom Morris on 2008-10-07
Vim isn't Eclipse or Visual Studio (etc.) if that's what you are after. And Vim has a fairly steep learning curve. I just started using it last week as a result of setting up a box with Linux on it (my main computer runs OS X, and I use TextMate on there).

It's worth learning Vim, as it's sort of a transcendent editor (like emacs, which I started learning before realising that Vim better fits how I think). You can use it in a GNOME GTK+ window, or in a terminal, or in a Mac or Windows application or even - with a bit of work - inside a Firefox form field. Where it's even more useful is when you are SSH-ed into some other box and need to edit some files.

Firstly, yes, change the settings on your /etc/vim/vimrc, or set up your .vimrc and .vim folders. Run vimtutor and follow the tutorial.

---

