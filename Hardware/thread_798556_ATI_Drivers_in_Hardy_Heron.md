---
title: "ATI Drivers in Hardy Heron"
date: 2008-05-18
forum: Hardware
---

### Post by Scarfy on 2008-05-18
Has anyone else experienced a massive degradation in the speed of their ATI drivers since upgrading from Gusty?

I'm currently developing OpenGL game, in Ortho mode (so basically it's fancy 2D) and the game crawls at points where it should.

I've also noticed that Blob and Conquer's frame rate dips a lot more often.

It is helps I'm using an ATI Radeon 9700 (128MB).

Steve

---

### Post by BLTicklemonster on 2008-07-10
I'm setting up Hardy on a computer for a friend who has been wanting Ubuntu for a while, and no matter what I do, I can't get the restricted manager to load up. I've enabled ubuntu restricted in add/remove, I've tried Envy, I've tried everything (in the middle of this: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method) right now, building the deb part).

This is really frustrating. I knew better than to use an ati card in her computer, but it's the only thing I had around, and she doesn't want to put a lot of money into this machine. It's a radeon 9200se with a dvi output for an lcd flat panel, which is what she wanted to have.

This is really frustrating because I keep telling her how cool ubuntu is. And I though ati was doing all kinds of stuff to make their drivers work well in linux?

The only drivers that work are the basic fglrx ones, and yeah I get 1400 fps in glxgears-is-not-a-benchmark, but still, I want better drivers running, and yes, I've tried the envy drivers shown in synaptic.

So why is there no restricted driver manager? I've seen this problem avoided in many posts here so far. I had no idea this was such a problem.

... okay, my stand by nvidia fx5200 pci card is sitting over there, but I really don't want to part with AN NVIDIA card when I can finally get this wretched ati product off of my property, know what I mean? :)

Help?

Anyone?


*Edit:

I'm stuck at this

```
Setting up fglrx-amdcccle (2:8.501-0ubuntu1) ...

```

point for a while in the terminal. Seems like it's taking way too long.

---

### Post by markbuntu on 2008-07-13
The 9200 series is not supported by the ati driver.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

You need to use the radeon open source driver for that card.

---

### Post by svivian on 2008-07-13
Yes, I'm having the same problem, since upgrading to 8.04 everything's a little slower (KDE runs like a snail).
My card is: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]

Can you point me to that radeon driver? I don't see it in synaptic.

---

### Post by markbuntu on 2008-07-13
The Radeon x1300 is supported by the ati restricted driver so you would be better off with that. If you want instructions on installing the latest ati driver you can get them here, (follow Method 2 if you want the latest one, 8.6):


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by BLTicklemonster on 2008-07-13
> **markbuntu said:**
> The 9200 series is not supported by the ati driver.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

You need to use the radeon open source driver for that card.


AHA! I KNEW IT! They're out to get me. I knew it all along. 


These cards burn don't they? Well heck, with enough gas, I guess anything will burn, won't it? Yeah, gas. Lots of gas.

By God, messing with me all the time, I knew ATI had it out for me all along.

---

### Post by svivian on 2008-07-13
Thank you markbuntu! That page solved all my problems!

I ran **fglrxinfo** and it said I was using the mesa drivers. So I simply uninstalled **xserver-xgl** in synaptic and everything's perfect again. :)

---

