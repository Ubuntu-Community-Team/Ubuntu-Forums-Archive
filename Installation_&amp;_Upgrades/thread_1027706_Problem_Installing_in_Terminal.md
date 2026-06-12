---
title: "Problem Installing in Terminal"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by DGSpeir on 2009-01-01
So I'm officially a day into Ubuntu, just enough time for me to be able to grind my teeth at its complexity, slam my fists at its seemingly impossible installation dilemmas, and then calm myself down upon realizing how much, aside from the problems I am having with it, I actually love it. 

Now, onto my problems. One of my biggest road blocks came when I slid in the first disk of Return of the King and Totem wouldn't play it. I began on a quest to try and fix this problem, none of which worked. I've come across a few DVD playing programs (kaffiene, xine, vlc), but I can't seem to get any of them installed and working without some kind of error message in the terminal. 

My latest attempt was to install Kaffiene. I popped open the terminal and followed the instructions the [official download page]("http://kaffeine.kde.org/?q=download") gave me for installing it. 

So I type "apt-get install kaffeine" into my home directory. 

I get this error:
```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Every time I try to install something I get an error message very similar to that. My first request is that someone would please help me with this issue, my second request is that someone would fill me in on the best program to install for DVD playing. 

Sorry, I'm sure you guys get hounded by noobs all day long. All help is appreciated, thanks.

---

### Post by melojo on 2009-01-01
put sudo infront of it

```
 sudo apt-get install
```

or you can use synaptic package manager in the system>administration

---

### Post by melojo on 2009-01-01
you might also need to install the restricted extras

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by DGSpeir on 2009-01-01
Oh. I knew it would turn out to be something simple.
I'm using the Synaptic Package Manager, but can you tell me why it gave me this error just for future reference. 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kaffiene

```

EDIT:
I tried to install restricted extras and got this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by melojo on 2009-01-01
kaffeine was spelled wrong

---

### Post by DGSpeir on 2009-01-01
Oh, yep. That would create a problem...I feel dumb.
What about the restricted extras problem? (Edited into my previous reply.)

---

### Post by Copernicus1234 on 2009-01-01
Close the Synaptic Package Manager before running the install command from the terminal. Only one instance of it can run at a time, weather you run it from the terminal or from the GUI. :)

---

### Post by melojo on 2009-01-01
> **Copernicus1234 said:**
> Close the Synaptic Package Manager before running the install command from the terminal. Only one instance of it can run at a time, weather you run it from the terminal or from the GUI. :)

+1

good point!!

---

### Post by DGSpeir on 2009-01-01
Okay, I installed the restricted extras and Kaffeine successfully, but when I try to play my DVD in the program I just get a black screen. Any idea why?

---

### Post by oldos2er on 2009-01-01
Have you installed libdvdcss2? See [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by doglover56 on 2009-01-01
I had a similar problem. If playing multimedia is a primary use, like it was for me, it was a lot easier to install Linux Mint, which is basically Ubuntu with the stuff you are trying to install. It just plays the DVDs and other stuff right out of the box. Ubuntu is great also, I have them both on my machine.

IMF

---

### Post by DGSpeir on 2009-01-01
Well, I'll look into that.
Now I have a whole other problem. It seems to be one thing after another...
When I opened Kaffeine to play the DVD it froze, so I shut down the computer. When it came back on I got this message upon opening Synaptic Package Manager.
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by oldos2er on 2009-01-01
Open a terminal and run "sudo dpkg --configure -a"

---

### Post by theozzlives on 2009-01-01
Type:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
then:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by DGSpeir on 2009-01-01
Wow, Okay it finally works.
This is one complicated OS. Haha.
It's going to take some getting used to. Thanks for all the help guys.

---

