---
title: "VirtualBox answer to driver probs?"
date: 2009-06-07
forum: Hardware
---

### Post by Ethelbert2 on 2009-06-07
[COLOR="DarkGreen"][FONT="Georgia"]OK I have given Linux a four week run recently for the second time (tried in 2007).  But once again I have problems with hardware.  I am willing to try searching for knowledge and battling with installation instructions though it is headbanging at times - and I **want** Linux to work for me. Specifically I cannot find drivers for a Canon i965 printer, an Epson 3170 scanner and have trouble with the Radeon video card (4350) though maybe that is solvable.  Modems are troublesome too.

I also have a problem with some software, notably OCR stuff and Photoshop which I use (I know GIMP does lots but not the same).

So my question is - must I give up on Linux for two more years,(?) because I am certainly not going to buy new hardware (it's a waste and I can't afford it anyway). And my second question is - could using VirtualBox solve all that? which is to say would it work inside an Ubuntu install well enough to use the Win drivers and software?? What is people's experience (honestly now - not anti-Microsoft partisanship which I understand but which colours too many "just as good as..." replies.) 

What's the point you might say - lettng me feel Ubuntu is workable enough to use is the answer. I am not a perfectionist - just want it to go.[/FONT][/COLOR]  Thanks

---

### Post by albinootje on 2009-06-07
> **Ethelbert2 said:**
> Specifically I cannot find drivers for a Canon i965 printer, an Epson 3170 scanner and have trouble with the Radeon video card (4350) though maybe that is solvable. 

Which Ubuntu release are you using ? Jaunty/9.04 or Hardy/8.04 ?

A quick search shows this : [http://ubuntu.flowconsult.at/en/epson-3170-installation/](http://ubuntu.flowconsult.at/en/epson-3170-installation/)
And this : [http://www.openprinting.org/show_printer.cgi?recnum=Canon-i965](http://www.openprinting.org/show_printer.cgi?recnum=Canon-i965)

And at work I have a scanner which is not supported by Linux yet, working in a MS-Windows guest VM with VirtualBox.

---

### Post by Ethelbert2 on 2009-06-07
[COLOR="DarkGreen"][FONT="Georgia"]Well I did not try, or even discover before, the Epson solution you post (thanks). [That comes out of the blue after chasing around for ages trying to find one!]

I did try and work things for the printer with the Gutenprint stuff but it was too complicated and I got no good results - you are supposed to be able to find i965 in the list but I could not, even though the page posting says it is included. Perhaps I did not do it correctly.

I then tried a commercial Linux print driver you can buy from Germany (on 30 day trial)  - the name escapes my mind for the moment - but though it was promising it did not work quite right either - colours looked muddy and the test alignment pages printed only the first of two before telling me the test was over. (Tried this twice).

I took 9.04 off my main computer but still have 8.10 on an old one (I cannot use the new distribution because the card is a Radeon 7000 which will not work in 9.04 I discovered (after about a fortnight of struggling with numerous distributions).)  So I will have a go with that in my next spare moments and re-try the printer. 


There is a thread discussing the ATI drivers for newer Radeon cards in 9.04 which would be suitable for the main computer but I found that discussion extremely overpowering - I am no programmer or expert even after days of messing around.  I did not really understand it. 

I think I am losing energy on this.

[/FONT][/COLOR]

---

### Post by albinootje on 2009-06-07
> **Ethelbert2 said:**
> Well I did not try, or even discover before, the Epson solution you post (thanks). [That comes out of the blue after chasing around for ages trying to find one!]


No problem. I used the following in the most popular search-engine :
```

"epson 3170" ubuntu

```
After using that it was the first link on the first page of results.  The "" signs usually help a bit to filter out other possibilities.

I would try Ubuntu 8.10 if I were you, because some of the new problems with the ATI and Intel videocards are really not so easy to get around and can be time consuming.

---

### Post by andyprough on 2009-06-07
> **Ethelbert2 said:**
> [COLOR=DarkGreen][FONT=Georgia]And my second question is - could using VirtualBox solve all that? which is to say would it work inside an Ubuntu install well enough to use the Win drivers and software?? What is people's experience (honestly now - not anti-Microsoft partisanship which I understand but which colours too many "just as good as..." replies.) [/FONT][/COLOR]

Yes, I've got an Epson printer and an HP all in one printer/scanner working great in WinXP under VirtualBox on Ubuntu 9.04. Took a few minutes to set it all up properly (had to give myself privileges with the vbox usb group in order to run the printer). Give it a try, you'll be surprised, it seems to work at native speed for printing and scanning.

---

### Post by Ethelbert2 on 2009-06-08
[COLOR="DarkGreen"][FONT="Georgia"]Thanks again to Albinootje.  Just to point out I am not so silly as not to have looked for the driver but the advice I found on various sites and forums all told me that Epson was a problem, that the 3170 was unsupported and that there were no Epson dirvers.  And the main Epson site I tried (UK I suppose) did not have them. 

I guess that is a problem with Googling etc - even the obvious places like the Ubuntu forum do not always give you the right hits and can even send you in the wrong direction. Incidentally a Google in the UK does not always give the same as in the Netherlands which I guess is your location. 

Anyway I now have something to try.  Still not able to make the printer work but the VirtualBox info above is encouraging especially if it can work on 9.04.

My real hankering is to use the 64bit version, since my main processor will suport it. I gave 9.04 Ubuntu 64 a short run, but that really did prove too difficult for my skills - though if a Win32 Virtual Box or other emulation will work inside it might just do the trick..... 
[/FONT][/COLOR]

---

### Post by albinootje on 2009-06-08
> **Ethelbert2 said:**
>  Incidentally a Google in the UK does not always give the same as in the Netherlands which I guess is your location. 

Yes... but I'm avoiding [http://www.google.nl](http://www.google.nl) like a plague, and I'm using Scroogle and Google UK exclusively.
> 
Anyway I now have something to try.  Still not able to make the printer work but the VirtualBox info above is encouraging especially if it can work on 9.04.

Good luck!
> 
My real hankering is to use the 64bit version, since my main processor will suport it. I gave 9.04 Ubuntu 64 a short run, but that really did prove too difficult for my skills - though if a Win32 Virtual Box or other emulation will work inside it might just do the trick..... 


I'm avoiding 64 bit as I find using 32 bit on various machines much easier to handle (installing/configuring/maintaining).

---

