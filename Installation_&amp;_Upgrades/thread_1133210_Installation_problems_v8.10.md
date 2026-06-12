---
title: "Installation problems v8.10"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by foley on 2009-04-22
Hello there, I am new to Linux/Ubuntu and am thus at your mercy :)

I ahve a fairly new netbook from dell with an atom processor.  When I purchased it, they gave me an option of either vista or ubuntu and I chose the former. Unfortunately, even the basic home of Vista runs so slowly on the netbook that it is not even worth using so I decided to switch.

I bought an Ubuntu DVD from amazon, version 8.10 and began the installation process...from the DVD.

The initial process works well, it let's me get to the language selection screen and then gives me options to either "try Ubuntu without changing system" or "Install Ubuntu"

I have tried both of these options and each time after it seems to be "installing"...the next screen is a DOS-like screen with a root command at the bottom: "ubuntu@ubuntu_$"

there is no GUI...



Has anyone run into this problem before? Is there a solution? Am I doing something wrong?

Thanks a lot for your help in advance.

---

### Post by 5nak3 on 2009-04-22
I have no experience in what is happening, however, if I was to hazard a guess I would assume, the disk is throwing you into the alternative install method.

Probably due to the lack of power from the netbook, it is likely decided you are best suited to installing via terminal.

I would suggest to Google "ubuntu alternative install step by step" or something similar see if this throws up anything of use, alternatively wait until someone with more experience can help.

Best of luck!

---

### Post by foley on 2009-04-22
Thanks for the reply. You may be right, although it is somewhat doubtful given that this very netbook (I have the Inspiron mini 12) was offered from Dell with Ubuntu..silly me just chose Vista.

The hardware should be fine...

---

### Post by 5nak3 on 2009-04-22
I think you may have misunderstood my previous comment. The hardware might be fine, but from my understanding (again limited) when it comes to installing Ubuntu you have two options GUI based and alternative install. 

The GUI is more resource intensive, so you need more processing power, and ram. 

The alternative install is a command based install that does the same thing, but in a command (dos like) format. Once this is complete the GUI gnome desktop should be good to go.

I'm not particularly up to date with PC hardware as the last time I bought a PC was when P4 with hyper-threading technology was all the rage. But if I am not mistaken the atom processors are a low powered processor and, I'm guessing you probably are running 1gb of ram under the hood which means that the mix of ram and low processing power may limit the ability to boot into a GUI from the livecd.

Just a thought, I hope somebody with more knowledge comes around soon, but for the time being I think google may be your best friend.

---

### Post by foley on 2009-04-22
I think you are right! It is only 1 gig of ram...and an atom processor. (I just needed this netbook to check e-mails)

Hopefully someone here knows what my next step would be.

Thanks

---

### Post by sailthesea on 2009-04-22
There are much lighter Disros of Ubuntu/Linux available that would be better suited to your needs Not sure what you should look for but the right one for you is out there for sure!

---

### Post by snowpine on 2009-04-23
Hi Foley, don't listen to the misleading advice above... the Dell Mini 9 with Atom Processor and 1gb ram is more than capable of running Ubuntu!

If you are getting the ubuntu@ubuntu prompt, then you have successfully installed the command line version of Ubuntu. Try typing 'startx' (without the quotes) at the command line... does that start the graphical interface? If not, you can install it by entering the following (you will need a wired internet connection):

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

When prompted for a password, enter your regular user password that you provided during the installation. 

Here is more info (including a fix for the sound issue you will no doubt discover): [http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html](http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html)

I will leave you with this thought: Ubuntu 8.10 is not your only option. Dell made a special version of Ubuntu specifically for the Mini 9. It comes factory installed. If you want this special version, read this thread: [http://mydellmini.com/forum/dell-mini-9-ubuntu-restore-iso-image-t287.html](http://mydellmini.com/forum/dell-mini-9-ubuntu-restore-iso-image-t287.html) You might also consider Ubuntu 9.04, which is being released today, if you like trying new (and potentially buggy) software. 9.04 has better support for the Dell Mini out of the box than 8.10.

Hope that helps, I will subscribe to this thread in case you have any issues.

---

### Post by IsAB on 2009-04-23
I've had similar issues on my desktop, turns out that i had the onboard vga enabled in the bios in addition to a pcie vga (wich is the one i'm using), and X would get confused and wouldnt start up, throwing me to the command prompt.

I doubt this exact case is your problem on your netbook but it might be worth a try to look into the xorg.x.log file which i believe is located in /var/log/ (but i'm not sure, maybe its in /etc/X11/.... somewhere, i dont have access to the xubuntu machine right now) to see if for some reason X cant initialize.

---

