---
title: "keep terminal from closing"
date: 2008-07-18
forum: General Help
---

### Post by Ed54_3 on 2008-07-18
How do i keep the terminal from closing after running something in it?  I need to be able to see the result, but i can't since it closes in a split second after opening.

---

### Post by pauper on 2008-07-18
Could you provide a few examples of commands you are running?

When some program takes over your terminal simply press Ctrl-c to kill it, now
type that command again and add " &" symbol at the end (this will fork it into
background).
To bring it back: 

```
fg
```

To view the list of programs you set to background:

```
jobs
```

If you running gnome-terminal you can right click in it and select "Edit
current profile...". Then select "Title and ..." At the bottom there is an
option "When command exits", try setting it to "Hold the terminal open".

---

### Post by SunnyRabbiera on 2008-07-18
There is an issue with the default terminal in hardy, I suggest using a alternative like roxterm.

---

### Post by Squid Tamer on 2008-07-18
In a script add either 

```
read a
```
or
```
sleep 10
```
as the last line.

The first makes ti wait for you to press enter.
The second makes it wait for ten seconds.

---

### Post by lswb on 2008-07-18
How are you opening the terminal where the command is running? Is it from a launcher of some kind, or from the main menu or a hotkey?

---

