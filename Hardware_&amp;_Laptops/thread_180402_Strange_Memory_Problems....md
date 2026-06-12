---
title: "Strange Memory Problems..."
date: 2006-05-22
forum: Hardware &amp; Laptops
---

### Post by pyromidget on 2006-05-22
Hi all, hope you can help with something.  This isn't anything to do with Linux as far as I can tell, but its got me stumped nonetheless.

I have 2x 512MB sticks of RAM to go into my current box.  Both sticks are identical (make, speed etc) as far as I can tell and both definitely work as I have tested them individually in the machine.  My problem begins when I try to use BOTH of them at the same time.  Despite being able to use them individually ok, when I boot up with both in the machine, the POST still only recognises 512MB in total, and no variation on placements and order will make it see otherwise…

I’m not sure what information any of you kind folks might need to help me with this, but ask away and I’ll post it up when I get home from work.

Any help would be appreciated as swap space just isn’t nearly as fast as RAM and my box is beginning to suffer :(

Cheers,  Martin.

---

### Post by tseliot on 2006-05-22
Can you describe the position of your 2 sticks of RAM?

Let's suppose you have 4 slots.

Let's use this scheme:

```
R     F    R     F
A     R    A     R
M     E    M     E
      E          E
```

Where RAM stands for 1 RAM stick and FREE stands for a free slot.

Did you put your RAM sticks according to my scheme? If not, can you try it?

---

### Post by pyromidget on 2006-05-22
Its a PIII mobo, so only 3 slots.

At the moment its set up as:

```

[FONT="Courier New"]R     F     R
A     R     A
M     E     M
      E[/FONT]
```
But i've tried it in every concievable arerangement.  I can't remember exactly, but i *think* the mobo is a "Soltek SL-65 EP-T" or something like that...

---

### Post by tseliot on 2006-05-22
[QUOTE=pyromidget]Its a PIII mobo, so only 3 slots.

At the moment its set up as:

```

[FONT="Courier New"]R     F     R
A     R     A
M     E     M
      E[/FONT]
```
But i've tried it in every concievable arerangement.  I can't remember exactly, but i *think* the mobo is a "Soltek SL-65 EP-T" or something like that...[/QUOTE]
Does the BIOS detect all your RAM? If not, your motherboard might be the problem

---

### Post by pyromidget on 2006-05-22
Well i've figured out the problem... My mobo only supports up to 512!!  Think i may need to invest a little cash at some point soon.

Sorry to have wasted your time :oops:

---

### Post by tseliot on 2006-05-22
[QUOTE=pyromidget]Well i've figured out the problem... My mobo only supports up to 512!!  Think i may need to invest a little cash at some point soon.

Sorry to have wasted your time :oops:[/QUOTE]
No, problem. I'm glad you figured it out in the end.

---

### Post by pyromidget on 2006-05-22
Yeah...

I've got an old skeleton floating about somewhere.  I guess i'll chuck the other stick and a few hard drives into that and set it up as a storage server or something.

Cheers anyways. :)

---

