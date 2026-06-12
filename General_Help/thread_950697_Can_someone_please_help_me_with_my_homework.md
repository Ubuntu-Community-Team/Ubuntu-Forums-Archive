---
title: "Can someone please help me with my homework?"
date: 2008-10-17
forum: General Help
---

### Post by verona87 on 2008-10-17
The story is that my ******* *** lecturer gave us this program to write in Haskell on Monday, but the thing is he expects us to write it, & he didn't even teach us how to do **** like this. This assignment has just stumped me. Please, please, cood sumbody help me? I've attached a link to the assignment below.

[http://www.sendspace.com/file/kp7i68](http://www.sendspace.com/file/kp7i68)

---

### Post by Sam on 2008-10-17
From the [Forum Code of Conduct](http://ubuntuforums.org/index.php?page=policy):
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

### Post by DrMega on 2008-10-17
> **verona87 said:**
> The story is that my ******* *** lecturer gave us this program to write in Haskell on Monday, but the thing is he expects us to write it, & he didn't even teach us how to do **** like this. This assignment has just stumped me. Please, please, cood sumbody help me? I've attached a link to the assignment below.

[http://www.sendspace.com/file/kp7i68](http://www.sendspace.com/file/kp7i68)

Your lecturer will be testing not only your technical skill, but your ability to research stuff yourself, as you will need to do when you go into the industry.

---

### Post by Fingel on 2008-10-17
Thats rough man. I reccomend getting rid of all distractions and staring at the assignment for a good 15 -20 min or until you come up with some idea.

---

### Post by verona87 on 2008-10-17
oops, sorri, i did not see that, o well, i gess i fail

---

### Post by mbeach on 2008-10-17
perhaps if you posted in the programming section what you have thus far, and what part in particular has you stumped.  I doubt anyone here will hand you a completed assignment.

---

### Post by verona87 on 2008-10-17
this is it

--Recursive algorithim that solves Towers of Hanoi
solveHanoi :: Int -> IO ()
solveHanoi n = mapM_ putStrLn (hanoi_helper 'a' 'b' 'c' n)
          
hanoi_helper :: Char -> Char -> Char -> Int -> [String]
hanoi_helper source using dest n
    | n == 1 = ["Move " ++ show source ++ " to " ++ show dest ++ "."]
    | otherwise = hanoi_helper source dest using (n-1) ++ hanoi_helper source using dest 1 ++ hanoi_helper using source dest (n-1)

--Apply Hanoi solution to creation of backup schedule
createSchedule :: Int -> IO ()
createSchedule n = mapM_ putStrLn (sched_helper 'a' 'b' 'c' n)

sched_helper :: Char -> Char -> Char -> Int -> [String]
sched_helper source using dest n
    | n ==1 = ["Tape 1" ++ "\t\t"++"Tape 2" ++ "\t\t"++"Tape 3" ++ "\t\t"++"Tape 4"++"\t\t"++   "Tape 5"]
    |n ==2 = ["Tape 1" ++ "\t\t"++"Tape 2" ++ "\t\t"++"Tape 3" ++ "\t\t"++"Tape 4"++"\t\t"++   "Tape 6"]
    | otherwise = sched_helper source using dest n

--Print the 31 Day schedule
printBkpSch::Int-> [String]
printBkpSch n = ["\t\t"++"Mon"++"\t\t"++"Tues"++"\t\t"++"Wed"++"\t\t"++"Thurs"++"\t\t"++"Fri"++"\n"++"Week 1|"++"\t"]



--printWeek
--          |x<=0= error
--          |x 'mod' 2 == 0 = ["Tape 1" ++ "\t\t"++"Tape 2" ++ "\t\t"++"Tape 3" ++ "\t\t"++"--Tape 4"++"\t\t"++"Tape 6"]
--          |otherwise = ["Tape 1" ++ "\t\t"++"Tape 2" ++ "\t\t"++"Tape 3" ++ "\t\t"++"Tape ---4"++"\t\t"++"Tape 5"]

---

### Post by Uchiha_madara on 2008-10-17
so verona87 did you find the Solution ???

hehehehehehehehehehee

your Lecturer is a Criminal man

---

### Post by verona87 on 2008-10-17
well, no

---

### Post by TeXtonyx on 2008-10-17
Your question appeared today, the 17th, the day the assignment is 
due. You are supposed to have a partner. Working with computers 
requires organized thinking. Somebody mentioned searches which is
more important than any other function of efficient computer use.

Using Google is a must. How did you get into a Haskell programming
class without having mastered computer fundamentals? I googled
The Towers of Hanoi Haskell program and found many webpages. One 
of which was '108 different programs for solving the towers of Hanoi'.

[http://www.kernelthread.com/hanoi/](http://www.kernelthread.com/hanoi/)
-- -- The Towers Of Hanoi -- Haskell -- Copyright (C) 1998 Amit Singh. 
All Rights Reserved. -- [http://hanoi.kernelthread.com](http://hanoi.kernelthread.com) 
-- 

dohanoi(0, _, _, _) = [] 

dohanoi(n, from, to, using) = 
dohanoi(n - 1, from, using, to) ++ 
[(from, to)] ++ 
dohanoi(n - 1, using, to, from) 

hanoi(n) = dohanoi(n, 1, 3, 2)

You are not prepared for this course. Drop it before you bring
down your grade average. In a Linux SysAdmin course they teach
you about the different backups and usually practice simple scripts.

"is he expects us to write it, & he didn't even teach us how to 
do **** like this."

So do your partner and other students agree with your statement?
I find it very unbelievable, but I suppose your instructor could
be unqualified. The evidence all points to your maintenance of
pre-adult work habits. Search skills and persistence, conquer all. Find 
a Python script for backups and translate it into Haskell. Use Google:

[http://wiki.answers.com/Q/Implement_a_recursive_algorithm_in_Haskel_that_solves_the_Towers_of_Hanoi_and_apply_that_algorithm_to_the_development_of_a_backup_schedule_where_the_movement_of_a_disc_corresponds_to_the_use_if_a_tape](http://wiki.answers.com/Q/Implement_a_recursive_algorithm_in_Haskel_that_solves_the_Towers_of_Hanoi_and_apply_that_algorithm_to_the_development_of_a_backup_schedule_where_the_movement_of_a_disc_corresponds_to_the_use_if_a_tape)

"Implement a recursive algorithm in Haskel that solves the Towers of Hanoi
and apply that algorithm to the development of a backup schedule where 
the movement of a disc corresponds to the use if a tape?"

---

### Post by TeXtonyx on 2008-10-17
[http://www.pcmag.com/article2/0,2817,1155464,00.asp](http://www.pcmag.com/article2/0,2817,1155464,00.asp)

"The Towers of Hanoi (Table 4) strategy offers the greatest backup depth 
using the fewest tapes. The pattern of tape use in this strategy matches 
the order of moves in the logic game of the same name."

Theorem: Single Parent
Every node in a binary tree has exactly one parent,
except for the root which has no parent.

---

### Post by bodhi.zazen on 2008-10-17
> **verona87 said:**
> The story is that my ******* *** lecturer gave us this program to write in Haskell on Monday, but the thing is he expects us to write it, & he didn't even teach us how to do **** like this. This assignment has just stumped me. Please, please, cood sumbody help me? I've attached a link to the assignment below.

[http://www.sendspace.com/file/kp7i68](http://www.sendspace.com/file/kp7i68)

Although we all feel your pain, and we have all had our share of cruel teachers, you are expected to use this as a learning process.

Please do not use these forums for assistance with "home work".

---

