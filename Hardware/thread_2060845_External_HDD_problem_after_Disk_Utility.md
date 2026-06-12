---
title: "External HDD problem after Disk Utility"
date: 2012-09-21
forum: Hardware
---

### Post by EduardoCR on 2012-09-21
Hello everyone. 
I've managed to get myself in trouble after messing around with Disk Utility in Ubuntu. My 2TB WD external HDD was formatted with NTFS, and it was working fine in Ubuntu; but I wanted to use it with my new iMac. So I opened up Disk Utility and tried to see if it was possible to use it to switch to FAT32. And this is where I f---ed up... Because I somehow, by mistake, applied a change in the file system and now my external HDD is not recognized, either by Ubuntu or the iMac. Even in Windows I get the message that the drive is not formatted. What can I do to go back to where it was, and not lose any data ?
Please, please help.

---

### Post by jonnyboysmithy on 2012-09-21
First things first. Do you have a copy of your data somewhere else?
Formating will make whatever files are on it inaccessible, they will still be there. If you put anything on the drive it will overwrite those files and make them unrecoverable. So don't use the drive.
Do you know format you changed it to?
Have a read on [here,]("http://ubuntuforums.org/showthread.php?t=1784235") it discusses exactly the same problem.

To quote from the linked thread:
			 		   		 		 		> Is it  possible?…..yes. Is it guaranteed?…..no. Sometimes tools like testdisk  work, sometimes they don’t. crispy_420 has already given you some very  wise advice, but please let me go a step or two farther. You should  clone (make an exact copy) of the original drive, albeit a hosed up one  at the moment, then make your data recovery attempts on the clone, not  the original. That way you can screw up as many times as you need before  you get the hang of testdisk, or whatever recovery tool you use,  without further damaging the original. 
1.	Get yourself a hard drive of equal capacity to make the clone
2.	Read up on the dd command
3.	Be patient
4.	When, or if, you’re successful with the recovery, use the extra drive to make frequent backups> I think the message is 'don't despair'. I know that, if the worst comes  to the worst, there are some very capable data recovery companies who  will almost certainly be able to recover your data (and, yes, they will  take your money as well :sad: .) 

The advice of making an exact copy of the drive and doing your recovery attempts on that is the most sound to date. 

Fingers crossed for you.
But have a read around anyway.

Good luck ;)

---

### Post by EduardoCR on 2012-09-24
Hello and thanks for your kind reply. I'm a bit away from my system for a few days, but I will definitely look into the options you mention, especially testdisk. I'll be back with some news after I get some results, whatever they may be...

Thanks again.
[]("http://ubuntuforums.org/member.php?u=1265949")

---

### Post by EduardoCR on 2012-09-26
Boy, it worked like a charm !...

I visied the [thread]("http://ubuntuforums.org/showthread.php?t=1784235") you advised and gave TestDisk a go. And it really did the trick !

I think the best notion anyone can take from this is: never give up ! there's always someone capable of lending a hand and willing to do so.

Thanks again, buddy !

---

### Post by jonnyboysmithy on 2012-09-30
Great, I'm glad you got it solved. If you mark the thread as SOLVED it will make it easier for others to find (at top of page> thread tools>mark thread as solved).

---

