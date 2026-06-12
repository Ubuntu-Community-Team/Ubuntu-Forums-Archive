---
title: "[SOLVED] ttf-mathematica 4.1 errors"
date: 2008-11-22
forum: General Help
---

### Post by COLiNx86 on 2008-11-22
Whenever I try to install something it always shows this at the end of installation 
```
E: ttf-mathematica4.1: subprocess post-installation script returned error exit status 1

```
How can I get rid of this, it's kind of annoying?

---

### Post by COLiNx86 on 2008-11-23
anyone?

---

### Post by gianluca.pettinello on 2008-11-25
I found a solution to uninstall ttf-mathematica:

- create the folder /usr/share/fonts/truetype/ttf-mathml

- create inside the 12 fonts: math1b__.ttf   math2b__.ttf   math3b__.ttf   math4b__.ttf math1mb__.ttf  math2mb__.ttf  math3mb__.ttf  math4mb__.ttf
math1m__.ttf math2m__.ttf   math3m__.ttf   math4m__.ttf
math1__.ttf    math2__.ttf    math3__.ttf    math4__.ttf
by copying a generic truetype font (es. ttf-liberation) and renaming it

- launch: sudo defoma-font register-all /etc/defoma/hints/ttf-mathematica4.1.hints

At this point you have registered the fonts and you can safely uninstall the package


Gianluca
Ubuntu is the freedom to use the brain work of the others
Linux is the freedom to use your own brain

--------------------------------------
MOLON LAVE

---

### Post by COLiNx86 on 2008-11-25
Thank you very much.

---

### Post by anatolica on 2008-11-26
This worked for me, too. Thanks a lot.

---

### Post by d0.fnal on 2008-12-10
Thank You so much, man you have solved a big issue for me. It was really annoying and causing headache!

d0.fnal

---

### Post by rjray on 2009-01-07
Just in case someone from the Ubuntu team is reading, the problem lies in the fact that the .exe file that the package tries to download as part of the installation has moved-- the URL that is fed to wget returns a 301 response. Whoever is responsible for the ttf-mathematica package could fix this quite easily by finding out the new URL and updating the pre-install script.

---

### Post by milu on 2009-01-23
Thanks Gianluca !

I had lost also the /etc/defoma/hints/ttf-mathematica4.1.hints, but copying ttf-freefont.hints and editing the font names inside to become math1b__ttf etc worked as said above. One comment: the whole idea was for me to use mathematica through a remote desktop (from work). To make the fonts work for mathematica 6 I just copied the fonts from the system at work to my system (scp..) into:
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Fonts/Type1 ( a few MB ). Works for me....

---

### Post by sfordin on 2009-01-28
There's another way to solve this problem that was discussed in these forums in the Absolute Beginner section. Scroll down to the bottom of [this page]("http://ubuntuforums.org/showthread.php?t=1009844").

I'm not sure about the pros and cons of the solution described there, but it worked fine for me. It's certainly less work than the excellent solution recommended here.

Hope this helps,

Scott

---

### Post by tbranham on 2009-04-25
Thanks sfordin. That's a better solution, because I actually wanted the fonts ;)

Just in case, the solution was to do the following:

```
sudo sed '65cURL="http://support.wolfram.com/technotes/fonts/windows/files/"' -i /var/lib/dpkg/info/ttf-mathematica4.1.postinst
sudo aptitude install ttf-mathematica4.1

```

---

### Post by Monotoko on 2009-04-25
> **rjray said:**
> Just in case someone from the Ubuntu team is reading, the problem lies in the fact that the .exe file that the package tries to download as part of the installation has moved-- the URL that is fed to wget returns a 301 response. Whoever is responsible for the ttf-mathematica package could fix this quite easily by finding out the new URL and updating the pre-install script.

.exe file :confused:

---

