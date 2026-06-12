---
title: "laptop"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by bedlam on 2006-11-25
I have a laptop that I desperately want to install edgy eft on as I also have it on my desktop
However everything goes fine with a fresh install right to the point where I have to log in as I can hear the two beeps but just before this login the screen dissapears after being there up to this point.
I had the same problem with dapper
The specs are
evesham-quest roma T 37
graphics-ati mobility radeon 700
motherboard-microstar int'l co ltd
processor-amd turion 64 mt-37
dislay monitor-eisa code
chipset-radeon express 200p
I've tried both *86 and amd 64 versions
Thanks in advance

---

### Post by junglepeanut on 2006-11-25
Which driver are using? You do have x700 right? Can you get to a root terminal (some people can't but they mostly have x850, most can)? Have you added the section about disabling composite if you are using an ati proprietary driver?

---

### Post by bedlam on 2006-11-26
Yes it is an x700
After install all I can do is press cont+alt+f8 or f6 and get a blotchy coloured unreadable screen, pressing cont+alt+f7 gets me a black screen in which I can do nothing
My fresh install consists of removing my windows hard drive and replacing it with another, so I guess it would be edgy drivers only
I've found three items about composite, in synaptic (from my desktop) but would not know which to choose or how to install them if I could. Would there be a way to incorporate them into an iso image of edgy eft
Finally I should have mentioned that I am an absolute beginner in the Linux world

---

### Post by junglepeanut on 2006-11-26
You are lucky the x700 is easy to configure I have the same one, right now you are using the open source drivers which are very finicky but actually should work. Also the pastel screen you are seeing is a bug. So lets get you to a spot where that should only happen when you try to logout, not shutdown or restart excepts for a flicker.

Start root (some of these sudos are extra but no harm in typing them) this means from the boot option choose "single user" then follow these commands.

Copying from the wiki.
```

sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
sudo apt-get install fglrx-control
sudo depmod -a
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

then edit this file to say 
you can use nano or vim whichever you prefer, alot of new users prefer nano (and older ones too) but I prefer vim, use the "i" key to insert into the field and "esc" to go to command area in vim. thus edit after hitting i and then hit escape to then type :wq to save(w) and quit(q) if you make an error and just cant get the file back the way you had it use :q! to quit and dont save anything. 

```
sudo vim /etc/X11/xorg.conf
```
> 
Section "Extensions"
        Option      "Composite" "0"
EndSection


funny mine says "Composite" "disable" probably do exactly the same thing,
oh yeah I used to put "false" and that worked to. 

Hope this helps. After doing all of this reboot. or type startx.  You should not need to login root anymore for awhile.

---

### Post by junglepeanut on 2006-11-26
If this does not work then it is probably that your monitor has weird specifications and I will need to know more about it.

---

### Post by bedlam on 2006-11-28
Well, It's been some time I know but at last good news.
I installed the 64 bit version because this gave me an operating system with a blind screen with which i was able to log on as root and get a command line
I followed the instructions till I got to                                                                                                                                                                                                                                              "sudo vim /etc/X11/xorg.conf". I trolled up and down numerous times but could not find any entries to change regarding "Extensions or Composite". It was so frustrating, Q or W didn't work, neither did Esc so in the end I pressed Ctrl+Alt+Del, got a message about broadcast and the machine rebooted.
I just let it carry on thinking nothing had changed and I would have to keep it as a Windows machine (I know) but ECSTASY, the screen that had been eluding me for so long was there. I nearly cried.
Thank you so much (junglepeanut) for helping me on this issue

---

### Post by junglepeanut on 2006-11-29
Ok, I would still add that section to your xorg.conf, only because it says to in the wiki. especially if you are going to use beryl later ( I think.)

I would also take a few minutes if you want to learn vim (or learn emacs), since you have graphics you could open a terminal and type vimtutor this way if you have issues you can use those. Many people also like nano. For some reason I don't.

But for just getting the xorg.conf set up properly you can now do 

sudo gedit /etc/X11/xorg.conf

since this is nice notepadish editor it should be straight forward to just cut and paste those lines from here into the file at the bottom and save.

Hope everything stays working well.

---

