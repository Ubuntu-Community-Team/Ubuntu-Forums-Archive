---
title: "[SOLVED] Command Line Help Please"
date: 2008-07-29
forum: General Help
---

### Post by Krupski on 2008-07-29
Hi all,

I love being able to recall past used commands in 'bash', but I wish to do one more thing (that I was able to do in Windows running JPSoft's 4NT shell):

Let's say I type a command:

# ls -laF

then another

# apt-get update

then more

# lots-more-commands

THEN I want to re-run the ls command which is buried in the bash history.

In 4NT, I could just hit "l" or "ls" (i.e. the first or first few characters of the command I wanted to recall) then hit up-arrow and the old command (or commands matching my input) would be immediately found.

Is there any way, in bash, to do this?

Currently I have to hit a zillion up-arrows until I find the old command I want. I imagine that I *should* be able to get it by specifying a character or two of the line I want.

Anyone know how?

Thanks!

-- Roger

---

### Post by unoodles on 2008-07-29
history | grep <expression>

for example if you know you used the command 'ls', type history | grep ls

---

### Post by howlingmadhowie on 2008-07-29
in the z-shell you can use exclamation mark and the first letter then tabbed completion.

bash supports
!xxx

where xxx is the number of the command in the history.

---

### Post by pauper on 2008-07-29
Press Ctrl-r (to abort--Esc). After doing this, your prompt changes to:

```
(reverse-i-search)`':
```

Type a few letters of the command you're looking for:

```
(reverse-i-search)`grep': dmesg | grep iwl3945
```

To execute that command again, press Enter. To edit it, press the left or
right arrow key.

---

### Post by unutbu on 2008-07-29
Type Ctrl-r and then just start typing the command. The bash command line will try to complete the command for you. Just press Enter when it's found the right one.

Pressing Ctrl-r repeatedly will make the command searcher find the next match in the history.

---

### Post by Krupski on 2008-07-29
> **unutbu said:**
> Type Ctrl-r and then just start typing the command. The bash command line will try to complete the command for you. Just press Enter when it's found the right one.

Pressing Ctrl-r repeatedly will make the command searcher find the next match in the history.

THAT'S WHAT I WAS LOOKING FOR!!!!! THANK YOU!!!

-- Roger

---

### Post by Krupski on 2008-07-29
> **pauper said:**
> Press Ctrl-r (to abort--Esc). After doing this, your prompt changes to:

```
(reverse-i-search)`':
```

Type a few letters of the command you're looking for:

```
(reverse-i-search)`grep': dmesg | grep iwl3945
```

To execute that command again, press Enter. To edit it, press the left or
right arrow key.

THAT'S WHAT I WAS LOOKING FOR!!!!! THANK YOU!!!

-- Roger

---

### Post by geirha on 2008-07-29
an addition to pauper's post: If you have more than one command that matches grep, cycle through them by hitting ctrl+r several times. E.g. *Ctrl+r grep Ctr+r Ctrl+r* will show you three commands that matches grep (last run first).

EDIT: Beaten to the punch by unutbu :S

---

### Post by Krupski on 2008-07-29
> **geirha said:**
> an addition to pauper's post: If you have more than one command that matches grep, cycle through them by hitting ctrl+r several times. E.g. *Ctrl+r grep Ctr+r Ctrl+r* will show you three commands that matches grep (last run first).

EDIT: Beaten to the punch by unutbu :S

Excellent - thank you!

-- Roger

---

### Post by smilingfrog on 2008-08-01
I didn't know about the ctrl-r. Thanks!

To look throught the entire history for one string, I use ```
history | grep <string> 
```

To match two strings from the history :

```
history | grep -e '<string1>|<string2>'
```

To match both strings:

```
history | grep <string1> | grep <string2>
```

Then to run the command, prefix the line number with '!':

```
!nnn
```

or to print it to the screen without running the command

```
!nnn:p
```

if I want the line to be changed slightly. Then I use the up arrow to select the most recent history and edit that.

The ctrl-r trick is fantastic. Anyone have a method that would make the above quicker?

---

