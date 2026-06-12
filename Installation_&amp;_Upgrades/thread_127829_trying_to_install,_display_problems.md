---
title: "trying to install, display problems"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by Burnz316 on 2006-02-09
hey..

ok so i just tried to install ubuntu (dual boot with WinXP Pro) and it went thru the installation process fine but when it got to the end and goes to start ubuntu the screen goes all funny. (lines appear and its a funny yellow and grey colour. sorta looks like a lot of rectangles)

anyone else have this problem? i can't get into ubuntu so can i fix this problem without re-installing or did i do something wrong?

sorry if this question has been asked before, if it has just point me in the right direction. :???: 

thanks :)

---

### Post by Mustard on 2006-02-09
What graphics card do you use?

---

### Post by Burnz316 on 2006-02-09
sorry, was trying to show my computer specs in my sig..

anyways its a Nvidia 7800GT

---

### Post by thecheeks on 2006-02-10
i have the same problem, installtion completes entirely, it asks what res serverX should be at, lil more configureation then a MILLION different colors appear. same thing for livedvd and installtion

using nvidia6600gt. ive installed Mandrake and that worked perfetly before..

---

### Post by orev on 2006-02-10
search the forums and how tos (i think a how to is also in the wiki), you will need to get the nvidia drivers up and going for your install

have no fear, its not tough...

P.S.  Sweet box....(I'm an AMD guy....but hey...)

---

### Post by Burnz316 on 2006-02-10
yeah i had the problem orginally with the live cd so i thought i would install it, cause would really like to try out linux and ubuntu, but yeah got the problem again.

---

### Post by thecheeks on 2006-02-10
[QUOTE=orev]search the forums and how tos (i think a how to is also in the wiki), you will need to get the nvidia drivers up and going for your install

have no fear, its not tough...

P.S.  Sweet box....(I'm an AMD guy....but hey...)[/QUOTE]
um browsed the wiki real fast and didnt find it, if you know where it is can you PLEASE post it? i want ubuntu so bad...

edit: beacuse i dont know how to install the drivers WITHOUT the gui... yes im moving from windows into linux so i dont know...

---

### Post by Burnz316 on 2006-02-10
how do u install the drivers if u cant see anythin on the screen, can u get to the terminal or a command prompt to do it from there instead?

---

### Post by orev on 2006-02-10
here is the best "how to" thread that I could find (quickly):

[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidi](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidi)

I'm not sure if I completely understand....can you get to the command line or no?

---

### Post by Burnz316 on 2006-02-10
ubuntu boots up but the screen is so messed up it is impossible to see anything within ubuntu.. 

so how do u get to the command line? without being able to see anything within the ubuntu gui..

thanks for your help..

p.s. i did search and find that post but how would i get to the terminal without being able to see anything?

---

### Post by n00buntu on 2006-02-10
I had a similar problem.  What I did was to boot to recovery, then I typed:

   dpkg-reconfigure xserver-xorg

which allowed me to set the driver to vesa (the generic) instead of nv.  After reconfiguring, I typed:

   starx

which allowed me to get to the gui. (you could reboot instead).  You could try that.  I think the default settings were fine, except that the nvidia driver wasn't working.

---

### Post by thecheeks on 2006-02-10
[QUOTE=n00buntu]I had a similar problem.  What I did was to boot to recovery, then I typed:

   dpkg-reconfigure xserver-xorg

which allowed me to set the driver to vesa (the generic) instead of nv.  After reconfiguring, I typed:

   starx

which allowed me to get to the gui. (you could reboot instead).  You could try that.  I think the default settings were fine, except that the nvidia driver wasn't working.[/QUOTE]
you mean "startx"

but yeah that makes sense the vesa's have always worked for me, manually installing the latest nvidia drivers will work better i bet, i did it with mandrake once.

lil off topic and im sure i can find it but im off to school rite now, how do you make Windows the default OS in GRUB and boot to it if no selection is made in 5 secs?

---

### Post by orev on 2006-02-10
Best to boot to recovery...

---

### Post by Mustard on 2006-02-10
Alternatively, you could try ctrl + alt + f1 when you get the jumbled up screen, this might put you at the login prompt and you could log in using command line frome there.

---

### Post by arckeda on 2006-02-10
you say xserver, i think driver, try crtl-alt-F1
If that dont work get you *** to the bash menu somehow and type sudo dpkg-reconfigure xserver-xorg then selsect vesa as driver, that dont work use vga
If you cant do that install in professional and selecting the driver is one of the options, I might be wrong but thats what id do, try on live cd first.

---

