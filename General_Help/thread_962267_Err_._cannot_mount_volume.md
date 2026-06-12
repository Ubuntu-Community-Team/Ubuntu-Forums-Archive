---
title: "Err . cannot mount volume"
date: 2008-10-29
forum: General Help
---

### Post by jehad4t on 2008-10-29
[CENTER][COLOR="Red"][SIZE="3"]Hi ...  :-D
i have err . i wont to copy my files but i can`t
this a mass
[IMG]http://images.q8boy.com/images/hlcjdwpkax3b21q7s35j.gif[/IMG]

:confused:[/SIZE][/COLOR][/CENTER]

---

### Post by jehad4t on 2008-10-29
hallo

---

### Post by vanadium on 2008-10-29
Did you read the text on the screenshot you posted? There is the answer. Ubuntu will not automatically mount a drive that is not "clean" because doing so can risk to further corrupt the file system.

You should use Option 1. Option 2 is useful for an emergency, if you do not have Windows anymore. In the latter case, you'd better reformat the drive to a linux file system. It appears that the tool ntfsfix (part of the ntfsprogs package) can also help to make the drive as 'clean', but I do not have experience with this.

---

