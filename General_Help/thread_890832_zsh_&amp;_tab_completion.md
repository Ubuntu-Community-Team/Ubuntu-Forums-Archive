---
title: "zsh &amp; tab completion"
date: 2008-08-15
forum: General Help
---

### Post by bismark on 2008-08-15
General zsh question here.

I'm having problems with tab complete listing the available commands
```

$ nm<tab>

```

It gives me (thats a space at the end)
```

$ nm 

```

Then if I hit <tab> again I get
```

$ nm 
file
bin/                  downloads/            new_zshrc             temp/                 
Desktop/              old_zshrc                         
Documents/            media/                PDF/

```

What I want it to do it go through the whole list of commands that start with `nm` such as nm, nmap, nm-applet, nmblookup, nm-editor, etc.

Can anyone point me in the right direction?

Thanks,
Bismark

---

### Post by ibuclaw on 2008-08-15
What does
```
/bin/echo $PATH
```
Produce?

Perhaps you are missing some binary paths in that variable...


Regards
Iain

---

### Post by bismark on 2008-08-15
No I've the check the path and all the programs are there.  I think it has to do with the fact that 'nm' is also program.

If I do 'n<tab>' I get a HUGE list.  However since 'nm' is also a program itself it automatically assumes that when I hit tab I want to jump to parameters.  'vi' has the same program.  'v<tab>' gives me a list which includes vi,vidmode,view,viewres,vigr,vim,etc. but 'vi<tab>' jumps to entering parameters.

I'm guessing it's something in my .zshrc and my tab completion setup but after a few days of trial and error I still haven't figured the right setting for it.

---

