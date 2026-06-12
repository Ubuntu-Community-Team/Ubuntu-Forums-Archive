---
title: "IBM ThinkPad T20 and Edgy"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by omiazad on 2006-12-30
Hello Everyone,
I'm using Ubuntu Edgy on a IBM T20 ThinkPad laptop. But I'm facing some problem while the computer boots. When the computer boots, sometimes it hangs just before starting GDM. I boot the computer in recovery mode and type startx at the prompt, and it hangs. But sometimes it goes smoothly.

Mostly it happens when I shut this computer down and start after a hour or few. When the Ubuntu startup logo goes off and just before the log-in screen appears, it hangs.

Do you know any solution of this problem?

---

### Post by mmustic on 2006-12-30
Hey,
I have an older laptop (Lifebook Fujusu, 500mhz, 198ram, Ati AGP), and Edgy does not run well
on my computer. I have all types of X problems. I went back to 6.06LTS due to the problems. 6.06 works great on my hardware. I have heard that Edgy is does not do well with ATI G.C. and I think IBM T20-T30 had ATI.

---

### Post by omiazad on 2006-12-31
No Brother,
This T20 has S2 Savage. At least Windows Driver shows that.

---

### Post by po0f on 2006-12-31
omiazad,

What does the device section look like in /etc/X11/xorg.conf?  And post the output of:
```
[FONT="Courier New"]$ grep EE /var/log/Xorg.0.log[/FONT]
```
after X fails to start please.

---

### Post by Mark Stosberg on 2007-01-20
I was interested in running Ubuntu on my T20, but I was never able to confirm that suspend/resume could work properly. So, I've continued to use Mandriva, which works well in all aspects of hardware support. 

Also, Mandriva has better built-in wifi tools right now-- I know first hand from comparing my experience to a friend who has a Ubuntu laptop. So, while I run Ubuntu on a desktop and would consider trying Feisty on a laptop when it is released, I recommend Mandriva on the T20 right now. 

There is a page with details about installing Mandriva on the T20 here:
[http://www.thinkwiki.org/wiki/Installing_Mandriva_Linux_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Mandriva_Linux_on_a_ThinkPad_T20)

  Mark

---

### Post by mattotoole on 2007-03-08
Mark, while we appreciate your help, the point of this forum is getting *Ubuntu* to work.

---

### Post by al7kz on 2007-03-18
edit

---

### Post by ali4949 on 2007-03-28
I am running dapper on a T30 and no problems so far.. majority of the stuff worked out of the box, and no problems with the ATI 7500 chip set yet. Just posting my personal experience on running ubuntu on a thinkpad. there are some problems with the hibernate/suspend as in screen goes weird when it comes back from sleep, but it always recovers and my thinkpad function keys work just fine.. there are lots of utilities in the ubuntu repositeries that help make a thinkpad work and behave just as well as WINBLOZE machine.

---

### Post by meffie on 2007-08-01
Hello All,

I encountered the same symptoms with Feisty on an IBM thinkpad T20. Turning acpi off in the kernel fixed the hangs.  Add the parameter acpi=off to the first kernel line in the grub config file:

[FONT="Courier New"]/boot/grub/menu.lst
...
title   Ubuntu, kernel ...
root  (hd0,0)
kernel   /boot/vmlinuz-... ro quiet splash **acpi=off**
[/FONT]

---

### Post by omiazad on 2007-08-02
Nice tip!
But some days ago I through that laptop away, so no chance to check that out.

But thanks for the tip indeed.

:popcorn:

---

### Post by mattotoole on 2007-10-21
Everyone,

Please get it out of your heads that there is any similarity between the T20, T30, or T-whatever.  Though they look similar and have similar features, each model is a completely different machine with its own hardware, chipsets, etc. 

The T2x models are most similar to each other, but still different enough that it makes no sense to think, for example, that if something worked on your T23 it should work on someone else's T20.

---

