---
title: "Intel GMA 950 and Opengl don't get along."
date: 2008-10-30
forum: General Help
---

### Post by CraymelCage on 2008-10-30
I have a a problem with the on board intel chipset and opengl.

[[IMG]http://img252.imageshack.us/img252/9928/screenshotow9.th.png[/IMG]](http://img252.imageshack.us/my.php?image=screenshotow9.png)[[IMG]http://img252.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

When anything uses opengl like I have mplayer using it in here the video will over lap and leave a trail behind when dragging the window. I can simply not use it for mplayer (but the crisp and clear subtitles make me wanna stay). I also use zsnes mednafen and pSX and they all use open gl. Are there any fixes for this problem?

---

### Post by stoodleysnow on 2009-01-24
This is exactly the same problem I have. Can anybody please shed some light on the situation? It also extends for me to Compiz Fusion (some features crash or fail to appear) and Wine (clashes with anything else on the screen)

---

### Post by CraymelCage on 2009-04-09
Well I'm going to bump this considering my problem hasn't magically disappeared. I have discovered that this problem only occurs when having any form of compiz affect on. There is a problem that also occurs with xv video drivers and compiz with this graphics card. If there is any thing with a shadow over a video the shadow is replaced with a blue (very bright blue) colour. I'm using ubuntu 8.10 on a acer aspire 5610 with the same gma chipset. If anyone knows anything! I beg you! Please share your knowledge.

---

### Post by CraymelCage on 2009-04-15
bumpers!

---

### Post by VonSpyder on 2011-09-13
sadly it seems there just isnt any support for the gma950...the most common vid card in netbooks....really funny when youre running Ubuntu Netbook edition and its not really equipped to handle a netbook. For my desktop Ubuntu is second to none. For netbooks, for the time being, stick with windows.

---

### Post by gandaran on 2011-09-13
> **VonSpyder said:**
> sadly it seems there just isnt any support for the gma950...the most common vid card in netbooks....really funny when youre running Ubuntu Netbook edition and its not really equipped to handle a netbook. For my desktop Ubuntu is second to none. For netbooks, for the time being, stick with windows.
well, I don't agree, I have a Toshiba (Intel Atom 1.6) netbook with Intel GMA 950 graphics and is running Ubuntu 11.04 desktop version with the unity desktop working perfectly, no problems at all.

---

### Post by VonSpyder on 2011-09-13
> **gandaran said:**
> well, I don't agree, I have a Toshiba (Intel Atom 1.6) netbook with Intel GMA 950 graphics and is running Ubuntu 11.04 desktop version with the unity desktop working perfectly, no problems at all.

Thats fine. Go run something that requires opengl. Go ahead Ill wait. ;)

---

### Post by gandaran on 2011-09-14
> **VonSpyder said:**
> Thats fine. Go run something that requires opengl. Go ahead Ill wait. ;)
okay, name one application I should try then I will do it.
I think google earth requires opengl and runs very well on the Intel graphics on the netbook and this desktop too.

---

### Post by VonSpyder on 2011-09-14
> **gandaran said:**
> okay, name one application I should try then I will do it.
I think google earth requires opengl and runs very well on the Intel graphics on the netbook and this desktop too.

Try the following:
CairoDock (WITH opengl not the nonopengl one)
Supertux 2
GLMatrix screensaver

---

### Post by gandaran on 2011-09-14
> **VonSpyder said:**
> Try the following:
CairoDock (WITH opengl not the nonopengl one)
Supertux 2
GLMatrix screensaver
well, for cairo dock I know it _runs fine_ as I used to have it installed before on 10.10 but now on 11.04 with unity I don't want to use cairo dock anymore, as for supertux 2 it's not in software center (only supertux 2D) so I wont be installing the app also searching for GLMatrix screensaver in synaptic I get 'exscreensaver-gl' but don't know if it's the same thing you are talking about.

---

### Post by VonSpyder on 2011-09-14
> **gandaran said:**
> well, for cairo dock I know it _runs fine_ as I used to have it installed before on 10.10 but now on 11.04 with unity I don't want to use cairo dock anymore, as for supertux 2 it's not in software center (only supertux 2D) so I wont be installing the app also searching for GLMatrix screensaver in synaptic I get 'exscreensaver-gl' but don't know if it's the same thing you are talking about.


Cairodock has two versions though, one is opengl and one is non-open gl. they both look identical. Supertux 2 is indeed in the software center, im looking right at it. and the GLmatrix screen saver giving you that message is my point: GMA 950 does NOT have open gl and without it Ubuntu is pretty well neutered.

---

### Post by gandaran on 2011-09-15
> Cairodock has two versions though, one is opengl and one is non-open gl. they both look identical
I know that, there was both options in the applications menu and I did run the cairo GL on Ubuntu 10.10 without problems.
```
 Supertux 2 is indeed in the software center
```
I will install over the weekend to try, it's 59 MB download, I cant do it at home as my mobile internet plan has a monthly 2GB cap.
I will let you know how it works then.

to tell the truth when I bought the netbook I was a bit disappointed as it would work nicely with Ubuntu releases up to 9.04 only but when Ubuntu started using the new Intel drivers problems started, Ubuntu did not run on my netbook anymore freezing all the time, I read somewhere updating Bios would fix the problem with Intel drivers, I did the update and that small netbook single core atom 1.6 still surprises me today with how well Ubuntu works on it.

---

### Post by gandaran on 2011-09-16
supertux 2 runs fine here to.
but now I'm a bit confused, I checked my netbook specifications online and it shows GMA 950 graphics and always thought it was the 950 card but lspci shows something different
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

``` 
I will have to find out why.

---

### Post by VonSpyder on 2011-09-16
> **gandaran said:**
> supertux 2 runs fine here to.
but now I'm a bit confused, I checked my netbook specifications online and it shows GMA 950 graphics and always thought it was the 950 card but lspci shows something different
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

``` 
I will have to find out why.

check in your supertux 2 settings and make sure open gl is enabled (as it can be switched to other rendering) if it runs with open gl rendering then your pc somehow has the answers to this problem which has plagued netbook users for years.

---

