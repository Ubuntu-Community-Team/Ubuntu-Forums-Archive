---
title: "How do I safely delete unncessary partitions in Ubuntu 9.04?"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by Unew on 2009-05-01
I need guidance on how to safely delete two unnecessary Ubuntu 9.04 partitions in my Vista / Ubuntu dual boot system. The unecessary partitions were created when I reinstalled Ubuntu 9.04 on my laptop.  I was having a problem so I reinstalled the OS, which resulted in my having four Ubuntu related partitions on my hard drive. Now that my original problem has been solved, I want to delete all unecessary Ubuntu related partitions. However, I'm not absolutely sure which partitions are active, which ones I can safely remove.  I'm concerned about deleting anything that could "break" my dual boot process.

I ran the "sudo bash ~/Desktop/boot_info_script*.sh" command and attached is a copy of the "Results.txt" file.  Can someone please give me step-by-step instructions for safely deleting the unnecessary partitions?  I have a copy of gParted on a LiveCD. 
 

Also, is there anything special I should be aware of or do when I delete the unnecessary partitions? If I simply use a tool like gParted to delete the unnecessary partitions, would that likely cause any problems?

I'm learning here, and want to proceded cautiously.  Thanks in advance for the help!

---

### Post by lindsay7 on 2009-05-01
I do not see the file "results.txt" you talked about.

---

### Post by Unew on 2009-05-01
Sorry, the attachment (results.txt) for my previous post was too large. Here it is as a zipped file....  Thanks!

---

### Post by lindsay7 on 2009-05-02
That is one messed up menu.lst file. There are duplicates of everything and I just am not sure of all that is going on here. Grub).97 is looking at sda7 so I would think that sda7 and sda8 are the Ubuntu partitions that are the good ones and the ones to keep.  What I am not sure of is what will happen if you delete sda5 and sda6. I do not know if that would change partition numbers if you delete them and reboot. What I am worried about is what is now sda7 and sda8 changing partition numbers when you delet sda5 and sda6.

In the absence of an expert looking at this and telling you for sure that you can delete those two partitions. I would leave well enough alone. Those extra partitions are small and are not going to hurt you by leaving then alone. sooner or later you will end up doing a clean install and that will clean this all up.

I know you do not want to screw up a now running system so unless you get someone to tell you with confidence that you can delete these, just live with them.

One more thing that may help. get the *.txt file and post it using the ## in your post. More people can see it that way and you may get more help. Some people may not want to go to the trouble of opening a zip file to look at this.

---

### Post by Unew on 2009-05-02
Thanks for your advice.  I'll just leave the unnecessary partitions alone; everything appears to working well right now.

---

