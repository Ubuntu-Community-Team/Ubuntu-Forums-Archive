---
title: "howto configure ethernet PCMCIA cards ?"
date: 2005-02-04
forum: Hardware &amp; Laptops
---

### Post by dusu on 2005-02-04
I've recently installed Ubuntu Hoary on my laptop, using a wireless ethernet PCMCIA card. Up to there, no problem. The card was recognized and I was surfing straight. Ubuntu really rules. :D 
But now I would like to make Ubuntu work with another ethernet PCMCIA card I have. Of course, this one does not work since the installation was made without it. :-( 

Can any one tell how I can make this card be recognized ?
I'me new here, I've looked at other threads and at wikis, but could not find the answer.  :confused: 

Thanks for your help

---

### Post by mendicant on 2005-02-04
What make and model?  Does dmesg say anything when you plug it in?

---

### Post by dusu on 2005-02-08
[QUOTE=mendicant]What make and model?  Does dmesg say anything when you plug it in?[/QUOTE]

First of all, let me mention that I installed Warty, not Hoary. That was a mistake in my post.

Second, dmesg tells me everything is fine (in the end I get *eth0: link up*, ...). This is surprising since usually when a PCMCIA card is recognized the computer makes some beeps that he does not do with this card (?).

Third, I also have to apologize for not giving all details (I stupidly wanted to keep the post short). I have used my wireless card in the lab where I work, whereas the other card (let's call it the wireplain) was used at home. Now it's not that the wireplain card does not work, it's that both do not work at home. So it is not a problem of driver, but a problem of setting up the internet connection properly.

I'll try to fix this, but any idea is welcome.

---

### Post by mendicant on 2005-02-08
eth0 is moderately strange for a laptop computer's wireless card, unless the laptop does not have built-in ethernet--of course, it could be a relatively old laptop, or a super thin/light model (like the c1xs on my desk).

It should usually beep.  Look for cs: memory probe ... in your logs.  Also look here:
[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html)

In particular, the section (2.6) Failure to detect card insertions and removals, and the file is in /etc/default/pcmcia

---

### Post by dusu on 2005-02-12
[QUOTE=mendicant]eth0 is moderately strange for a laptop computer's wireless card, unless the laptop does not have built-in ethernet--of course, it could be a relatively old laptop, or a super thin/light model (like the c1xs on my desk).
[/QUOTE]

My laptop is indeed an old one (three years old) and was one of the cheapest at the time, explaining why I have no built-in-ethernet.

[QUOTE=mendicqnt]It should usually beep.  Look for cs: memory probe ... in your logs.  Also look here:
[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html)
In particular, the section (2.6) Failure to detect card insertions and removals, and the file is in /etc/default/pcmcia[/QUOTE]

Thanks for the info, I'll try my best to make this work !

---

