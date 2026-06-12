---
title: "Compiz Fusion Problems"
date: 2008-09-29
forum: General Help
---

### Post by linuxnublol on 2008-09-29
I have followed this guide: [http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-ati-mobility-radeon-9200)
both page one and page 2, but I am still not able to use compiz fusion..well at least the features of it.

What I do have:
Advanced Desktop Effects Settings
Emerald Theme Manager
Compiz Fusion Icon

I have set it so that Compiz Fusion Icon runs on start-up...
Am I missing something?

Hopefully it's a simple solution.

---

### Post by Therion on 2008-09-29
The best tutorial I've yet found on [Getting Compiz Up and Running](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074).  You've got CCSM installed, so that's good...  Follow the rest of the guide and see if it helps.


Edit: Improved the link.

---

### Post by linuxnublol on 2008-09-29
> **Therion said:**
> The best tutorial I've yet found on [Getting Compiz Up and Running](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074).  You've got CCSM installed, so that's good...  Follow the rest of the guide and see if it helps.


Edit: Improved the link.

Bare with me if you will.
I just loaded ubuntu 8.04 last night (full install erased xp)
What is CCSM?

EDIT1: never mind It says what it stands for in the first paragraph of the guide you gave me :P

Edit2: The guide you gave me showed me how to choose which efects I wanted...My problem is that even if I choose those the effects still wont work...neither will any of the shortcuts (e.g. ALT-CTRL-LEFT/RIGHT)

---

### Post by Therion on 2008-09-29
Do you have either the open-source or Restricted Driver installed for your video card or graphics chipset?

For that matter what video card or graphics chipset do you HAVE?  You'll need a graphics solution that supports Compiz AND you'll need the correct driver installed before you can run Compiz.

---

### Post by Kevbert on 2008-09-29
Welcome to Ubuntu.
To check what card you have go to Applications-Accessories-Terminal and enter
```
lspci
```
The display card should be the last item displayed.  Compiz will work with most ATI, Nvidia and Intel cards (but not VIA).
Another thing you could try is to run [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check").  This will give us an idea of the problem. It may be that you're using the wrong display driver or don't have 3d graphics acceleration enabled.

---

### Post by linuxnublol on 2008-09-29
ok I opened up my computer and here is my graphic card: 
ATI RAGE 128 Pro


Edit: using Kevbert's way it displayed:
 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF

---

### Post by Therion on 2008-09-29
> **linuxnublol said:**
> ok I opened up my computer and here is my graphic card:  ATI RAGE 128 Pro
Compiz will only work with graphic cards with at least 64 MB of memory.  Yours has 32MB.

---

### Post by linuxnublol on 2008-09-29
> **Therion said:**
> Compiz will only work with graphic cards with at least 64 MB of memory.  Yours has 32MB.

I have another one let me check the model its nVidia I know that... give me a sec here..


EDIT: alright here it is: 
 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by Therion on 2008-09-29
> **linuxnublol said:**
>  VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
Alright... Well, while that's no barn-burning card, it will support Compiz.

It's a huge improvement over that ATI "card".

---

### Post by linuxnublol on 2008-09-29
> **Therion said:**
> Alright... Well, while that's no barn-burning card, it will support Compiz.

It's a huge improvement over that ATI "card".

LMAO!
Well what are your suggestions now?
I have installed the driver...it automatically detects it...and it says its in use..sooo..what do you suppose I try now?

---

### Post by Therion on 2008-09-29
Card is installed and you're using the Restricted Driver for it, yes?  

If so, then go back to the tutorial in my previous post and start from there.  Now that you're using a card that *supports* Compiz, Compiz should start working once you've got it set up.

---

### Post by linuxnublol on 2008-09-29
wow!
I just found out the problem.

Thanks to you.
I clicked on your Ultimate Edition Link (in your sig).
I looked at the screen shots (drivers ect..)
I saw they were using EvnyNG. So I thought I might as well download it.
So I download and install it..I click on Nvidia and it finds my graphic card drivers ect...It says I need to restart my computer and when I log back in BAM! It was all ready to go. So now Compis-Fusion works!
Thank you so much!
and I'll think about installing Ultimate Edition...what makes it so different from the regular Ubuntu?

---

### Post by Therion on 2008-09-29
> **linuxnublol said:**
> wow!
I just found out the problem.

Thanks to you.
I clicked on your Ultimate Edition Link (in your sig).
I looked at the screen shots (drivers ect..)
I saw they were using EvnyNG. So I thought I might as well download it.
So I download and install it..I click on Nvidia and it finds my graphic card drivers ect...It says I need to restart my computer and when I log back in BAM! It was all ready to go. So now Compis-Fusion works!
Thank you so much!
and I'll think about installing Ultimate Edition...what makes it so different from the regular Ubuntu?
Glad you got it working.  All EnvyNG does, though, is install the driver for your video card... Be warned, you'll need to reinstall it (the driver) if and when you receive a kernel update.

As for Ultimate Edition... Most people think it's nothing more than plain vanilla Ubuntu with a new theme applied and a lot of additional software installed.  It's not.  Yes, Ultimate Edition is Ubuntu-based (version 1.9 is Hardy Heron-based) has a different theme applied and definitely has a LOT of additional software pre-installed, but then it's creator applies his secret-sauce to it.  It's basically hand-tweaked from the ground up and super-charged at the coding level.  It's like Ubuntu on *steroids*.

I suggest you give it a go sometime.

---

### Post by linuxnublol on 2008-09-29
> **Therion said:**
> Glad you got it working.  All EnvyNG does, though, is install the driver for your video card... Be warned, you'll need to reinstall it (the driver) if and when you receive a kernel update.

As for Ultimate Edition... Most people think it's nothing more than plain vanilla Ubuntu with a new theme applied and a lot of additional software installed.  It's not.  Yes, Ultimate Edition is Ubuntu-based (version 1.9 is Hardy Heron-based) has a different theme applied and definitely has a LOT of additional software pre-installed, but then it's creator applies his secret-sauce to it.  It's basically hand-tweaked from the ground up and super-charged at the coding level.  It's like Ubuntu on *steroids*.

I suggest you give it a go sometime.


Could I burn Ultimate Edition to a CD-R? I don't have any DVD-R's at the moment..

---

### Post by Therion on 2008-09-29
> **linuxnublol said:**
> Could I burn Ultimate Edition to a CD-R? I don't have any DVD-R's at the moment..
In short, no.  If we could squeeze it all on to one CD, it wouldn't be **Ultimate Edition**.  

In point of fact, it's a real effort to contain all of it's a-- kicking superiority on just one *DVD*.

The UE Themes Pack you'll notice is a separate download.  It's too much to experience, all at once, for mere mortals so we had to split it up into two downloads.  It's for your own protection.

---

### Post by linuxnublol on 2008-09-29
lol alright...well I'll see if I can provide a mirror for you guys.

---

