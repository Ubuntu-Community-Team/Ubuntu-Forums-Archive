---
title: "Inspiron 6000 arrow keys in VI create letters"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Migalicious on 2006-10-27
In Edgy, when I go into insert mode in VI and I try to use the arrow keys, it produces A,B,C,D depending on what key.  This never used to happen in 5.10 or 6.06.  I tried switching to different keyboard modes (default, dell, dell media keyboard, dell inspiron 6000/8000) and none of them make a difference.

---

### Post by spine on 2006-10-28
I have a desktop and the same thing happens any clues yet?

---

### Post by pot on 2006-10-28
I get the same behaviour in vim when in vi compatible mode, try entering:

```
:set nocompatible
```

Also, I think vim-tiny is installed by default, though I can't quite remember (which is bad considering I only installed edgy yesterday!) so you may wish to

```
apt-get install vim
```

to get a full featured version of vim, if you need things like syntax highlighting

---

### Post by Migalicious on 2006-10-28
> **pot said:**
> 
```
:set nocompatible
```


Awesome! That worked, thanks!

---

### Post by Migalicious on 2006-10-28
Is there any way I can set it in nocompatible by default?

---

### Post by pot on 2006-10-29
Just add:

```
set nocompatible
```

(no need for a colon this time) to your .vimrc file in your home directory (just create it if it isn't there)  This will just change it for your user, if you want to change it system wide, you could edit /etc/vim/vimrc.tiny - from the looks of the comments in that file you could also get the nocompatible behaviour by starting vim with 'vim' instead of 'vi'

Hope that helps

---

