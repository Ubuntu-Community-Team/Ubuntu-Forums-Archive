---
title: "Synaptic: Packages not authenticated"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by flit on 2009-05-18
Greetings,

I got 2 Ubuntu versions, version 7.10 is offline and version 8.10 is online.
I am trying to install software offline but I am receiving 
the error message that some packages are not authenticated.

I copied the files from /var/cache/apt/archive after I
executed the following command: 
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

I added the line: file://home/$USER/Desktop/Archives/ /
to sources.list

I executed the commands:
sudo aptitude update
sudo apt-get update
sudo apt-get upgrade

I also tried to install the software via command line
wit the same result. [sudo apt-get install <software>]

Did I do something wrong? Can somebody help me with this issue?

Thanks in advance.

---

### Post by mac9416 on 2009-05-18
I don't fully understand your problem, but if you want to install software on an offline computer, [Keryx]("http://keryxproject.org") will do the job. :-D

---

### Post by EXCiD3 on 2009-05-18
Adding a repository requires a GPG authentication key. These are found on all of the online servers if you explore the dists directory on a mirror such as [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)

These are there to help authenticate the repositories and one such as your offline repository does not have an authentication key. Its not necessary because you download the packages on a machine that trusts the repository and you are also creating the local repository yourself so, if you trust yourself (maybe its best if you don't :P) then you can just ignore this or create your own key. I'm not for sure what you need to do to create your own key and set that up unfortunately. Hopefully someone has a link to it. :)

---

