---
title: "No sound on firefox"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by swong1 on 2005-12-17
Hi there,

I have a dual-boot Dell inspiron 6000. I use firefox on both Windows and Ubuntu. 
Whenever I visit a site that has sound, I get sound under Windows, but not in Ubuntu (5.04). Here's is one example:

 [http://www.hazza316.co.uk/roger.html](http://www.hazza316.co.uk/roger.html)

However, I do get sound while playing CDs and DVDs.

What gives?

---

### Post by Vorian on 2005-12-17
try #killall esd.

Worked for me on hoary.  I have a 6000 as well, and Breezy is much more compatable.

Have fun!

---

### Post by swong1 on 2005-12-18
It worked on the site I provided above! Wow, thanks Vorian.
But there is still no sound on movie preview site like king kong.

Feliz Navidad!

---

### Post by Vorian on 2005-12-18
Have you insalled mplayer for firefox or are you using realplayer?  If you are using mplayer, have you insalled all the codecs? [listed here]("http://www.ubuntuguide.org/#codecs")

---

### Post by swong1 on 2005-12-18
[QUOTE=Vorian]Have you insalled mplayer for firefox or are you using realplayer?  If you are using mplayer, have you insalled all the codecs? [listed here]("http://www.ubuntuguide.org/#codecs")[/QUOTE]

That was going to be my next question. I installed mplayer as per the instructions listed on the unofficial ubuntu site. I also installed all the codecs except w32codecs. Synaptic couldn't locate its whereabouts. Am I missing a repository? Is this the reason why I couldn't play wmv files?

---

### Post by Vorian on 2005-12-19
What repositories are you using?

check out the PLF repositories (Penguin Liberation Front)

[HERE]("http://wiki.ubuntu-fr.org/doc/plf")

---

### Post by swong1 on 2005-12-20
[QUOTE=Vorian]What repositories are you using?[/QUOTE]

I used the repositories described on the Unofficial Ubuntu page. 

[QUOTE=Vorian]
check out the PLF repositories (Penguin Liberation Front)
[HERE]("http://wiki.ubuntu-fr.org/doc/plf")[/QUOTE]

I followed the instructions on the site you provided. After doing

*sudo apt-get update*

I got the following error message (after all the packages has been updated):

> 
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

Should I be worried?

Also, I downloaded and installed w32codecs from the site. Synaptic indicates that I already have libdvdcss2 and sun-j2re1.5.
I finally have audio and video! Thanks Vorian. The snag is, I need to execute *killall esd* everytime before opening firefox to get sound on firefox. The side effect is, it kills all other bells and whistles and logout jingle. A minor trade off.

---

### Post by Vorian on 2005-12-20
Just remove the PLF repository from your sources, and use apt-get update.  

When I was using Hoary, I used official and backports only....  I forgot you are using Hoary, not Breezy.  

I highly recomend upgrading to Breezy, hardly any tweeking needed for the Inspiron 6000

here's the how-to if youre interested [http://www.ubuntuforums.org/showthread.php?t=74990]("http://www.ubuntuforums.org/showthread.php?t=74990")

Wifi, energy management, speed, and a few other features that make Breezy, well Breezy!

enjoy!:p

---

### Post by swong1 on 2005-12-21
[QUOTE=Vorian]Just remove the PLF repository from your sources, and use apt-get update.  

When I was using Hoary, I used official and backports only....  I forgot you are using Hoary, not Breezy.  

I highly recomend upgrading to Breezy, hardly any tweeking needed for the Inspiron 6000

here's the how-to if youre interested [http://www.ubuntuforums.org/showthread.php?t=74990]("http://www.ubuntuforums.org/showthread.php?t=74990")

Wifi, energy management, speed, and a few other features that make Breezy, well Breezy!

enjoy!:p[/QUOTE]


Cool! I was thinking about upgrading but was a little bit apprehensive. Thanks a lot Vorian. Have a nice day/Christmas/Holiday...

---

### Post by Vorian on 2005-12-23
[QUOTE=swong1]Cool! I was thinking about upgrading but was a little bit apprehensive. Thanks a lot Vorian. Have a nice day/Christmas/Holiday...[/QUOTE]

Happy Christmas to you too!

---

