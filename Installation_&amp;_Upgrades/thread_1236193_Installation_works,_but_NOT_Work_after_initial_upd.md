---
title: "Installation works, but NOT Work after initial update: blank blu screen after login"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by tomasrey88 on 2009-08-10
Hi,

I installed xubuntu 9.04 on my laptop dell latitude cpi d300xt 128 mb ram, 6.5 gb hd, and 300 mhz PII. It worked fine after intial install. However, after the initial update and reboot, it would no longer work. I could get as far as the login screen, but after login all I get is a blank blue screen. What should I do? 

I read somewhere that there is a bug in ubuntu that with acpi power management switched on, one would experience logon failure. If so, how do I turn off acpi power management. Please, if I have to tinker in the command line, please let me know exactly what to type in or I will be lost as I am a noob. Thank you. 

If acpi power management is not a problem, then what is and what is the fix? Thanks.

Much appreciation,
:P

I've already turned off power management in bios.
I tried to log into failsafe gnome, but was not able to, but it did log me into the terminal. So, what commands do I use to fix it?  Thanks.

---

### Post by P4man on 2009-08-10
Minimum requirements for Xubuntu are:

Minimum requirements

    * 333 MHz processor
    * 192 MB of system memory (RAM) 

Dont worry about the cpu speed, but you probably just dont have enough RAM.

With 128Mb, you might want to try puppy linux [http://www.puppylinux.org](http://www.puppylinux.org) instead. OR even Damn Small Linux (just be prepared for something of a shock lol).

---

### Post by tomasrey88 on 2009-08-10
No, it says on the xubuntu website: 1.5 gb hd and 128 mb ram are the minimum. It was working fine until after the update. there is a program/package after the update that caused this. 

xubuntu website:
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

I have read the forum and others have got ti running with just 128 mb ram just fine. 

Please advise. 

Thanks,
:P

---

### Post by P4man on 2009-08-10
hmmm.. okay, well, im no xubuntu expert, but try this:
after logging in, press control+alt+F1. That will (hopefully) give you a terminal. Log in there (if needed) and type:

```
cat /var/log/messages
```

See if it throws some errors that can help us further.
To return to the gui, normally you press control+alt+F7. I suspect that wont work in your case, but it doesn't hurt trying. 

More stuff to try from the console:

```
sudo /etc/init.d/xdm restart
```

that should restart the desktop manager (xfce in your case). It may also generate an error that might help us further.

---

### Post by tomasrey88 on 2009-08-10
cat /var/log/messages yielded many pages of stuff, but I can't cut and paste it in here and I can only see the last page. All the previous pages are invisible. The up arrow key doesn't seem to work in this version of terminal. From what I can see, there's no errors nor anything out of the ordinary. An example is: 
Aug 10 11:47:35 panda-pandamonium kernel: [ 63.994114] eth0: found link beat
Aug 10 11:47:35 panda-pandamonium kernetl: [ 63.994154] eth0: autonegotiation complete: 100baseT-FD selected

sudo /etc/int.d/xdm restart yielded 
sudo: /etc/init.d/xdm: command not found
**I probably typed this command in wrong. What did I do wrong?**

> **P4man said:**
> hmmm.. okay, well, im no xubuntu expert, but try this:
after logging in, press control+alt+F1. That will (hopefully) give you a terminal. Log in there (if needed) and type:

```
cat /var/log/messages
```See if it throws some errors that can help us further.
To return to the gui, normally you press control+alt+F7. I suspect that wont work in your case, but it doesn't hurt trying. 

More stuff to try from the console:

```
sudo /etc/init.d/xdm restart
```that should restart the desktop manager (xfce in your case). It may also generate an error that might help us further.

---

### Post by P4man on 2009-08-10
Like I said, Im not exactly a xubuntu expert and I dont have it installed here.. so i can be wrong at times :p

Not sure which login manager xubuntu uses, I figured it would be xdm, but perhaps its gdm then, just like in ubuntu. In which case, your command would be:

```
sudo /etc/init.d/gdm restart
```

btw, you can use TAB key for autocomplete. That way you almost can't make typing errors. For instance, type:

sudo /et  <tab> and it will complete to:
sudo /etc/     continue typing:
sudo /etc/ini  <tab> nothing happens, because there is probably more than 1 possibility. press <tab> again until you see all choices.

Not all that useful perhaps here, but get used to it, you'll be thankful later :)

---

### Post by tomasrey88 on 2009-08-11
I typed that and all I got was a black screen with a single blinking cursor.

Anybody knows how to fix this? I'll mail you a Michael Jackson or Elvis Presley CD....

---

### Post by tomasrey88 on 2009-08-12
Thanks P4man,

I resisted installing Puppy Linux because I was afraid that it would be difficult to install as I heard that all Linux stuff except for Ubuntu is difficult to install. Boy, was I wrong! I couldn't get Xubuntu to work after the update on my laptop. Before the update, I tried to get my wireless card to work, but it did not work. It was also complicated to install wireless devices with Xubuntu. I tried for a week to do this, without success.

Now, out of desperation, I went to the Puppy Linux website. Installation was more difficult than Xubuntu, but they had very thorough documentation with screen shots on their website, so it went O.K. Then, the wireless was a breeze to get working. When Xubuntu was working before the update, it was really slow and the mouse cursor was real jumpy. However, with Puppy Linux, the graphics movements were smooth and everything was just as fast as a new computer. Wow! 

My assessments;

Ubuntu: great for desktops and old but not ancient computers. I have Ubuntu 8.04 running on a 512 MB, 700 mHz, 20 GB HD computer and it works fast, like a new computer. Two Thunbs up :P

Xubuntu: supposed to be for ancient computers and laptops because the desktop environment is lighter than Ubuntu. That is the theory, but in practice it has failed its goals. That's because it is still too heavy to run fast on ancient computers and the set-up procedure for wireless is way too complicated for the general public (noobs) to handle. Two Thumbs down :confused:

Puppy Linux: succesds where Xubuntu fails. while not as easy to set-up as Xubuntu, the website documentation was thorough and easy to understand. The wireless set-up procedure was a breeze and I had wireless up and running in minutes! However, this is not suitable for any graphics applications as the graphics were grainy and rough. I think that this handling of graphics is probably a necessity because the entire OS and apps bundled with it are designed to run in less than 128 MB of RAM. Puppy is suitable for casual use such as websurfing, email, and text editing. However, it is not suitable for any heavy duty use. I would use Ubuntu for that. I have Puppy Linux running on a 128 MB, 300 mHz, 6 GB HD computer. Two Thumbs up :guitar:

Have fun guys,
:lolflag:

---

### Post by P4man on 2009-08-12
Ive used puppy for a while when I was stuck with an old laptop (similar specs as yours). I was quite impressed by it. its not as polished as ubuntu, but it gets the job done and makes an old machine really fly. Kinda funny to boot a 6-7 year old laptop and get on the internet like 5x as fast as friends with brand new vista laptops with 20x more ram and 5x the cpu speed :p

Anyway, good luck with it!

---

### Post by tomasrey88 on 2009-08-13
If it weren't for the fact that Puppy runs everything in root, Puppy would be perfect.

---

