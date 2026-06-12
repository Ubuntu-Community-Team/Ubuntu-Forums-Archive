---
title: "Failed install on 2 different Computers"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Herber on 2009-04-25
:confused:Can anyone tell me if I will ever be able to use future versions of Ubuntu on my computer.  I have attempted installation on 2 computers with failure in both.  I have had great success with ubuntu in the past (since 6.10).  I have ATI graphics cards in both computers, and that may be the issue.  One card is 10years old, the other a year old. (I7000 in a dell Inspiron, and another ATI 2600 PRO in a dell desktop).  Will canonical fix the issue?

---

### Post by mikewhatever on 2009-04-25
What issue? ATI graphics? What's the problem exactly?

---

### Post by Herber on 2009-04-25
Problem:  On install of a 9.04 from a downloaded and Check summed CD my Dell Inspiron 7000 Hangs on the "ubuntu" logo screen with the progress indicator at about 10%.  This same thing happened when I tried to upgrade from 8.10 to 9.4 from a functioning 8.10 install on the same machine.  I then tried to install on a Dell 8200 Desktop which had a prviously functioning 8.10 install. Booting  on the LIVE disk leaves me with a black screen with some color noise at the top, but a functioning mouse pointer visible in the screen.

While reviewing the forums I see there is something about a ATI graphics driver change (which resulted in similar problems) that will not support some graphics cards.  Since both computers have ATI cards and I have never had a problem getting UBUNTU to install on any computer since 6.10, I thought that was probably my problem?

Help?

---

### Post by axel_2078 on 2009-04-25
Have you tried using different boot parameters before installing? I have to use the noacpi, noapic, and nolpic options in order to get it installed on my laptop.

---

### Post by Herber on 2009-04-25
I have not changed any of the boot parameters, and I wouldn't know where to start.  I will look into that in the help info.  I have not had to change any of that stuff for the previous versions of Ubuntu these machines had installed on them.  

Do you know if this "fglrx" driver problem might be the culprit?

---

### Post by mikewhatever on 2009-04-25
> **Herber said:**
> I have not changed any of the boot parameters, and I wouldn't know where to start.  I will look into that in the help info.  I have not had to change any of that stuff for the previous versions of Ubuntu these machines had installed on them.  

Do you know if this "fglrx" driver problem might be the culprit?

It's possible there is a problem with ATI cards and 9.04, but it isn't a known issue. You could try booting in safe graphics mode from the live cd by pressing f4 at the menu screen, or using a text installer from the Alternate cd. Staying with Intrepid is also an option, at least until the issue is clarified.

---

### Post by Herber on 2009-04-26
> **mikewhatever said:**
> It's possible there is a problem with ATI cards and 9.04, but it isn't a known issue. You could try booting in safe graphics mode from the live cd by pressing f4 at the menu screen, or using a text installer from the Alternate cd. Staying with Intrepid is also an option, at least until the issue is clarified.

I'll Try the F4 trick today, thanks.

---

### Post by axel_2078 on 2009-04-27
If that doesn't work, you can select F6 to modify your boot parameters.

---

### Post by 1roxtar on 2009-04-27
I had a failed install when I tried do a dual-boot on my laptop.  I had to delete the Ubuntu partition, fix my MBR and reinstall Windows.  After I got the machine going again, I reinstalled Ubuntu/Jaunty with Wubi and EVERYTHING works perfectly.  I also installed Jaunty onto my Acer Aspire One netbook with Wubi and it works great too!!!  I love Ubuntu and I'm going to stick with it!!!
(FYI: I'm a Ubuntu/Linux virgin, but I am settling down with this awesome OS)

---

### Post by Herber on 2009-04-29
Hey thanks for the suggestions, The Safe video mode made an install on the Desktop Dell 8200 possible and the new 9.4 OS is great.  I think the problem on the old Dell laptop is that the Max machine memory is 320MB.  But the live disk says it needs 380+MB to run.  So I Guess the old Dell Inspiron 7000 is stuck in 8.10?  Does anyone know a way around this?  The 9.4 information says I only need 256MB to run 9.4.

---

### Post by Herber on 2009-05-01
Ok, I want to summarize my current situation.  The problem with installation on the Dell Desktop 8200 was solved by using the safe graphics mode.  Installation of the 9.04 went well.

The older laptop a Dell Inspiron 7000 still is hanging during the "Ubuntu" screens with the progress bar moving back and forth.  If I wait long enough I will get kicked out to a black screen with what looks like some code on it.  
-- Safe video doesn't help
-- I don't think it is the memory problem I wrote about earlier because the same memory requirements are on the Ubuntu 8.10 install that is flawless.
-- I have tried to install with changes to APIC etc without benefit.

Any other suggestions, I still think Ubuntu is great, and I can certainly live with 8.10.

---

