---
title: "Wine V Virtualbox"
date: 2008-11-19
forum: General Help
---

### Post by Kzap333 on 2008-11-19
Sooo, before I start I'll apologice in advance for my spelling, I'm typing this at school and they don't have firefox (let alone Ubuntu).
Anyway the back story; We have justed built a new main computer for our house (2.9GHz 64 bit duelcore prosesor 4GB of RAM and 500GB HDD). On our old computer we had a duel boot with Windows XP (for games only) and Ubuntu for everything else. However my mum got anoyed as everytime my brother had be playing Warcraft3 she had to restart to check the e-mail. So on this new computer I want too only install Ubuntu, and either use and virtual XP enviroment though something like VMwhare or use wine (actuall a freind of mine got a free copy of Crossover from something called 'the lame duck chalange').
Anyway in your opionin wich would be best for games. You know the sytem speck wich would be simplest for a family. If you really think the best idea is duel boot then that's what I'll end up doing.

I hope this makes sense.

---

### Post by Peter09 on 2008-11-19
Some but not all games will run fine under wine. Look at the gamers forum on this site for help.


VirtualBox has no 3D graphics support so thats a no-go for you.

---

### Post by jespdj on 2008-11-19
VMWare or VirtualBox is definitely not the best choice for games. Those products don't support 3D accelerated graphics in the virtual machine, so you most likely will not be able to play games with a lot of 3D graphics in VMWare or VirtualBox.

Wine does (partly) support it, and many games work on Wine.

Why don't you just try out Wine with your particular game to see if it works?

---

### Post by Peter09 on 2008-11-19
Here is a link for wine

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by CholericKoala on 2008-11-19
If you want performance for games, you HAVE to dualboot.  Wine can give some performance, but it is not nearly as good as a pure boot.  Crossover does a decent job, but if you do not have an awesome vid card then you do not have much of a choice as of now.

---

### Post by hyper_ch on 2008-11-19
> **Kzap333 said:**
> Sooo, before I start I'll apologice in advance for my spelling, I'm typing this at school and they don't have firefox (let alone Ubuntu).
I wonder what a browser has to do with correct spelling?

Depending on the game you can run it with wine... Civ III and IV work fine... WoW works fine... no clue about WC3.

VmWare has now also support up to directx 9 - however it requires a bit of tweaking (you need to manually set a few things) and you need a video card that supports an according opengl version (I have not tried it myself, but I read about it).

---

### Post by Kzap333 on 2008-11-19
Okay thanks for all the input. so virtualbox is a no go.
BTW firefox has a built in spell checker (have you not noticed it).
I'll try the games with cross over but we may end up duel booting again. The problem is we have over 25 games and we want all (or as many as posible) to work.

---

### Post by binbash on 2008-11-19
warcraft 3 works better than windows at my box with wine

---

### Post by hyper_ch on 2008-11-19
> **Kzap333 said:**
> BTW firefox has a built in spell checker (have you not noticed it).
Yet you shouldn't depend your spelling skills on a spell checker ;)

---

### Post by Kzap333 on 2008-11-19
> **hyper_ch said:**
> Yet you shouldn't depend your spelling skills on a spell checker ;)
I'm deslecsic (why do they make that word SOOO hard to spell) and I'm am never ever going to be in a situation where I need to spell something and not have a laptop or phone on me.
I'm even aloud to use one for my exams but I lose all the marks for spelling (which I would not get anyway).
I gave up on spelling in year 5 (I wrote about some pie-rats in a boot).
**Anyway** I'm going to put the computer on a **duelboot** and have some games that run though crossover (eg warcraft3) on ubuntu and all use Windows when my family want to play 'The Sims' or something that needs windows.

---

### Post by Trafferth on 2008-11-19
Definitely dual-boot - wine is hit-and-miss, whereas virtual machines have no 3D support.

-T :)

---

### Post by hyper_ch on 2008-11-19
> **Trafferth said:**
> whereas virtual machines have no 3D support.

vmware has

---

### Post by Trafferth on 2008-11-19
> **hyper_ch said:**
> vmware has

True, but isn't it 'experimental' support that only extends as far as DX8?  Seems a waste if you have a nice DX9-capable graphics card.  Plus, depending on how fast the host machine is, there is likely to be a significant performance hit, which when playing games is not exactly what you want to happen.

Still, worth a try to see if it does what you want.

-T :)

---

### Post by hyper_ch on 2008-11-19
well, in vmware workstation 6.5 it's already enabled by default and it goes to dx 9.0c

[http://www.vmware.com/products/ws/new.html](http://www.vmware.com/products/ws/new.html)
> 
Richest Desktop Experience

    * Access applications within virtual machines as if they were part of the host operating system desktop with &#8220;Unity&#8221; view
    *** Support for DirectX 9.0c with Shader Model 2 3D graphics**
[...]


---

### Post by Trafferth on 2008-11-19
> **hyper_ch said:**
> well, in vmware workstation 6.5 it's already enabled by default and it goes to dx 9.0c

[http://www.vmware.com/products/ws/new.html](http://www.vmware.com/products/ws/new.html)

Cracking! Well worth a go, then.

-T

---

### Post by Kzap333 on 2008-11-25
In the end we went for a program called Cedega (something like that). It's not free and it's not opensorce but soo far it's been better than Wine (or Crossover).

---

