---
title: "Vi(m) regexp substitution help needed"
date: 2008-09-08
forum: General Help
---

### Post by eentonig on 2008-09-08
all you regexp guru's, can someone give me some guidance?

I need to match a pattern that 
- starts with 'spawn...' 
- continues over several lines and 
- ends with 'OrderID'

And I want to replace them with just '\tOrderID'

But I'm having problems to have vim match a pattern that continues over multiple lines.

---

### Post by justleen on 2008-09-08
input:
```
all you regexp guru's, can someone give me some guidance?

I need to match a pattern that
- starts with 'spawn...'
- continues over several lines and
- ends with 'OrderID'

And I want to replace them with just '\tOrderID'

But I'm having problems to have vim match a pattern that continues over multiple lines.
```

```

:%s/spawn.*\n\(.*\n\).*.OrderID/\tOrderID/

```

output:```
all you regexp guru's, can someone give me some guidance?

I need to match a pattern that
- starts with ' OrderID'

And I want to replace them with just '\tOrderID'

But I'm having problems to have vim match a pattern that continues over multiple lines.

```

like that?

---

### Post by eentonig on 2008-09-08
That's what I would have thought, yes. but I get an error message that the search pattern isn't found.


I'll give you some real data 
> spawn ssh username@ipaddress


Please note that this system is meant as hop-system. i.e. you log in to this
system and then another. It is not meant for running advanced scripts or
as a production environment.

When your password is about to expire, use the 'passwd' utility to change your password. If you do not change your password before it expires your account will be locked.

...(text continues)
Trying ipaddress ...        OrderID:

---

### Post by justleen on 2008-09-08
errr... quite baffling.. I'll try some more here..

---

### Post by eentonig on 2008-09-08
Thanks.

This might be usefull as well. I'm running Ubuntu in AndLinux, because I'm not allowed to install linux on the laptop. 

> root@andLinux:~/bin# vim --version
VIM - Vi IMproved 7.1 (2007 May 12, compiled Jan 31 2008 12:05:33)
Included patches: 1-138
Compiled by [email]buildd@rothera.buil[/email]dd
Huge version without GUI.  Features included (+) or not (-):
+arabic +autocmd -balloon_eval -browse ++builtin_terms +byte_offset +cindent
-clientserver -clipboard +cmdline_compl +cmdline_hist +cmdline_info +comments
+cryptv +cscope +cursorshape +dialog_con +diff +digraphs -dnd -ebcdic
+emacs_tags +eval +ex_extra +extra_search +farsi +file_in_path +find_in_path
+folding -footer +fork() +gettext -hangul_input +iconv +insert_expand +jumplist
 +keymap +langmap +libcall +linebreak +lispindent +listcmds +localmap +menu
+mksession +modify_fname +mouse -mouseshape +mouse_dec +mouse_gpm
-mouse_jsbterm +mouse_netterm +mouse_xterm +multi_byte +multi_lang -mzscheme
-netbeans_intg -osfiletype +path_extra -perl +postscript +printer +profile
+python +quickfix +reltime +rightleft -ruby +scrollbind +signs +smartindent
-sniff +statusline -sun_workshop +syntax +tag_binary +tag_old_static
-tag_any_white -tcl +terminfo +termresponse +textobjects +title -toolbar
+user_commands +vertsplit +virtualedit +visual +visualextra +viminfo +vreplace
+wildignore +wildmenu +windows +writebackup -X11 -xfontset -xim -xsmp
-xterm_clipboard -xterm_save
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
      user exrc file: "$HOME/.exrc"
  fall-back for $VIM: "/usr/share/vim"
Compilation: gcc -c -I. -Iproto -DHAVE_CONFIG_H     -O2 -g -Wall     -I/usr/include/python2.5 -pthread
Linking: gcc   -L/usr/local/lib -o vim       -lncurses -lgpm    -L/usr/lib/python2.5/config -lpython2.5 -lutil -lm -Xlinker -export-dynamic -Wl,-O1 -Wl,-Bsymbolic-functions


and
> root@andLinux:~/bin# uname -a
Linux andLinux 2.6.22.18-co-0.7.3 #1 PREEMPT Wed Apr 16 18:50:10 UTC 2008 i686 GNU/Linux


---

### Post by hugmenot on 2008-09-08
```
%s/spawn\_.\{-}OrderID/\tOrderID/
```

Using \_.* instead of .* can be compute intensive. \{-} is the non-greedy version of the kleene star.

---

### Post by eentonig on 2008-09-09
I'll try this later version later on.

For now, I wrote a bash script that selected those lines one by one and then deleted them from the source file.

---

### Post by justleen on 2008-09-09
And so another day went by with a learning lesson! Cheers, Hugh-me-Not!

---

### Post by hugmenot on 2008-09-09
Be aware that these constructs are Vim-specific. Other regex engines don&#8217;t have non-greedy patterns, or they use a different notation.

A really useful help page is
```
:help pattern-overview
```

But the preceding sections are also instructive.

---

