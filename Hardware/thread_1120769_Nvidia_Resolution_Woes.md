---
title: "Nvidia Resolution Woes"
date: 2009-04-09
forum: Hardware
---

### Post by jcapinc on 2009-04-09
I had the ultimate setup things were great!  I had a 1900x1080 acer moniter and a 1280x1024 dell monitor and things looked great I had nvidia twinview set up through their utility and quite frankly my setup was flippin sexy.

I like ubuntu updates, I really do, I know that it is improving my computer so when I saw a restricted driver update I thought "great!!! my graphics card will run faster!"  and I updated and to my dismay on restart only one of my moniters was on!  I did not think it would change my configuration!

So I played with it and found two things, the first of which is my real problem: First, nvidia wont let me change the resolution high enough on my huge-resolution monitor.  It's maximum resolution is about 1390x960 and it simply refuses to give me options higher then that, no matter what I do.  Second, it appears to read both my LCD moniters as CRT moniters, and normally I would not care, but normally it would work!  so the fact that it is reading crt moniters might have something to do with the problem.

I will try to give my rig information as best I can:

Ubuntu 8.10 intrepid 32 bit
Dell Vostro 200
intel core 2 duo E4500
Nvidia GeForce 7300 LE
4 gig ram

Dell E197FPf (res 1280x1024) Working Correctly
Acer AL2032W d (res 1900x1080)  Working Incorrectly

Thank you in advance for any help you can give me

---

### Post by askreet on 2009-04-09
First thing is to make sure you're still actually using the nvidia drivers:

$ glxinfo|grep direct
direct rendering: Yes

And let's see how Xorg is configured:

$ cat /etc/X11/xorg.conf|grep Driver
    Driver         "nvidia"
    Driver         "nvidia"

Does it say "nvidia"?  Once or twice?

What about:
$ lsmod|grep nvidia
nvidia               6909268  40 
i2c_core               31892  1 nvidia
agpgart                42184  2 nvidia,intel_agp

HTH,
askreet

---

### Post by ussndmac on 2009-04-09
Interestingly I have a Dell 1530 laptop with a 23" Acer on the VGA port.

It is seen by the drivers pretty much automatically, at the 1920 resolution.

But I get lots of 60Hz banding on the Acer and the drivers eat so much cpu that it effects rt operation of other apps.


PS: jcapinc: sorry I don't have aim, but I notice you are in Nashua, I'm just west of there.

Mac

---

### Post by askreet on 2009-04-09
> **ussndmac said:**
> PS: jcapinc: sorry I don't have aim, but I notice you are in Nashua, I'm just west of there.

I think you're confusing me with the original poster.

Hollis?

- askreet

---

### Post by jcapinc on 2009-04-09
wow.... whats crazy is that askreet you are in nashua, mac you're in hollis?  but the crazy coincidence is I live in New Boston, right near Milford/Mont Vernon ect. 

Thats pretty funny, I am like the only Ubuntu/Linux fan I know, we should get together sometime!

By the way askreet I will follow your advice soon and get you all that information, I am pretty certain that I am using nvidia drivers but for proof's sake I will follow your instructions, its on my to-do list and Im just so blasted busy today.

thanks again

---

### Post by ussndmac on 2009-04-11
I'm actually in Brookline, but, I spend way too much time in Milford...I'm the tech director at the Amato Center. And that's my part time avocation...;)

Getting together sounds good to me. Just not this weekend...gotta go do the easter dinner @ the inlaws.

At this point my extern monitor is on hold until I get 24 channels of audio in working with ffado/jackd. It works, but crashes for some unknown reason after recording for a while. "A while" can be anything from 5 minutes to 2 hours. I need 2 hours consistently.

> **jcapinc said:**
> wow.... whats crazy is that askreet you are in nashua, mac you're in hollis?  but the crazy coincidence is I live in New Boston, right near Milford/Mont Vernon ect. 

Thats pretty funny, I am like the only Ubuntu/Linux fan I know, we should get together sometime!

By the way askreet I will follow your advice soon and get you all that information, I am pretty certain that I am using nvidia drivers but for proof's sake I will follow your instructions, its on my to-do list and Im just so blasted busy today.

thanks again

---

