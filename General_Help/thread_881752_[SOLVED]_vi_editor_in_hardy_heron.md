---
title: "[SOLVED] vi editor in hardy heron"
date: 2008-08-06
forum: General Help
---

### Post by sulekha on 2008-08-06
Hi ,


i find it very difficult to the edit the files such as
/etc/hosts, /etc/network/interfaces .... using vi editor , in ubuntu 8.04, has the commands changed ?

---

### Post by kihjin on 2008-08-06
You are really using vi or are you using vim? Check out your /etc/vim/vimrc file, make sure it's to your liking. 

Specifically make sure either **set nocompatible** is set or if compatible is set, comment it out!

Also you might have a conflicting .vimrc in your home directory, check that out too.

---

### Post by sulekha on 2008-08-07
> **kihjin said:**
> You are really using vi or are you using vim? Check out your /etc/vim/vimrc file, make sure it's to your liking. 

Specifically make sure either **set nocompatible** is set or if compatible is set, comment it out!

Also you might have a conflicting .vimrc in your home directory, check that out too.



the following are the contents of my /etc/vim/vimrc file,

i haven't seen an entry by name **set nocompatible** and there is no .vimrc in my home directory



" All system-wide defaults are set in $VIMRUNTIME/debian.vim (usually just
" /usr/share/vim/vimcurrent/debian.vim) and sourced by the call to :runtime
" you can find below.  If you wish to change any of those settings, you should
" do it in this file (/etc/vim/vimrc), since debian.vim will be overwritten
" everytime an upgrade of the vim packages is performed.  It is recommended to
" make changes after sourcing debian.vim since it alters the value of the
" 'compatible' option.

" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
runtime! debian.vim

" Uncomment the next line to make Vim more Vi-compatible
" NOTE: debian.vim sets 'nocompatible'.  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
"syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark

" Uncomment the following to have Vim jump to the last position when
" reopening a file
"if has("autocmd")
"  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
"    \| exe "normal g'\"" | endif
"endif

" Uncomment the following to have Vim load indentation rules according to the
" detected filetype. Per default Debian Vim only load filetype specific
" plugins.
"if has("autocmd")
"  filetype indent on
"endif

" The following are commented out as they cause vim to behave a lot
" differently from regular Vi. They are highly recommended though.
"set showcmd		" Show (partial) command in status line.
"set showmatch		" Show matching brackets.
"set ignorecase		" Do case insensitive matching
"set smartcase		" Do smart case matching
"set incsearch		" Incremental search
"set autowrite		" Automatically save before commands like :next and :make
"set hidden             " Hide buffers when they are abandoned
"set mouse=a		" Enable mouse usage (all modes) in terminals

" Source a global configuration file if available
" XXX Deprecated, please move your changes here in /etc/vim/vimrc
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif

---

### Post by kpkeerthi on 2008-08-07
Install this package
```
sudo aptitude install vim-full
```

---

