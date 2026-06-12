---
title: "[SOLVED] can I uninstall evolution-data-server-2.22??"
date: 2008-08-22
forum: General Help
---

### Post by PaulNKS on 2008-08-22
I am new to Ubuntu and have been playing with it for about 2 weeks and have it on a dual boot with XP.  I use Thunderbird.  My system suddenly started running slow and the fan is running more than usual.  When I check the system monitor, evolution-data-server-2.22 is hogging anywhere from 85% to 95% of the cpu resources.  I am assuming this is the reason for the slow down in speed.  Will it "break" anything if I uninstall all evolution components or at least the evolution-data-server-2.22?  

I am running an AMD 64bit with kernel 2.24.16.  I found that after hard freezes, if I don't install the updates. I eliminate the hard freezes.

Thank you in advance for any help.
PaulNKS.

---

### Post by my_key on 2008-08-22
If you want to use evolution, then you will need the evolution-data-server since it's one of evolution's dependancies. But you can easily have evolution-data-server not starting at boot by editing your session (System > Preferences > Sessions) by unchecking the box next to it. Your calendar applet wil not show your events or items if evolution-data-server isn't running, but at least you would not lose valuable resources.

If you are able to reproduce this problem, you might consider filing a bug?

Hope this helps.

edit: I forgot to state this clearly, but you might already have figured this out: if you only use thunderbird, it's save to uninstall evolution-data-server and thus evolution.

Michael

---

### Post by PaulNKS on 2008-08-22
Michael,
Thank you for your quick help.  I tried that solution, but when I rebooted, the data-server-2.22 also started up again.  I went ahead and removed Evolution since I use Thenderbird and it solved my problem.  

Thank you again.
Paul

---

### Post by rpaco on 2008-11-17
I expect some of the more knowledgeable guys may laugh at this but try using the Synaptic Package Manager and doing a search on Evolution, then ticking all the items it comes up with and mark for removal. Though I am sure there is a quicker command line method of doing this. Something along the lines of Sudo Apt-Get remove Evolution, (I am guessing here)

I have been tempted to change over to Thunderbird because of the frequent freezes that Evolution causes.

---

