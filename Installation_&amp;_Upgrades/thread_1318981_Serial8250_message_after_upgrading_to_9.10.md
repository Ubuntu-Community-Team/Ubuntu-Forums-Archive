---
title: "Serial8250 message after upgrading to 9.10"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by c_tekken on 2009-11-08
Hello,

  I just upgraded my computer from Ubuntu 9.04 to 9.10. Now i'm faced with a problem that i have not idea how to begin troubleshooting. when my computer boots up (dual boots windows vista and linux - defaults to linux) i get black screen with an endless loop of the following message:

[  xx.xxxxxx] serial8250:  too much work for irq17

  I would greatly appreciate any assistance that may be offered on this issue. My knowledge is fairly limited when it comes to linux.

Thank you!

---

### Post by kubug on 2009-11-08
Me too. It looks like the IRQ is being flooded. Wonder if setting the "irqpoll" flag on the kernel would get this resolved.

---

### Post by kubug on 2009-11-08
> **kubug said:**
> Me too. It looks like the IRQ is being flooded. Wonder if setting the "irqpoll" flag on the kernel would get this resolved.

I can answer my own post. It doesn't work. 

What happened was that the "modem-manager" used 95% of my CPU after that and the message wouldn't disappear. 

Not sure where the issue lies but since I have a PCI modem, I just removed it from my motherboard. No more message. If you have a laptop, you may be able to disable the modem in the BIOS.

---

### Post by c_tekken on 2009-11-08
I was not as lucky, i removed the modem from my PC but now i have another problem. When my computer boots up i have a black screen with white writing that keeps flickering...

[INDENT]Starting up ...
Ubuntu 9.10 hostname tty1

hostname login: * Stopping the Firestarter firewall...

hostname login:
password:
[/INDENT]
I try to type in my user name and password, but the pc seems to only accept keyboard intermittently which makes it impossible to type in my user credentials.

---

### Post by kubug on 2009-11-09
By any chance, do you have an nvidia video card?

---

### Post by c_tekken on 2009-11-09
[FONT=Verdana][SIZE=2]I do not, i have a silicon integrated systems card. I saw a post for "[/SIZE][/FONT]**[B][FONT=Verdana][SIZE=2]9.10  boots to tty1 CLI only" that sounds just like what i'm running into now, but I do not have an Nvidia card and when i went to SIS website i was unable to find updated drivers. I wanted to mention that i am able to ssh to the problem computer, in case that helps at all. [/SIZE][/FONT]**
[/B]

---

### Post by kubug on 2009-11-09
The reason why I am asking is because I messed up my nvidia install (I downloaded from their website) and it did the same thing. Once I fixed my drivers it all worked.

I think ubuntu is trying to get a low-setting x back up and not succeeding. Thus the flicker.

When I get home I am going to plug the modem back in and then remove the "modemmanager" package to see if that fixes the messages. Then we can be sure it's in that package where is issue lies. You may want to try that and see if your x comes back up, but it's sound unrelated.

---

### Post by c_tekken on 2009-11-09
I will go ahead and try that as well. Thank you!

---

### Post by c_tekken on 2009-11-13
I think I'm just going to do a fresh install of 9.10 and see how that works. This problem is way over my noob skills. Thanks for you help.

---

### Post by kubug on 2009-11-13
Sorry if I couldn't help more. Usually I wouldn't suggest a new install (Windows way of doing things), but maybe you are right. Especially if you don't have any important information to lose on it.

---

