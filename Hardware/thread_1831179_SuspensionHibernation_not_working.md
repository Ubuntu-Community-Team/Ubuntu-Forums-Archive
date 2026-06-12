---
title: "Suspension/Hibernation not working"
date: 2011-08-23
forum: Hardware
---

### Post by MiracleCat on 2011-08-23
Hi,

I have a HP dm1-3060la, neither suspension or hibernation seem to be working.

Basically the netbook won't comback from both. It just shows a black screen (turned on but blank).

Hope anyone can help me.

---

### Post by shubham1 on 2011-08-23
when it shows blank screen after opening or after closing if after opening
then try to do this when you open
click near middle and type your password and press enter and wait for few seconds
try moving your mouse to get it active it can take time it happens always to me.

---

### Post by sbraz on 2011-08-23
> **shubham1 said:**
> when it shows blank screen after opening or after closing if after opening
then try to do this when you open
click near middle and type your password and press enter and wait for few seconds
try moving your mouse to get it active it can take time it happens always to me.

try this:
```
sudo apt-get remove uswsusp
sudo apt-get install hibernate
sudo hibernate
```

---

### Post by shubham1 on 2011-08-23
> **sbraz said:**
> try this:
```
sudo apt-get remove uswsusp
sudo apt-get install hibernate
sudo hibernate
```
thansk but my hibernate works fine.
but i have installed hibernate as you said.

---

### Post by sbraz on 2011-08-23
so do your pc wake up correctly after running **sudo hibernate**?

i was messing with tuxonice (another method for hibernate/suspend) and i had to do exactly the same thing to recover hibernation capabilities. :)

edit: sorry i misread your name i thought you started the thread :D

---

### Post by scottishbloke on 2011-08-23
Its a bug and It has been reported here...[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748994](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748994)

---

### Post by MiracleCat on 2011-08-23
Suspension was a problem with the propietary ATI driver, I removed it and suspension now works.

Hibernation still not working, ill try the code above.

"sudo apt-get remove uswsusp
sudo apt-get install hibernate
sudo hibernate"

---

### Post by MiracleCat on 2011-08-23
I did what you wrote,

after [b]sudo hibernate[b] it showed something like "looking for splash....none" then "s2disk: snapshotting" and did nothink for like 15 mins. then I turned my PC off.

---

### Post by scottishbloke on 2011-08-24
From suspension I just typed In my password then hit enter, Got In no problem.

---

### Post by MiracleCat on 2011-08-24
OK, so the bottomline is:

Suspension was a graphic driver problem.
Hibernation is a ubuntu bug that needs to be solved.

---

### Post by shubham1 on 2011-08-24
it is my solvde thread of hibernate problem
[URL="http://ubuntuforums.org/showthread.php?p=11178866#post11178866"]http://ubuntuforums.org/showthread.php?t=1822222
[/URL]

---

### Post by shubham1 on 2011-08-24
is it linking to same this thread but

---

### Post by MiracleCat on 2011-08-24
> **shubham1 said:**
> is it linking to same this thread but

I'm sorry i don't understand. Those commands didn't solve my problem with hibernation.

---

