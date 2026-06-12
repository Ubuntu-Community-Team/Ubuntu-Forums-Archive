---
title: "Wide Screen"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by AmpersUK on 2008-02-27
I have a Fujitsu-Siemans Lifebook (P Series) and am having problems with the wide screen.

A window which is full size, such as trying to set up Evolution, does not fit, and the boxes for making the next move are off the screen.

It is a standard model but I don't know what graphics this computer tablet notebook uses.

If there is anyone else who has a P1510 (W82) model, I'd really appreciate some help. Also if you have managed to get the touch screen working.

I started using Linux last week so am pretty much a beginner.

Ampers

---

### Post by oldsoundguy on 2008-02-27
run in terminal:

sudo lshw

that will give you your hardware list and tell you what display chip is on board.

That is needed before suggestions can be made.

---

### Post by AmpersUK on 2008-02-28
I haven't got wifi activated yet and had a long list of info around two video sections so thought I would contact Fujitsu-Siemens direct. Here is their reply to me.

Hi,

Working on the premise you are referring to a Lifebook P1510. The graphics controller is a Intel 915GMS controller.

Kind regards,

UK Helpdesk

---

### Post by Yellow Pasque on 2008-02-28
do a search on a program called 915resolution. You can install the program on Ubuntu with:
```
sudo apt-get install 915resolution
```
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

### Post by AmpersUK on 2008-02-28
Thank you for your assistance. It is greatly appreciated.

---

### Post by AmpersUK on 2008-02-28
I still seem to have a problem and hope someone can help.

I did as you say as follows:

ampers@Notebook:~$ sudo apt-get install /tmp/915resolution/915resolution-0.5.3/915resolution
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package
ampers@Notebook:~$

So: sudo apt-get install /tmp/915resolution/915resolution-0.5.3/915resolution is the address of the file but I get "Couldn't find..."

I did say I was an absolute beginner but from previous computer experience I would guess that my problem here is one of two things.

1. I need more of an address before "/tmp" as this is not the first level from "ampers". Perhaps I could put: install ~915resolution ?

2. The file name of 915resolution needs a fullstop and further letters after it which aren't shown on the computer. In Windows I guess itwould be ".exe"


Ampers.

---

### Post by Yellow Pasque on 2008-02-28
:? Do you not have internet access on the computer? What version of Ubuntu are you using? You should be able to install by typing:
```
sudo apt-get install 915resolution
```

---

### Post by oldsoundguy on 2008-02-28
either no internet access or the repositories have not been set up or set up properly.  Trying to install from your optical drive.

The single most helpful site for basic set up and adding programs:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by AmpersUK on 2008-02-28
I did try sudo apt-get install 915resolution first on my P series.

However I worked it out.

I typed in

cd ~/Downloads/915Resolution first to get into the right directory and then typed in

sudo apt-get install 915resolution

And it all worked like a dream.

Now to contact F-S again and try and find out the actual make and model of the monitor. I am still getting the evolution program going off the bottom of the screen

Did you manage to get Wireless working with your P1510 and, if so, can you give me some pointers.

I have to go to Paris and would like to get it working by then (16th March).

Ampers.

---

