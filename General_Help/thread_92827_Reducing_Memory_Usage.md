---
title: "Reducing Memory Usage"
date: 2005-11-20
forum: General Help
---

### Post by organgtool on 2005-11-20
I am attempting to run Ubuntu Breezy Server on a machine with 64MB of RAM.  I have removed many unnecessary services, but upon booting up, Ubuntu uses 60MB of RAM and 10MB of swap for a total of 70MB.  I did a pmap of all of the processes on the system and the total memory usage came out to 27MB.  So what is using the other 43MB of RAM?  I know the kernel and kernel modules take up their own memory, but are they actually consuming that much RAM?

In any event, is there any way to reduce the amount of memory Ubuntu is using?  I am only attempting to run a server with DHCP, bind, and a few other daemons, so I don't understand where all of the memory is going.  Thanks for any help you can provide.

---

### Post by ofek on 2005-11-20
Many ppl here may not like my advice, but i think u should realy rethink why u want ubuntu as your server.
For your needs i think slackware could do a better job.

---

### Post by organgtool on 2005-11-20
I'm actually migrating my server to Ubuntu from Red Hat because I have really grown fond of the apt package management and the large number of available packages in the apt repositories.  What really sold me on Ubuntu was when I upgraded the entire distribution from Hoary to Breezy with absolutely no problems.

Also, for the most part, Ubuntu isn't too bloated.  I'm just trying to trim anything off that I can.  I once worked for a company that ran a customized version of Linux in 8MB.  I don't expect to get my server running that slim, but I would like to do anything I can to trim the fat.

---

### Post by ofek on 2005-11-20
You could try installing a new kernel on your own.
By that you could configure it to suit your system. 
I dont think that will help as much as you need it to, but atleast its a start ;)  and i luv apt-get as well.

---

### Post by ranf on 2005-11-20
[QUOTE=organgtool]I am attempting to run Ubuntu Breezy Server on a machine with 64MB of RAM.  I have removed many unnecessary services, but upon booting up, Ubuntu uses 60MB of RAM and 10MB of swap for a total of 70MB.  I did a pmap of all of the processes on the system and the total memory usage came out to 27MB.  So what is using the other 43MB of RAM?  I know the kernel and kernel modules take up their own memory, but are they actually consuming that much RAM?
[/QUOTE]
I'm just looking at your MB numbers and wonder why my small laptop with X, Xfce says it only uses 64 MB and no swap (it has 128 MB RAM).

Maybe the output of `ps ax' gives some general guidance on what to remove.

---

### Post by RAOF on 2005-11-20
It's entirely possible that most of the other 40 MB or so is being used as disc cache.  I seem to remember that the kernel will page out infrequently accessed memory to swap in order to increase the amount of ram available for the cache.

Although 40MB seems a bit much on a 64 MB system :)

---

### Post by ofek on 2005-11-20
a Little dumb question.
Are you using any desktop enviorment?

---

### Post by organgtool on 2005-11-20
I am not running any kind of graphical environment.  My goal is to use as few resources as possible.  I am running just the command line.  I removed the following services:

alsa
alsa-utils
atd
mdadm-raid
mountnfs

In addition to the Breezy Server installation, I have added:

bind
dhcp daemon
ssh daemon

And I'm planning on adding:

snort
tripwire
aide
openswan
iptables configuration

I think I figured out where some of that space was going.  Supposedly the kernel will hold on to memory for caching purposes.  Is there any way to tell how much memory is being used just by the kernel and the kernel modules?  If I had this number, I could figure out how much memory the kernel was reserving as cache and I know how much room I have to work with.

---

