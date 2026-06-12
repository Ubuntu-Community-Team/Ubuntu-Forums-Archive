---
title: "[SOLVED] Processor &amp;quot;in use&amp;quot;"
date: 2008-11-14
forum: General Help
---

### Post by pTiUnXgRuUpLiEnZgZu on 2008-11-14
Ok, if this isn't really specific/descriptive, then plz don't bash me, i'm just a kid.

You know how sometimes i one of your toolbars, the one where all your applications are shown, theres a little line graph thing that shows how much of your processor is being used? Well for the past 1/2 hour i haven't been running any apps, other than mozilla firefox, and it says my processor is 100% in use. Also, its been making a loud busing noise, and its really bugging me. How do I get it to stop :confused:

---

### Post by Idefix82 on 2008-11-14
Which processes are using most of the CPU? You can see it by typing in
```
top
```
in the terminal or in the "line graph thing".

---

### Post by pTiUnXgRuUpLiEnZgZu on 2008-11-14
Ok, so I click on the terminal, and a window appears that with the following tabs: Systems, Processes, Resources, File Systems.

When I go to Processes, theres a really really long list of processes, but most of them are sleeping, and about 4 are running. 

When I go to Resources, under the bar CPU history, it says CPU 1 is 100% in use, and CPU 2 keeps switching from 99% to 100%.

How do I, erm, un-run the processes? 

Will that lower the blue line on the terminal?

How do I know which processes I need to be running, and which ones I don't need?

Is having your CPU 100/99% in use a bad thing, or is it just the annoying noise? (my processor has only been 100% in use for like 1 second before)

---

### Post by Idefix82 on 2008-11-14
Having both cores at 100% indicates that there is something wrong. The processes in the list that you were referring to can be sorted by CPU consumption. Which are the top ones? You can actually see how much CPU each one is using. I recommend you using the first method I described (open the terminal and type in 'top') since it updates more frequently and it's easier to see what is going on.

---

### Post by pTiUnXgRuUpLiEnZgZu on 2008-11-14
Thanks :)

I closed all the processes that were using lots of my processor. Now, its not making that annoying humming noise, and the terminal shows that it is barely being used at all.

---

### Post by Idefix82 on 2008-11-14
I am not sure it's a permanent solution though, because in all likelyhood these processes will be started next time you log in. Besides, they might actually have been useful. Do you remember which processes you killed?

---

