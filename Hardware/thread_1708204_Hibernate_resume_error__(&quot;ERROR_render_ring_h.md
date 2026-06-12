---
title: "Hibernate resume error  (&quot;*ERROR* render ring head not reset to zero)"
date: 2011-03-16
forum: Hardware
---

### Post by sathyashrayan on 2011-03-16
Dear group members,

**laptop:** Dell Inspiron N5030,

**OS:** using Ubuntu 10.10 - the Maverick Meerkat - released in October 2010

**kernel version:** 2.6.35-28-generic

I see this error in my screen when i resume from Hibernate. Is this a error or bug? Hardware or software? Does it harm my system in longer-run or shall I ignore? 

"*ERROR* render ring head not reset to zero ctl 00000000 head XXXXXXX tail 00000000 start XXXXX
 *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start XXXX "

This is a follow up thread of this thread.

[http://ubuntuforums.org/showthread.php?t=1675699](http://ubuntuforums.org/showthread.php?t=1675699)

Since i did not get any message for my post I am reposting it. I hope some one might answer now. Thanks

---

### Post by Artemis3 on 2011-03-16
If it works, ignore them, period.

---

### Post by GTMoraes on 2011-03-16
I get this too, the more I hibernate/suspend it, the more it accumulates. Makes a visual pollution and the cause of those messages might make the startup longer. Not sure.

Machine: Acer Aspíre 1410 (Celeron ULV 723 | 2GB DDR2 800 | Intel 4500 mHD)
O.S.: Ubuntu 10.10 Maverick Meerkat
Kernel:**** 2.6.35-28-generic

---

### Post by sathyashrayan on 2011-03-16
Thanks all for the reply. I don't find this error during suspend. I am getting it during Hibernate alone. After I restart/ shout down the errors are starting newly. I mean the error of previous set of Hibernate has gone and new set of error starting.

 My little knowledge tells that its a HD error. I am worried about the HD life in the long-run. 
 I also get some more error with usb port too. 

How can I post such errors with dmesg? Shall i attach whole dmesg?

---

### Post by Artemis3 on 2011-03-17
Use pastebin and put a link maybe? Is your swap bigger than your ram?

---

### Post by sathyashrayan on 2011-03-17
> **Artemis3 said:**
> Use pastebin and put a link maybe? Is your swap bigger than your ram?

hi Artemis3,
  Yes. I went to system->administrator-> disk utility and saw the boxed diagram of HD memory, I can see the swap space as 6 gb.. I think my RAM is 2 GB. I have attached 1 file. 


One is: mem.txt with the command "sudo lshw -c memory"

And the pastebin link: [http://pastebin.com/hJRCahGJ](http://pastebin.com/hJRCahGJ)

---

### Post by Artemis3 on 2011-03-17
That appears to be a [harmless issue](http://amailbox.org/mailarchive/linux-kernel/2010/12/5/4655062).

---

### Post by sathyashrayan on 2011-03-17
> **Artemis3 said:**
> That appears to be a [harmless issue]("http://amailbox.org/mailarchive/linux-kernel/2010/12/5/4655062").

hi Artemis3,
  I saw this link. I even given the same link in other post too. cross check my first message in this thread. But it seems to be too technical for a beginner like me. Though the error is less harfull can any one explains what the thread  [http://amailbox.org/mailarchive/linux-kernel/2010/12/5/4655062](http://amailbox.org/mailarchive/linux-kernel/2010/12/5/4655062) talks all about?

---

### Post by drnessie on 2011-03-22
I am getting these errors too.

To be honest, I do not care if it's harmless. I want to remove it, or at least remove the output.

The more I hibernate, the longer un-hibernation takes, and I believe it is just because of this *ERROR*.

Acer Apire 1825PTZ, 3GB RAM, 9 GB Swap, Intel Pentium.

---

### Post by sathyashrayan on 2011-04-21
It is now solved in 11.04..Did any one got it solved?

---

