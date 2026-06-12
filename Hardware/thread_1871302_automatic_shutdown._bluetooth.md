---
title: "automatic shutdown. bluetooth?"
date: 2011-10-28
forum: Hardware
---

### Post by ruediger_007 on 2011-10-28
first of all Hi!!!

I am running
ubuntu oneiric with 3.0.0-12-generic on a Amilo A1630. 

I installed ubuntu yesterday and on random the laptop shuts down (sometimes it works 5 hours, sometimes 1 hour).

during the shutdown process and after closing the x window i can see:

starting bluetooth
speed dispatcher
closing bluetooth 

sorry but i cant see more since it is just for a sec and i cant find anything about it in the log files. 

any hint what i can do that the laptop doesnt shut down anymore?

cheers!

---

### Post by airplanesimen on 2011-10-28
> **ruediger_007 said:**
> first of all Hi!!!

I am running
ubuntu oneiric with 3.0.0-12-generic on a Amilo A1630. 

I installed ubuntu yesterday and on random the laptop shuts down (sometimes it works 5 hours, sometimes 1 hour).

during the shutdown process and after closing the x window i can see:

starting bluetooth
speed dispatcher
closing bluetooth 

sorry but i cant see more since it is just for a sec and i cant find anything about it in the log files. 

any hint what i can do that the laptop doesnt shut down anymore?

cheers!
first i can say that is nothing wrong with your bluetooth, and it isnt that which causes the shutdown. i should have some more info about this, please, if you have the possibility to. i dont know, but try this:
sudo apt-get install gshutdown
install that, and see if you can do some changes there to prevent it from shutting down th system.

---

### Post by ruediger_007 on 2011-10-29
Hi thanks for the reply!

isnt the prog just a gui for the shutdown command? i can set this all manually but  there are no options to prevent the system from shutting down. 

are u sure that the bluetooth has nothing to do with is?? than i will skim throu the log files again and look if i can find other failures or errors.

---

### Post by airplanesimen on 2011-10-29
> **ruediger_007 said:**
> Hi thanks for the reply!

isnt the prog just a gui for the shutdown command? i can set this all manually but  there are no options to prevent the system from shutting down. 

are u sure that the bluetooth has nothing to do with is?? than i will skim throu the log files again and look if i can find other failures or errors.

Yes, i am absolutely sure that it isnt any problem occured by your bluetooth. okay, hmm, when you are in ubuntu, install this:

[http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/](http://www.lucidtips.com/2009/06/06/monitor-cpu-and-hard-drive-temperatures-on-ubuntu-linux/)

So you can check your temperature of your proccesor, HDD and else of your system. Because, if those temperatures is too high, your ubuntu/system will keep shutting down without reason.
Check the numbers, and reply to me with them. good luck. 
If they are too high, you need to clean your computer for dust :P

---

### Post by ruediger_007 on 2011-10-29
hey.

i checked the values and everything is ok. i switched to enlightenment and everything is absolute fine now no turn offs anymore. seems the shutdowns were initiated by unity. this is not a solution at all, i know,  but i wanted to use e17 anyway so i am ok with it. 

anyway. thanks for your help men!!!

---

### Post by airplanesimen on 2011-10-29
if u are okay with it, thats good ;) So, if u mean it is solved, go to "thread tools" at the top of this page, and set this topic to "solved" :P
Good luck further :P

---

