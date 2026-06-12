---
title: "Borland C\C++ on Unbuntu?"
date: 2008-07-28
forum: General Help
---

### Post by favadi on 2008-07-28
I need Borland C\C++ for some special works. 
Have any way to run Borland C\C++ complier on Ubuntu?
Thanks if you can give me a solution. It's so painful to dual boot. :(

---

### Post by lisati on 2008-07-28
Hmmmm you've given me an idea (I have a copy of Borland C++ Builder lurking around waiting to find a use, I need to brush up on my C/C++)

You might want to try running it with Wine (a Windows compatibility layer)

---

### Post by favadi on 2008-07-28
> **lisati said:**
> Hmmmm you've given me an idea (I have a copy of Borland C++ Builder lurking around waiting to find a use, I need to brush up on my C/C++)

You might want to try running it with Wine (a Windows compatibility layer)

Borland C++ Builder is very bad. :(

---

### Post by rEbyTer on 2008-07-28
Use just gcc/g++. If you insist that bad BC 3.1 you might try it with dosbox.

**apt-get install dosbox**

and then read the manual. If you have problems to get it to work please tell me and I will answer.

With wine wont work.

---

### Post by lisati on 2008-07-28
> **favadi said:**
> Borland C++ Builder is very bad. :(
I've only used it for a few programs (less than five, source files since lost)....I might have a play with it some time using Wine, but it's not high on my list of priorities. The copy I have probably wouldn't work too well in DOSBOX, since it's a Windows program - I'd rather use Turb C.

gcc & g++ are probably of more use in a Linux environment.

---

### Post by rEbyTer on 2008-07-28
Borland C++ 3.1 will not work in wine because it's a DOS application. With DosBOX will work just fine, i've tried it when i was at a programming contest. :| It's just TOO bad to use that 13years old(or idk) program.

---

### Post by lisati on 2008-07-28
> **rEbyTer said:**
> Borland C++ 3.1 will not work in wine because it's a DOS application. With DosBOX will work just fine, i've tried it when i was at a programming contest. :| It's just TOO bad to use that 13years old(or idk) program.

I think we're at crossed purposes here, thinking of two similarly named but different packages from Borland. The one I have is "Borland C++ Builer" which won't run in DOS because it's a Windows program.......

---

### Post by rEbyTer on 2008-07-28
Now I know what you mean, sorry.

---

### Post by lisati on 2008-07-28
> **rEbyTer said:**
> Now I know what you mean, sorry.

That's ok......

---

### Post by favadi on 2008-07-28
I need use Borland compiler. 
It's great if I can use it on a IDE such as Anjunta, but... :(

---

### Post by rEbyTer on 2008-07-28
You can use very well gedit and gcc/g++.

Open up gedit, write a program, save it. Then open a terminal go where you saved the file and then type:

```
g++ program_name.cpp
``` for C++ programs.

then execute the program with:
```
./a.out
```

to specify a program name use
```
g++ program_name.cpp -o program_name.out_or_whatever_you_like
```

---

### Post by favadi on 2008-07-28
Some Old program of my project was written by Borland C++, and it use some Dos library. Perhaps, Dual boot is the best solution. :(

---

### Post by rEbyTer on 2008-07-28
You can do it.
```
sudo apt-get install dosbox
```

Then run dosbox. Mount your drive where you have BC 3.1. Got to BC folder. and then run it like you where on a DOS terminal in windows. Please tell me what you don't understand in this post, I will help you.

---

### Post by favadi on 2008-07-28
> **rEbyTer said:**
> You can do it.
```
sudo apt-get install dosbox
```

Then run dosbox. Mount your drive where you have BC 3.1. Got to BC folder. and then run it like you where on a DOS terminal in windows. Please tell me what you don't understand in this post, I will help you.

I understand what you've said, but I don't want to run BC like that. I want to use BC complier with a IDE such as C-free or DevCpp (in Windows).

---

### Post by rEbyTer on 2008-07-28
So, try to run Devccpp under wine. Tell me if it works.

---

### Post by favadi on 2008-07-28
> **rEbyTer said:**
> So, try to run Devccpp under wine. Tell me if it works.

Yes, I'll try later. Using Windows make me so painful.

---

### Post by rEbyTer on 2008-07-28
Try Vista if you want it. It's much better than XP. :| I'm running Ubuntu on an external HDD because I rock with it. It works on every computer. :) and this is nice.

In the SSD I have arch linux, and on the 8GB SD card I have Win XP.
btw, i have eeepc :P. I love my computer.

---

### Post by favadi on 2008-07-28
> **rEbyTer said:**
> Try Vista if you want it. It's much better than XP. :| I'm running Ubuntu on an external HDD because I rock with it. It works on every computer. :) and this is nice.

In the SSD I have arch linux, and on the 8GB SD card I have Win XP.
btw, i have eeepc :P. I love my computer.

I think Xp is better than Vista. Vista's user interface make me think that it's not good for word. :D
And, C-free can't work well with BCC on Wine. :(
I'll try DevCPP & Code Block.

---

