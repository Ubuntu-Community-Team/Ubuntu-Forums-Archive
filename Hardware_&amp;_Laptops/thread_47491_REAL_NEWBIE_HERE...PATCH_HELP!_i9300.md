---
title: "REAL NEWBIE HERE...PATCH HELP! i9300"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by jodar on 2005-07-08
So I love kubuntu, and love my inspiron 9300.  I am really liking it all...I tried to follow the guide here

rtr.ca/dell_i9300/

which I believe is Mlords....

anyhow, I know NOTHING about how to do linux from the ground up, so some quick questions I have that I can't seem to find:

1.  Where do I get the 2.6.12.2 kernel (saw the other thread, so check this off)
2.  physically HOW do I upgrade (the other thread talks about it, so I'll check it out..if it's all in there, then check this one off too..I haven't had a chance to try just yet)
3.  when you say to patch the kernel...how do I do that?  And is this done pre or post upgrading to it (I didn't know if you prep the kernel first or what)...
4.  I noticed that in binding some of the functions, one gets bound to F-14...I can't ge t mine to do that at all...I've tried Fn+every F button and can't get it to work...

I basically just need physical (type this, do this) commands to do some of the stuff cause I'm having trouble finding anything related to some of these things (patching, etc..) that aren't dealing with really advanced problems, way beyond me.

I guess I'm just asking if there is anyway that someone can dumb down the guide for me a bit...it's pretty great already, and I'm really anxious to learn all this.....

---

### Post by petehall on 2005-07-09
There's a GUI for installing new packages which I believe you can access by typing ```
sudo kynaptic
```. Within this program, you want to search for a package called something like linux-image-2.6.12-2-386 and install that. It may not be available in the repository yet though. If it isn't, you're probably better off waiting for it to be available, unless you have a specific need for it.

To install from the command line would be something like ```
sudo apt-get install linux-image-2.6.12-2-386
``` - this should automatically update the menu for your boot loader, so when you restart your computer, the new kernel will be presented to you as an option.

---

