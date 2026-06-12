---
title: "Problem in writing executable script"
date: 2008-10-14
forum: General Help
---

### Post by augustineprasad on 2008-10-14
[B]#to start gedit(a text editor)& firefox

gedit
firefox[/B]

[I]when i execute this exuctable scipt,first the editor opens up but not the firefox..... so once when i close the editor the firefox pops up....Is there any solution to pop up both in the same time within a single executable script

[/I]
---Aj

---

### Post by justleen on 2008-10-14
```
 gedit & firefox & 
```

thing is, your shell will always wait for a command to complete. the & sign forces the application to start in the background, so it wont wait for it to complete.

Advantage is that you can still use the terminal when you launch stuff in the background.. (need to press enter to get a prompt back)

---

### Post by meganox on 2008-10-14
```
#!/bin/bash

( gedit & )
( firefox & )

```
This detaches both programs from the current terminal so they will remain open if you close the terminal.

---

