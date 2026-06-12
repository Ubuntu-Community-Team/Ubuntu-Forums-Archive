---
title: "Ubuntu 17.1 live disk wont run on Dell Presition t3400 with ATI FireGL V7700"
date: 2018-02-06
forum: Hardware
---

### Post by Webmaster45 on 2018-02-06
I just got a Dell Presition T3400 with a ATI FireGL V7700 graphics card.  I first installed Windows 7 and it works fine.  Then I put in the Ubuntu 17.1 live disk to install Ubuntu as a dual boot.
It started up got past the purple introscreen and went to black with flashing curser in upper left corner and then it just stopped and nothing else happened.  I think its because the ATI graphics card is not supported by ubuntu.  Even verbose and safe graphics mode did not work.  I know Linux drivers are available on ATIs support site but if I cant install Ubuntu to use them what good are they.  Anybody got any ideas?  Will Ubuntu 18 support this graphics card in the future?

---

### Post by mörgæs on 2018-02-06
Have you tried X/Lubuntu in a live boot?

---

### Post by Yellow Pasque on 2018-02-06
Do not use any driver from ATI/AMD site. Any driver for this GPU will be too old to work on modern Linux kernels. The correct driver is already available in the kernel.

---

### Post by QIII on 2018-02-06
Hello!

It's not a matter of Ubuntu not supporting the card.  The issue is that for many years now AMD has not developed a driver for that card that supports current Linux distributions.

While the default open source Radeon driver should work (surprised if it doesn't), there is no proprietary Linux driver available.

I'd try a lighter DE as suggested.

---

### Post by Webmaster45 on 2018-02-07
I tried Lubuntu I got the same result.

---

### Post by Webmaster45 on 2018-02-08
I also tried Fedora same result,  Any thoughts?

---

### Post by Webmaster45 on 2018-02-08
I also tried Ubuntu 17.1 with wubi same result.  I wonder Could a Bios setting stop Ubuntu from working its running Bios version A14?

---

### Post by mörgæs on 2018-02-08
A14 is as new as it gets.

Have you tried boot options like nomodeset?

---

### Post by Webmaster45 on 2018-02-09
I did not see that one. How do I get to the [COLOR=#000000]nomodeset option?  Verbose did not work and safe mode did not work.[/COLOR]

---

### Post by mörgæs on 2018-02-11
[https://i.stack.imgur.com/FfEwE.png](https://i.stack.imgur.com/FfEwE.png)

---

### Post by Webmaster45 on 2018-02-11
Your Idea worked.  It was very slow and grueling install with lots error messages but it installed lubuntu and it worked but its stuck in 4:3 configuration for screen even though I have wide screen.  I later installed mate it worked with same screen orientation issue.  Unity works the same as does Gnome but its a start and I appreciate all your help.  hopefully either canonical or ati will create a better driver down the line.   If you guys know where I can get better driver please let me know.  Thanks Again.

---

### Post by Yellow Pasque on 2018-02-11
If you boot with 'nomodeset' parameter, you're going to be stuck at basic resolution regardless of desktop environment.

> hopefully either canonical or ati will create a better driver down the line. If you guys know where I can get better driver please let me know. 

Again, Ubuntu already has the correct driver. For some reason, it doesn't work. I see a similar complaint:
[https://bbs.archlinux.org/viewtopic.php?id=169020](https://bbs.archlinux.org/viewtopic.php?id=169020)

When you boot without nomodeset, can you press Ctrl+Alt+F1 to get to a terminal when you see the blinking cursor?

---

