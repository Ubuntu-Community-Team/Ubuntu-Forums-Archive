---
title: "MX Revolution, power loss broke middle click"
date: 2008-11-01
forum: Hardware
---

### Post by malcolmci on 2008-11-01
Hey everyone,

I've been a satisfied Ubuntu user for little under a month now, but I've recently encountered a problem with my MX Revolution mouse.

See, I switched it off to give it a clean, and when I switched it back on again, the middle-click no longer works - it now switches it between click-to-click scroll and free scroll.

This exact thing happened in Windows when the drivers weren't installed. Thing is, there's no SetPoint for Ubuntu.

I've been searching high and low all evening: I came across a thread about editing a bunch of Xorg files, only to realise the method had been superceded by btnx, only to realise that btnx no longer works with 8.10 Intrepid.

Under xev, middle-click isn't detected whatsoever.

I would imagine that this would be a rather common problem, seeing as the MX Revolution is quite a popular mouse and that more than a few have been powered off in their time, so I'm hoping that there also lies a simple solution.

All the same, thanks in advance for any help you could kindly offer.

---

### Post by malcolmci on 2008-11-01
Bump.

---

### Post by malcolmci on 2008-11-01
Bump.

All I need to know is how to map buttons (specifically, middle-click) in Intrepid. All the methods I've found so far have been outdated.

---

### Post by iamnotthemessiah on 2008-11-01
joining u on this one
in hardy there was btnx
would love to once again use the revolution search button as middle click (search button on a mouse, whats that about anyway)

---

### Post by capnrobalo on 2008-11-01
Hi,
I just discovered the same issue as the OP.  I did some quick searching and found a command line utility to change the modes.  My Mx Revolution is back to 'normal'.  After compiling it, just run 'sudo ./revoco click'.

Original thread - search for the post by Froese
[http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/](http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/)

Link to source
[http://goron.de/~froese/revoco-0.1.tar.gz](http://goron.de/~froese/revoco-0.1.tar.gz)

Good luck.

---

### Post by malcolmci on 2008-11-01
Edit: Didn't see above post, I'll give that a shot, thanks! :)

---

### Post by malcolmci on 2008-11-01
> **capnrobalo said:**
> After compiling it...

Hi Capnrobalo. I haven't compiled a program before, so I found a page on the wiki guidiing me through it. However, when the guide told me to run the configure file in the extracted directory, I realised there is no such file there.

Thus, I'm lost on how to compile/install it.

---

### Post by malcolmci on 2008-11-01
Ah, I realised the configure part wasn't necessary.

So I cd'ed into the revoco directory, ran 'make', but after running 'checkinstall', I get this:

make: *** No rule to make target `install'.  Stop.

:/

---

### Post by capnrobalo on 2008-11-01
Ok.  I'm assuming you have extracted the source tar file.  If not, you can easily do this by running the command 'tar -zxvf revoco-0.5.tar.gz'.   Once you have done that, you will have a directory called 'revoco-0.5'.  In this directory there is a Makefile and the source files.  The Makefile has the instructions for compiling the program, all you need is to type 'make' and the 'make' program will do the compile for you.  Once the compile is complete, you will have the program called 'revoco'.  There is no installation required - just run it from the directory where you compiled it.  If you are looking for a menu item or something in the Ubuntu desktop, this is not the solution for you ...  Hope that helps.

---

### Post by malcolmci on 2008-11-01
> **capnrobalo said:**
> Ok.  I'm assuming you have extracted the source tar file.  If not, you can easily do this by running the command 'tar -zxvf revoco-0.5.tar.gz'.   Once you have done that, you will have a directory called 'revoco-0.5'.  In this directory there is a Makefile and the source files.  The Makefile has the instructions for compiling the program, all you need is to type 'make' and the 'make' program will do the compile for you.  Once the compile is complete, you will have the program called 'revoco'.  There is no installation required - just run it from the directory where you compiled it.  If you are looking for a menu item or something in the Ubuntu desktop, this is not the solution for you ...  Hope that helps.
Mate, you're a modern day legend.

Thanks a ton :)

---

### Post by solidboss on 2008-11-03
How do I 'run' the application? I've following the instructions and compiled it, bit I can't figure out how to actually get it going. Can someone help me out?

Solid

---

### Post by Nicks Spleen on 2008-11-03
If you have a terminal opened to the revoco-0.5 folder then to run the program you would type.

sudo ./revoco *command*
 
If you run the program without a command it will give you this:

Revoco v0.5 - Change the wheel behaviour of Logitech's MX-Revolution mouse.

Usage:
  revoco free                     - free spinning mode
  revoco click                    - click-to-click mode
  revoco manual[=button[,button]] - manual mode change via button
  revoco auto[=speed[,speed]]     - automatic mode change (up, down)
  revoco battery                  - query battery status
  revoco mode                     - query scroll wheel mode
  revoco reconnect                - initiate reconnection

Prefixing the mode with 'temp-' (i.e. temp-free) switches the mode
temporarily, otherwise it becomes the default mode after power up.

Button numbers:
  0 previously set button   7 wheel left tilt
  3 middle (wheel button)   8 wheel right tilt
  4 rear thumb button       9 thumb wheel forward
  5 front thumb button     11 thumb wheel backward
  6 find button            13 thumb wheel pressed
 

For instance if you wanted to check what mode the battery is in, you would type:
sudo ./ revoco mode

Or to have it auto change: (change 15 to a speed that you like)
sudo ./revoco auto=15,15

Or to have it manually change using the search button:
sudo ./revoco manual=6,6

---

### Post by solidboss on 2008-11-12
Awesome! Thank you so much for your help. I was a little busy with school so I never got around to trying it out again till now, and it worked like a charm!

I think this thread can be marked SOLVED now.

Solid

---

### Post by agmk on 2008-12-02
you can still also still use btnx for its revoco functionality, even though its keybinds are broken.

---

### Post by arius13721 on 2009-01-19
OMG... thank you guys. I had the same problem and I was ready to shoot myself over this. This was hands down the weirdest issue I've ever come across.

---

### Post by JMonkeYJ on 2009-01-20
Using revoco is nice, and solves part of the problem, but no one has addressed the other problem: how do you remap the buttons? specifically, since my middle-click no longer works, how can i map the search button to middle-click?

---

### Post by thewooster on 2009-02-10
Hey, so I've compiled the program etc. . .

And when I try to run "sudo ./revoco click" or any command I get this error:

> revoco: No Logitech MX-Revolution (046d:c51a) found.


Has anyone encountered this error?

---

### Post by trinaryouroboros on 2009-03-04
:popcorn:

Definitely much happier now.

Currently using the latest Intrepid updates/etc., didn't have to modify my xorg.conf or anything, however, I did install btnx - pretty much useless.

I downloaded the aforementioned revoco source, changed to it's directory and did:

make
sudo ./revoco manual=6

All my buttons are working perfectly happy.  The above command sets the Search button on the mouse to be the free-spin/click-by-click scroll wheel mode, while leaving the middle mouse button the heck alone, so it can serve as a middle mouse button again.  

I'm back to middle-mousing for the Compiz cube, middle-mousing to open firefox links in new tabs, middle-mousing to copy/paste, and everything.  

Even the back/forward high thumb buttons work fine.  My next mission is to investigate the Tilt options, and to get the thumbwheel to perform it's duty (I presume it's supposed to scroll Left and Right, doesn't do this yet, and when I push in the thumbwheel it acts like a right-click for some reason.)

---

