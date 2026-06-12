---
title: "[SOLVED] New life for an old Dell"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by Guitar John on 2008-04-06
My old Dell Inspiron 3500 recently came back to me to see if I could do anything with it.  Specs were pretty ancient:
6 GB, 160 MB Ram, 366 MHz Celeron...you get the picture.

For under $100 I upgraded to 60GB and maxed out the Ram at 256 MB.

I installed [xubuntu 7.10]("http://www.xubuntu.org/") which went pretty well.  I'm posting this message using the Dell.  

Now the 2 issues.  The most annoying is that when I scroll down a page, the page sort of rolls down in waves.  

The second is that I have no sound.  I suspect that the answer lies somewhere in [this thread]("http://ubuntuforums.org/showthread.php?t=284405&highlight=nm256")...specifically in walzi's post:> Instead of creating the /etc/modprobe.conf file you just have to add a file in /etc/modprobe.d (all files in this directory are read by modprobe) and instead of
Code:

blacklist snd-nm256

I did
Code:

alias snd-nm256 snd-sb8



If that is what I need to do, do I create a new file or add to an existing one?  Also, do I have to be root?  If so, how do I do that and how do I avoid locking myself out of my system as another poster described?

Thank you in advance for any assistance.
-John

---

### Post by ugm6hr on 2008-04-06
I have no idea what that sound post does - but if you want to give it a try:

Create a new file named "sound" in that directory:

```
gksudo mousepad /etc/modprobe.d/sound
```

Add the relevant line:
> alias snd-nm256 snd-sb8

And save the file.

As for the scrolling in waves.... That's due to the low hardware specs.

Only solution might be to try a lighter browser - Opera is a good choice.

---

### Post by Guitar John on 2008-04-06
I have sound.  Thank you so much.  \\:D/

> As for the scrolling in waves.... That's due to the low hardware specs.
I suspected that was the case.  It doesn't just do it in Firefox, but it does seem to happen in any application that is HEAVY.  Oh well, considering that the computer was gathering dust, now I can return it to my sister-in-law as a working machine.  She needs it for e-mail, IM, and the kids' school work and for that it will do just fine.  

-John

---

### Post by ugm6hr on 2008-04-07
> **Guitar John said:**
> I suspected that was the case.  It doesn't just do it in Firefox, but it does seem to happen in any application that is HEAVY.  Oh well, considering that the computer was gathering dust, now I can return it to my sister-in-law as a working machine.  She needs it for e-mail, IM, and the kids' school work and for that it will do just fine.  

Xubuntu 7.10 is heavier in terms of apps than previous versions.

Worst offenders:
GIMP
OO Writer

AbiWord is installed - so OO can just be removed.
mtpaint is in the repos - not nearly as powerful as GIMP, but has enough basic image editing (I used it with PuppyLinux).

---

