---
title: "[SOLVED] vim and :syntax enable :set mouse=a"
date: 2008-08-07
forum: General Help
---

### Post by jerome1232 on 2008-08-07
Is there a way to get vim to auto run :syntax enable and :set mouse=a every time I open it?

---

### Post by cdtech on 2008-08-07
You could use an alias like I do with the color depth:
```
alias vi=’vim -T xterm-256color’
```

---

### Post by jerome1232 on 2008-08-07
yes that would work nicely, thank you

---

### Post by cdtech on 2008-08-07
Your welcome.....:)

---

### Post by jerome1232 on 2008-08-07
okay to make an alias permanent would I just create a file call ~/.bashaliases and add the line: alias vi='vim "+syntax enable" "set mouse=a"'

mostly i'm unsure of the syntax that should be in the file

---

### Post by Dr Small on 2008-08-07
Why don't you set those commands in either /etc/vimrc or ~/.vimrc ?

---

### Post by jerome1232 on 2008-08-07
ah that works, I edited ~/.vimrc, although the alias option would be nice just so I could use vim without those options (actually I can't think of why I wouldn't want those options)

After looking at the man page it looks like I can use -u to specify alternate profiles so I think this works well.

thanks

---

