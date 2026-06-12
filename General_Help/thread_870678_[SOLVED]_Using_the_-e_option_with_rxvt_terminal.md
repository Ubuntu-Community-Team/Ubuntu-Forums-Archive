---
title: "[SOLVED] Using the -e option with rxvt terminal"
date: 2008-07-26
forum: General Help
---

### Post by powerpleb on 2008-07-26
I'm looking for a way to display the cal command in it's own window. I thought I could use.
```
rxvt -e cal
```
But it only flashes up and quickly goes away. Whereas if I put in something like.
```
rxvt -e vim
```
it remains. 
I'm guessing the -e option terminates the terminal window when the application I ran exits. It there any way around this? Save just opening a new terminal and typing in cal of course.

---

### Post by mali2297 on 2008-07-26
In xterm and urxvt, you can use the *hold* option:
```

urxvt -hold -e cal

```
But it does not seem to be present in plain rxvt.

You can try
```

rxvt -e "cal; bash"

```
This works in xterm but not urxvt.

---

### Post by powerpleb on 2008-07-26
Thankyou, the first solution worked for me as I think I have urxvt installed anyway.

---

