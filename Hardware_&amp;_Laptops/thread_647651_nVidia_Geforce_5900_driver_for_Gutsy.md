---
title: "nVidia Geforce 5900 driver for Gutsy"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by nikRbokR on 2007-12-22
hello,

 finally got Ubuntu 7.10 installed. it showed me the restricted drivers for my Nvidia Geforce 5900 graphics card.  i told it to install the driver and then i rebooted as it told me to. Before the driver, i got 2 resolutions (860 x 640) and (640 x 480).  However, after the reboot, I only get 640 x 480.  can someone please help me?  i have absolutely no experience with linux, so i am clueless.

tnx a bunch.

---

### Post by taurus on 2007-12-22
Open a terminal, Applications -> Accessories -> Terminal, run

```
gksudo nvidia-xconfig
```

---

### Post by nikRbokR on 2007-12-22
> **taurus said:**
> Open a terminal, Applications -> Accessories -> Terminal, run

```
gksudo nvidia-xconfig
```

after doing this... what do I do?  i did it, but it didn't do anything.  i still have the same resolution settings.

it tells me this:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

what do i do after this? i believe that my 3d is working, for i have put on the highest effects and it is working.

tnx

---

### Post by taurus on 2007-12-22
You now need to restart X server or even reboot if you wish, <Ctrl><Alt>Backspace.

Otherwise, post your /etc/X11/xorg.conf
```
cat /etc/X11/xorg.conf
```

---

### Post by nikRbokR on 2007-12-22
thanx 4 ur help.

i'm stepping out now.  but, i'll do so l8r.

---

### Post by taurus on 2007-12-22
Run that command from a terminal.  It will display the whole file so you need to scroll up and copy, highlight, with the left mouse button.  Then, paste it here with the middle button.  Now, scroll down and copy the rest of the output and paste it here.  So, cut/copy with the left button and paste with the middle one--cut 'n paste.

But try to reboot your machine first to see if you get a higher resolutions.

---

### Post by LuisC-SM on 2007-12-22
IMHO, I think the best is to backup your /etc/xorg.conf and then you can reconfigure your card as mentioned above.
You can also do the following to keep a copy of your xorg.conf file in your main dir.
```
$ sudo cat /etc/xorg.conf > xorg.conf.txt
```
Cheers
Luis

---

### Post by taurus on 2007-12-22
> **LuisC-SM said:**
> IMHO, I think the best is to backup your /etc/xorg.conf and then you can reconfigure your card as mentioned above.
You can also do the following to keep a copy of your xorg.conf file in your main dir.
```
$ sudo cat /etc/xorg.conf > xorg.conf.txt
```
Cheers
Luis

I assume you know that is a wrong command because there is no such thing as /etc/xorg.conf.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by LuisC-SM on 2007-12-22
> **taurus said:**
> I assume you know that is a wrong command because there is no such thing as /etc/xorg.conf.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

LOL.. sorry

**/etc/X11/xorg.conf** I meant to say

Luis

---

### Post by nikRbokR on 2007-12-24
I had it working w/ Analog display.  however, with digital, it has once again gone to just 680x x 480.  I tried the gksudo command, but even after doing Ctrl + Alt + Backspace, it has only 680x480 res.  No idea y, but will try to post the xorg.conf thing soon.

---

### Post by nikRbokR on 2007-12-30
I installed Ubuntu about a week ago.  The computer I have is terrible at the moment (the motherboard is screwed-up and it freezes during boot up, so it's become even worse now!).  However, I was having some trouble w/ the nVidia Graphics Card I had in there.  I think it is a GeForce 5900.  I installed the driver it told me to in the Restricted Drivers section on initial start-up, but it really didn't do much good.

I wanted the screen res to get to 1280x1024.  However, I only got that up and running after [[COLOR="DarkOrange"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=647651&highlight=5900").  So, I had that working.  The computer wuz freezing up and I wuz busy, so I didn't touch it 4 a few days.  However, I tried it again, and the res was once again 680x480 or wutever.  The main difference was that now, instead of analog, i was using digital.  I have no idea why it would do this!  I tried the fixes from w/e the post above said, but it wuzn't working (it would freeze up b4 i could do anything ;) ).

I was wondering if I had installed the wrong driver?  I went to the nVidia site and the latest driver for GeForce 5900 (for Linux) wuz 2003.  Should I go and install the latest driver for linux (Sept. of this year)?

Thanks for ur help.

---

### Post by nikRbokR on 2007-12-30
I installed Ubuntu about a week ago.  The computer I have is terrible at the moment (the motherboard is screwed-up and it freezes during boot up, so it's become even worse now!).  However, I was having some trouble w/ the nVidia Graphics Card I had in there.  I think it is a GeForce 5900.  I installed the driver it told me to in the Restricted Drivers section on initial start-up, but it really didn't do much good.

I wanted the screen res to get to 1280x1024.  However, I only got that up and running after [this post]("http://ubuntuforums.org/showthread.php?t=647651&highlight=5900").  So, I had that working.  The computer wuz freezing up and I wuz busy, so I didn't touch it 4 a few days.  However, I tried it again, and the res was once again 680x480 or wutever.  The main difference was that now, instead of analog, i was using digital.  I have no idea why it would do this!  I tried the fixes from w/e the post above said, but it wuzn't working (it would freeze up b4 i could do anything ;) ).

I was wondering if I had installed the wrong driver?  I went to the nVidia site and the latest driver for GeForce 5900 (for Linux) wuz 2003.  Should I go and install the latest driver for linux (Sept. of this year)?

Thanks for ur help.

---

### Post by Yellow Pasque on 2007-12-30
Why did you open another thread? You should have just bumped that one (preferably by posting your xorg.conf file)

---

### Post by nikRbokR on 2007-12-30
Lol... ;)  How do I bump a thread? (I tried posting it, but by the time I had it copied and pasted into the message box on the thread, the comp froze :(  lol... ya I know, the comps in a sad state.)  When I get it running again, i'll try to do that.

---

### Post by Yellow Pasque on 2007-12-30
Bump at your request. Please post your /etc/X11/xorg.conf file.

---

### Post by Yellow Pasque on 2007-12-30
OK, well I bumped it for you. Now a mod can delete this thread (and its duplicate). Man, your computer must be in a sad state.

---

### Post by nikRbokR on 2007-12-30
Haha... you have no idea!  Had to go out and buy a new comp just to use one!  How did u bump it by the way, for future use?  Do u have any idea of how to fix it?

---

### Post by overdrank on 2007-12-30
> **nikRbokR said:**
> Haha... you have no idea!  Had to go out and buy a new comp just to use one!  How did u bump it by the way, for future use?  Do u have any idea of how to fix it?

Hi and to bump your thread you just make a post. You have been asked questions in your other thread
[http://ubuntuforums.org/showthread.php?t=647651](http://ubuntuforums.org/showthread.php?t=647651)

---

