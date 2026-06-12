---
title: "question about internet time usage and processes"
date: 2008-10-03
forum: General Help
---

### Post by sadak on 2008-10-03
please help me.

is there any tool that can show me how long have I been surfing the internet, something like knowing my internet time usage? 

again, another question,in windows ,when we open task manager then it lists all the active processes, however in linux,when i use system monitor, there's either the word: sleeping or running??what is it? can I just end the processes that is sleeping? are there any recommendation on the processes that might not be useful for me,or maybe the one that is rarely used?

---

### Post by unutbu on 2008-10-03
> is there any tool that can show me how long have I been surfing the internet

Good question. I don't know.
> 
sleeping or running??what is it?

A process can go to sleep and then wake up, and then go back sleep.
At any given moment almost all processes are asleep and only those that are occupying the CPU's brain power is labeled as running.

If you type into a terminal
```

man ProcessName
```

where ProcessName is something like 'bonobo-activation-server'

then you will get a blurb describing what the process is for.
Based on that you may be able to decide if you want it running.

The best way to turn off a process depends on how the process was started. 
Some might have been started by the system at boot time, others might have been selected to start when you log in. 

If you post the names of the processes you wish to shut off, we might be able to help you shut them off.

---

### Post by aeiah on 2008-10-03
> **sadak said:**
> please help me.

is there any tool that can show me how long have I been surfing the internet, something like knowing my internet time usage? 


you could probably create something that'd do that, yea. it depends how you connect to the internet though. what do you use?

---

### Post by sadak on 2008-10-03
Thanks, I am using adsl ,is that the answer you are looking for??

---

