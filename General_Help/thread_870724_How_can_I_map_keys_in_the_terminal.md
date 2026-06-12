---
title: "How can I map keys in the terminal?"
date: 2008-07-26
forum: General Help
---

### Post by mydatespots on 2008-07-26
I use [XShell]("http://www.43things.com/entries/view/3302950") (a sort of PuTTY on steroids) on Windows to connect to my Ubuntu box. My shell is bash.

How can I map keys so that when I press Ctrl+LeftArrow, the shell does Alt+B (move cursor one word to the left) and when I press Ctrl+RightArrow, the shell receives Alt+F (move cursor one word right)?

I think this is very basic customization, but I haven't found a short answer for it after quite a lot of searching. I found this [Linux keyboard and console FAQ]("http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html#ss5.13") but it's overly long and complex. What I want is very simple, just to map two keyboard shortcuts. How can I do that, easily, **on the Ubuntu box** (not in XShell, Putty, on Windows, or in my brain)?

Thanks!
[IMG]http://automaticallyyours.com/img/U2FsdGVkX1-KWUxvEydxBC-uo5sgfBb6/smiley.gif[/IMG]

---

### Post by pauper on 2008-08-01
> How can I map keys so that when I press Ctrl+LeftArrow, the shell does Alt+B
(move cursor one word to the left) and when I press Ctrl+RightArrow, the shell
receives Alt+F (move cursor one word right)?

Here is a quick fix:

```
echo "\"\e[1;5C\": forward-word
> \"\e[1;5D\": backward-word" >> ~/.inputrc
bash
```

To view all default bash keybindings:

```
bind -p
```

And some here:

```
stty -a
```

> ...after quite a lot of searching.

```
man bash
```

/^READLINE

:wink:

---

### Post by mydatespots on 2008-12-22
[QUOTE=pauper;5505633]Here is a quick fix:

```
echo "\"\e[1;5C\": forward-word
> \"\e[1;5D\": backward-word" >> ~/.inputrc
bash
```

Thanks, but that apparently did nothing. To be clear, I created .inputrc and added the following two lines:
```
"\e[1;5C": forward-word
"\e[1;5D": backward-word
```

Worse, if I simply create a 0-byte .inputrc, when I press Delete in the SSH client, a tilde (~) is echoed instead of the character under the cursor being deleted.

I'm sorry, but WTF is it so complicated to bind Ctrl+Arrows to left/right word?!

---

