---
title: "mighty mouse BT with macbook"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by tgomas on 2006-12-10
Has anyone successed to connect a bluetooth mighty mouse with a macbook c2d under edgy?

---

### Post by .bashrc on 2007-03-13
Hi, a little bit older thread but might I revive it since I got it working a minute ago! 

Admittedly, I don't know what you need to have, except for bluetooth drivers installed (though I don't know what exactly) and a program called 'hidd', which you should already have installed (mine was already installed)

Read the man page on hidd. 

Here are some step by step instructions on how I got it working (by accident, more or less):

0. start with the mouse turned off
1. run 'hidd --server' from the command line (probably already running)
2. run 'hidd --search' and when it starts searching, turn your BT mighty mouse on. 
     the idea is that it will spit out a hw address, which you can now use to explicitly create a connection
3. turn off the mouse. run 'hidd --connect hwaddresshere' where you change 'hwaddresshere' with whatever bt hw address you found, and once you hit enter, turn the mouse back on again to let it be found.

And it should get it working. Maybe it's not so complicated but I found that if the mouse didn't connect with the green light on it usually failed. 

Right click, left click, and up/down scrolling all work. I don't even know where to start on figuring out the other 2 buttons and horizontal scrolling, but hey, it has basic functionality. Oh, and a non-note about power management/consumption - I don't have any idea how this is different from Mac OS X to Ubuntu. 

Best,
.bashrc

---

### Post by .bashrc on 2007-03-13
one more note. looks like the middle button is actually performing paste commands. useful to know, though I'd still like to be able to change it ....

---

