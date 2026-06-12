---
title: "Help with a particular laptop brand... very annoying issue"
date: 2011-05-31
forum: Hardware
---

### Post by KidneyBean on 2011-05-31
Hello all. 

I have an Acer Aspire 5315. The only modification I've made to it in terms of hardware is having added another gig of RAM thus increasing my allotted total to 2 gigs. All of the other specs are the same the day I purchased it.

I just installed Ubuntu and I'm loving it- only, my laptop keeps shutting down! Having browsed for hours on the Ubuntu forums over how to solve this issue, I came across a few threads- but they were heavily outdated. 

I need an expert on the Acer Aspire 5315 to provide me with a step by step guide to fixing the "fan issue" that has plagued this laptop brand forever. Apparently there are a few fixes- only I haven't seen anything concrete that I can use. 

By the way, the issue IS with the fan. It's a widely known fact. Even the pre-installed Vista kept shutting down on me (which before my research, I thought Vista was the issue). 

Thanks for your help.

---

### Post by KidneyBean on 2011-05-31
I'm sorry to do this, but I'm bumping my own thread as I'm really in need of a solution.

---

### Post by IWantFroyo on 2011-05-31
If it's not with a particular system, it may be the BIOS. Updating it may fix the problem. Here's some instructions:
[http://www.wikihow.com/Update-Your-Computer%27s-BIOS]("http://www.wikihow.com/Update-Your-Computer%27s-BIOS")
Just make sure that you put your computer on one of those air-conditioning vents on the floor or a cooling stand while flashing. Having your computer crash in the middle of that would likely brick your computer.

---

### Post by KidneyBean on 2011-05-31
Thanks for the reply. Only, threads here on the Ubuntu forums all seem to indicate that this is a hardware issue relating to the fan of this particular model. Many have stressed that it is not the BIOS. 

The problem with these Acer Aspire 5315 models is that the fan is faulty. It doesn't kick in when needed. Thus, becoming overheated, the computer shuts down. The system can sometimes go a long time before this occurs- but it does- and when it does, it's quite annoying. 

I found a script for a different model of the Acer with similar issues- but couldn't find one for the Aspire 5315. If anyone out there with knowledge of the fan issue in the Acer Aspire 5315 would like to share a step by step way of resolving the problem, please, be my guest.

---

### Post by FatalChaos on 2011-05-31
I haven't dealt with this particular computer before, but I have dealt with fan issues before. One thing that could resolve your problems is to access the bios (commonly but not always f12 during boot) and to manually set the fan to always be on. Usually the bios will let you specify if the computer should automatically control the fan or to manually set the fan to always be on at low/med/high speed. You probably won't need high, experiment with low/med.

---

### Post by KidneyBean on 2011-05-31
Hmm, I could give this a shot and I'll report back some other time on the progress. However, if anyone out there reading this has solved this problem 100%, please provide your input- it would be much appreciated!

---

### Post by KidneyBean on 2011-06-01
I'm bumping this thread. 

Here is the solution to my problem- it's a script designed to control the fan of my laptop. I KNEW it wasn't a BIOS thing. But here's the REALLY crappy part- the install commands when punched into the terminal DO NOT WORK. I'm told that "no such file or directory exists". 

Will someone please help me out or do I have to keep bumping?

---

### Post by KidneyBean on 2011-06-01
[http://ubuntuforums.org/showthread.php?p=10887931#post10887931](http://ubuntuforums.org/showthread.php?p=10887931#post10887931)

Sorry, forgot to post the link to the thread that contains the solution I'm looking for. There it is above.

---

### Post by gordintoronto on 2011-06-02
You have not said at what point you got the error message. Before the first command, you must cd to the folder where the file was downloaded to.

Actually, I never do it that way, I always find the file in the Nautilus file manager and double-click it, then select "extract" in the graphical window.

BTW, you have never mentioned which version of Ubuntu you installed. Sometimes that is helpful.

---

