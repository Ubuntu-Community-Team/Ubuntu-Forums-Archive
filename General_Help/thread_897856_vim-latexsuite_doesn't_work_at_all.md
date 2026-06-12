---
title: "vim-latexsuite doesn't work at all"
date: 2008-08-22
forum: General Help
---

### Post by sampei01 on 2008-08-22
Hi, I installed vim-full and vim-latexsuite and I can't use that plugin. Vim doesn't find its command, it's like the vim-latexsuite package is not installed. Even "sudo vim-addons -w install latex-suite" doesn't work and after that "vim-addons status" says that the plugin status in "broken" and not "installed". Changing the "runtimepath" doesn't work too. How could I fix it? Thank in advance.

---

### Post by LateNiteTV on 2008-08-22
add the following to your .vimrc file:
```
set runtimepath+=/usr/share/vim/addons/
```

---

### Post by sampei01 on 2008-08-23
> **LateNiteTV said:**
> add the following to your .vimrc file:
```
set runtimepath+=/usr/share/vim/addons/
```

It doesn't work. the commands ```
gvim file.tex
``` and ```
gvim file
``` say:
```
Error detected while processing /usr/share/vim/addons/plugin/remoteOpen.vim:
line   37:
E174: Command already exists: add ! to replace it
line   38:
E174: Command already exists: add ! to replace it

```

Those lines are:
```
com -nargs=1 RemoteOpen :call RemoteOpen('<args>')
com -nargs=? RemoteInsert :call RemoteInsert('<args>')

```

Changing ```
com
``` to ```
com!
``` and ```
"com
``` stops the warning about remoteOpen.vim but latex-suite still don't work.

Any hint?

---

### Post by hugmenot on 2008-08-23
Sounds like it is loaded twice. Can you check if you have two installations, or if you somehow load it in your rc files? If installed system-wide as an addon you don&#8217;t need to load it there.

---

### Post by sampei01 on 2008-08-23
I removed ~/.vim and didn't get that error, but latex-suite doesn't work. I removed the runtimepath from ~/.vimrc and used vim-addons, but the error came back:
```
$ sudo vim-addons -w install latex-suite
Info: installing removed addon 'latex-suite'
Info: Rebuilding tags since documentation has been modified ...
Processing /var/lib/vim/addons/doc/
Info: done.
$ sudo vim-addons status
# Name                     User Status  System Status 
latex-suite                 removed       broken        
matchit                     removed       removed       
$ gvim /tmp/file.tex
Error detected while processing /var/lib/vim/addons/plugin/remoteOpen.vim:
line   37:
E174: Command already exists: add ! to replace it
line   38:
E174: Command already exists: add ! to replace it

```

I don't know why it says that latex-suite is broken, I've just installed it.

---

### Post by hugmenot on 2008-08-23
Can you purge the package, and then reinstall?

sudo aptitude purge vim-latexsuite

then 

vim-addons

then

sudo aptitude install vim-latexsuite

then 

vim-addons

then sudo vim-addons -v install latex-suite

---

### Post by sampei01 on 2008-08-23
```

sampei@ubuntu:~$ vim-addons
# Name                     User Status  System Status
latex-suite                 removed       removed
matchit                     removed       removed
sampei@ubuntu:~$ sudo aptitude purge vim-latexsuite
[everything goes right]
sampei@ubuntu:~$ vim-addons
# Name                     User Status  System Status
matchit                     removed       removed
sampei@ubuntu:~$ sudo aptitude install vim-latexsuite
[everything goes right]
sampei@ubuntu:~$ vim-addons
# Name                     User Status  System Status
latex-suite                 removed       removed
matchit                     removed       removed
sampei@ubuntu:~$ sudo vim-addons -v install latex-suite
Info: installing removed addon 'latex-suite'
Info: Rebuilding tags since documentation has been modified ...
Info: executing '/usr/bin/helpztags /home/sampei/.vim/doc/'
Processing /home/sampei/.vim/doc/
Info: done.
sampei@ubuntu:~$ vim-addons
# Name                     User Status  System Status
latex-suite                 broken        removed
matchit                     removed       removed
sampei@ubuntu:~$

```

---

### Post by hugmenot on 2008-08-23
and with -w for system-wide?

edit: ah, that was my own typo ...

---

### Post by sampei01 on 2008-08-23
I repeated the whole process with '-w' instead of '-v' and nothing changed
```
# Name                     User Status  System Status 
latex-suite                 removed       broken        
matchit                     removed       removed     
```

---

### Post by hugmenot on 2008-08-23
No idea then. Sorry.

---

### Post by omer.qadir on 2008-11-17
Don't know if you found a solution yet... but check out

[http://ubuntuforums.org/showthread.php?t=577217](http://ubuntuforums.org/showthread.php?t=577217)




> **hugmenot said:**
> No idea then. Sorry.

---

### Post by philofellow on 2009-05-01
try to get System Statues of latex-suite as Installed in vim-addons.  
Then use "sudo vim file.tex" instead of "vim file.tex"
And it will work. 
I think it's a bug.

See details in [http://philofellow.blogspot.com/2009/05/vimlatexsuite-in-ubuntu-904.html](http://philofellow.blogspot.com/2009/05/vimlatexsuite-in-ubuntu-904.html)

Good luck.

---

### Post by Geraba on 2010-01-15
I have a similar problem... When I didn't the "vim-addons install -w latex-suite", my gvim was running just fine... But it seemed that latex-suite was broken...
Then I run this command, now I have the same error...

---

### Post by geo909 on 2010-01-22
Hey guys,

I ran into this page when I was looking for a solution to a similar (the same?) problem. What I found here did the job for me:
[http://vim-latex.sourceforge.net/documentation/latex-suite/recommended-settings.html](http://vim-latex.sourceforge.net/documentation/latex-suite/recommended-settings.html)

---

