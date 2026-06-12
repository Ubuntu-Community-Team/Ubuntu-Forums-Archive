---
title: "Move Ubuntu installation?"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by DoRullings on 2009-06-11
Hi everyone. This is my first post in this forum, and I hope you fine people can help me with something I assume is possible, but I don't know how.

I have set up Ubuntu on a server with a lot of configurations and applications that I want to keep. Everything is installed on a single 80GB HDD  and I plan to install two 1TB disks and mirror them (Raid 1). Now I would like to copy everything from the 80GB over to the two 1TB harddrives including Ubuntu installation, application, MBR, and whatever I need to copy to make the current installation to run on the new Raid setup. I will then remove the 80GB.

Now so the question is:

 - Is this doable?
 - Can someone tell me how to do it? (Preperation, precautions, commands, etc.)

I have read some threads and articles with guids, but I'm not sure if they can be used in this case

If someone would be so kind to help me with this, or point me to an article that suites my need I would be very grateful.

Thanks!

- Thomas

---

### Post by ronparent on 2009-06-11
Yes it is doable. You didn't say whether yiu were using 8.10 or 9.04. Also whether your raid is software raid or fakeraid? Also is windows involved?

You have probably seen this, but, it is the best guide to installing ubuntu to a fakeraid: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by DoRullings on 2009-06-12
ronparent: Thanks for your reply! I didn't notice it because I didn't subscribe.

I planned to use fakeraid (the raid controller on the motherboard), or maybe you would advice me to do something else? Windows is not involved. It is Ubuntu 9.04.

The "tricky" part, if it is tricky, is that I have an installation I'm very happy with and want to move this over to the new array 1 setup so that  I'm sure that all the files are backed.


Thanks,
Thomas

---

### Post by ronparent on 2009-06-12
The tricky part is figuring out what you want to do and what you are working with. You have the option of a software raid if you don't have to co-access the raid with windows. However it is not apparent from your post what you actually want to do, which flavor of raid in or was originally setup in the raid bios and what version of ubuntu you are using. 

Once the raid is activated it colud be a simple matter of copying it to the raid drive and deleting the original.

---

### Post by DoRullings on 2009-06-13
Hi again :-)

I'll try to be little bit more clear. 

Nothing has been setup yet, except from the "old" Ubuntu 9.04 server installation that I want to keep. The HHD's haven't even been bought yet. This is a plain Ubuntu server and Windows will never be installed on this machine. 
Can you give me an advice about whether I should choose "fake raid" or "software raid"? Which one is fastest, pros and cons, etc? I didn't know about the "software raid" option until you brought it up. 

Thanks,
Thomas

---

### Post by ronparent on 2009-06-13
The software raid is called mdadm. These howto's Will tell you how to implement:

[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ubuntuforums.org/showthread.php?t=1027240&highlight=raid](http://ubuntuforums.org/showthread.php?t=1027240&highlight=raid)

The pro and cons of software raid vs fakeraid I've seen mostly boil down to personanal preferences bolstered by strong biased opinions. In my opinion they are both workable and comparable, each with it's own set of limitations and advantages. It is an adventure to set up and operate however and be prepared to learn some of the details to avert disaster.

---

