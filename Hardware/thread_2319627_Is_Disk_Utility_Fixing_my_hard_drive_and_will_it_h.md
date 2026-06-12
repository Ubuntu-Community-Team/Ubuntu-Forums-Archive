---
title: "Is Disk Utility Fixing my hard drive and will it help?"
date: 2016-04-06
forum: Hardware
---

### Post by jackyhughes on 2016-04-06
I could not install Ubunto and did various tests and concluded my hard drive had failed. 

Then I read about disk utility and used it to discover there were 5 bad sectors on the disk.

Running the short assessment then showed that 5 bad sectors were reduced to 2

I am now running the longer (tens of minutes test.)

**Will this fix my hard disk enough to use it for a while longer?**

(I understand that this might not be a permanent solution and that the hard disk could fail again, but would back everything up anyway)

I just do not have the technical knowledge to know what I am doing.



Thanks

---

### Post by jackyhughes on 2016-04-06
```
ubuntu@ubuntu:~$ badblocks -svn /dev/sda
badblocks: Permission denied while trying to determine device size

What exactly happened and what do I do about it?
```

I have 2 bad partitions
 

Thanks

---

### Post by howefield on 2016-04-06
Threads merged.

---

### Post by Bucky Ball on 2016-04-06
```
ubuntu@ubuntu:~$ sudo badblocks -svn /dev/sda
```

Try that. Please use code tags for terminal output (see the green link in my signature at bottom of this post).

---

### Post by jackyhughes on 2016-04-06
```
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo badblocks -svn /dev/sda
ubuntu@ubuntu:~$: command not found
```

I copied and pasted so what am I doing wrong?

I am now totally confused. The reason for each separate thread was because recently I posted a problem and someone asked me to ask just one question. I actually thought it made more sense to ask what I wanted to know in one thread. It does feel as if there is no way of ever knowing how to post correctly on this forum and it gets very intimidating for those of us who are not very expert. 

I do not mean you are, but it does rather feel as if it is impossible to understand how to post so as to get the answer to a problem. Most issues have more than one question.

---

### Post by howefield on 2016-04-06
> **jackyhughes said:**
> I am not totally confused. The reason for each separate thread was because recently I posted a problem and someone asked me to ask just one question. I actually thought it made more sense to ask what I wanted to know in one thread.

It can be quite complicated to navigate around the forum but it is in your own best interest to ask the best possible question in order to get help, have you ever read the forums [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules") and in particular the [Posting tips]("http://ubuntuforums.org/showthread.php?t=2158945") linked from it. They might help you.

There is no problem in asking questions on the same subject/topic within the same thread. Different topics within the same thread can be problematic.

I don't want to take your thread even further away from your original posting so will leave at that.

---

### Post by Bucky Ball on 2016-04-06
```
sudo badblocks -svn /dev/sda
```

That is all you need. Not the 'ubuntu@ubuntu' part that was in the command in my last post. That is your user and machine which you will see before the cursor.

---

### Post by jackyhughes on 2016-04-06
My problem is solved. To recap:

I could not restore grub as there is no P working on the keyboard and this is needed to input the code. I could not get any external keyboard to work.
I inserted the old 12.04 disk I have knowing (as it worked on the Toshiba) that the disk worked.
Because grub has failed before and I have reinstalled several times I needed to know if the hard disk was broken.
I knew about Boot repair. I tried that from the disk and it did not work.
Gparted initially remained blank leading me to believe the hard disk might be broken.

I needed to know the state of the hard disk because I could not reinstall Ubuntu 

I did not realise I could use disk utility till this morning. 
This showed that the hard disk did exist. It showed 5 bad partitions which went down to 2 on using disk utility
I looked somewhere on this forum and found someone talking about 11 bad partitions which made me think I could delete the  2 bad ones and carried on inputting all sorts of things people suggested to no avail.

Then I thought about it. If you can resize partitions, then why not do this? I tried to do it in gparted and this would not work. A lot of my problem stemmed from gparted and boot repair not working and that was why I thought the hard disk was completely gone. My assumption was that they could not find the hard disk because it had probably completely broken.
Now I knew the hard disk must be there because otherwise disk utility would not show it.

My thought was that would I, by increasing the size of the new partition and decreasing the size of one of the old bad ones, create new and working partition? I don't know which thread I read but I usually do  not post and look for a thread and the thread I found discussed this.

I also wondered if maybe Ubuntu was not  installing because it needed more space. That had been puzzling me all along as I was sure there was enough space even when I saw there were two partitions.

It occurred to me that if the installation disk had an advanced option I should look there and hey presto! I found I could resize the partitions. I resized the new one I assumed the disk would create to the maximum.

The installation worked. I have just upgraded to 14.04 or whatever the latest is and am considering the 15. whatever just to see what happens.

I realise from reading here that the hard disk could do the same thing again as it is presumably getting old and that is why it failed. I don't mind as I will just back everything up.

Thank you to those who did try to help.  This was a tricky problem for a non technical person who simply hopes someone will give them magic code and it will work! o 

Interestingly, I can now see all the partitions. My next project will be to get into them. So far I cannot seem to drop down to them on starting up when the correct place appears.  Never mind for now. I have reinstalled Ubuntu despite every thing I did or did not do.

Thank you for those who did try to help me.
I have no idea if what I just wrote would confuse someone or help them, or that everyone who is really clever is splitting their sides laughing, but had I NOT posted I would not have eventually solved the problem because I would still be inputting code that did not work.

I may even have used the wrong word for the wrong thing.  Who cares now the thing is working again. I will start on a bicycle next and you can thank your lucky stars you do  not have to answer my posts on a bicycle forum!

---

### Post by Bucky Ball on 2016-04-06
Thanks for sharing. Please mark as solved. See the first link in my signature at the bottom of this post for how.

---

