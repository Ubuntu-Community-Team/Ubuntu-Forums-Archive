---
title: "Dual screens, how can I make each its own desktop?"
date: 2009-01-16
forum: Hardware
---

### Post by charlescarroll1 on 2009-01-16
I posted a thread yesterday on the issue I am having with using dual screens disables desktop effects [here]("http://ubuntuforums.org/showthread.php?t=1040975").  Still haven't solved the problem as of yet.

Now I am wondering if anyone knows how to make each screen its own desktop (or workspace) rather than having each screen apart of one desktop (or workspace).

And suggestions would be much appreciated :)

---

### Post by Rohan Kapoor on 2009-01-17
Firstly, please explain what you want again.

Secondly, what manufacturer of cards do you have?

---

### Post by jpkotta on 2009-01-17
You could run 2 X servers, one for each screen, but that has the large disadvantage that the screens are *completely* independent -- you can't move windows between them.

---

### Post by Rohan Kapoor on 2009-01-17
Card manufactufer please...

---

### Post by charlescarroll1 on 2009-01-17
> **darth-vader said:**
> Card manufactufer please...

Oh, I apologize.  It's an ATI Radeon Xpress 1150. My laptop is a Dell Inspiron 1501.

> **jpkotta said:**
> You could run 2 X servers, one for each screen, but that has the large disadvantage that the screens are *completely* independent -- you can't move windows between them.

So when you say independent, I wouldn't be able to move my cursor back and forth between screens?

---

### Post by lakersforce on 2009-01-17
I want a generic solution!

---

### Post by Rohan Kapoor on 2009-01-18
> **charlescarroll1 said:**
> Oh, I apologize.  It's an ATI Radeon Xpress 1150. My laptop is a Dell Inspiron 1501.



So when you say independent, I wouldn't be able to move my cursor back and forth between screens?

Move cursor but no windows. BigDesktop is what I use for 1 large display on two monitors!

>  	
Re: Dual screens, how can I make each its own desktop?
I want a generic solution! 

Impossible!

---

### Post by ruff on 2009-01-18
If you are referring to how it acts with Desktop Cube rotation etc under compiz desktop effects, there is an option in the CompizConfig Settings Manager to make the desktop act as multiple cubes instead of one large one.

In Desktop Cube options, under the General TAB there is Multiple Output Mode. Change this to Multiple Cubes instead of the default of one big cube.

---

### Post by lakersforce on 2009-01-18
> **darth-vader said:**
> 
Impossible!

If it's possible in Windows, I am sure it's possible in GNU/Linux too!

---

### Post by Rohan Kapoor on 2009-01-18
> **lakersforce said:**
> If it's possible in Windows, I am sure it's possible in GNU/Linux too!
It's not generic in Windows! It only looks like that because all the drivers go through the standard screen resolution box, but ATI has it Catylst Control Center and Nvidia has it's own thing. That's the same In GNU/LINUX, each manufacturer has it's own driver utility. The only thing that is universal is the xorg.conf located in '/etc/X11/'. You can try manually editing that if you want!

---

### Post by charlescarroll1 on 2009-01-18
****, I thought I started a new thread and thought I wasn't replying to this one.

---

### Post by charlescarroll1 on 2009-01-18
Damn it.  I am sorry.

---

### Post by charlescarroll1 on 2009-01-18
Thanks everyone. I realized that I could a new panel and drag it to the second desktop, which is really what I was looking for.

> **ruff said:**
> If you are referring to how it acts with Desktop Cube rotation etc under compiz desktop effects, there is an option in the CompizConfig Settings Manager to make the desktop act as multiple cubes instead of one large one.

In Desktop Cube options, under the General TAB there is Multiple Output Mode. Change this to Multiple Cubes instead of the default of one big cube.

I could not find Multiple Output Mode in Compiz. In display settings there is Detect Outputs and underneath is a box with the outputs listed.

> 1280x800+0+800
1280x800+0+0
Are you referring to this? If so, what would I edit?

Underneath this is Overlapping Output Handling.

---

### Post by ruff on 2009-01-19
> **charlescarroll1 said:**
> Thanks everyone. I realized that I could a new panel and drag it to the second desktop, which is really what I was looking for.



I could not find Multiple Output Mode in Compiz. In display settings there is Detect Outputs and underneath is a box with the outputs listed.



Underneath this is Overlapping Output Handling.



No. I was referring to the Compizconfig settings manager. You may need to install it via synaptic if you do not have it installed.

---

