---
title: "Unable to Access Users After Upgrade"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by dave r on 2009-08-21
Upgraded to 64 bit from 32 bit, see this thread [http://ubuntuforums.org/showthread.php?t=1244420&highlight=32+bit+to+64+bit](http://ubuntuforums.org/showthread.php?t=1244420&highlight=32+bit+to+64+bit). Left the home partition alone and retained both data and settings. But there are three users on the computer and I can only access one user, me. if we try to log on one of the other users we get the mesage user doesn't exist, if I try and recreate one of the other users I get the message that the user exists. So how can I get the logon for the other two working? Will I have to delete these users and start again? If so how?

---

### Post by ronparent on 2009-08-21
I'm having simular problems. It get a bit complicated. Rather than deleting the users and losing all data associated with them, I plan on moving them to home-bu. I hope to then recreate those users (same names, passwords). Then I plan to copy the users from home-bu back to home (overwriting the users in home). Not done yet. I will then probably have to then reclain ownership of thase accounts in home to permit them to be used. To do that I would have to boot on the recovery mode and drop to a root prompt. At that point I should be able to reclaim each user in turn by entering the following commands:

[B]chown -R user:user /home/user
chmod 644 /home/user/.dmcr
chmod 644 /home/user/.ICEauthority[/B] 

Again, do above for each user ID. Then I will **exit** and continue booting. Hopefully then each user will boot properly. It is your choice, following the principal of conservation of agony, whether to just start each user with a blank slate or to try to reclaim their user accounts. To give credit, I borrowed the above routein from [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck to both of us!

---

### Post by dave r on 2009-08-21
ronparent  as the folders on mine are empty it looks like the data and settings have gone, so I am now looking at deleting the folders, creating new ones and restoring data from back up. though separate home partitions sounds like a good idea, I might do it for one of them

---

### Post by dave r on 2009-08-21
I have solved this by starting a sesion as root and deleting the folders. I have now created new users and restored data from back up.

---

### Post by ronparent on 2009-08-21
I am happy to report that I accomplished my task exactly as I had outlined and restored all user environments as planned. I do agree that sometimes you are better off starting with a new slate. It is all about minimizing your headaches and balancing the time spent against what you hope to recover. I guess it is a happy outcome for both our cases.

Yes, setting up a separate /home partition can make it easier to maintain multi-user environments during upgrades.

---

### Post by dave r on 2009-08-23
:P ronparent looks like we are both sorted now. You will have to explain to me some time how you set up a second home partition, I mentioned it on here and it got a less than enthusiastic reception.

---

### Post by ronparent on 2009-08-23
dave r: That was the reference I gave you previously - **[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)** explains it fully.

It has worked out good for me - simplifys upgrades somewhat. Give a yell if it gives you any problems.

---

