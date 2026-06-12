---
title: "Printer Drivers deleted!!?"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by cypher35 on 2006-09-06
Alright, so i'm helping a friend set up kubuntu linux over the phone.  While setting up his printer, after selecting the driver from the massive list of manufacturers and models, we ran into an error message:

> Unable to load the requested driver:
Unable to create the Foomatic driver [...] blah blah blah

I recognized this because it is the same error that I recieved while setting up my printer driver...  So i ran a quick search and found the same thread that i used to fix my problem ([here](http://ubuntuforums.org/showthread.php?t=101317))

The thread suggested running the command:
```
sudo foomatic-cleanupdrivers
```

So i instructed my friend to run this line in the terminal, and after it did it's thing, i had him go back into the "Add printer" wizard.  Only problem is, this time, there are no Manufacturers, Models, or Drivers of any kind listed...  it's just blank.

Have all of the drivers been deleted, relocated, or in some other way corrupted beyond repair?

The only thing i can think of that he may have done differently is that he kept the Add Printer Wizard open while he ran the command (i forgot to tell him to close out first).  So after running the command, he closed out and re-entered the printer manager under system settings to find all the drivers missing.


Is there an easy way to re-install them using the Kubuntu install cd?  He does not have an internet connection at the moment, so synaptic is out of the question.


Please help me, i just convinced my friend to make the switch to linux and i'm hoping this whole situation doesn't turn him off to it.

---

