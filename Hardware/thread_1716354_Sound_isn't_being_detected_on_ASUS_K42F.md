---
title: "Sound isn't being detected on ASUS K42F"
date: 2011-03-28
forum: Hardware
---

### Post by NotYetReady on 2011-03-28
Greeting!

I've been searching in this forum over and over about this issue and tried countless solution, none solved, but even made it worse! 

At start, built-in speaker wasn't working at all unless I plug my headphone and listen through my headphone. I tried to find a solution for it and found some... 
I followed the instructions, typed and installed countless of software and/or terminal command. 
However, I installed *1.0.23.0* of *alsa driver linuxant* then I got this error (screen-shot attached). After that, I re-installed it which worsen it even more. 
Surprisingly, I can't even listen through my headphone anymore!

This's my sound card as lspci identified it:
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)


Whenever I try to run a music, I get this error:
p, li { white-space: pre-wrap; } *[COLOR=#ff0000]Potential ALSA version problem:[/COLOR]*
 *[COLOR=#000000]VLC failed to initialize your sound output device (if any).[/COLOR]*
 *[COLOR=#000000]Please update alsa-lib to version 1.0.23-2-g8d80d5f or higher to try to fix this issue.[/COLOR]*
 


My device is ASUS k42f, running Ubuntu 10.10 on it

and yes.. I've followed the instructions in this thread                                                                                         [I][COLOR=Blue][Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=touchpad"), 
[ASUS K52/ASUS A52]("http://ubuntuforums.org/showthread.php?t=1460790&")[/COLOR][/I] and many more.

I'm very frustrated and honestly looking for a solution for this issue.

Yet, I've more issues to argue whether Ubuntu have a solution for them or not
as well as, whether Linux will be newbie-friendly or not...


Peace~
NotYetReady

---

### Post by NotYetReady on 2011-03-28
I decided to reinstall Ubuntu 10.10 desktop with all its misfortune and install Ubuntu 10.10 netbook. And wish that Ubuntu's developers to focus on simplifying their OS instead of inventing new features following LibreOffice's developers path on focusing to simplify the software instead of adjusting new features that no one could actually benefit from the magical features but expert users.

I hope you don't take my opinion as an offensive but as an advice if you really want to attract more users and then commercial companies to port their software in Ubuntu. It's funny and sad that I came to conclude that Ubuntu 8.10 was less troublesome than current edition in term of drivers :(.

Yet.. my problem remain unsolved waiting for the knight to solve it :popcorn:
  
 

Peace~
NotYetReady

---

### Post by lidex on 2011-04-03
> I hope you don't take my opinion as an offensive but as an advice if you really want to attract more users and then commercial companies to port their software in Ubuntu.
**It's free!**
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

