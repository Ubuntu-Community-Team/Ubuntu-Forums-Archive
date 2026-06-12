---
title: "black scren after installed ubuntu 10.04 in notebook asus UL80VT"
date: 2010-05-02
forum: Hardware
---

### Post by saidh4ndra on 2010-05-02
after installed ubuntu 10.04 and i installed driver VGA 210 m and then reboot, but after that black scren, any some one help me,, any forum ask ubuntu dosn't suport with grapick card nvidia in notebook asus UL80VT ,, hmmmm :confused:

---

### Post by Vakman on 2010-05-28
Hm, I also have this problem. I am reinstalling Ubuntu now though and am going to install the drivers correctly as I think it was user error last time but I did not see my GRUB2 boot when it started up.
Either way, we will see and I hope someone answers here.

---

### Post by Musicologynut85 on 2010-05-28
Put in a LiveCD and boot it up, when you get to the screen with the universal access symbol at the bottom (right before the UBUNTU with the dots) hit f6, that should take you to the typical options screen.

Select your language, then hit f6 then his esc.

There should be a CLI type thing near the bottom of the screen. Use the arrow keys (left and right) to figure out where the cursor in it is, then move the cursor to right after where it says "quiet splash" (before the hyphen "--").

Type in "xforcevesa" and it should install without going to the bank screen.

Now the problem is I don't know how to switch to another graphics driver...
I'll come back once I figure that part out and post again.


*sigh*

---

### Post by Vakman on 2010-06-02
> **Musicologynut85 said:**
> Put in a LiveCD and boot it up, when you get to the screen with the universal access symbol at the bottom (right before the UBUNTU with the dots) hit f6, that should take you to the typical options screen.

Select your language, then hit f6 then his esc.

There should be a CLI type thing near the bottom of the screen. Use the arrow keys (left and right) to figure out where the cursor in it is, then move the cursor to right after where it says "quiet splash" (before the hyphen "--").

Type in "xforcevesa" and it should install without going to the bank screen.

Now the problem is I don't know how to switch to another graphics driver...
I'll come back once I figure that part out and post again.


*sigh*

Yes, my problem is that I 1. Can't switch to my Intel card and 2. I can't install my nVIDIA drivers and there are problems with 2D & 3D acceleration and what not. We will see soon I hope.

---

