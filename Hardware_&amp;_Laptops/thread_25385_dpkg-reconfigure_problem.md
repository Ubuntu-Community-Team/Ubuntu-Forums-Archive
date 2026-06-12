---
title: "dpkg-reconfigure problem"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by Requiem on 2005-04-10
Like usual, i have problems with an nvidia  (vanta) card. 

So I followed some instructions about other nvidia cards (nforce mostly) so i thought that i should give it a try too. 

>>type dpkg-reconfigure -plow xserver-xfree86

Or so they say. Typing this into the tty showed a menu of possible video cards but alas, completely irresponsive, no keyboard or mouse input at all the only thing i could still do was to ctrl+alt+f2 into another tty but that doesn't really help.

I also tried with:
        dpkg-reconfigure xserver-xfree86

(sans -plow) and everything was the same. So besides getting vanta drivers from nvidia, what advice would you share with me?

---

### Post by RastaMahata on 2005-04-10
why are you using -plow?
sudo dpkg-reconfigure xserver-xorg
select nv
default for everything else (just press enter)
see what happens

---

### Post by Requiem on 2005-04-11
[QUOTE=RastaMahata]why are you using -plow?
sudo dpkg-reconfigure xserver-xorg
select nv
default for everything else (just press enter)
see what happens[/QUOTE]

Because some ppl said to use it with -plow and somewhere i read that it was for low priority.

I thought  that sudo was for use inside the "main" ubutu session (warthy isn't it?) i was typing into a root term, none the less, i'll try your way.

Thankyou, i'll come back later with news...

---

### Post by az on 2005-04-11
If you want dpkg to ask you every question in the package install script, use -plow.

---

### Post by Requiem on 2005-04-11
Thanks, but is there some trick to use dpkg-reconfigure? i mean, it just doesn't work, Not a single key in the keyboard moves or selects anything.

---

### Post by az on 2005-04-11
Typical ncurses keys are tab, enter and space...

Can you type anything at all?

---

### Post by Requiem on 2005-04-20
News news! sorry for the long wait (work in RL...)

The bad news is that no, i can't type anything at all once i've run "dpkg-reconfigure xserver-xfree86" except ofcourse ctrl+alt+F[1-7].

The good news is that I managed to configure linux before booting (I had to learn about GRUB a little)

Another good new is that I could do it using only the rudimentary help inside GRUB so, the help really works! Kudos to the GRUB team! 

I consider my self a power user but not quite the hacker, I'm a little green when it comes to hardware too. But somehow I managed to...

But the thing that still bugs me is, Why was dpkg freezing on me anyway? Since i'm interested in the progress of free software I want to help solve this problem so it doesn't happens to someone else, any pointers on how can I be of help?

---

