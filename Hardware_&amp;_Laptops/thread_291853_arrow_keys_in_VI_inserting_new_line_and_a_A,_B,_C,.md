---
title: "arrow keys in VI inserting new line and a A, B, C, D"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by chopz on 2006-11-03
When i am editing a file using vi and I hit one of the arrow keys after pressing going into edit mode, vi then adds a line below the current one with an "A" "B" "C" or "D" depending on which arrow key I push.  Does anyone know the correct term type I should be using?  I currently have mine set to vt100 but it doesn't seem to matter which type I have it set to.

Thanks!

---

### Post by lloyd_b on 2006-11-03
Try this:
```
**export TERM=ansi**
```
and see if it helps.

I would suggest installing the package "vim-full" - this will make it possible to turn on some useful features (such as syntax highlighting for many file types).  By default, Ubuntu installs "vim-tiny", which is much smaller, but lacks a lot of features.

FYI: With "vim-full" installed, the term type "xterm" works fine as well.

Lloyd B.

---

### Post by Whoopie on 2006-11-03
Installing vim-full helped. Thanks a lot!!!

---

### Post by chopz on 2006-11-03
Worked for me too!  Thanks!

---

### Post by lynxus on 2007-04-23
Sweet , worked for me aswell.

Latest Ubuntu7.4

Maybe ubuntu should have vim-full by default to stop these issues from coming up ?

---

### Post by kebab_kid on 2007-05-07
I hate to say this, but installing vim-full hasn't worked for me.  Is there anything else I need to set (edit a config file or something?).  Or could it be a problem with how vi sees my keyboard mapping?

---

### Post by lloyd_b on 2007-05-07
>  I hate to say this, but installing vim-full hasn't worked for me. Is there anything else I need to set (edit a config file or something?). Or could it be a problem with how vi sees my keyboard mapping?

An experiment:  In a terminal window:
```
export TERM=ansi
vi somefile
```

And see if your arrow keys work correctly.  If so, you can add the "export..." line into ~/.bash_profile.

Please run the following command (in a terminal window), and post the results:
```
ls -l /etc/alternatives/vi
```
I'm curious to see which "vim" variant it's pointing to...

Lloyd B.

---

### Post by moixa on 2007-05-07
use keys h j k l
THE keys that move the cursor

---

### Post by lynxus on 2007-05-07
Personally i think thats just stupid using HJKL by default for cursor movement! Why not use the arrow keys? or at least map both by deafult ?

Pfft

---

### Post by lloyd_b on 2007-05-07
> **moixa said:**
> use keys h j k l
THE keys that move the cursor

Those keys are an alternative for those poor souls that have to work on terminals that don't have arrow keys, but they are NOT an equivalent.  For example, with the arrow keys it's possible to move the cursor ***while in insert mode***, something that the alternate keys (obviously) cannot do.

May I suggest that you limit yourself to posts that are geared towards resolving the problem (why the arrow keys aren't working) rather than suggesting inferior substitutes?

Lloyd B.

---

### Post by kebab_kid on 2007-05-08
Thanks Lloyd B.  I'd tried TERM=xterm, but not TERM=ansi.  The latter works.

/etc/alternatives/vi is pointing to vim-full

---

### Post by lloyd_b on 2007-05-08
> **kebab_kid said:**
> Thanks Lloyd B.  I'd tried TERM=xterm, but not TERM=ansi.  The latter works.

/etc/alternatives/vi is pointing to vim-full

Them I'm clueless as to what the root problem is.  Perhaps it *does* have something to do with your keyboard mapping.

At any rate, by adding that "export..." line in ~/.bash_profile, you should have a usable solution (though I would be happier if we could identify *why* you're having this problem with vim-full).

Lloyd B.

---

