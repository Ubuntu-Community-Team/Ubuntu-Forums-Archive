---
title: "RAM upgrade, Ubuntu does not recognize new memory"
date: 2008-08-30
forum: Hardware
---

### Post by homeriq5 on 2008-08-30
I recently installed 512 MB memory thingy on my Sony Vaio VGN-S260, however upon restart I saw from the system monitor that the level of my RAM did not change (still around 512 MB).  Is this an ubuntu problem?  How can I go about troubleshooting and remedying this?

Thanks for all you help

---

### Post by tliotis on 2008-08-30
Hello , in some systems the first 512 Ram means the VGA graphics ram and not the Ram memory!check it with live cd the mem test writes the sum of memory

---

### Post by Sef on 2008-08-30
Applications > Accessories > Terminal

Then paste or type in this command:

```
free -m
``` 

That will tell you how much ram your computer sees.

---

### Post by homeriq5 on 2008-08-30
This is what I get from running the command:

```
homeriq5@homeriq5-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           502        496          6          0         14        217
-/+ buffers/cache:        264        238
Swap:         1474          0       1474

```

I think that the computer doesnt even see the new RAM I installed? I thought you can just pop in the new memory module, restart, and its good to go.  Is it common for this to happen when installing?  Could the module just be out of place or something?

---

### Post by Mister.Vash on 2008-08-30
If you go into your BIOS setup, what does the system report as your memory?

---

### Post by homeriq5 on 2008-08-31
around 512, should be around 1 gig

---

### Post by Sef on 2008-08-31
Have you checked to make sure your ram was installed correctly?

---

### Post by homeriq5 on 2008-08-31
Well, theres only one orientation that the RAM can be installed in, right?  I opened up the laptop and checked the module again and it seemed to snap into place the right way.  Maybe its defective?  I guess I'll have to try to return it to the person I bought it off of

---

### Post by mellowd on 2008-08-31
What does your bios say? If it shows 512mb only then you've either put it in incorrectly or its defective.

If it shows 1gb and ubuntu only shows 512mb, then you know it's a problem with ubuntu

---

### Post by IntuitiveNipple on 2008-08-31
The VGN-S260 will support a maximum of 1GB in 2 banks over 2 sockets (1 bank per socket).

The memory type is 144-pin DDR MicroDIMM Non-ECC PC 333MHz.

What memory module part number have you installed?

As a test of the module itself, try removing the first (known good) module and inserting just the new module.

If that works you are dealing with an issue of the memory in the second socket not being recognised. If it doesn't work you know that module is bad or not correct.

---

### Post by taburde on 2011-02-08
I am actually having the same problem on my machine. I recently installed six gig of RAM, but the system is still saying that I have just 3.4 gig.

---

### Post by scheuri on 2011-02-09
> **taburde said:**
> I am actually having the same problem on my machine. I recently installed six gig of RAM, but the system is still saying that I have just 3.4 gig.
That could have many more reasons. And since you have not indicated what hardware (exact information!) you use, I can only guess:
- There are boards who are not able to address more even if there are empty memory banks
- You are using 32bit instead if 64bit version of Ubuntu
- You are using a 32bit version which has PAE not activated
- Its defective

Check your BIOS...if it says 6GB RAM, then very good step. Then install a 32bit kernel (if you are on 32bit) that has PAE activated.

---

### Post by linuxd00 on 2011-02-09
@OP:

if not even your BIOS recognizes the ram id guess that its not a Ubuntu related problem but hardware. Please check that your RAM:

- is compatible to your mainboard (example using PC800 RAM in a board that needs PC1600)
- is not defective
- you have the newest BIOS version
- the contacts are clean (seriously.. wash your hands when touching hardware). This was a common problem with nintendo cartridges :)

---

### Post by cascade9 on 2011-02-09
@ linuxd00- I dont think that the OP is going to notice, this thread is pretty old (august 2008) and they havent been online here since 16-04-2010...

@ taburde- you should porbably start a new thread. I wouldnt be suprised if this one get shut when the right (or wrong depending on your point of view) admin/mod sees it.

---

### Post by linuxd00 on 2011-02-10
i didnt notice this thread was so old :).
Still i think  answers are ok to stay as long as they help solve a problem. For other people who have the same problem and come here by means of search function.

so if any admins should mark this thread solved so that  people dont answer to it anymore?

---

### Post by cascade9 on 2011-02-11
> **linuxd00 said:**
> i didnt notice this thread was so old :).
Still i think  answers are ok to stay as long as they help solve a problem. For other people who have the same problem and come here by means of search function.

so if any admins should mark this thread solved so that  people dont answer to it anymore?

Its not a 'generic' problem. Every system has different max RAM, RAM compatibility, etc. So unless somebody coming here had a Sony Vaio VGN-S260 its not going to help.

Why mark it as 'solved'? It doesnt look solved, and marking it as such isnt going to help anyone...

---

### Post by linuxd00 on 2011-02-11
not true... 

its a generic problem when the bios doesnt recognize.. and the common guidelines to check wether its hardware based or not (so as to then resolve if its ubuntu related or not) are generic as well. 

My proposition to mark it as solved would refer to the OP who has not shown up in ages... *his* problem seems to be solved.

of course if *you *think that he still has this problem since 2008 up to now...

---

### Post by cascade9 on 2011-02-12
> **linuxd00 said:**
> not true... 

its a generic problem when the bios doesnt recognize.. and the common guidelines to check wether its hardware based or not (so as to then resolve if its ubuntu related or not) are generic as well. 

Ohh, its all very straight forward..unless you have a manufacturer who is dead, or you have a model that isnt on the manufcturers website, or you have a 'oddball' model, etc...

Its not generic at all. 

> **linuxd00 said:**
> My proposition to mark it as solved would refer to the OP who has not shown up in ages... *his* problem seems to be solved.

of course if *you *think that he still has this problem since 2008 up to now...

So, you started saying that you wanted this thread solved 'so that  people dont answer to it anymore', now you want it solved on the assumption that the OP did solve the problem? 

The OP might very well have fixed it, but not from any information on this thread. 

If you really want it marked as solved, either PM the OP asking to have them mark it as such, or you could even use the 'report abuse' button and see if you can get a mod/admin to mark it as solved. Though I doubt that would happen, its more likely just to get this thread locked.....which probably wouldnt be a bad thing IMO.

---

