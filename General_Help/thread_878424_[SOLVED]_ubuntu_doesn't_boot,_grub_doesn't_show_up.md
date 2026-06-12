---
title: "[SOLVED] ubuntu doesn't boot, grub doesn't show up"
date: 2008-08-02
forum: General Help
---

### Post by Mine's Ultimate R on 2008-08-02
I was curious as to why suddenly ubuntu won't boot? I've had it for quite a while now and everything has been working fine until this morning. It went into sleep mode and i wasn't able to resume which is normal. So I shut it down manually (pressing the power button) and turned it back on. After turning it back on, it showed my two options of which os to boot to (i suppose i have dual boot with windows vista and ubuntu) which is normal. I go down to ubuntu and choose it, but it doesn't load and go into the grub menu like it normally would. Instead it goes directly to a grub> command line. Pressing esc allows me to go to a screen which such options of "reboot", "command line", "halt", and a few "find" lines.
So I was wondering if anyone knew why this happened? And if I fix it will it happen again? I've been looking for the answer in these forums and still am looking as you read this, so if you know a link to the solution then it would be wonderful if you could direct me to it.

owen
sorry about the long post :)

---

### Post by phidia on 2008-08-02
The Ubuntu grub wiki to restore grub is [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub").
There are other guides too which might help all you need do is enter grub in the search box from that page. 
I just thought restoring grub might be the simpler thing.
I'm not sure why it happened but you do say that your computer won't resume from sleep. A cold shutdown like you are doing could be the cause. 
You can start a new thread for the sleep not working problem to get that fixed. Hope that's helpful.

---

### Post by Mine's Ultimate R on 2008-08-02
hmmm, so is that my only option? i can't get into ubuntu and i don't have a live cd, but i will take a look at the link

also for the suspend, i've done some work on that so now it wakes when i put it into suspend myself, but it doesn't wake when it goes into suspend by itself

gracias

---

### Post by phidia on 2008-08-02
It's not your only option if you don't have a livecd you can look at the repair method [here]("https://help.ubuntu.com/community/GrubHowto").
There is also a suspend sleep howto [here]("http://ubuntuforums.org/showthread.php?t=471855&highlight=grub").

---

### Post by Mine's Ultimate R on 2008-08-02
thank you very much, i will try those! and one other thing, i never partitioned my drives, will i ever have to do that?

edit: Now i'm a little confused. I am able to choose between windows vista and ubuntu, so is that the grub in action? Or is that the windows bootloader? Man this is frustrating. It just sits at a black screen. How can I access terminal anyway? or am i already in the terminal when it says "grub>"? The thing is that it acts differently from the terminal so i am not sure. 

The suspend links looks very promising but i won't be able to work on that until after i get ubuntu working :(

---

### Post by Mine's Ultimate R on 2008-08-03
oops, actually it isn't a real dual boot
i think i installed it inside windows, but anyway ubuntu still doesn't load

well nothing i tried worked (superdiskgrub thingy), so in the end i just reinstalled ubuntu :(

oh well, thanks for the help

---

