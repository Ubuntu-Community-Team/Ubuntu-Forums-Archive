---
title: "Segmentation fault with every program!!! Ready 2 Quit!!!"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by Nevermor7 on 2009-08-06
I am using a stock Gateway 507 GR with upgraded memory (1.5g.)  I use this desktop to surf the web, download tunes, and DJ.  I was running Hardy (Kubuntu) and upgraded to Jaunty- disaster.  Every program is error-ing and crashing/shutting down with a segmentation fault- Firefox, Rhythmbox, Totem, Transmission.  I have been googling answers this last week, but I'm finding my problem is bigger than what other people are having.

I wiped out my 200gb hard drive and reinstalled a fresh Ubuntu Jaunty release.... still the same problem.

I love the idea of ubuntu, but honestly I'm reaching my end.  I cannot have my DJ computer crash like mine is now.  Please.  I want to keep ubuntu.

Tell me what I need to do![-o<

(Ps-running transmission in terminal, screen just now flashed and I got this:
index 361 offset 0 length 65536 err 4
index 361 offset 65536 length 65536 err 4
...but Transmission is still running... *sigh*)

Windows/Mac CANNOT be more stable than Ubuntu... right?

---

### Post by oldrocker99 on 2009-08-06
Jaunty was disastrous for me for video card issues. I went back to Intrepid and am a happy camper. Back up your /home directory and install Intrepid, is my advice.

:guitar:

---

### Post by Charles Kerr on 2009-08-16
> **Nevermor7 said:**
>  (Ps-running transmission in terminal, screen just now flashed and I got this:
index 361 offset 0 length 65536 err 4
index 361 offset 65536 length 65536 err 4
...but Transmission is still running... *sigh*)

This is a Transmission debug message that's complaining about one of your peers sending an invalid request.  It's the peer's bug --  not Transmission's -- but  it shouldn't clutter your terminal like that.

Digging into the code, I'm impressed this terminal message has survived from at least 1.50 to 1.73.  The only reason it's lasted so long is because it almost never appears.  I've removed it in [http://trac.transmissionbt.com/changeset/8948/](http://trac.transmissionbt.com/changeset/8948/) so that, as of 1.74, that "almost never appears" will be "never appears".  Thanks for pointing this out.

If you have future problems with Transmission, the programmer team is more likely to see them if you report them to [http://trac.transmissionbt.com/newticket](http://trac.transmissionbt.com/newticket)[]("http://trac.transmissionbt.com/newticket") . :)

---

