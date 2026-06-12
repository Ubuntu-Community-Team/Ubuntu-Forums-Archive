---
title: "Suspend not working on Vaio VGN-FW530F"
date: 2011-07-18
forum: Hardware
---

### Post by Xanthanov on 2011-07-18
Hi all, 
    Any tips on how to fix suspend for this model would be great. Running Ubuntu 11.04 atm, but had same issue on 10.10. System appears to suspend, even the power light is red and flashing. But, when it wakes up it just reboots completely. 

I tried suggestions here: [http://bit.ly/fHcNip](http://bit.ly/fHcNip) to create files in /etc/pm/config.d.

I also tried:[http://bit.ly/fSSymX](http://bit.ly/fSSymX) this suggestion. Even verified the script ran by outputting to log file. No dice!

Thanks,
Charles

---

### Post by OpenSage on 2011-09-21
> **Xanthanov said:**
> Hi all, 
    Any tips on how to fix suspend for this model would be great. Running Ubuntu 11.04 atm, but had same issue on 10.10. System appears to suspend, even the power light is red and flashing. But, when it wakes up it just reboots completely. 

I tried suggestions here: [http://bit.ly/fHcNip](http://bit.ly/fHcNip) to create files in /etc/pm/config.d.

I also tried:[http://bit.ly/fSSymX](http://bit.ly/fSSymX) this suggestion. Even verified the script ran by outputting to log file. No dice!

Thanks,
Charles






I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time (although I never hibernate, so don't know if it will fix that). Hope this helps some people.\\:D/

---

### Post by dinoc on 2011-09-21
I've open a bug here for suspend/hibernation issue with natty and Sony Vaio, if you do have it, please post here, too:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/846357)

---

### Post by Toz on 2011-09-21
Out of curiosity, have your tried/does this fix work: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"). It has fixed suspend issues on a number of other newer notebooks.

---

