---
title: "How to delete ThinkVantage backup file?"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by ppl on 2006-05-06
Just got a new thinkpad z60t,after tried to creat a backup file for my Windows XP couldn't figaure out how to delete it, really don't want a useless windows backup occupy 5G space!But the problems is: I can't find it! After create the backup, it is reported to be succed created in C drive, but I can't find where it is. the c drive used space became 5G bigger, but the total files in C: drive remain the same size, looks like the backup file couldn't be seen by windows file system. Then how could I find and delete it?

---

### Post by elamericano on 2006-05-06
The best answer is... delete your Windows partition :-P

It's really a Windows question, isn't it?
Open explorer
Change Folder Options
The second or third tab has check boxes, two of which say
"Hide endings of known type" and
"Hide system files" or something like that.
The point is, don't hide anything.

Then hit F3 (or otherwise select search)
change preferences to advanced.
Open the option to search by size.
Look for all files that are at least 50000K (you could go bigger, but it's good to check for unecessary large files from time to time.

I don't know the name, but it's the 5GB file ;-)
You probably can't remove pagefile.sys, but don't worry. That's your swap file. Anything else is fair game. Good luck.

(I had to do that from memory, because I don't use MS anymore. Thank You Linux!)

---

### Post by ppl on 2006-05-06
Thanks for the reply!
I did the "don't hiding any things" and the "search any thing bigger than 100M(to be safe if the backup up file are packed to small package)". But still get not result.
I guess the best answer is delete the Windows partition, but unfortunately I still need a Windows for my PDA and webcam. So I still need install a window after that.:(

---

### Post by elamericano on 2006-05-06
I was only half serious when I recommended removing the partition. Of course it shouldn't be required, even for Windows problems.

I looked up this feature, and it said it creates a .bak file. You might look for that (*.bak). It also said that you choose where it goes. You might start the program again just to see where it pompts you to save the file.

If all that fails, there are some freeware utilities to help you find where your drive space went:
[http://www.spillett.net/dirgraph/](http://www.spillett.net/dirgraph/)
[http://windirstat.sourceforge.net/](http://windirstat.sourceforge.net/)

---

### Post by ppl on 2006-05-06
Thanks for the informatin, I missed the post and decided to use thinkVantage to set the C drive to factory default this afternoon. 
It is a relative new system just 3 days old. But either Windows or Lenovo really sucks, my laptop refuse to finish the Windows install. I think it is possible something to do with the updated BIOS,and after  turned off the bluetooth in BIOS the install succeed at last! 
Really appreciate your help.

---

