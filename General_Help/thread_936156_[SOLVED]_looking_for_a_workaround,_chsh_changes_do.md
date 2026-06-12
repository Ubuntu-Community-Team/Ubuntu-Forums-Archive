---
title: "[SOLVED] looking for a workaround, chsh changes don't stick."
date: 2008-10-02
forum: General Help
---

### Post by Xnyper on 2008-10-02
Hi all,

I'm in a UNIX class at school, and we all have shell accounts on the server.  The login shell is set to tcsh.  I dislike tcsh.  I wanted to change my login shell to bash so that I can put [FONT="Courier New"]set -o vi[/FONT] in .profile and use vi editing at the command line.

So that's what I did:
```

chsh
password
/bin/bash
```

and then edited .profile accordingly.  I logged out and logged back in, and all was well, for a time.

The next day, I logged back in, and was in a tcsh shell.  so, after another chsh, all was well for a time.  
I logged out and back in twice during that hour-long class, and was happily in my bash shell with the options I wanted enabled.

an hour later, I logged back in, and was in a tcsh shell.

What is going on?  Is some script running periodically that resets everyone's login shells to tcsh?  Sounds silly to me but it's the kind of silly thing that I would expect from our university.  

Well, it's not my system to troubleshoot, and its only a few commands every time I login, but if there is a way, I want to find it (this is school for Pete's sake, I'm here to learn eh?).  My .profile and .chsrc and all of those aren't being messed with... but my login shell is.

Perhaps something that I can add to .login or .cshrc to change the login shell at login?
Any other ideas?
Or should I just deal with it and fork a bash each time I login?


Edit: I had done some searching, but after posting I did a little more and found this:
[http://www.cfdlab.ae.utexas.edu/~mclay/bash.html](http://www.cfdlab.ae.utexas.edu/~mclay/bash.html)
Seems like my problem is more common than I thought.

---

