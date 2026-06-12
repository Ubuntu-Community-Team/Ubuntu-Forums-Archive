---
title: "where did all my files go?"
date: 2008-11-15
forum: General Help
---

### Post by antord on 2008-11-15
My computer has reverted to how it was 2 weeks ago! All work drivers and programs are exactly how they were thwn. Can I get the documents back? if so wher are they hiding?
Any ideas would be much appreciated..

---

### Post by antord on 2008-11-17
anyone got any ideas on thins one?

---

### Post by Junkieman on 2008-11-17
do you use any kind of backup/restore software on your system? have your documents also 'reverted' to 2 weeks ago, or is your home folder empty?

---

### Post by Sam on 2008-11-17
Use
```
locate *pattern*
```
where *pattern* is part of any filename you looking for.

---

### Post by antord on 2008-11-17
I don't use any backup or restore programs. Yes all my documents have reverted also, my home folder still has files in it but they are from 2 weeks ago. Also all programs and drivers are old too. I tryed the locate command but it turned up nothing..

---

### Post by pp. on 2008-11-17
What OS are you using, and how do you know the age of your files?

---

### Post by antord on 2008-11-17
Hi PP,
I upgraded to 8.1 now but the files went missing whilst using the previous ubuntu. I still have the old system in a seperate partition. How do I know the age of my files? I recognised them as I saw them two weeks ago as they are. Maybe a backup image of the system was reinstalled by the system because of a problem?

---

### Post by pp. on 2008-11-17
I'm sorry but the sequence of events has not become any clearer to me. As far as I can make out, you either have installed the 'new' version of Ubuntu into another partition as the one which the preceding ubuntu version ran in, or you have somehow turned back your system clock by two weeks.

If it really is Ubuntu you're running, it can't be 8.1. There are 8.4 and 8.10, for the versions released in April and October 2008, respectively. There has not been a January version.

---

### Post by Junkieman on 2008-11-18
Im also not sure what you mean, please clarify for us. it sounds like you installed the new OS on a different partition than your old OS? if so then you have duplicates of your documents on two partitions perhaps. Are you sure you're looking at the latest copies of your documents?

---

### Post by antord on 2008-11-18
Sorry to confuse. Let me start again. I was using 8.4 whilst using 8.4 my system seemed to go back to a state that it was in 2 weeks ago. I.e all documents, programs, drivers, even desktop picture etc reverted to how they had been two weeks ago (lets call this state A). I carried on using this old system and a week later it jumped forward to the 2nd state i.e how it was before it reverted (lets call this state B)! This freaked me out so I installed 8.10 and all is well. I kept the old system on a serperate partitiom and now am trying to find documents that are from the old system i.e. State B. If I boot to the old partition it is 8.4 but in state A. Somewhere on this partition must be backup data of State B (as it found them once whilst running 8.4!):confused:
I hope this adds some clarity but it is a confusing sequence of events.. Thanks for your replies any more help would be great.

---

### Post by Junkieman on 2008-11-18
> **antord said:**
> I carried on using this old system and a week later it jumped forward to the 2nd state i.e how it was before it reverted

so your files went back in time -2 weeks and then a week later they were restored again? strange. Ideally you should have solved the old-files problem before installing the new OS to avoid stacking up problems - then it gets tricky to solve...

perhaps your system clock was changed to -2 weeks and then changed back :confused: verify your file contents not the timestamps in this case.

---

