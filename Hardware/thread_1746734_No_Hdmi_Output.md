---
title: "No Hdmi Output"
date: 2011-05-02
forum: Hardware
---

### Post by cochoa on 2011-05-02
Using the newest version of ubuntu, 11.04. Note I am no tech genious and am completely new to Linux and ubuntu, I know nothing basically and am trying to learn. I cannot figure out how to get the HDMI port on my laptop to output video to my tv, it was working ok, just grainy and distorted like everything was out of sync and creppy looking. Until I downloaded the NVidia drivers, now no display at all. All i need is Video and Audio out of my HDMI port, 

OS: Ubuntu 11.04
Video Card: Nvidia GeForce Go 7600

I managed a clean wipe of this computer ealier today (first tried DBAN, when that failed to work, I used KillDisk) so this is a completely new system basically. So be gentle with me and apply lots of stupid people terms. lol.

---

### Post by barthus on 2011-05-02
This is a small note only (I cannot help you because I still have Ubuntu version 10.10): A nice little program, which I use for handling the HDMI and VGA outputs, is disper:

[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

However, I don't know if it runs also under 11.04, but I guess so.

With respect to your problem: somewhere, there must be the preferences for audio and screen. Did you play around with all possible configurations?

---

### Post by cochoa on 2011-05-02
Like I said before I am all but computer illiterate lol. barth this is a kool program but how do i get it to work. I know, i know, but i said i was learning. bare with me please.

---

### Post by barthus on 2011-05-02
> **cochoa said:**
> Like I said before I am all but computer illiterate lol. barth this is a kool program but how do i get it to work. I know, i know, but i said i was learning. bare with me please.

Okay, before you install some other program I would say that you try first with the screen and audio settings. Try to find the nVidia settings and the audio ones (should be somewhere in the menu). In the nVidia settings you will find then the option to change the screen. Try out ... then tell us.

---

### Post by cochoa on 2011-05-02
Hot dam, Go figure i listen to a complete stranger and it works perfectly :) Beats the crap out of windows support lol thanks Bart.

---

### Post by barthus on 2011-05-02
> **cochoa said:**
> Hot dam, Go figure i listen to a complete stranger and it works perfectly :) Beats the crap out of windows support lol thanks Bart.

:wink: Cheers.

---

### Post by cochoa on 2011-05-02
Ok so i need to do a bit of fine tunign to get the resolution set up right i currently have about 3/4 of the screen vise able on my laptop and everything on the tv screen is really tiney still its a start and a darn good one if i do say so myself.

Also i wanted to test some stuff on youtube. but Mozilla says i cant find suitable plug-ins got any advice on that one? thanks again barthus

---

### Post by barthus on 2011-05-02
Good!

******************************************************

If you feel enough advanced (is also some good training): Disper

You can install disper as follows:

Open a shell and type:

1. sudo     add-apt-repository ppa:wvengen/ppa
2. sudo apt-get update
3. sudo apt-get install disper

Then you can install 3 new starters in a task bar (google how one is doing this) with some commands. In my case, I have

```
disper     --displays=DFP-0 -s (Laptop)
disper --displays=DFP-1 -s (HDMI)
disper     --displays=CRT-0 -s (VGA)
```You get a list of the display identifiers (DFP-0 ...) by typing 
```
disper -l
```into a shell. Note that the screens must be all connected for obtaining the correct identifiers. You only use your identifiers.

So, what does all this mean? => By clicking onto one of the starters, you switch the screen. Only one is always active.


Cheers.

---

### Post by barthus on 2011-05-02
> **cochoa said:**
> Also i wanted to test some stuff on youtube. but Mozilla says i cant find suitable plug-ins got any advice on that one? thanks again barthus

Go to the Software center or whatever it is called. Search for a program that is called Adobe flash. Install it. Then you can watch YouTube videos.

---

### Post by cochoa on 2011-05-02
> **barthus said:**
> Good!

******************************************************

If you feel enough advanced (is also some good training): Disper

You can install disper as follows:

Open a shell and type:

1. sudo     add-apt-repository ppa:wvengen/ppa
2. sudo apt-get update
3. sudo apt-get install disper

Then you can install 3 new starters in a task bar (google how one is doing this) with some commands. In my case, I have

```
disper     --displays=DFP-0 -s (Laptop)
disper --displays=DFP-1 -s (HDMI)
disper     --displays=CRT-0 -s (VGA)
```You get a list of the display identifiers (DFP-0 ...) by typing 
```
disper -l
```into a shell. Note that the screens must be all connected for obtaining the correct identifiers. You only use your identifiers.

So, what does all this mean? => By clicking onto one of the starters, you switch the screen. Only one is always active.


Cheers.

I hate to quote your response in its entirety, how do i open a shell. Like i sadi I am new to Linux and more than willing to learn.

---

### Post by barthus on 2011-05-02
> **cochoa said:**
> I hate to quote your response in its entirety, how do i open a shell. Like i sadi I am new to Linux and more than willing to learn.

In this case I suggest you to google key words like 'shell', 'terminal' and 'basic unix/linux commands' before you do anything with the shell. It takes about 1/2 day to obtain an overview and specific feeling.

Switching to Linux means also some little investment into learning the basics of shell commands.

---

### Post by barthus on 2011-05-02
I forgot to say that you should read something about the following commands:

sudo
apt-get
dir
cp
rm
etc.

---

