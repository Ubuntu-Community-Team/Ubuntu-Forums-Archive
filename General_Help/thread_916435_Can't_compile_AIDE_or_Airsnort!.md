---
title: "Can't compile AIDE or Airsnort!"
date: 2008-09-10
forum: General Help
---

### Post by Panarchy on 2008-09-10
Hello

Just tried compiling AIDE 0.13.1 and airsnort-0.27e.

However, I ran into some problems (see below);

I navigated to it (cd) ran ./configure (this is on ubuntu),

Got this error;

configure: error: C compiler cannot create executables

So then I tried Cygwin on XP 64-bit.

And got this error;

configure: error: no acceptable C compiler found in $PATH

Even tried with command prompt, but of course got the not recognized as an internal or external command, operable program or batch file error.

How do I allow ubuntu to create executables?

Please either tell me what other method I can use to get it to work, or give me precompiled AIDE and airsnort programs.

Thanks in advance,

Panarchy

---

### Post by oldos2er on 2008-09-11
In order to compile source code on Ubuntu, you first need to install the package "build-essential".

---

### Post by Panarchy on 2008-09-11
so, I should type this into terminal;

sudo apt-get install build-essential

EDIT;

Thanks, seems to be working, currently downloading. Will tell you if I'm able to compile

---

