---
title: "Hybrid graphics: switching between two ATI video cards"
date: 2011-09-09
forum: Hardware
---

### Post by Tikichan on 2011-09-09
Hello! This is my first post here after I started using Linux (natty), so please excuse the noobness.  

My problem is basically this: I have two graphics cards and wish to switch to the other (the descrete one I believe).

Q1. Is there a method to switch between two ATI cards when using fglrx?
Q2. If not, what can I possibly do except buy a new laptop / Windows (both not really viable options for economic reasons) or make myself go insane by googling guides and trying the same things over and over again? (Which is horrible, because I'm so new to Linux doing almost anything is quite difficult)

I tried using the xorg drivers and switcheroo, but just couldn't get it to work. 

Main reason why I would like to use the fglrx drivers: when I *think* I finally got the xorg drivers installed properly, I experienced several small graphical errors (such as little dots in specific areas and crazy lines of colour shooting out from certain spots on the screen). It is possible I just didn't do it right (although I got a lot of help from a friend who seemed to know what he was doing), but to me it seems like the only way to have my graphics working normally is with fglrx :/

These are the graphics cards that I have:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]

I realize that ATI cards aren't the best with Linux but I just I happen to have only them. 

I have been intending to play WoW on my laptop  (Fujitsu Siemens Amilo Xa 3520), which is why I need to switch the graphics card being used - everything else works normally, but if the lesser card is used, playing the game is impossible because of a graphical jungle of colourful lines on ecstacy shooting around the screen - just like back on Windows if I accidentally hit the button which switches between the cards. This button does not work on LInux ofc. And yes, I actually did get WoW working apart for the graphics... I just reinstalled Ubuntu to see if that would help in any way but, needless to say, it didn't.

I would really appreciate any help, for I find myself stuck and frustrated after almost a week of working on this every night in vain.

---

### Post by Tikichan on 2011-09-11
Could somebody at least answer 'question 1'? 

Thanks a lot to anyone who bothers to!

---

### Post by Leopardson on 2011-09-11
I have the same issue. I have a Radeon 4200 and a radeon 5650. Ubuntu only uses the 4200 and I cannot figure out a way to switch to the 5650. It's like having normal clothes for when you're working, a hospital gown for when you are sick, and then the government makes you wear hospital gowns to work. No fair.

---

### Post by Tikichan on 2011-09-17
I guess I have no choice but to buy Windows then :( My knowlidge of Linux and tweaking it just isn't good enough to solve  this.

---

### Post by SeijiSensei on 2011-09-17
Can you turn off one card in the BIOS?

---

### Post by Tikichan on 2011-09-18
> **SeijiSensei said:**
> Can you turn off one card in the BIOS?

No, I don't have that option anywhere.

---

### Post by .... on 2011-09-18
> **Tikichan said:**
> Could somebody at least answer 'question 1'? 

Thanks a lot to anyone who bothers to!
With Catalyst 11.8, I see options for aticonfig to switch between two AMD/ATI adapters. I can't verify if they actually work.
```
aticonfig --help
```
...
```
PowerXpress options:
  --px-list-active-gpu
  --pxl
       List current activated GPU
  --px-dgpu
       Activate discrete GPU (High-Performance mode), must re-start X to take effect
  --px-igpu
       Activate integrated GPU (Power-Saving mode), must re-start X to take effect
```

---

### Post by Tikichan on 2011-09-20
> **.... said:**
> With Catalyst 11.8, I see options for aticonfig to switch between two AMD/ATI adapters. I can't verify if they actually work.
```
aticonfig --help
```...
```
PowerXpress options:
  --px-list-active-gpu
  --pxl
       List current activated GPU
  --px-dgpu
       Activate discrete GPU (High-Performance mode), must re-start X to take effect
  --px-igpu
       Activate integrated GPU (Power-Saving mode), must re-start X to take effect
```

Thank you so much, I didn't know I could do this with aticonfig!

I encounter a strange problem though:

1) It says that the discrete GPU is already active, which I don't really believe. Is it possible that ATI is mistaken in this - or am I to just accept the fact that my video card *will not work* with Linux? (Because if it IS active, it certainly is not working with WoW the way it should, but rather just like it did back in first post.)

```
~$ aticonfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).
```2) I cannot switch between the cards

```
$ aticonfig --px-dgpu
PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver for changes to take effect!
PowerXpress: Fail to switch GLX link file, please check whether driver install correctly

``````
$ aticonfig --px-igpu
PowerXpress: Integrated GPU is selected (Power-Saving mode), please restart Xserver for changes to take effect!
PowerXpress: Fail to switch GLX link file, please check whether driver install correctly

```Any ideas? I tried googling the PowerXpress error, but found nothing to solve it so far.

---

### Post by Tikichan on 2011-09-20
Also, even though the --pxl command gives me the discrete GPU as the one being used, when I check *ATI Catalyst Control Centre*, it mentions only the lesser graphics card (the integrated one) as the "OpenGL renderer". Isn't this contradicting?

---

### Post by vitakraft on 2011-09-22
Are you on 64-bit?

Because I have the same issue and I think it's because of amd64

---

### Post by Tikichan on 2011-09-22
> **vitakraft said:**
> Are you on 64-bit?

Because I have the same issue and I think it's because of amd64

No, I'm not :/

---

