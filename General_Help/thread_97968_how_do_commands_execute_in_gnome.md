---
title: "how do commands execute in gnome?"
date: 2005-12-02
forum: General Help
---

### Post by capaci on 2005-12-02
this might be a weird question for most people, but i know that someone must know about what i'm going to ask. ok, when you run a command in a terminal, you have that context in which stdout, stderr, and stdin come from. when you click on an icon in gnome, what is the context in which it is run? 

here is the reason i ask. i'm working on a script derived from another script that i found using xwininfo. i click the icon, and the script starts. what the script is supposed to do is open a terminal window and set its transparency. if there's a way to get that new windows window id, i'd like to know because that might help. right now what the script does is use xwininfo to get all the window ids of the terminals open currently and calls transset-df with those ids. 

what's happening is when i click the icon the first time (and there is no terminal window open already) it opens the terminal, but fails at setting the transparency. now if i run the script from within that terminal, or any terminal, or click the icon while a term window is open, it sets the transparency correctly. i'm stumped and would love any kind of input to further this along. thanks a lot.

---

### Post by RAOF on 2005-12-02
I believe that each of stdout, stdin, and stderr are redirected to /dev/null.  Until it opens a terminal, stdout & stderr go nowhere, and there's nothing in stdin.

My guess at what's happening is a primitive form of race-condition:  Your script says "open a termnial", then says "loop through all the terminal window ID's & set the transparency", yes?  If there's no terminal window open first, it's possible that you're trying to get the terminal IDs **before** the terminal you've opened is fully created, and so it doesn't get listed.  Perhaps when there's another terminal open the listing of terminal IDs becomes slow enough that your newly opened terminal has enough time to get listed.

---

### Post by 23meg on 2005-12-02
It may be that your script can't "catch" the new terminal the moment it's created. Use a parallel "sleep" command to make it wait for about a second and then perform the operation. See my scripts in [this thread]("http://www.ubuntuforums.org/showthread.php?t=81727") where I do exactly what you describe.

---

### Post by capaci on 2005-12-02
thanks guys, i already thought of the things you mentioned though. you both know exactly what i'm trying to do, but it's just not working. the sleep didn't help with the first term window. though it did help with the problem that sometime a new term wouldn't get set transparent because it was created too slow. i was messing around with that when i first had the problem, but it still doesn't help the main problem.

---

### Post by capaci on 2005-12-02
[QUOTE=23meg]It may be that your script can't "catch" the new terminal the moment it's created. Use a parallel "sleep" command to make it wait for about a second and then perform the operation. See my scripts in [this thread]("http://www.ubuntuforums.org/showthread.php?t=81727") where I do exactly what you describe.[/QUOTE]

you're not doing exactly what i'm doing. you're setting the trans based on the name, and if two windows have the same name only one gets set. that's why i'm looping through the window ids of all the ones with the same name and setting it based on id. the sleep after the creation of the window doesn't seem to help, though i think that it should.

---

