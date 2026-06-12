---
title: "a strange situation with my ATI card - and the solution I have found"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by nikosal on 2008-02-27
Hello there, 
I will describe you a strange situation with my card and the solution I may apply, just in case you have something else to propose. 

Before the problem: I could start up ubuntu with no problem every time. I just had slow gnu-backgammon graphics at 3D. So I decided to install the third party, closed code (sorry, my ubuntu is greek, so I don't know the right english language terms) driver for ATI. 

The problem: Now one every two start ups I have the following thing happening. Grub is loading, but exactly at the moment the "drum" is heard monitor loses contact with the main unit and the blue led of my monitor (blue = monitor working properly) becomes orange (=as if the pc was shut off, which is not happening of course). The OS is still there and if I blindly type my user name and password the log in will continue successfully (but still, with the monitor off). 

The solution: I have to restart and then I have a something like 50% chance that the situation will not arise and the log in will finish successfully. Of course this is not a real solution. Also, if I uninstall the closed code ATI driver system is again ok. But as I said, my 3D backgammon is terribly slow.  

So, any real solution here?? 

Thanks in advance.

---

### Post by Sam Lars on 2008-02-27
You probably don't want to say that you've found a solution in the title if you are looking for one. :)
What do you get from
```
cat /var/log/Xorg.0.log | grep EE
```
after an unsuccessful boot?

---

### Post by nikosal on 2008-02-27
hehe thanks for the first advice. 

Now, sorry for my newbie question regarding your second advice: You mean I call console and type cat etc AFTER I am able to log in properly?

If you mean that, then I take the following: 

(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

---

### Post by Sam Lars on 2008-02-27
Sorry, no, I mean after you get a blank screen, press Ctrl+Alt+F1 to get a terminal.  Log in, and then run that command.

---

### Post by nikosal on 2008-02-27
Fine, I just did so. What I got was EXACTLY THE SAME with what I had already typed a couple of posts above. Any guess? 

*And btw: When I have failed to log in into the graphics environment and have called up the terminal with ctr + alt + F1 like you said, what is the command to try to load the graphics env. from there??? *

---

### Post by Sam Lars on 2008-02-27
startx should start the graphics again, or at least try.

---

### Post by Yellow Pasque on 2008-02-27
> **Sam Lars said:**
> startx should start the graphics again, or at least try.
No, you would have to kill the X server before that would work. Try Ctrl+Alt+F7

---

### Post by Sam Lars on 2008-02-27
> **Temüjin said:**
> No, you would have to kill the X server before that would work. Try Ctrl+Alt+F7
Correct, you should
```
killall xorg
```
first.  Thanks for seeing that.
However, if you just switched out of an X that was not working, you don't want to switch back...

---

### Post by Yellow Pasque on 2008-02-27
> 
However, if you just switched out of an X that was not working, you don't want to switch back...

I've actually heard of a Ctrl+Alt+f7 sometimes being successful in fixing display issues, esp. when coming out of suspend.

Thanks for that command; I never used it. I shall put it in my bag o' tricks and put it to good use.

---

### Post by nikosal on 2008-02-28
Ctr + Alt + F7 actually brings again monitor online and solves my problem!! Thank you all for this!

---

### Post by Sam Lars on 2008-02-29
Yes, I haven't thought of that before, I'll add that to *my* bag of tricks.  Thanks.

---

