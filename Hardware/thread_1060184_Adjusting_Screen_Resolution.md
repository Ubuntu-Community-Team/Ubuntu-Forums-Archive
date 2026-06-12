---
title: "Adjusting Screen Resolution"
date: 2009-02-04
forum: Hardware
---

### Post by Da Mangaka on 2009-02-04
So I have re-installed Ubuntu 8.4 after a mistake I did, and I am back basically on the beginning: my screen resolution is around 640x480 and my screen supports up to 1024 but I can't change it.
It's a Dell by the way, but I don't know what Video Card it has.
I remember having installed a nvida card the first time I fixed this problem but I am not sure where I got that info

Another thing is that I got into terminal and type this:

```
sudo dpkg-reconfigure xserver-xorg
```

where I configure Mouse, Keyboard and Screen but I don't see any change. My fear is that since I did some changes before the dpkg, it will go into low resolution mode or just simply a black screen.
How do you fix this problem? Or how do you make your computer detect your card?
Is is safe to restart to make it better?

---

### Post by cariboo on 2009-02-04
Go to System-->Administration-->Hardware Drivers and activate the recommended restricted driver for you video card and any other hardware that is listed there.

Jim

---

### Post by Da Mangaka on 2009-02-04
< _<
There isn't anything in there
It's blank

```
No proprietary drivers are in use in this system
```

Now what? . _.;

---

### Post by Gridpoet on 2009-02-04
yeah, i'm having similar problems. I've been scouring the net and keep finding the: > "sudo dpkg-reconfigure -phigh xserver-xorg"

command thrown around, but when i run this in terminal under 8.10, at least on my system, it does absolutely nothing...

i would love to see Ubuntu add some more manual configuration options for resolution that are time based... so at least if someone tries a resolution that isn't supported it will auto reconvert... because at the moment this is the problem i've had on 2 different computers...

i've tried to manually set my res. , but i admit i just have no idea how to format the commands... 

i would use ENVY, but i;m pretty sure this laptop is using the intel extreme graphics adapter... which to be honest is kind of strange that Ubuntu didnt pick it up automatically... i figured i would have no problem with it... (because my desktop PC ATI 4850 has been a nightmare >_<)

any help would be appreciated

...sorry for the wind-baggery

---

### Post by Da Mangaka on 2009-02-05
Turns out that I only needed to reset the comp after doing that command line...
The thing was that I was unsure to do so since the last time I did something alike (try to solve this problem), it went all black < <


About your problem (yes, you poster up from me), I don't know how different is 8.4 from 8.10
You could try what I did (the commandline I have in my original post), reset/turn off the comp and see if it works

Thanks again ~:KS

---

