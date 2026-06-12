---
title: "Desperate and need assistance"
date: 2008-11-09
forum: General Help
---

### Post by hyburn on 2008-11-09
hey guys, I posted a link needing help for an on-board driver. now I installed a realtekalc260 driver through a wine program, should I be worried? how do I know if it is the right one? is linux going to lock me out? PLEASE HELP

---

### Post by soro2005 on 2008-11-09
If you install something in wine, it's not going to have any effect on your normal linux operations. On your wine operations maybe. Of course, it's also not going to do anything for your sound on linux.

---

### Post by hyburn on 2008-11-09
will you PLEASE help me?

I hope this info helps

Card: HDA Intel                                                              
Chip: SigmaTel CXD9872RD/K

---

### Post by soro2005 on 2008-11-09
Well, I don't know how to help you. Perhaps, you could describe a little better what exactly you cannot get done. I think that your soundcard should normally be supported out of the box. So what did you try to get it to work? What is not working? What ubuntu version are you using? Are we still talking about the:

product: 82801G (ICH7 Family) High Definition Audio Controller
vendor: Intel Corporation

By the way, you should bump your threads, rather than open duplicates. And it's also better for people's willingness to help you out if you give your threads a title that describes the problem, and not your state of desperation.

*Edit* Ah, ok, I see. Unfortunately, it looks like it's a difficult one. For reference: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244754)

---

### Post by hyburn on 2008-11-09
ok will do regarding the threads.

ok I have a manufacturer Sony Vaio, and I HATE WINDOWS! there that feels better. I installed ubuntu a few months back, and havent had any audio. I am going crazy without music to listen to. I have to use on-board sound, as I cant find a driver for my Sound blaster live 24-bit.

unless you know where to find a driver for this card.

linux version: HH

I hope this helps you understand the crappy stuff I use

```
&#9474;/proc/asound/version:                                      #         &#9474;
&#9474;        &#9474;====================                                       #         &#9474;
&#9474;        &#9474;Advanced Linux Sound Architecture Driver Version 1.0.16.   #         &#9474;
&#9474;        &#9474;Compiled on Nov  6 2008 for kernel 2.6.24-21-generic (SMP).#         &#9474;
&#9474;        &#9474;                                                           #         &#9474;
&#9474;        &#9474;/proc/asound/cards:                                        #         &#9474;
&#9474;        &#9474;===================                                        #         &#9474;
&#9474;        &#9474; 0 [Intel          ]: HDA-Intel - HDA Intel                &#9618;         &#9474;
&#9474;        &#9474;                      HDA Intel at 0x55200000 irq 21       &#9618;         &#9474;
&#9474;        &#9474;                                                           &#9618;         &#9474;
&#9474;        &#9474;/proc/asound/devices:                                      &#9618;         &#9474;
&#9474;        &#9474;=====================                                      &#9618;         &#9474;
&#9474;        &#9474;  0: [ 0]   : control                                      &#9618;         &#9474;
&#9474;        &#9474;  1:        : sequencer                                    &#9618;         &#9474;
&#9474;        &#9474;  4: [ 0- 0]: hardware dependent                           &#9618;         &#9474;
&#9474;        &#9474; 16: [ 0- 0]: digital audio playback
```

---

### Post by soro2005 on 2008-11-09
Well, as far as I can see from the bug report I have referenced above, there might be a problem with your model. It should be supported, but sometimes the things aren't what they should be. In any case, there is a chance that newer kernels support your sound card. So you could burn yourself an Intrepid Live CD, and see whether it works in Intrepid.

What's definitely *not* going to work is to install a Windows driver.

In the worst of cases, you may want to consider to get a inexpensive soundcard somewhere.

---

### Post by hyburn on 2008-11-09
will do thanks

---

### Post by sirebral on 2008-11-09
KevOB from: [http://dreamlinuxforums.org/index.php?topic=1333.0](http://dreamlinuxforums.org/index.php?topic=1333.0)

posted

> 
This is an alsamixer problem.
With the Creative cards some feature can be disabled on installation.
To fix:
Open a console.
Run alsamixer.
Search for the disabled options - this can be anything from the master volume to,
on the audigy cards, muting the audigy and its mixer. You may need to go through them one by one.
There can be more than one turned off or down. First check the master volume, which is frequently set to
zero! Set this about 80+ before testing anything else. Look particularly for muted items.

This problem is common across Linux versions with Creative cards because of the large number of internal
options they have. 

Maybe that will help?

---

