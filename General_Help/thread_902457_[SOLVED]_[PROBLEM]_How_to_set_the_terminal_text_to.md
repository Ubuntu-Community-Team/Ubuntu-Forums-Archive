---
title: "[SOLVED] [PROBLEM] How to set the terminal text to color from black and white."
date: 2008-08-27
forum: General Help
---

### Post by aidave on 2008-08-27
I've noticed on a lot of systems, the terminal will have very colorful text.
For example, the output of "ls -l" will be filled with more than 1 color.  

In Ubuntu it is plain 1 color only.  How do we get it to be colorful again?

---

### Post by aidave on 2008-08-27
Decided to try installing Konsole.  

Fixed!  :)

---

### Post by Minipalmer on 2008-08-27
Hmm, I'll have to check that out. Don't forget to mark your thread as solved. :)

---

### Post by aidave on 2008-08-27
How do I mark it as solved?

---

### Post by Het Irv on 2008-08-27
It is in the Thread tools menu above your first post.

---

### Post by DaymItzJack on 2008-08-27
Open ~/.bashrc and change
```
# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_colored_prompt=no

if [ -n "$force_color_prompt" ]; then
```

to
```
# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_colored_prompt=yes

if [ -n "$force_colored_prompt" ]; then
```

Notice I changed 'no' to 'yes' and changed 'force_color_prompt' to 'force_color**ed**_prompt', I think this typo still exists, if it doesn't then just ignore the 'ed' part.

---

