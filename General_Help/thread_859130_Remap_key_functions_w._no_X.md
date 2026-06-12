---
title: "Remap key functions w. no X"
date: 2008-07-14
forum: General Help
---

### Post by adcwoef on 2008-07-14
Hi there!

I'm running Ubuntu Server 8.04 and I really really want to swap the *fn* and *CTRL* button because their current location does not fit my finger stroke at all is there an such application that can switch functions for keys? I think there is a graphical tool for that in GNOME but I'm not running X no more.

Thanks for help!

---

### Post by echo314 on 2008-07-14
Try [this]("http://articles.techrepublic.com.com/5100-10878_11-5683375.html?tag=rbxccnbtr1"), I think its what you want (found by some searching)

Basically, use the read command to figure out how the key is represented. For example, F12```
$ read

^[[24~
```

*from the article*

The next step is to bind that key sequence to a particular shell command. For example, you can bind [F12] to the "history-search-backward" shell command:

$ bind '"\e[24~": history-search-backward'

Make sure you write the key sequence as \e[24~ rather than ^[[24~. This is because the ^[ sequence is equivalent to the [Esc] key, which is represented by \e in the shell. So, for instance, if the key sequence was ^[[OP the resulting bind code to use would be \e[OP.

Not only does the bind command bind function keys, but you can also use bind to map key sequences (such as [Esc][P] or [Esc][Q]) by writing the bind key code as \ep and \eq respectively.

---

