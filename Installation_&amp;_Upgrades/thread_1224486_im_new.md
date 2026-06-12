---
title: "im new"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by yogesh1 on 2009-07-27
I had installed ubuntu 9.04..i had no sound..may be a driver problem..i had updated the latter as it instructed me..I had understood how to install the provided programs in the add remove programs option..I did it all yesterday,because today morning,the upper tool bar had disappear and i had to re-isntall ubuntu!I saw how you people run windows xp on linux,how you get a 3-d desktop,etc...but its totally different!I need help to get a pc like demonstrated on you tube..how to get the sound,how to run xp,how to run any program I was using on windows on linux,as i saw for some,it was made possible...i got a problem with my web cam and floppy drive also..please help me out!thanks in advanced!

---

### Post by scrooge_74 on 2009-07-27
Take it easy, in this cases is better if you make a separate thread for each problem

You have:

1. no sound
2. no tool bar on top
3. virtualizing XP
4. 3D desktops

1. open terminal type alsamixer
2. I think is gnome-panel from terminal
3. First learn to walk then you can run with it
4. Enable compiz, but first tells us what video card you have 9.04 has some issues with some video cards

---

### Post by yogesh1 on 2009-07-27
i think its ATI Radeon

---

### Post by fbugnon on 2009-07-27
Welcome to Ubuntu Forums!

You might want to look at the Ubuntu Official Documentation at to get familiarized with your new system ([https://help.ubuntu.com/](https://help.ubuntu.com/)).

Regarding your questions:

> **yogesh1 said:**
> I need help to get a pc like demonstrated on you tube..how to get the **sound**

Please provide further information on your hardware so that users can help you with this.

> **yogesh1 said:**
>  (...) I need help to get a pc like demonstrated on you tube..(...) how to **run xp**(...)

To run Windows inside Ubuntu (if that's what you're looking for) you can use VirtualBox ([www.virtualbox.org](www.virtualbox.org)).

> **yogesh1 said:**
>  (...) I need help to get a pc like demonstrated on you tube..(...) how to _run any **program** I was using on windows on linux_ 

This can be achieved using Wine ([www.winehq.org/](www.winehq.org/)), you can check their site to see what programs are supported.

Hope this helps.

---

### Post by scrooge_74 on 2009-07-27
> **yogesh1 said:**
> i think its ATI Radeon

Before going any further make sure what you have and research because ATIs are giving a hell of a time to people trying to use 9.04 seems ATI don't want do make new drivers. So you may have problems with 3D using 9.04.

I had to downgrade a friend to 8.04 because of this problem

---

### Post by yogesh1 on 2009-07-27
for the sound
 creative sound blaster



and i regained the tool bar on re -installation

---

### Post by yogesh1 on 2009-07-27
i had downloaded virtual box,but there was no way of installing it

---

### Post by yogesh1 on 2009-07-27
do i have to downgrade me also?
however,I'll have to wait till next month(few days:)) for any download exceeding 50mb
my package limits to 3 Gb per month

---

### Post by yogesh1 on 2009-07-27
yes boss,its that ATI damn thing

---

### Post by yogesh1 on 2009-07-27
ATI radeon 7000 (RV100)

---

### Post by fbugnon on 2009-07-27
> **yogesh1 said:**
> i had downloaded virtual box,but there was no way of installing it

It is easier to simple type (on a terminal):

```
sudo aptitude install virtualbox
```

Or, if you rather not use the terminal, go to Synaptic (Ubuntu graphical software manager), search for Virtualbox and check it to install it.

---

### Post by yogesh1 on 2009-07-27
sorry for lateness,but the programs are still being downloaded;
does linux have any download accelerator program?

---

### Post by ibuclaw on 2009-07-27
> **yogesh1 said:**
> sorry for lateness,but the programs are still being downloaded;
does linux have any download accelerator program?
In my personal opinion, download accelerators are a myth. So don't be fooled by it. =)


On a serious side. What are you downloading? Where are you downloading it from?

Regards
Iain

---

### Post by yogesh1 on 2009-07-28
I was downloading virtual box,but it cancelled!
re-downloading it!hope it'll work

---

### Post by yogesh1 on 2009-07-28
I've successfully installed virtual box,and a windows in it!however,in both the windows and linux ubuntu9.04,when I try to install my sound card,it says;
please ensure that your sound blaster hardware is properly installed before running this setup program


my sound card is "sound blaster live!5.1,creative"
my speakers are 
"mercury",5.1


and how can I fit the window to screen?it stay in the middle of the screen,and does not fit screen even when i tried 
Ctrl+A
Ctrl+F
Ctrl+G


thanks in advanced

---

### Post by scrooge_74 on 2009-07-28
For what is worth, I think you need to have your hardware properly config and running in linux so XP can detect it

---

