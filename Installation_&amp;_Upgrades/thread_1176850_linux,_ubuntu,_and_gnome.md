---
title: "linux, ubuntu, and gnome"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by TooCrooked on 2009-06-02
hi,

i barely have a concept of what the "kernel" is. i know a great deal about windows, but i honestly cant explain what the kernel is or does with any authority.

as such, i hope that if i understand the relationship between all the layers in ubuntu, i might understand the nature of an operating system in greater detail.

so here's my question: how is ubuntu layered? it's my understanding that Linux is the open-source kernel (the foundation?) that ubuntu is created on. i assume that ubuntu is simply some extension/variation of that open sourced kernel (when stripped from the gui). ubuntu would then have some proprietary commands/operations in that allow it to run and do whatever it is that it does under the hood. finally, i assume that gnome is simply the GUI in which ubuntu is released on, and perhaps is changeable assuming i dont like gnome for some reason?

is this correct? can anyone expound on all this for me? 

also-- is it possible to install ubuntu without the gui? and then from there, to install the gui on top? i believe that if im to become proficient in linux, i need to start from the bottom and work my way up. im pleased with the ease that ubuntu installs, but i realize that im possibly handicapping myself by letting the software do all the work.

---

### Post by quixote on 2009-06-02
You have the right general idea.  Think of it as concentric circles.  The innermost circle is the kernel.  That's the only part that has access to the nuts and bolts of the machine, and its only contact with the outside world is through the root user.  If you're not the "admin" (in windows-speak) you can't do anything system-wide.

The next circle out is the "shell."  This is still a command line environment. Users interact with the shell.  Among the different distributions of linux, there are subtle variations in the commands that can be used and their exact syntax.  Ubuntu is one of those distributions. 

There aren't any proprietary components anywhere along the line.  The only proprietary system-type stuff are drivers for some hardware where the manufacturers refuse to provide the necessary information.

Ubuntu has made one of the biggest efforts of any linux distro to make the gui desktop easy to use.  You could think of the gui as a third circle, although I don't think that would officially be exactly right.  There's a boatload of different gui's: gnome (ubuntu), kde (kubuntu), xfce (xubuntu, low memory usage), and more.

Yes, you can install ubuntu without a gui.  I believe that's what the server install is.  Of course, that includes all the server software.  There's a thread about [installing a minimal Ubuntu]("http://ubuntuforums.org/showthread.php?t=1155961"), which sounds like what you may be looking for.

Have fun! :D

---

### Post by Niva on 2009-06-03
Handicapping yourself?  

You are, I think you should go back to writing code in straight binary.  Actually Assembly is accpetable too for real men.

Jokes aside, use the software, it's there to free you from the absurdities computers require of us.

---

### Post by TooCrooked on 2009-06-03
thanks quixote, that was a very helpful, useful post.

> **Niva said:**
> Handicapping yourself?  

You are, I think you should go back to writing code in straight binary.  Actually Assembly is accpetable too for real men.

Jokes aside, use the software, it's there to free you from the absurdities computers require of us.

All jokes aside, your last sentence is EXACTLY why i want to learn linux from the ground up. I work in IT, and the people that i hate seeing hired (and always end up being more of a liability than anything) are the guys who want to be spoon fed.

I appreciate ubuntu's live CD being what it is, but it's too much of a handicap. quixote seems to understand that, and i greatly appreciate his useful, on topic input!

---

### Post by Niva on 2009-06-07
So I have a question for you, why Ubuntu if all you want is a bare kernel?  I suggest you take an operating systems class, lots of schools offer it.  Last I checked one of my local universities had a class where you get to build your own Kernel.  You sound real cool but what you're doing is wasting your time if you think you can absorb all the aspects of a full OS like Ubuntu.  You couldn't even learn the entire linux kernel alone if you spent a year studying it.  Rather pick some detailed aspect and work on that, focus your concentration and learn how things are done.  I'm still really unsure as to what you're aiming at all to do but you are handicapping yourself if you refuse to use stuff without knowing where all the nuts and bolts go.  You also asked a very newbie question and yet you claim to work in a technical area where other people are liabilities?  You can't work in IT and not know what a kernel is.

---

### Post by quixote on 2009-06-07
(Folks, this is kind of OT but I just wanted to ask what's the point of badgering TooCrooked about why he wants command line Ubuntu.  

Why not?  

Linux is about doing whatever you like.  Go do your thing, and let him do his.)
:popcorn:

---

### Post by Niva on 2009-06-07
Yeah, I don't mean to badger, if it's coming off that way I'm sorry.  

I just find it odd that he thinks he's handicapping himself by using Ubuntu as a full OS, or any OS for that matter.  

Anyways, carry on now, I'm moving on too :)

---

### Post by chronographer on 2009-06-07
What I did, which gave me a great understanding of the LInux operating system, is to install debian. This dumps you at the command line. Then you must apt-get everything else!

Try it out, but in a virtual machine. Install virtualbox [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and then make a VM for debian. Then download the netinstall CD [http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst) and install just the basics. You then need a GUI (like gnome, xfce or kde) and a session manager (like gdm or kdm or xdm) and then can install other softwares on top.

---

### Post by TooCrooked on 2009-06-08
> **chronographer said:**
> What I did, which gave me a great understanding of the LInux operating system, is to install debian. This dumps you at the command line. Then you must apt-get everything else!

that's outstanding information. coincidentally, today i was troubleshooting a vista problem ("a problem" being a grievous understatement) and i needed to install some sort of network bandwidth monitor. i stumbled on a site that explained doing the apt-get for a package called "bwm-ng". this led me to question what "apt" was, and another site explained how it is something that began with debian.

its nice to have the package explorer thing, but at the end of the day it's just doing the apt stuff in the background, so it only seems logical that i understand the foundational stuff so i can better understand things that are built on that foundation.

---

### Post by chronographer on 2009-06-11
apt-get is great. you can try also aptitude:
```
sudo aptitude install firefox
```

also, if you open a terminal and run aptitude, it opens a GUI (written in ncurses I reckon)

another helpful thing for finding packages or package names is firstly <tab>. i.e. if you go sudo apt-get install firef<tab> it will auto complete! on top of this is ```
apt-cache search firefox
``` which will give you a list of all packages with this in their name or description!

For an easter egg try ```
apt-get moo
``` and ```
aptitude moo
``` and ```
aptitude -v moo
``` hint. keep adding more -v

---

