---
title: "About VI editor"
date: 2008-07-25
forum: General Help
---

### Post by satimis on 2008-07-25
Hi folks,


Ubuntu 7.04 server amd64


I didn't run VI for sometimes after turning to NANO.


Just tested VI on terminal as follow;

$ vi testing
:a
typing the text here
(pressing [ESC] key)
ZZ [Enter]

it didn't save and exit.  Then continued

pressing [Ctrl]-[
ZZ [Enter]

still didn't work.

Continued again
:wq [Enter]

Also without result.


Please shed me some light.  TIA


B.R.
satimis

---

### Post by pauper on 2008-07-26
```
:~$ ls -l /usr/bin/vi
lrwxrwxrwx 1 root root ... /usr/bin/vi -> /etc/alternatives/vi
:~$ ls -l /etc/alternatives/vi
lrwxrwxrwx 1 root root ... /etc/alternatives/vi -> /usr/bin/vim.gnome
```

That is on Gutsy Desktop 32 bit. Run ":version". The default is, I believe,
[corrected:] vim.tiny. This should bring you up to date:

```
vimtutor
```

---

### Post by satimis on 2008-07-26
> **pauper said:**
> ```
:~$ ls -l /usr/bin/vi
lrwxrwxrwx 1 root root ... /usr/bin/vi -> /etc/alternatives/vi
:~$ ls -l /etc/alternatives/vi
lrwxrwxrwx 1 root root ... /etc/alternatives/vi -> /usr/bin/vim.gnome
```

That is on Gutsy Desktop 32 bit. Run ":version". The default is, I believe, vim.basic.
This should bring you up to date:

```
vimtutor
```
Hi pauper,


Thanks for your advice.


I found following tutorial;

UNIX and Linux
Vim Tutorial
[http://www.biochem.ucl.ac.uk/~mckenzie/vim/tutorial.html](http://www.biochem.ucl.ac.uk/~mckenzie/vim/tutorial.html)


I can't manage the commands there, example;

```

Moving Around
start of line	0
end of line	$
left 	h
right 	l
down 	j
up 	k
back one word	b
forward one word	w
back one paragraph	{
forward one paragraph	}
go to line 33	33G

```

While typeing I need to go one line up, [ESC]+k not work.  Same as [ESC]+j


B.R.
satimis

---

### Post by Bachstelze on 2008-07-26
Works For Me™. Are you using [FONT="Courier New"]vi[/FONT] or [FONT="Courier New"]vim[/FONT]?

---

### Post by satimis on 2008-07-26
> **HymnToLife said:**
> Works For Me™. Are you using [FONT="Courier New"]vi[/FONT] or [FONT="Courier New"]vim[/FONT]?
Hi HymnToLife,


I see.  Sorry I made a mistake previously.  I should started vim NOT vi.


Thanks


B.R.
satimis

---

### Post by pauper on 2008-07-26
:h 'compatible'

```
'compatible' 'cp'	boolean	(default on, off when a |vimrc| or |gvimrc| file is found)
[right]global
{not in Vi}[/right]
	This option has the effect of making Vim either more Vi-compatible, or
	make Vim behave in a more useful way.
	This is a special kind of option, because when it's set or reset,
	other options are also changed as a side effect.  CAREFUL: Setting or
	resetting this option can have a lot of unexpected effects: Mappings
	are interpreted in another way, undo behaves differently, etc.  If you
	set this option in your vimrc file, you should probably put it at the
	very start.
	By default this option is on and the Vi defaults are used for the
	options.  This default was chosen for those people who want to use Vim
	just like Vi, and don't even (want to) know about the 'compatible'
	option.
	When a |vimrc| or |gvimrc| file is found while Vim is starting up,
	this option is switched off, and all options that have not been
	modified will be set to the Vim defaults.  Effectively, this means
	that when a |vimrc| or |gvimrc| file exists, Vim will use the Vim
	defaults, otherwise it will use the Vi defaults.  (Note: This doesn't
	happen for the system-wide vimrc or gvimrc file, nor for a file given
	with the |-u| argument).  Also see |compatible-default| and
	|posix-compliance|.
	You can also set this option with the "-C" argument, and reset it with
	"-N".  See |-C| and |-N|.
	Switching this option off makes the Vim defaults be used for options
	that have a different Vi and Vim default value.  See the options
	marked with a '+' below.  Other options are not modified.
	At the moment this option is set, several other options will be set
	or reset to make Vim as Vi-compatible as possible.  See the table
	below.  This can be used if you want to revert to Vi compatible
	editing.
	See also 'cpoptions'.

 option      + set value       effect~

'allowrevins'  off             no CTRL-_ command
'backupcopy'   Unix: "yes"     backup file is a copy
               others: "auto"  copy or rename backup file
'backspace'    ""              normal backspace
'backup'       off             no backup file
'cindent'      off             no C code indentation
'cedit'      + ""              no key to open the |cmdwin|
'cpoptions'  + (all flags)     Vi-compatible flags
'cscopetag'    off             don't use cscope for ":tag"
'cscopetagorder'  0            see |cscopetagorder|
'cscopeverbose'   off          see |cscopeverbose|
'digraph'      off             no digraphs
'esckeys'    + off             no <Esc>-keys in Insert mode
'expandtab'    off             tabs not expanded to spaces
'fileformats'+ ""              no automatic file format detection,
               "dos,unix"      except for DOS, Windows and OS/2
'formatoptions'+ "vt"          Vi compatible formatting
'gdefault'     off             no default 'g' flag for ":s"
'history'    + 0               no commandline history
'hkmap'        off             no Hebrew keyboard mapping
'hkmapp'       off             no phonetic Hebrew keyboard mapping
'hlsearch'     off             no highlighting of search matches
'incsearch'    off             no incremental searching
'indentexpr'   ""              no indenting by expression
'insertmode'   off             do not start in Insert mode
'iskeyword' + "@,48-57,_"      keywords contain alphanumeric
                               characters and '_'
'joinspaces'   on              insert 2 spaces after period
'modeline'   + off             no modelines
'more'       + off             no pauses in listings
'revins'       off             no reverse insert
'ruler'        off             no ruler
'scrolljump'   1               no jump scroll
'scrolloff'    0               no scroll offset
'shiftround'   off             indent not rounded to shiftwidth
'shortmess'  + ""              no shortening of messages
'showcmd'    + off             command characters not shown
'showmode'   + off             current mode not shown
'smartcase'    off             no automatic ignore case switch
'smartindent'  off             no smart indentation
'smarttab'     off             no smart tab size
'softtabstop'  0               tabs are always 'tabstop' positions
'startofline'  on              goto startofline with some commands
'tagrelative'+ off             tag file names are not relative
'textauto'   + off             no automatic textmode detection
'textwidth'    0               no automatic line wrap
'tildeop'      off             tilde is not an operator
'ttimeout'     off             no terminal timeout
'whichwrap'  + ""              left-right movements don't wrap
'wildchar'   + CTRL-E          only when the current value is <Tab>
                               use CTRL-E for cmdline completion
'writebackup'  on or off       depends on +writebackup feature
```

---

### Post by Bachstelze on 2008-07-26
There is a vimrc file by default in Debian/Ubuntu, and the 'compatible' option is therefore disabled (unless explicitly re-enabled).

---

### Post by pauper on 2008-07-26
> There is a vimrc file by default in Debian/Ubuntu,..

System-wide--yes, i.e. /etc/vim/vimrc and /usr/share/vim/vimrc, but no user
$HOME/.vimrc ([color=blue]1)[/color] see below).

> and the 'compatible' option is therefore disabled (unless explicitly re-enabled)

[highlight]Let see...[/highlight]

:version

VIM - Vi IMproved 7.1 (2007 May 12, compiled Oct  5 2007 00:47:59)
Included patches: 1-56
...

```
options.txt, lines 1522-1529:
When a |vimrc| or |gvimrc| file is found while Vim is starting up, this option
*(compatible)* is switched off, and all options that have not been modified will
be set to the Vim defaults.  Effectively, this means that when a |vimrc| or
|gvimrc| file exists, Vim will use the Vim defaults, otherwise it will use the
Vi defaults.  [i][font=freesans](Note: This doesn't happen for the system-wide vimrc or gvimrc
file, nor for a file given with the |-u| argument) ([color=blue]4)[/color] see below).[/font][/i]  Also see
|compatible-default| and |posix-compliance|.

starting.txt, lines 904-908:
*compatible-default*
_When Vim starts, the 'compatible' option is on._  This will be used when Vim
starts its initializations.  [i][font=freesans]But as soon as [color=blue]1)[/color] a user vimrc file is found,
or [color=blue]2)[/color] a vimrc file in the current directory, or [color=blue]3)[/color] the "VIMINIT" environment
variable is set, it will be set to _'nocompatible'_.[/font][/i]

[color=blue]2)[/color] options.txt, lines 2505-2514:
'exrc' 'ex'		boolean [highlight](default off)[/highlight]
global
{not in Vi}
Enables the reading of .vimrc, .exrc and .gvimrc in the current directory.  If
you switch this option on you should also consider setting the 'secure' option
(see |initialization|).  Using a local .exrc, .vimrc or .gvimrc is a potential
security leak, use with care!
also see |.vimrc| and |gui-init|.
This option cannot be set from a |modeline| or in the |sandbox|, for security
reasons.

[color=blue]3)[/color] starting.txt, lines 766-773, 786-790:
*VIMINIT* *.vimrc* *_vimrc* *EXINIT* *.exrc* *_exrc*
c. Four places are searched for initializations.  The first that exists is used,
the others are ignored.  The $MYVIMRC environment variable is set to the file
that was first found, unless $MYVIMRC was already set.
- The environment variable VIMINIT (see also |compatible-default|) (*)
	The value of $VIMINIT is used as an Ex command line.
- The user vimrc file(s):
 "$HOME/.vimrc" (for Unix and OS/2) (*)
...
- The environment variable EXINIT. The value of $EXINIT is used as an Ex
  command line.
- The user exrc file(s).  Same as for the user vimrc file, but with "vimrc"
  replaced by "exrc".  But only one of ".exrc" and "_exrc" is used, depending
  on the system.  And without the (*)!
```

```
:!echo $VIMINIT
:~$ vim



Press ENTER or type command to continue
```

```
[color=blue]4)[/color] starting.txt, lines 428-432:
-u {vimrc}	The file {vimrc} is read for initializations.  Most other
		initializations are skipped; see |initialization|.  This can
		be used to start Vim in a special mode, with special
		mappings and settings.  A shell alias can be used to make
		this easy to use.
```

Let's recap the default settings:

- $HOME/.vimrc does not exist (or $HOME/.gvimrc);
- exrc is not set;
- $VIMINIT is not set;
- $MYVIMRC is not set;
- no "-u" argument, i.e. "vim -u {vimrc}"

Ergo, you are running in "compatible" mode.

[edit:] I welcome your corrections :).


To satimis:

Check your current status:

:set compatible?

Offtopic, but something to be aware of in the future, please see ":h 'paste'"

---

### Post by fyo on 2008-07-26
Last I checked, Ubuntu defaults to **vim-tiny**, not the real (full) vim. Use apt-get or Synaptic to install the latest, greatest vim ;-)

---

### Post by Bachstelze on 2008-07-26
Right. I stand corrected. But that doesn't matter the slightest bit, because the devault system-wide vimrc *does* set 'nocompatible'.

---

### Post by Bachstelze on 2008-07-26
> **pauper said:**
> rc}"

Ergo, you are running in "compatible" mode.

[edit:] I welcome your corrections :).



From the default Debian system-wide vimrc:

```
" Uncomment the next line to make Vim more Vi-compatible
" NOTE: debian.vim sets 'nocompatible'.  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible
```

So I was wrong as to why 'nocompatible' is set by default in Debian, but the fact that it is remains.

---

### Post by pauper on 2008-07-26
I stand corrected :oops:.

```
[color=green]:~[/color]$ **find / -name vimrc 2> /dev/null**
/etc/vim/vimrc
/usr/share/vim/vimrc
[color=green]:~[/color]$ **grep -C 10 compatible /etc/vim/vimrc**
" [highlight]All system-wide defaults are set in $VIMRUNTIME/debian.vim[/highlight] (usually just
" /usr/share/vim/vimcurrent/debian.vim) and sourced by the call to :runtime
" you can find below.  If you wish to change any of those settings, you should
" do it in this file (/etc/vim/vimrc), since debian.vim will be overwritten
" everytime an upgrade of the vim packages is performed.  It is recommended to
" make changes after sourcing debian.vim since it alters the value of the
" 'compatible' option.

" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
[highlight]runtime! debian.vim[/highlight]

" Uncomment the next line to make Vim more Vi-compatible
" [highlight]NOTE: debian.vim sets 'nocompatible'.[/highlight]  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
"syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark

" Uncomment the following to have Vim jump to the last position when
[color=green]:~[/color]$ **cd /usr/share/vim**
[color=green]:/usr/share/vim[/color]$ **find . -name debian.vim**
./vim71/debian.vim
[color=green]:/usr/share/vim[/color]$ **grep -C 3 compatible ./vim71/debian.vim **

" Normally we use vim-extensions. If you want true vi-compatibility
" remove change the following statements
[highlight]set nocompatible[/highlight]       " Use Vim defaults instead of 100% vi compatibility
set backspace=indent,eol,start  " more powerful backspacing

" Now we set some defaults for the editor
--
set ruler               " show the cursor position all the time

" modelines have historically been a source of security/resource
" vulnerabilities -- disable by default, even when 'nocompatible' is set
set nomodeline

" Suffixes that get lower priority when doing tab completion for filenames.
```

[edit:]
All right, done a few tests with Hardy Live CD (desktop, 32 bit).

```
vi
:set compatible?
compatible
:q

vim
:set compatible?
nocompatible
:q
```

```
[color=green]:~[/color]$ **ls -l /usr/bin/vi**
lrwxrwxrwx 1 root root ... /usr/bin/vi -> /etc/alternatives/vi
[color=green]:~[/color]$ **ls -l /etc/alternatives/vi**
lrwxrwxrwx 1 root root ... /etc/alternatives/vi -> /usr/bin/vim.tiny
[color=green]:~[/color]$ **find / \( -name rofs -prune \) -o -name *vimrc* -print 2> /dev/null**
/usr/share/vim/vimrc
/usr/share/vim/vimrc.tiny
/etc/vim/vimrc
/etc/vim/vimrc.tiny
[color=green]:~[/color]$ **grep -C 5 compatible /etc/vim/vimrc.tiny**
" [highlight]Vim configuration file, in effect when invoked as "vi".[/highlight] The aim of this
" configuration file is to provide a Vim environment as compatible with the
" original vi as possible. Note that ~/.vimrc configuration files as other
" configuration files in the runtimepath are still sourced.
" When Vim is invoked differently ("vim", "view", "evim", ...) this file is
" _not_ sourced; /etc/vim/vimrc and/or /etc/vim/gvimrc are.

" Debian system-wide default configuration Vim
set runtimepath=~/.vim,/var/lib/vim/addons,/usr/share/vim/vimfiles,
/usr/share/vim/@VIMCUR@,/usr/share/vim/vimfiles/after,
/var/lib/vim/addons/after,~/.vim/after

[highlight]set compatible[/highlight]

" vim: set ft=vim:
```

So, as long as you invoke editor as "_vi_" and obey [post=5463223]*compatible-default*[/post] settings,
you are in _compatible_ mode.

> **fyo said:**
> Last I checked, Ubuntu defaults to vim-tiny, not the real (full) vim.

You are 100% right. :oops:

To satimis:

I apologize, I forgot to mention that I purged vim-tiny package long ago and
have vim, vim-gnome and dependencies installed, so the proper link is
/etc/alternatives/vi -> /usr/bin/vim.tiny (see the [post=5460573]original response[/post]:
/etc/alternatives/vi -> /usr/bin/vim.gnome).

---

