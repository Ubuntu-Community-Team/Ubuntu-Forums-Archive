---
title: "numeric keypad just stopped working"
date: 2008-05-25
forum: Hardware
---

### Post by braganfamily on 2008-05-25
Numeric keypad just stopped working.  Using Hardy Heron.  It has been fine until something happened last night.  Had a package install freeze up, rebooted and finished.  But, somehow a new kernel "rt" kernel showed up and now number keypad not working.

Any ideas?

bobby

---

### Post by villain222 on 2008-05-27
me too.  seems to have something to do with the recent gnome updates.  gnome-keyring had some errors on line 9784 character 68 (which didn't exist)

also I had to reinstall gdm the other night along with a reinstall of ubuntu-desktop.  My logging in has been fine, but my number pad has been knocked out.  I first noticed it when I was using vnc to remote to my desktop from work.  I just thought is was some kind of connection error.

I've also been playing with virtualbox recently.  Maybe a problem with the way the inputs are grabbed from the host to guest machine.  

Any of this sound familiar???  lots of possibilites, hard to narrow it down without others having the same problems.

---

### Post by villain222 on 2008-05-27
found this in another forum post.  it worked.  much simpler than i thought.


Russel Cook:
In breezy, if you press CTRL-SHIFT-NUMLOCK you turn the keypad into a
keypress/mouse cursor mode. Try typing ctrl-shift-numlock to turn this
mode off and then see if the keypad works or you now have control of the
numlock LED.

---

### Post by braganfamily on 2008-05-27
Yes!!!

It worked.  Thanks a million.

bobby

---

### Post by cybrsaylr on 2008-05-28
Thanks villain222,
I was havng the the same problem. A couple days ago the number keypad on the right of the keyboard stopped working. I did what you said on post#3 and it works again!

---

### Post by parsim on 2008-05-31
> **villain222 said:**
> Russel Cook:
In breezy, if you press CTRL-SHIFT-NUMLOCK you turn the keypad into a
keypress/mouse cursor mode. Try typing ctrl-shift-numlock to turn this
mode off and then see if the keypad works or you now have control of the
numlock LED.

Ahhh, thank you! Fixed for me.

---

### Post by magodfrey on 2008-06-01
Villain222 for pointing in the right direction and Russel Cook for the original: Thanks very, very much - I've been sweating for a full day trying to solve this same problem, the answer is so simple it took all of 3 seconds.

---

### Post by asphixmx on 2008-06-09
I had no idea about this "mouse emulation". A few days ago the my numeric keypad stopped working...and noticed the cursor moved while I pressed the numbers. Now it is fixed... CTRL-SHFT-NUM LOCK... wow! what a strange key combination LOL. Thanks for solving my problem.

---

### Post by editrix on 2008-06-10
I wish I could say this worked for me :-(

The popup message I got said someone had pressed Shift-Numlock (N.B.: no mention of CTRL)

But turning it on and off again only shut off the numlock button, which isn't having any effect anyway.

---

### Post by acmarfil31 on 2008-06-25
Thank you for this post.  Kudos to you.

---

### Post by maurotdo on 2008-06-29
This page was a life-saver. Keypad stopped working after a hard "push-the-power-button-for-8-sec" power-off. Tagged it on delicious to help other people find this solution!

---

### Post by Euperia on 2008-08-12
I had this issue after connecting remotely via VNC [using Preferences > Remote Desktop].

Could it be that Remote Desktop/VNC is using the ctrl-shift + num-lock to handle the mouse moving  and it doesn't return it after?

---

### Post by villain222 on 2008-08-13
got something new about this.  It apparently is very similar to another forum in Hardy about going into the keyboard preferences and hitting the mouse keys tab and deselecting the box to control the cursor via the num pad.  I don't have the original post, but I did find out the hard way that in gutsy it's not there.  you have to go the universal access settings throught the preference menu.  then you hit the keyboard accessibility tab and then you can find the Mouse keys tab.  Its just a gui way of doing what I said.  

I had this problem again when I was using vnc to control my home comp.  I had to dig up my own answer which wasn't working, probably because vnc doesn't send all the commands through.

What's messed up is you have a box to enable the keyboard accessibility tools that wasn't selected but the mouse keys were set.  I had enable and deselect the mouse keys and then it worked.  Then i turn off the keyboard accessibility box again.  Still works.  pain in the rear!

Hope this saves someone else.

---

### Post by villain222 on 2008-08-13
vnc is at the root of my problem and sounds like a few others have it too.  I think the key is to not screw up and hit too many command keys when remoting in,  some kind of flaw with the input being sent.  I think it happened this last time when I hit shift+tab when I was filling out a form.

---

### Post by skinkone on 2009-05-16
Worked on Jaunty Jackalope too!

---

### Post by Spartanis on 2009-06-27
> **villain222 said:**
> found this in another forum post.  it worked.  much simpler than i thought.


Russel Cook:
In breezy, if you press CTRL-SHIFT-NUMLOCK you turn the keypad into a
keypress/mouse cursor mode. Try typing ctrl-shift-numlock to turn this
mode off and then see if the keypad works or you now have control of the
numlock LED.

THank you for sharing that. This solved my problem also. :)

---

### Post by Nomadito on 2009-08-05
> **Spartanis said:**
> THank you for sharing that. This solved my problem also. :)

Here also! Thank you!!!:P

---

### Post by ubushiba on 2010-02-17
Works on karmic also.
This newbie has been fighting the problem for a week, should have looked here first.

THANK YOU !!!

---

### Post by Arnie Tchelakian on 2010-04-29
Vilain222 saved the day!! Thanks so much :-):KS

---

### Post by lofty40 on 2010-11-13
Even with Ubuntu 10.10 this is still valid.

Regards

---

### Post by roboa1983 on 2011-01-06
I had this problem using ubuntu 10.04 from within a virtual machine (using virtualbox).
Thanks, villain222! Given so many thank yous in this post, isn't the name ironic? ;)

---

### Post by payne technologies on 2011-02-11
Some things never change (10.10)...thanks for the answer to this 
perplexing problem:


Originally Posted by villain222  
Russel Cook:
In breezy, if you press CTRL-SHIFT-NUMLOCK you turn the keypad into a keypress/mouse cursor mode. Try typing ctrl-shift-numlock to turn this mode off and then see if the keypad works or you now have control of the numlock LED.

---

