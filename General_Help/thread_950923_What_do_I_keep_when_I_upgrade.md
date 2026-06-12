---
title: "What do I keep when I upgrade?"
date: 2008-10-17
forum: General Help
---

### Post by chenguo4 on 2008-10-17
With home in a separate partition, of course.

I notice in my home folder there's all these hidden folders for my programs. From what I know however, most of my programs are executed from /usr/bin, which is obviously not in my home folder.

So question is, when say, I upgrade to Ibex or just reinstall because something got screwed over, what is replaced and what isn't?

Thanks in advance.

---

### Post by snova on 2008-10-17
First of all, unless you know that upgrading off the internet is not feasible, I suggest you go that way instead of reinstalling.

The hidden folders in your home directory don't contain programs. Their purpose varies depending on the exact program, but they usually contain your configuration.

The package manager should never touch your home directory.

---

