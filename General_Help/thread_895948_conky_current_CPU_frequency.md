---
title: "conky: current CPU frequency?"
date: 2008-08-20
forum: General Help
---

### Post by hardysummer on 2008-08-20
I cannot figure out how to get the currently used CPU frequency on conky.  There is one for hard drive space, swap, and RAM, but is there one for the CPU?  Not the percentage.

---

### Post by Locutus_of_Borg on 2008-08-21
Frequency: $freq MHz

will display something like:

Frequency 1667 MHz

---

### Post by beem0r on 2008-08-21
Like he said. Note that this will give you your 'total' clock speed. Note too that there is no such thing as 'currently used' clock speed. A 3.0 GHz CPU with 33% load is still running at 3.0 GHz.

---

### Post by Locutus_of_Borg on 2008-08-21
well, for instance, on battery power, my CPU frequency lowers to 1000 MHz to conserve battery life, this is reflected in conky with the above line

---

### Post by bunnyhugh on 2008-08-22
Here is the a copy of what I have in my .conkyrc that displays the cpu frequency.
${color lightgrey}Core 1 Freq: $color${freq_g (1)} GHz

I have one line for each core, (yes I know it's pointless  showing a line for each core, because the frequency of the cores dont't change independently)

The magic bit is the keyword "freq_g" which return the frequency in GHz if you want MHz use "freq" the number in brackets specifies which core/cpu to look at, if it's left blank then the default is cpu 1.

Assuming that you are using some sort of frequency scaling then, you will see the conky display change as the frequency scaling does its stuff.

Have look at the man page for conky for more information.

Hope this helps

---

