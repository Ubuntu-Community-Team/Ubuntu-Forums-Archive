---
title: "Howto transfer settings..."
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by TiredBird on 2009-05-08
I use several computers and several operating systems. (Ubuntu and Kubuntu, 6.06, 8.04, 8.10 and 9.04). 

I want to experiment with the latest and greatest and make improvements in my system and its capabilities. However, it is necessary that I am able to access all of my data and use all of my programs at all times. 

Recently I have been using Ubuntu 8.10 for most of my work. However, sometimes, because I have not installed or configured something properly, it is necessary to go back to an older system. (Two days ago I had to use 6.06 because of something that was installed and operational there that was not yet working on the newer systems.)

The problem I am constantly faced with is the differences I have created in settings, configurations and installed programs. I use the same data on all systems but each system has its own desktop, its own scripts, icons, etc., which makes it very difficult to jump between systems.

I have just spent several months getting 8.10 set up the way I want it, (icons, programs, etc.) and today I installed 9.04, (fortunately on a separate partition), If I have to set it up all by hand, its going to be a couple of months before I can do anything meaningful with it and I still have things I can't do with 8.10, not because it isn't capable of doing it, but because I haven't had the time to make the necessary customizations for it to work.

I realize that each release is going to obsolete some things, but hopefully there is some way that I can automatically transfer ***most*** programs and settings from one release to another. 

Suggestions anyone?

---

### Post by TiredBird on 2009-09-14
I'm still trying to solve this problem - can anyone help?

---

### Post by TiredBird on 2009-10-13
bump...

---

### Post by Lars Noodén on 2009-10-14
Make your home directory a separate partition in ext3 format.  

Make one swap partition. 

Make separate partitions for each of your systems.  I find that for a desktop, 15GB is ample for experimentation and excessive installation.  

When you do each installation do the manual partitioning every time.  Be sure to select the same home partition and mount it as /home.  Be sure the partitioning tool is set **NOT** to format the /home partition.

That will keep your desktop settings and anything that you have configured to use your home directory for.  You'll have to add the programs to each system though.  If you keep a text file with the names of the packages you can use that to load APT-get.

The above works even for other systems, but I find that OSX, for example, has a bit of trouble with EXT.

---

### Post by TiredBird on 2009-10-14
> **Lars Noodén said:**
> ...That will keep your desktop settings and anything that you have configured to use your home directory for...

I've done everything you suggested. Actually I've been trying to make this work for a couple of years now. But for some reason I can not do it as simply as you say.

Personal computers, (I actually have several), are both a hobby and a tool for me. For the part of my life where the computer is a tool, it has to work when I need it. I can't afford to be fritzing around with it when I'm in that mode.

On the other hand, I do like to experiment, try new systems, tune up the ones I have, etc. But when I'm trying new stuff, I still have to be sure that I can make it all work when needed.

Presently, I have an 8.04 command line only system on one partition; an Ubuntu 8.04 Gnome system on another partition; and an Ubuntu 9.04 Gnome system on another partition. And when 9.10 is finally released I plan to have another partition for it.

The 8.04 CLI is for emergencies. (In case I screw something up and can't get into any of my GUI's.) This one is called 'emergency'.

The Ubuntu 8.04 Gnome system is my fallback GUI, when I have to get real work done and something about 9.04 is causing me some trouble that I can't easily fix. I call this one 'stable'.

The Ubuntu 9.04 Gnome system is the one I use most of the time. But, I am often trying out new things with that so it is not always stable. I call that one 'testing'.

When I install Ubuntu 9.10 Gnome, it will initially be called 'experimental'. But as soon as it is running reasonably and has my most used software installed in it, it will be redesignated 'testing' and the 9.04 system will be wiped out.

10.04 will go through this same procedure, but being an LTS system, it will not be disposed of when 10.10 comes out. Instead, it will probably replace 8.04. Or at least thats the way I migrated from 6.06 to 8.04.

What I would really like to do is to use the same /home directory for each of them. That way I would have the same data and same desktop settings with each system. 

However, those dot files that are a part of each users home directory seem to vary somewhat from release to release. Or at least I can't seem to make it work. When I try that I get errors about missing 'auth' files or something like that. 

In order to narrow in on the objective I have created another partition that is used by all systems. That partition mounts on each system's '/srv' directory. 

Because each system mounts this partition, I know that any changes I make in that part of the file tree will be there for each system. It also allows me to have common storage directories for things like icons, scripts, configuration files, etc.

What I have had to do is to have a separate home directory for each system, each with its own set of dot files. Also in each home directory are links to the home data partition which is mounted on the '/srv' tree.

This is pretty kludgy but it does work. There are a couple of problems I would like to eliminate. 

With this scheme, each desktop has its own settings. If I am using 9.04 and make a change, when I go to 8.04, the desktop is different until I make the change there too. A minor change is not a real problem. But getting 9.10 to look like my other desktops is going to be a major consumption of time.

The data is only linked to from each system. If I make some changes and don't copy a link over to the other systems, I could be missing a whole bunch of data.

And thats the rest of the story. Is there any hope or am I stuck with what I am doing?

---

### Post by raymondh on 2009-10-14
I have used apton from one computer to another.  Note that I have used in same version Ubuntu ... not from "Intrepid-transfering-to-Jaunty".

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Hope this helps you.

Best,

---

### Post by TiredBird on 2009-10-14
> **raymondhenson said:**
> I have used apton from one computer to another.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Hope this helps you.

Best,

Thanks for the tip. I looked at the referenced web-site and decided it wasn't what I was looking for. However, it was interesting and it was something that I was not previously aware of.

I have my own local repository for 8.04 and 9.04 and APTonCD seems to fit in there somewhere. Not sure yet but its got me thinking.

Thanks again but I'm still looking...

---

