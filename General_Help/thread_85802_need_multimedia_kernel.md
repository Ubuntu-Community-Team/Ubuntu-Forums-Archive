---
title: "need multimedia kernel"
date: 2005-11-03
forum: General Help
---

### Post by hardbop200 on 2005-11-03
Hello all,

New Ubuntu user here.

I am needing to get realtime capabilities on Breezy Badger for running music applications (like Jack, Ardour, etc.).  My first step in looking at this problem was to simply install jackd and qjackconnect from the main and universe repositories, and just as I expected, Jack could not get realtime capabilities.  

My next step was to look through the available kernel patches in the repositories, however none of these appeared to say anything about realtime, and to be honest, I don't know if there are any special steps to installing them, so I left them alone.

So here I am:  I need jackd to be able to get realtime capabilities.  I should also note that I've never compiled my own kernel, and don't care to, not because I don't want to learn, but that would violate my whole reason for moving to Ubuntu - ease of use.  Is there anything I can do here?  I've read on the web that some people have attempted to install the Agnula kernels with poor results (lockups, etc.).  I have also read that some have been able to load the realtime module with a command, but the thread didn't mention if this particular method worked.  

Any ideas?

Thanks,

Josh

---

### Post by metoo on 2005-11-03
Cannot give you help on this for ubuntu, but over at openSuSE there is a sub-project for jack optimization which might be what you are locking for. Different distribution, though.

---

### Post by MarcDM on 2005-11-03
Hey, 
I have an idea that might work. It's actually something I plan to do on the weekend. This solution is purely theoretical, as I haven't tried it. But it should work .

There's this really cool audio specific project (based in France I think), called [Agnula]("http://agnula.org"). They have a distro, [DeMuDi]("http://demudi.agnula.org") that is as Debian/sid based as Ubuntu is. Albeit with a older gnome. 

Anywho, my idea is to install all the desktop + ease-of-use goodies from Ubuntu with the realtime kernel, jackd and a few other apps from the Demudi repos. 

I suppose the process would include changing /etc/apt/sources to include the demudi repos, 
then apt-get update && apt-get install realtime-kernel-package + modules.
afterwords, I'd try to figure out what I broke, and what modules I'll need to compile from the Ubuntu Repos.

Another method would be to install Demudi, then just add the Ubuntu Repositories to Synaptic (yup they have it too), and install the stuff from Ubuntu that you don't have in Demudi. Like the new Gnome. 

I have them both installed on 1PC and I'm tellin u that, apart from the Gnome differences and kernel, the 2 systems look close identical.

I'll let u know the results of my experiments.

Marc DM

*Update *
I just read this on [their site]("http://www.agnula.org/project/") (I felt bad about not knowing) :
> The project is coordinated by [Centro Tempo Reale]("http://www.centrotemporeale.it/") (Florence, Italy) and sees the participation of a range of actors from the research, university and business arenas. 
But that was how the project started. More information on th current project sponsors can be found at :
[http://www.agnula.org/project/agnula_who/]("http://www.agnula.org/project/agnula_who/")

---

### Post by RAOF on 2005-11-04
[QUOTE=MarcDM]...
Anywho, my idea is to install all the desktop + ease-of-use goodies from Ubuntu with the realtime kernel, jackd and a few other apps from the Demudi repos. 

I suppose the process would include changing /etc/apt/sources to include the demudi repos, 
then apt-get update && apt-get install realtime-kernel-package + modules.
afterwords, I'd try to figure out what I broke, and what modules I'll need to compile from the Ubuntu Repos....[/QUOTE]
I suspect that you'll find that lots of stuff breaks.  It's likely that the Demudi packages are not built with gcc-4, and Ubuntu's are, so all the libs would be binary-incompatible.  Just the kernel + kernel pacakges would have a much better chance of working.  I'd download the appropriate .debs manually, and then dpkg -i them.

---

