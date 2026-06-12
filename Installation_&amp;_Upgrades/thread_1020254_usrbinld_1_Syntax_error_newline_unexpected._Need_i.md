---
title: "/usr/bin/ld: 1: Syntax error: newline unexpected. Need immediatel help"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by biky2004indra on 2008-12-23
Hi,
I am in a big problem. Please help me. my problem is that when i am trying to compile any c/c++ program using the command g++ -lm sample.c -o sample, where sample.c is my c program name, the the following error message is giving : /usr/bin/ld: 1: Syntax error: newline unexpected
          collect2: ld returned 2 exit status
I am using UBUNTU 8.10 and it was updated regularly. I have tried in various way to debug, but no one is working. How can i solve it. someone suggested to uninstall everything and reinstall again. i have already uninstalled g++ and gcc & then reinstalled again. but no positive result. can anyone tell me how can i solve it without formatting the ubuntu.
Thanks and waiting.

---

### Post by ezren on 2009-05-22
I am having the same issue with Ubuntu 9.04.  Does anyone have any leads on this issue?  I'd really hate to have to reinstall my whole system.  It seems I am unable to install any new software now...  I'm pretty new at Linux so forgive my ignorance ahead of time please.  

Thanks

---

### Post by westyfresh on 2011-02-27
Did you find a solution? I am getting the same error. I checked google and did not find the error.

```


/usr/bin/ld: 1: Syntax error: newline unexpected
collect2: ld returned 2 exit status


```

---

### Post by ankitanand on 2011-06-10
/usr/bin/ld is  a gnu linker program, available in binutils package. Reinstalling binutils will solve this problem

Run following command

[B]sudo apt-get autoremove binutils

sudo apt-get install binutils
[/B]

---

