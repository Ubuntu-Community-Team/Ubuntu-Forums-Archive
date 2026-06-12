---
title: "Switching video cards a problem? Ubuntu 14.04"
date: 2016-06-08
forum: Hardware
---

### Post by danny64 on 2016-06-08
Hello there,

I have a Ubuntu rig running 14.04, and a while back I switched from a Geforce 750 to a 970, and it wrecked the OS. I had to reformat and reinstall. 

Now I want to switch the 970 for a AMD 7870, and was worried that I would destroy the OS again. Can anyone verify whether it's safe to switch cards? If so, what do I need to do in term of drivers?

Sorry, I am VERY new to Linux in general, and have little to no experience working in terminals.

---

### Post by QIII on 2016-06-08
You likely did not wreck your OS before.  You most likely simply needed to uninstall the driver and reinstall it after replacing the cards.

Similarly, this time you need to remove the NVIDIA driver, switch the cards and then install the fglrx (AMD) driver -- or just use the default open source Radeon driver.

---

### Post by danny64 on 2016-06-08
> **QIII said:**
> You likely did not wreck your OS before.  You most likely simply needed to uninstall the driver and reinstall it after replacing the cards.

Similarly, this time you need to remove the NVIDIA driver, switch the cards and then install the fglrx (AMD) driver -- or just use the default open source Radeon driver.

Thank you for the reply.

I had our IT guy at work look at the OS before, who is familiar with linux, and after days of trying he was unable to fix it. Thus you are right, I may not have.

However, I wasn't able to do it with my skill level.

In terms of the advice you gave me, thank yoU! Should I just google "how to uninstall nvidia drivers in ubuntu 14.04" and the same for install of AMD? Sorry, I really am new to all this.

---

### Post by Bashing-om on 2016-06-08
danny64; Hello;

To remove the Nvidia driver:
```

sudo apt purge nvidia*
sudo rm /etc/X11/Xorg.conf

```


Install the ATI card .. and boot up .. You will boot up with the open source driver. Try it, you may be pleasantly surprised. AMD and our developers have done a LOT of work on the open source driver .

Else; in "Additional Drivers" one can choose to install the FGLRX (proprietary) driver.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by danny64 on 2016-06-09
> **Bashing-om said:**
> danny64; Hello;

To remove the Nvidia driver:
```

sudo apt purge nvidia*
sudo rm /etc/X11/Xorg.conf

```


Install the ATI card .. and boot up .. You will boot up with the open source driver. Try it, you may be pleasantly surprised. AMD and our developers have done a LOT of work on the open source driver .

Else; in "Additional Drivers" one can choose to install the FGLRX (proprietary) driver.
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


Thanks for the reply.

Unfortunately, the command "sudo rm /etc/X11/Xorg.conf" did not work. However I used the first command, installed the AMD GPU and booted up. 

The 'open source' drivers that automatically were used did not work. It wouldn't allow me to change ANY display settings at all, and I had two displays so I needed this. Also, the computer has a 27" monitor, and it was in really small resolution. Thus I had to download the FGLRX propriety driver, and it works perfect so far.

Hope this info helps further Ubuntu! If you want me to get any error codes for you let me know.

---

### Post by Bashing-om on 2016-06-09
danny64; Hey ...

The use of the config file /etc/X11/Xorg.conf has been depreciated, so I am not surprised that the file did not exist on your system. It does have it uses and will be used IF it does exist .

Well as :
> 
Thus I had to download the FGLRX propriety driver, and it works perfect so far.


We can conclude that this matter is concluded, I will leave it to QIII for closing remarks to the matter of substandard performance with the opensource driver; as he has the greater experience.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we are all in this together
[INDENT][INDENT][INDENT]and together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

