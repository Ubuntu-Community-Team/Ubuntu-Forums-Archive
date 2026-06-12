---
title: "Dell XPS 720 - No GUI ?"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Tarmacc on 2008-12-30
Hi

I'm a total Linux newbie but want to learn it.  A guy in work gave me an "Ubuntu 8.10 Desktop Edition" cd to install.

I loaded the installer program in Windows and chose to install Ubuntu as dual boot with XP.  It appeared to have worked yet clearly something is wrong as it does not boot to a GUI.  It goes to like a command prompt with something about 'BlueBox' or 'BlueSky' in the text above it.

Like I said, I'm a complete newbie with Linux so I don't know any commands to enter at a prompt.  Is there some option I must do at install that will let it launch the GUI properly or does it simply not run on this sort of computer?

Apologies for vagueness, - I would appreciate any assistance.


Many thanks in advance

---

### Post by Mathematician on 2008-12-30
hmm interesting, have you tried to change the boot settings in your BIOS to cd-rom boot, then run the live cd or install?

I would recommend trying out the live-cd without installing right away so you can see if you like the ubuntu distribution of linux. 

As for your problem in installing inside of windows, I apologize, I'm not familiar with that method of installation -hopefully someone with more experience can help you

---

### Post by Tarmacc on 2008-12-30
I tried booting into the Live CD and it did not show a GUI either!  It loaded into a command prompt too with "ubuntu@ubuntu:~$" at the prompt.  I wonder has this something to do with me having an SLI configuration in this computer maybe?

---

### Post by Mathematician on 2008-12-30
> **Tarmacc said:**
> I tried booting into the Live CD and it did not show a GUI either!  It loaded into a command prompt too with "ubuntu@ubuntu:~$" at the prompt.  I wonder has this something to do with me having an SLI configuration in this computer maybe?

hmm, do you know exactly what iso image your coworker burned to the cd? - your computer might not have the right configuration, -like you said, for that specific cd.

do you know that the cd works? - run the check cd integrity at boot

- I'm still a new guy as well - hopefully someone with more experience can help you out if this doesn't help

---

### Post by abn91c on 2008-12-30
> **Tarmacc said:**
> I tried booting into the Live CD and it did not show a GUI either!  It loaded into a command prompt too with "ubuntu@ubuntu:~$" at the prompt.  I wonder has this something to do with me having an SLI configuration in this computer maybe?
did you type [COLOR="Red"]**startx**[/COLOR] at the prompt?

---

### Post by Tarmacc on 2009-01-16
Sorry for delay - had problems loading these forums lately.  Thanks for replies.

I asked my co-worker where he got the CD and he said it was mailed to him from Ubuntu - i.e. one of the free CD's you order or something.  It is in an Ubuntu sleeve and stuff - it's not a downloaded ISO burned by him - it's one directly from Ubuntu.

By the way, the "BlueBox" thing was incorrect - it's actually called "BusyBox" when I boot from the installed version that appears.  The installed version stops with a prompt "Initframs" or something to that effect.

I didn't do that "startx" command - as I said, I'm as totally newbie as you can imagine with Linux and it's command syntax.  I will try and enter that command when I'm back at that computer later.

Thanks alot for your posts - all help and suggestions are appreciated.

---

### Post by Tarmacc on 2009-01-19
I booted the LiveCD and got to the ubuntu$ prompt again.  I entered "startx" and got an error.  It said the primary device was not PCI.  Fatal Error: No screens found.  It stopped there.

My graphics cards are 2 x NVidia GeForce 8800 GTX in SLI mode.  I think they are "PCIe" slots that they are in.  Will Ubuntu not run on this configuration or is there something I must do to allow it to boot using this graphics card configuration?

Many thanks.

---

### Post by 85stang on 2009-02-05
I have an XPS 720 and have the same problem I installed Mint 5.0 and it works great.  However when I try to boot the Mint 6 CD or Ubuntu 8.10, I get the same problem as the guy above.  If I try the command startx it says
Primary device is not PCI
(EE) No devices detected
[B]
Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.[/B]

I would like to upgrade to something 8.10 based, but I am stuck.  Why doesnt 8.10 detect a display?

---

### Post by 85stang on 2009-02-11
anyone?  Dreamlinux 3.0, Suse 11, and Mint 5 boot perfectly on this machine.  I tried the command suggested somewhere else, sudo /etc/init.d/gdm start, but that just gives a blinking cursor in the upper left.  I think next I will try the beta of 9.04 to see if it has the same problem.

---

### Post by avtolle on 2009-02-11
85stang; since Mint5 worked, you could try 8.04 LTS and see whether it works (it will be supported until 2011 as a LTS release), or use Mint5 if you like it.

Both: what you are running into is an issue with the graphics card, as I believe both of you have determined. From a Live CD for 8.10, to try to install, select Install in Safe (Low?) Graphics mode, an option revealed by pressing F4 at the initial screen. Otherwise, to get around the graphics problem during installation, d/l the alternate cd iso and burn it to cd as an image after checking the md5sum of the iso. It uses a text based installer, and will work in many situations where the Live (Desktop) CD will not. 

Another thought: one issue causing some of the problems is that visual effects are enabled with the Live CD, as I recall. There are some threads on the forum I recall discussing removing compiz and compiz core at the command line before beginning installation, just don't have a link.

---

### Post by avtolle on 2009-02-11
One other thing: see [https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options) for some boot options and how to use them. I note the message regarding PCI, and wondering if using one of the kernel options about turning PCI on (can't recall which one) might be helpful. There are a number of options given, try the ones that seem to fit, first alone and then in combination to see if you can arrive at something that will work.

---

### Post by the_analyzer on 2009-02-12
guys, I have the same problem. can you please help me.

this is my topic if you wanna help.

[http://ubuntuforums.org/showthread.php?p=6722110#post6722110](http://ubuntuforums.org/showthread.php?p=6722110#post6722110)

thnx

---

### Post by 85stang on 2009-02-12
I have different video cards, 2 8600 GTS in **non** SLI mode.  I run 3 mnonitors.  Is it possible the problem is 2 video cards?  I tried several of the boot options and the safe mode boot, none of them work.  maybe ill try pulling one of the video cards out and see if that does the trick. thanks for the suggestion of the alt CD, I didnt know there was a text based installer ISO, and i see that it comes in 64 bit.  That is the only reason I might want to change from mint 5, I have 6 GB of ram doing nothing.

---

### Post by Tarmacc on 2009-05-05
Did anyone manage to resolve this?  I tried with the new 9.04 version and it still fails with the same problem booting up.  :(  I also tried installing from the alternative cd text installer and it fell over on boot in the same way.

On another note, the netbook remix version works fine except for the sound on my HP Compaq Netbook - 8.10 ran fine with sound.  :S

---

### Post by 85stang on 2009-05-06
ok, I am able to install 9.04 if i take out one of my video cards.  however, the system will not boot as soon as i put the second card in, even with the latest nvidia driver installed.  I have 3 monitors so i have to have the second video card.  anyone else got 9.04 working with 2 video cards?

---

### Post by 85stang on 2009-05-07
Ok, I now have 9.04 working with 2 video cards on my XPS 720!  It worked fine with 8.04 and other distros, but could never get a GUI on 8.10 and newer Ubuntu.  I took one of my video cards out and finally got to the desktop on a live CD.  I installed the Nvidia driver, the i put
BusID    "PCI:1:0:0"
in the Device section of xorg.conf to find the correct bus id run "lspci" in a terminal.  I put the other card back in and run nvidia-settings and got everything set back up just like I had on 8.04

---

### Post by Tarmacc on 2009-06-03
> **85stang said:**
> Ok, I now have 9.04 working with 2 video cards on my XPS 720!  It worked fine with 8.04 and other distros, but could never get a GUI on 8.10 and newer Ubuntu.  I took one of my video cards out and finally got to the desktop on a live CD.  I installed the Nvidia driver, the i put
BusID    "PCI:1:0:0"
in the Device section of xorg.conf to find the correct bus id run "lspci" in a terminal.  I put the other card back in and run nvidia-settings and got everything set back up just like I had on 8.04


Apologies once again, but I am very much a Linux novice trying to learn.  How do edit the 'xorg.conf' and save it?  I assume when you said you installed the Nvidia driver, you did so when you got to the desktop and gained access to Nvidia website yes?

Thanks for any assistance.

---

