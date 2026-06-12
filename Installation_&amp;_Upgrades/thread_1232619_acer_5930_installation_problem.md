---
title: "acer 5930 installation problem"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Elisavet on 2009-08-05
Hello everyone!
I'm new to Ubuntu and new to this forum as well, although I've browsed it as a visitor about a hundred times :p
I have an Acer Aspire 5930 laptop with NVidia GeForce 9300M GS (256MB) and although I tried many times to install wubi, ubuntu and linux mint I experience the same problem again and again:
Once I boot my laptop with the LiveCD in, I get the usual Ubuntu or Mint screen and once it loads fully, the screen starts to shiver. I can barely see the exit/cancel/go away running button to cancel the installation. One time I managed to access the screen resolution properties (to check if the problem was the refresh rate) but I couldn't change a thing.
Same thing happened with wubi. Seems that my laptop shivers in the idea of running linux :(
Any ideas???
Should I try and burn the iso file in lower speed? because I get that many people had black or flickering screen problems and that was one of the most popular solutions proposed.
Thanks for your time

---

### Post by running_rabbit07 on 2009-08-06
You may want to try the Ubuntu Alternate install ISO. It will allow you to do the install via text mode instead of GUI and may be able to detect hardware and load drivers better.

Let us know how things go.

---

### Post by Elisavet on 2009-08-07
Thanks, I'll try it.
Nevertheless, I'm a little afraid to compile a whole OS through text and command mode... I'm not that familiar and I'm worried that I might mess things up.
Is there a guide ore something similar to review my steps during the installation, or the alt install is just like the live cd one but without the fancy graphics?

---

### Post by m0ar on 2009-08-07
I got that tip from a guy yesterday too, text install.

Just like you, I'm not trying that w/o a guide ^^

---

### Post by phillw on 2009-08-07
[SIZE=2]I'd certainly start off with a disc burnt at 4X or below - As you said, there have been a few reports of this being the problem.

regards,

Phill.
[/SIZE]

---

### Post by running_rabbit07 on 2009-08-07
The alternate install does not require you to give CLI commands. It requires you to use the arrow buttons, [tab] and [enter] kinda like when you go into BIOS. For the most part you just don't get to point and click.

You can also use the same LiveCD you already have and when the menu comes up look you can type F4. There will be other boot options to choose from. If you find that you are not sure with what you are looking at, you can always cancel and exit.

I installed Fedora on my machine last night and their installer is like the alternate installer. Fedora is yet another option for you if you are willing to try something different. It was the only OS so far that automatically recognized and installed drivers for my chipset which is nvidia like yours.

---

### Post by Elisavet on 2009-08-09
Well, thanks to you my problem was solved successfully.
All it took was a more careful cd burn and install in safe graphics!
Thanks people, you're the best

---

### Post by running_rabbit07 on 2009-08-09
Sweet! Congrats!

---

