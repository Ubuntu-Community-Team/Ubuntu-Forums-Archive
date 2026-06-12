---
title: "Very lost"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by polskimoose on 2009-01-18
I have a very small laptop that i was hoping to dual boot with windows and ubuntu, however whenever i try to install ubuntu it says i dont have enough ram.

i know that thats the problem, because i got damn small linux to work on it.  

it says i have 238 MB of memory, but the installation requires 256 MB.

is there a simple way to get more RAM???
or install it without using 256 MB of it?

---

### Post by Bucky Ball on 2009-01-18
You could try Xubuntu and use the alternate install disk.

There is also Ubuntu-minimal which installs enough to get things up then you install gnome, xfce, whatever desktop manager if you want one and whatever else you need from there.

You could also find out how much ram your laptop will take and replace or add to the existing ram.

---

### Post by polskimoose on 2009-01-18
and how exactly would i add more ram?

---

### Post by Bucky Ball on 2009-01-18
What laptop are you using? Generally there are a couple of panels on the bottom you can remove with a screw or two. Under one you will find the hard drive, under the other, you should see the ram.

* laptop ram is not real cheap, though.

You should weigh up the pros and cons before proceeding with that one if the machine is pretty old. But it can add life, undoubtedly.

---

### Post by polskimoose on 2009-01-18
its a last generation Dell inspiron 700 mini

what would unscrewing all that do?

---

### Post by Bucky Ball on 2009-01-18
> Generally there are a couple of panels on the bottom you can remove with a screw or two. Under one you will find the hard drive, under the other, you should see the ram.

You pull the ram out and put another stick in. Or you add another stick if there is a slot to do so.

---

### Post by polskimoose on 2009-01-18
where can i get one of those

---

### Post by Bucky Ball on 2009-01-18
On the bottom of the machine there should be a model number. What is it? Or do you have the manual? That will tell you what kind of RAM configurations are possible with your machine. If not, you can find the manual and the specs online from the model number.

---

### Post by polskimoose on 2009-01-18
i think the model number is PP07S

---

### Post by Bucky Ball on 2009-01-18
Cool. You can also type:

```
sudo lshw

```
... into a terminal and look for the bit that looks like this:

 ```
*-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
```

That identifies your ram, but I'll have a look for that model number. Should tell which is the model, not the serial, on the machine.

---

### Post by polskimoose on 2009-01-19
thank you so much

---

### Post by Bucky Ball on 2009-01-19
My pleasure. I imagine you have another slot there. From the stick that is in there, you will be able to tell what kind of RAM it is (DDR, DDR2,pc133 etc). I would be guessing but you might be able to put two gB sticks in there, which would give you 2Gb altogether, but that is a guess. Dell could tell you with an email.

That machine is not that old I don't think so might be worth the effort. With a gig it would fly (1 stick or a 2 x 512mb kit). :)

---

### Post by Bucky Ball on 2009-01-19
Hey, here is the manual!

[http://office.manualsonline.com/manuals/mfg/dell/inspirontm_700m_model_pp07s.html](http://office.manualsonline.com/manuals/mfg/dell/inspirontm_700m_model_pp07s.html)

*** Sorry, forget that link. Here is the Dell one:

[http://au.altavista.com/web/results?itag=ody&q=Dell+PP07S+&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=Dell+PP07S+&kgs=0&kls=0)

---

### Post by Bucky Ball on 2009-01-19
> Memory module connector  two SODIMM sockets (one user-accessible socket)
Memory module capacities 128, 256, 512 MB, and 1 GB
Memory type              3.3-V DDR SODIMM
Minimum memory           256 MB
Maximum memory           2 GB

That is all you need to know, from page 79 of the manual. The machine can take a maximum of 2 x 1gb DDR SODIMM RAM. Voila!

Have a search on the net, ebay or whatever and see if you can get some or go to your local computer store.

---

