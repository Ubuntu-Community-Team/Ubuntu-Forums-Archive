---
title: "Ubuntu 9.10 doesn't go to sleep"
date: 2010-03-09
forum: Hardware
---

### Post by Cavsfan on 2010-03-09
I don't mean to beat a dead horse If I am, but ever since I clean installed Ubuntu 9.10, 
I do not see a sleep function like I did on Ubuntu 9.04. Nor does it work to put my system 
to sleep at all. With 9.04 it would stop the fans and go to sleep just fine and would appear to be off. 
I had to touch a key and it would wake up just fine. It gave an error, but said that it recovered. 
I could live with that. But, I cannot leave Karmic running as it will not sleep.

I was just wondering if Karmic was going to be made to work this way?

I appreciate all of the hard work you people that program this stuff are doing!!!

I love Linux and Ubuntu! :D

Thanks in advance!
(and I know there are way too many Is up above)

---

### Post by efflandt on 2010-03-09
It depends what you mean by go to sleep, your power management settings, or if anything is interfering with that.

If you click on your username at the top of the screen you should see **Suspend** and **Hibernate**.

Suspend is a low power state that powers most things down except the RAM, so it can resume quickly.  Usually your power light will blink when it is in suspend.  I haven't had a computer that would wake up with a keypress or mouse movement in Ubuntu, but if I hit the power button it wakes up.

For Hibernate the system stores its RAM to the swap partition, then totally powers down.  When you turn it on and boot the same menu selection in grub, it should reload RAM that it saved in swap partition and resume quicker than booting from scratch.  However, for hibernate to work, your swap partition has to be at least as large as your RAM.

Whether any of that happens automatically after a period of inactivity depends upon your System > Preferences > Power Management settings.  Not sure which running applications might make your computer think it is not idle.

---

### Post by Cavsfan on 2010-03-10
Thanks efflandt,
I have tried clicking Hibernate by by name and it does as you have said. I had to press the 
power button for it to resume and it went back to where it was.

What I meant was when it goes to "sleep" after a period of inactivity. It doesn't do that with 9.10.
The monitor will turn off, but nothing else. The fans continue to run, etc. forever.

The only thing I have different is Awn for the dock instead of Cairo-Dock since the depository is 
unreachable or whatever. But, now that I think of it, I did have Cairo-Dock  for a good while and it did 
not go to sleep then either. It would pop up with something in a blue box saying see help for determining 
why it did not go to sleep when a hey was pressed.

9.04 would go to sleep as normal and the press of a key woke it back up, however 9.10 does not do that.
And I believe 9.04 had a Sleep option in the drop down list by my name and 9.10 does not.

I have been very happy with 9.10 except for that fact. I like the fans to turn off, etc.

---

### Post by Cavsfan on 2010-04-01
I am testing Lucid Lynx and it sleeps just fine, so I am going to resolve this thread.

---

