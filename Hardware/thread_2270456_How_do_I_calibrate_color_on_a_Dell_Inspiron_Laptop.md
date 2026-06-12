---
title: "How do I calibrate color on a Dell Inspiron Laptop?"
date: 2015-03-23
forum: Hardware
---

### Post by Lao_Ding on 2015-03-23
There have been topics on color calibration I know, but none have helped me. I want to know how to calibrate a Dell Inspiron for brighter colors and higher contrast. The profile I have available is supposedly for my device but frankly it's just plain awful. In Settings- Color I can click on the profile but Calibrate is greyed out. I added a generic Epson profile but there has been no change and I cannot calibrate that profile either.
I know the monitor is good because a month ago I was running Windows 7 on it and it was bright and shiny. Now it's so faded it looks like the monitor is on its last months of life. I know that is not true though, so what can I do to get things brightened up?
Thanks.

---

### Post by pdc on 2015-03-24
I sometimes think a forum can be like a poker game: if those seeking help don't show all their cards!!!!!!!! .......... it can be tricky; so please help us: what printer do you have ............ I am sensing Epson ?? ............. and can you open a terminal and paste this command in please 

```
dpkg -l | grep epson-inkjet-printer
```

---

### Post by Lao_Ding on 2015-03-24
Sorry, but I'm not writing about printing. I'm not even using a printer. I'm writing about the washed out colours and low contrast on my monitor. There should be a way to calibrate this. As it is, it makes my Ubuntu sessions very dreary.

---

### Post by Vladlenin5000 on 2015-03-25
Back to the poker game analogy... The cards you should be showing start with your hardware. There are hundreds of Inspirons already and each model can have several variants. Namely the graphics card/chipset is of utmost importance here, as well as the specific monitor (mate/glossy and recommended resolution).

---

### Post by Lao_Ding on 2015-03-26
Hi again.
Dell System-inspiron-N4110
Intel Sandybridge Mobile x86/MXX/SSE2
matte 1366x768

Obviously a total newcomer to Linux and Ubuntu, I was delighted at how perfectly it installed without the need for me to install any additional drivers. An Inspiron-N4110 color profile is installed in Settings-Color, but the Calibrate button is greyed out. The profile has some options such as Swapped Red and Green, etc., but nothing looks good. I can manually adjust the brightness of the screen, but cannot do anything for contrast, gamma, or white point (obviously that would be under calibrate unless there are some Dell hardware tricks that I don't know about it).
It's also obvious that screen looked pretty darn good under Windows, so there must be a better profile waiting to be made. I'm sure I could get it looking good myself if i just had the software tools, but the Color Settings manager won't let me adjust anything. Hence, a washed out appearance overall with faded colors. I work with graphics and pictures a lot so this is important to me.
I don't much about Terminal commands, but can follow along.
Thanks.

---

### Post by Lao_Ding on 2015-03-30
Well, I gave all the information asked for but no one seems to want to help. You keep mentioning poker- now it seems like bluffing.
I am willing to try hard to learn Linux and Ubuntu and share what I know with others, but for now I know next to nothing. Is this an open source community or not?

---

### Post by aljosa2 on 2015-03-30
Hi Lao_Ding,
Ubuntu is a computer operating system that seems to have a few Achilles' heels, and I would say thay you touched one of them.
Just like you, I'm also not satisfied with the color management in Ubuntu (two different Asus notebooks). 

Here's my advice: 
create a bootable LiveUSB

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

of Ubuntu 15.04

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and see if colors are different.
Although not perfect, situation in both of my cases is better.

---

### Post by Lao_Ding on 2015-03-30
Thanks for the response! I'll try it and post the results.

---

### Post by J_Me on 2015-03-30
Umm I did some reading up on this subject a while back. The two main options were
1- Buy a monitor calibrater device
2- Copy over the .icc/.icm files from windows to ubuntu(make sure you understand what you are doiing with this)

The first option seems to be the safest but costly and for the second option please do your own research on this I haven't tried it out myself so just giving you a starting point, it may very well break your machine so please be careful.

---

### Post by Lao_Ding on 2015-03-30
So it sounds like the 'Calibrate' option in Settings-Color works only with external monitors. Of course I could never make such a utility but it seems to me that a monitor is a monitor and there should be a way to compile a program that allows for an override calibration (gamma, white point, etc.) but no one has made it yet. Being a GUI end-user (Mac) until now (not unknown to tinker with Terminal though), I've always just taken things for granted.
There's no way I would buy #1 just for a Dell laptop, but by 2 I'm guessing you mean by 'break' that doesn't frying the screen with plasma burn but rather just having to slick everything and reinstall. 
I know it's a terrible thing to say, but if a USB boot works well I might just go with that and reinstall Windows. I don't have any Windows OS at all right now and do not particularly like Windows with all its popups and malware, not to mention all the unintuitive complexity just to get simple things done, and I have not missed (well, it was never my main OS anyway). So if I try coding from Windows' files to Ubuntu I'll certainly read up on it first.

---

### Post by aljosa2 on 2015-03-30
*_Asus N750JV review_:*
*This Haswell-powered behemoth is a **multimedia monster**, combining the power of Intel's latest CPU with a **potent GPU and soaring 17-inch screen**.*

You can imagine my disappointment when I discover that on my 1300 euro "multimedia monster", color correction options are available only for my 200 euro external TV screen :(


[IMG]http://i.stack.imgur.com/EOmq8.png[/IMG]

---

### Post by J_Me on 2015-03-30
> but by 2 I'm guessing you mean by 'break' that doesn't frying the screen with plasma burn but rather just having to slick everything and reinstall.I hope so but I personally wouldn't just stick any old .icc file in ubuntu and see what happens.
Anyway I did some poking around in kubuntu 14.04 and under system settings > hardware > color > profiles there's a whole list of pre-set .icc files to chose from. Not sure where those are for regular Ubuntu though.

---

### Post by Lao_Ding on 2015-03-30
Hi J, I see a lot of options too (all subdirectories under DELL) such as D55, D50, Swapped Red and Green, etc. and I can switch, but I cannot calibrate any of those either. If there's a generic sRGB profile I can use great- just as long as I can calibrate it. 
I'll continue to try to find out. I don't like the idea of hacking an .icc file into Ubuntu either. One thing I know- with Mac you can calibrate ANY monitor at all with the Display utility. That means the utility is vendor independent and works on basic display functions common to all. That's the utility I need- or a working profile that looks acceptable.

---

