---
title: "how to run a c script?"
date: 2008-07-20
forum: General Help
---

### Post by liu4gre on 2008-07-20
gcc *.c and gcc *.c -o * is a way, is there another way so that I just need to imput "ccc *", which has the same infect with gcc *.c -o *? Thanks

---

### Post by molotov00 on 2008-07-20
You would have to create a command (bash script) called ccc, which would serve as a wrapper.

"which has the same infect with..."
should be
"which has the same effect as..."

---

### Post by Separ on 2008-07-20
If I remember rightly, you can add a bash alias for that sort of thing in a separate file.

```
gedit ~/.bashrc
```
Uncomment these 3 lines.
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```
Then do:
```
gedit ~/.bash_aliases
```
and add this to it and save:
```
alias ccc='gcc *.c -o *'
```

---

### Post by crwmike on 2008-07-20
You can create an alias in ~/.bashrc or ~/.bash_aliases.

Look at the samples in your .bashrc file for the format.


EDIT:
Did it really take five minutes to write this.

---

