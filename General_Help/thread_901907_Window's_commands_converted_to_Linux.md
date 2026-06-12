---
title: "Window's commands converted to Linux"
date: 2008-08-26
forum: General Help
---

### Post by RyanfromtheShire on 2008-08-26
cmd /k ping dragonzip.com

cmd /k tracert dragonzip.com

I need to run those through my terminal, how would I go about doing this?

---

### Post by sstusick on 2008-08-26
just type in > ping dragonzip.com

---

### Post by RyanfromtheShire on 2008-08-26
And I figured I just do 

```
tracert dragonzip.com
```

as well?

---

### Post by tuxxy on 2008-08-26
You could also just open **system > admin > network tools ** , this will provide a GUI frontend for the tools :)

---

### Post by RyanfromtheShire on 2008-08-26
Oh ok, thanks! :)

---

### Post by mssever on 2008-08-26
> **RyanfromtheShire said:**
> And I figured I just do 

```
tracert dragonzip.com
```as well?
I assume that tracert means trace route. In that case, the command is traceroute.

---

### Post by mrsteveman1 on 2008-08-26
Some are the same everywhere, like netstat (though the options are different because MS has a thing for / stuff)

---

### Post by doas777 on 2008-08-26
not to hijack the thread, but anyone know of any good commands to replace the 'net' cmds ('net view' in particular)?

---

### Post by mssever on 2008-08-26
> **doas777 said:**
> not to hijack the threadBut you're doing it anyway. :) > but anyone know of any good commands to replace the 'net' cmds ('net view' in particular)?
What does net view do? I don't know DOS commands, but I'm quite familiar with Linux ones.

---

### Post by doas777 on 2008-08-26
> **mssever said:**
> But you're doing it anyway. :) 
What does net view do? I don't know DOS commands, but I'm quite familiar with Linux ones.

it enumerates the smb shares available on a target PC.

thanks,
frank

---

### Post by mrsteveman1 on 2008-08-26
> **doas777 said:**
> not to hijack the thread, but anyone know of any good commands to replace the 'net' cmds ('net view' in particular)?

I think smbtree does that, but i can't get it to work at the moment :D

---

