---
title: "Crossroad (Gutsy, Feisty, Edgy, Jaunty)"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by marsupy on 2009-09-17
[SIZE=2][COLOR=Black]Hi everone,

I'm new to this Ubuntu world and I'd really appreciate your help with this doubt. I have searched a lot, but **haven't** quite found a answer that satisfies me.

I want to install VMWare Server using the step by step tut I found here: [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)


My question is, which I find in a lots of tuts, which version do I follow? I have installed Ubuntu 9.0.4 Jaunty. This tut follows Gutsy, Feisty and Edgy... so Im stuck with which one to follow.

Can anyone help or point in the right direction?

Thanks[/COLOR][/SIZE]

---

### Post by running_rabbit07 on 2009-09-17
Should work with Hardy or Jaunty. Depends on whether you prefer LTS or not.

---

### Post by marsupy on 2009-09-17
> **running_rabbit07 said:**
> Should work with Hardy or Jaunty. Depends on whether you prefer LTS or not.

Well, Microsoft can be quite encryptic about their messages, but you've just beet them. :)
As I stated from my first post, I am new to Ubuntu (Linux) world. 
Your reply with "Hardy or Jaunty" still doesn't tell me if I should go down the route of Gutsy, Feisty or Edgy (from the tutorial)? 
And also you dropped another question in my head... what is LTS? Do I need to know what is LTS to install VMWare?

Sorry... I was just expecting better explanations from the Ubuntu forums. :confused: 

Cheers

---

### Post by Pyntix on 2009-09-17
LTS means Long Term Support. Some versions of Ubuntu (every two years I think?) are supported much longer than the regular ones (three years instead of 18 months) with fixes and updates.

And about the question Gustsy/Feisty/Edgy... I'm not sure but I suppose the best thing would be to follow the steps for the latest version, which would be Gutsy. Don't take my advice here too seriously though, I only have basic knowledge about linux and *buntu.

Good luck anyway. :)

---

### Post by E.S.B. on 2009-09-17
Well, you could probably follow that tutorial for Gutsy & Feisty but using Jaunty (latest version of Ubuntu) instead, with just a few minor adjustments.
Where it says:
```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
```
you would substitute gutsy for jaunty:
```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
```
By reading the tutorial that's the only thing I could spot that would differ.

Also, may I recommend you [virtualbox]("http://www.virtualbox.org/"). It's a nice virtualization software. If you need any help installing/configuring/using it, just post your questions.

---

### Post by running_rabbit07 on 2009-09-17
> **marsupy said:**
> Well, Microsoft can be quite encryptic about their messages, but you've just beet them. :)
As I stated from my first post, I am new to Ubuntu (Linux) world. 
Your reply with "Hardy or Jaunty" still doesn't tell me if I should go down the route of Gutsy, Feisty or Edgy (from the tutorial)? 
And also you dropped another question in my head... what is LTS? Do I need to know what is LTS to install VMWare?

Sorry... I was just expecting better explanations from the Ubuntu forums. :confused: 

Cheers

Gusty, Feisty, and Edgy are not supported and no longer have updates. Hardy is a Long Term Support version and Jaunty is the newest. 

I am sorry that you think I shorted you on knowledge there.  I would have figured that if you were looking to install something on a virtual machine, that would have done some homework before questioning the forum. If you were to have looked at the Ubuntu.com page where Ubuntu is downloaded, you would see Jaunty 9.04 and Hardy 8.04LTS. 

When in doubt of something please feel free to utilize google by searching for something like, "Ubuntu LTS," and you will get an swer to your question.

As for the first line of your response, I have never "beet" anyone. My original answer was plentiful enough that you could find the info you needed with a couple of clicks.

---

