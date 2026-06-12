---
title: "Screen resolution"
date: 2009-04-24
forum: Hardware
---

### Post by utnr6 on 2009-04-24
now what i can't understand is how stupid it is to search this forum... how are there so many posts and no real answers.
ive used ubuntu now for about the past 3 months and i'm just now starting to get really pissed

why will my screen resolution with jaunty not stay at 1280 800

please someone answer me that very basic/simple question

its a laptop intel chipset 4 series and core 2 duo and all that stuff and i just want my screen to stay the same

i'm dual booting w/ vista and im not about to install this crap or fix grub for the 20th time today

please, i know someone has the answer and searching this **** forum is worthless

---

### Post by dizzie on 2009-04-24
With an attitude like this you wont get far. 

However ; Try reconfigure your card (Got the right driver installed?) Fix Grub aswell, and you are good to go. 

I myself runs Both console and X in 1280x800 on my laptops and 1440x900 on my desktop.

Happy hunting :-)

---

### Post by prshah on 2009-04-24
> **utnr6 said:**
> 
why will my screen resolution with jaunty not stay at 1280 800


Depends on a lot of factors (Screen native resolution, Video memory, driver etc). However, ignoring all other factors, try appending the lines in red in your /etc/X11/xorg.conf file; open a terminal, and give this command to edit the file```
sudo cp -p /etc/X11/xorg.conf ~ && sudo vi /etc/X11/xorg.conf
```; then find the relevant section as below and add the lines in red> ```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
[color=red]        DefaultDepth    24
        SubSection      "Display"
                Modes   "1280x800"
        EndSubSection[/color]
EndSection

```

Post back if you run into trouble with the above.

---

### Post by utnr6 on 2009-04-24
my friend, i think you have saved my life

linux has decided to be my friend

so far so good, login screen and desktop both look good!!!  you should put that up on some of those intel graphics posts... i think other people are needing this

---

### Post by steinaro on 2009-04-24
Normally a better way to start searching for answers is through Google. That's what lead me to find the answer for this problem when I first installed Ubuntu. Usually the best threads are filtered through google, or whatever search engine you prefer.

I agree with you, it isn't easy to find something specific in this mess.:roll:

---

