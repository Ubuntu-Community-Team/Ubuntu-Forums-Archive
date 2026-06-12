---
title: "missing characters on console"
date: 2008-08-14
forum: General Help
---

### Post by rubing on 2008-08-14
Hey all, 

I installed Hardy on my compaq presario 700US.  When I enter a console via ctr-alt-Fx There are certain characters (e.g. ' -single quotes) that are missing and in their stead is just a blotchy looking block of white stuff.

Any advice?  How do I change the character encoding??  maybe it's not being set to utf-8??

BTW: characters are all fine in xterm.

Thanks!

---

### Post by Vivaldi Gloria on 2008-08-14
> **rubing said:**
> How do I change the character encoding?? 

```
sudo dpkg-reconfigure console-setup
```

---

### Post by rubing on 2008-08-15
coool...that's really useful!  However, this turns out not to be an encoding issue, but rather a font issue.  

If I type setupcon -f at the command line it uses a different font and is fixed.  Now, how do I get it to boot that way???

---

### Post by Vivaldi Gloria on 2008-08-15
> **rubing said:**
> coool...that's really useful!  However, this turns out not to be an encoding issue, but rather a font issue.  

If I type setupcon -f at the command line it uses a different font and is fixed.  Now, how do I get it to boot that way???

Did you try changing the font with "sudo dpkg-reconfigure console-setup". It asks which font to use at the end.

Also see

[http://ubuntuforums.org/showthread.php?t=329369](http://ubuntuforums.org/showthread.php?t=329369)

---

