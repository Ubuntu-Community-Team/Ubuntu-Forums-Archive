---
title: "[SOLVED] nautilus-open-terminal opens a terminal window at ~/Desktop, not ~"
date: 2008-09-23
forum: General Help
---

### Post by azredwing on 2008-09-23
Hi all,

I've got an annoying issue. I am running two Ubuntu boxes, one on my desktop and one on my notebook. I installed nautilus-open-terminal to get right-click-open-terminal capability.

When I right-click the Desktop on my main computer to open the terminal, the terminal is opened to ~. When I do the same on my notebook, it opens to ~/Desktop. It's an extra cd to go back to the home directory, but it's pretty annoying.

How do I set this such that it defaults to opening to ~ ?

Thanks!

---

### Post by azredwing on 2008-09-23
Haha, as soon as I posted this I realized what I had to do.

```
$ gconf-editor

```

There's an option for nautilus-open-terminal to open to ~.

Woo.

---

