---
title: "upgrade to Jaunty ruined video drivers, can't see anything"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by barraymian on 2009-04-25
hello there, 

i just upgrade to Ubuntu 9.04 last night and when it was at 99%, it gave me an error that it couldn't upgrade noip2 package. This is a program that lets me have dns address to access instead of remembering my ip address. anyways, the upgrade msg said that it must reboot since the system might be in an unstable state. and since then i can't boot into my computer. It starts fine but after i get the startup bar, this is the screen i get

[IMG]http://img211.imageshack.us/img211/4294/image003f.jpg[/IMG]

I've gone into recovery mode, validated packages (can't remember the exact option), have checked file system, have done what this post: [http://ubuntuforums.org/showthread.php?t=1136886](http://ubuntuforums.org/showthread.php?t=1136886) suggested but to no avail and i can't get into my computer anymore.

This sucks, can someone plz help me? it looks like the video driver was screwed

---

### Post by LinuxGuy1234 on 2009-04-25
> **barraymian said:**
> hello there, 

i just upgrade to Ubuntu 9.04 last night and when it was at 99%, it gave me an error that it couldn't upgrade noip2 package. This is a program that lets me have dns address to access instead of remembering my ip address. anyways, the upgrade msg said that it must reboot since the system might be in an unstable state. and since then i can't boot into my computer. It starts fine but after i get the startup bar, this is the screen i get

[IMG]http://img211.imageshack.us/img211/4294/image003f.jpg[/IMG]

I've gone into recovery mode, validated packages (can't remember the exact option), have checked file system, have done what this post: [http://ubuntuforums.org/showthread.php?t=1136886](http://ubuntuforums.org/showthread.php?t=1136886) suggested but to no avail and i can't get into my computer anymore.

This sucks, can someone plz help me? it looks like the video driver was screwed

You can install Ubuntu 9.04 from a ISO instead.

---

### Post by pjhudson on 2009-04-25
that's the screen I have before it goes to the "low graphics mode" box and freezes==  it's just a quick flash on mine though

---

### Post by psriram on 2009-04-25
My problem is little different 

I downloaded the iso from ubuntu website and installed as fresh copy 

Ubuntu 8.04 and 8.10 starts the installation with GUI but 9.04 was unable to detect my vga and installation went on the text mode. 
installed all the packages via aptitude and x11 is installed.

Now,
When boot up x window is not starting up instead login enabled using tty's

i tried to do this

sudo startx 

but result was command not found 

its says xinit package not installed and am trying to do this

sudo apt-get install xinit 

cd reads and says similar package x11-common is installed

what might be the problem of X window starting?

Kindly help 

-Sriram

---

### Post by barraymian on 2009-04-25
psriram, it would be better if u start a new thread for ur issue since it is a different issue. Let me get help for my issue here and u get ur on ur own :)

LinuxGuy1234, thanks for ur suggestion. I am gonna try that. in the meantime, anyone else have any ideas?

---

### Post by barraymian on 2009-04-25
so isn't there a way to fix my screen problem without needing to reinstall the entire OS from a iso image? there has to be a way. helppp :s

---

### Post by barraymian on 2009-04-27
i ended up installing 9.04 from an iso cd which fixed my problem. I must say i am extremely disappointed by the stability of Ubuntu

---

### Post by LinuxGuy1234 on 2009-04-30
> **barraymian said:**
> i ended up installing 9.04 from an iso cd which fixed my problem. I must say i am extremely disappointed by the stability of Ubuntu

Sometimes, Linux has bugs like Windows...

---

### Post by Person98 on 2009-04-30
I think i am having the same issue as you, after the loading screen it goes straight to that, I have checked my logs for errors and there doesn't seem to be any really showing. I really don't want to do a fresh install. I am also curious what graphics card and driver are you using? I also had no luck with the using the generic xorg.conf. I'll keep tinkering with it and see if can come up with something...

---

