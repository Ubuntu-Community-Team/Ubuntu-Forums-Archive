---
title: "Acer Aspire 5003 WLMi screen resolution and color problems"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by Arwen on 2007-10-16
Hello everyone!
I installed ubuntu 7.04 in my laptop,I post its hardware info below I problems.
I use 1024*768 resolution and I hate it because everything seems too big and the colours are fading(same happens with 640*480 and 800*600)A normal size of icons seems to be with 960*600 and also the colours look better.The problem is that it won't show up in whole screen 
but centered in it,framed with black.Well I hope you understand what I'm saying,it's sth like this:when you click on advanced post you see only the small window with the smileys,the one you write in,centered in your browser window and everything else around it is black.

If you had enough courage to undestand what I wrote,I would really really appreciate it if someone had a solution to my problem.Will "sudo apt-get install 915resolution" save me?
Thank you for any response:-)



ACER hardware:
AMD Turion64 ML-32 @1.8GHz(ubuntu is 32bit)
1GB RAM
VGA:SIS Shared 128MB

---

### Post by ljonesj on 2007-10-16
what is the video card intel intergrated, ati, or nvidia this will help in solving your problems

---

### Post by Arwen on 2007-10-16
It's SIS Shared,that's what it says it is..

---

### Post by ljonesj on 2007-10-16
i think means it uses part of system memory for video but i could be wrong

---

### Post by Arwen on 2007-10-16
Yes it uses a part of RAM when needed,is this a problem?

---

### Post by OldTimeTech on 2007-10-16
I have an Acer 9300-5005 and I did install the 64bit, the only trouble  I'm seeming to have with it now is the keyboard configuration.....believe it or not, I've had to use the International classic keyboard, so it doesn't give me all of the apostrophes and quotes.

It recognized the screen without a problem, I have bright colors and can run it clear up to 1950 x something.

---

### Post by ljonesj on 2007-10-16
no the shared memory is not a problem my acer 3680 uses an intel 950 graphics card what i was saying is the intel, nvidia, and ati are the only cards i know off. that are up to date i know of older cards but that was during the 90's you should have some where some documentation on the graphics card sis is something about shared memory. see if you can find more info about your card i still think its an intel, nvidia, or ati but i may be wrong

ok what is the model is your acer mine is acer aspire 3680-2682

---

### Post by Arwen on 2007-10-16
SIS=Silicon Integrated Systems

I did "sudo dpkg-reconfigure xserver-xorg " but I don't know what framebuffer is :-S
It seems that I'll have to face ubuntu reinstallation..

---

### Post by ljonesj on 2007-10-16
wait a minute i have an idea got to system, adminstaration then restriceted drivers management it should give you a list of what you graphics card is to install the restricted driver for the graphics card

---

### Post by Arwen on 2007-10-16
I did before and it said my hardware doesn't need any restricted drivers.

---

### Post by Arwen on 2007-10-16
:guitar: Finally I did it :-D That "sudo dpkg-reconfigure xserver-xorg " was the right thing to do and now I've set screen resolution to 1280*768 and everything is better except colours but I don't mind cause at least everything has the size I want :-)

---

### Post by kronictokr on 2008-04-16
you should also for sis linux driver update and install.
dont remember, i think i got it from their site. no matter how you have it set up , your system will look better after , way sharper, and crisp image.  i have the same model cpu as the poster. it worked for me. search the wikiubuntuguide<<<something like that and look , they have step by steps on where to find and what to do

---

