---
title: "greek keyboard on laptops with version 9.04"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by jubelbox on 2009-06-09
Grading up from 8.04 to 8.10 and to 9.04 have changed the behavior of my greek keyboard layout.
Switching from German to Greek layout with ubuntu 8.04 was absolut correct. Now on 9.04 I can not write the &#940;, an alpha with the stress-symbol above, nor some other vowels with the same stress-symbol. Nor other keys, like the pi, &#960;.
I presume, that in the newer version of ubuntu the combination with the Fn-Key makes problems. 
Is there anyone, who has an idea about these problems? Perhaps a solution?

regards, Jubel

---

### Post by zvacet on 2009-06-10
Did you installed locale under system>admin>laanguage support?If you do then look in system>preferences>keyboard that you have added both languages.You can easy switch keyboard layouts by right click on top panel>add keyboard indicator.

---

### Post by jubelbox on 2009-06-11
hmm, how to I delete a message? ;-)

---

### Post by jubelbox on 2009-06-11
> **zvacet said:**
> Did you installed locale under system>admin>laanguage support?If you do then look in system>preferences>keyboard that you have added both languages.You can easy switch keyboard layouts by right click on top panel>add keyboard indicator.

I did it. But switching between the two languages is not the problem. The keys which have a mapping with the blue FN key of the notebook make the problems. Exactly this mapping of the blue FN-scheme seems to be the primary mapping. Writing with the greek mapping fluently is not possible. Typing the normal greek characters "&#952;&#953;&#959;" ist only possible, if I press the FN-key and the correspondending key "uio".
In ubuntu 8.04 I just switched to the greek mapping, described above, and wrote fluently the text.

The effect can also be seen on other notebooks with the FN-key

regards, jubel

---

### Post by jubelbox on 2009-06-15
Problem solved.

I used  the Numlock- and CapsLock-LED to indicate, using the greek layout.
Now, using only the Keyboard-indicator in the panel, and switching off the NumLock-layout, everything is ok. All greek letters are reachable.

Until Ubuntu version 8.04 the NumLock obviously was OFF, with version 8.10 and up the NumLock seems to be ON.

regards, jubel

---

