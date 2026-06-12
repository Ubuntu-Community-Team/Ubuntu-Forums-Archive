---
title: "Compiling pygame 1.7 = hair loss"
date: 2005-11-18
forum: General Help
---

### Post by Bigglez on 2005-11-18
Hello - I have tried and tried to compile pygame 1.7 on Kubuntu 5.04 (Oh damn, just saw this is the 5.10 forum. Sorry.) and I cannot get it working.

I tried to install the pygame 1.7 debian package (not available in ubu repos) but it has deps and those are not available on the ubu repos either. I could force it, but I don't want to break kynaptic.

When I try to compile pygame1.7 using the "python setup.py install" it chokes on environment variables. These ones mainly:
CC, OPT, CCSHARED, SO
How many more, I just don't know. I traced these by following-along in the source code of the various python modules that threw errors.
I tried installing 'gcc' and then faking the flags.
I set CC to "gcc" and to "gcc-3.3" (exporting all the while) to no avail.
I even hacked the python code to make the vars a space " " when the flags were not found in the environment. Errors all the way.

I am used to Linux on Fedora and these flags just work. I am totally at sea on Kubuntu. Can anyone advise me as to what to do?

I tried the pygame IRC and they were stumped. Their opinion of Kubuntu was unflattering to say the least.

Oh yeah - I have all the SDL deps that pygame1.7 (from the source pov) seems to want.

---

### Post by Bigglez on 2005-11-18
Just a bump - Is there a better sub-forum for this kind of question?

---

