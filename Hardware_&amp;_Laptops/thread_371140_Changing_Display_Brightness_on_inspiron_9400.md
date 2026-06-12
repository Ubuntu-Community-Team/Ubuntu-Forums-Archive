---
title: "Changing Display Brightness on inspiron 9400"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by dom on 2007-02-26
Hi all

I have not been able to change the display brightness on the inspiron 9400 from dell using the keyboard (FN+<up arrow> or FN+<down arrow>)

Has anybody else with one of these laptops noticed this, or found a solution ?

---

### Post by nachotronics on 2007-02-26
I had the same problem, the best solution i found was blacklisting the "video" module, this can be done by typing the following into terminal:
```
echo 'blacklist video' | sudo tee -a /etc/modprobe.d/blacklist
```
This will prevent the "video" module from getting loaded on system startup, so you need to reboot for the changes to make effect.

I tried searching what that module was intended for, but couldn't find much information, i only know it has something to do with video and acpi. I have done this almost a month ago, and i haven't had any problems or noticed any other changes besides the ability for adjusting brightness.

Hope this helps.

---

### Post by dom on 2007-02-27
Thanks dude,

I read somewhere else that many if not all of the function related keys generate acpi events rather than key codes, so your theory sounds sound :)

Will try it out tonight and report back.

---

### Post by tschneiter on 2007-02-27
This worked for me, also got sleep mode working properly on my lappy. Good stuff.

However, this kind of thread is exactly what the search button on top is made to prevent, there is quite the same thing on page 2 right now....

---

### Post by dom on 2007-03-02
> **tschneiter said:**
> This worked for me, also got sleep mode working properly on my lappy. Good stuff.

However, this kind of thread is exactly what the search button on top is made to prevent, there is quite the same thing on page 2 right now....

:)

Of course I searched, I didn't find it, or I wouldn't have posted.

But, I found it now, my terms in the initial search were obviously too specific.

For anybody reading, the other/initial  thread about this is at :

[http://www.ubuntuforums.org/showthread.php?t=290994&page=3&highlight=display+laptop+brightness](http://www.ubuntuforums.org/showthread.php?t=290994&page=3&highlight=display+laptop+brightness)

---

