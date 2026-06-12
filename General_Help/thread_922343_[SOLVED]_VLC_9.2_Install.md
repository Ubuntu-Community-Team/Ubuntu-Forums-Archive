---
title: "[SOLVED] VLC 9.2 Install"
date: 2008-09-17
forum: General Help
---

### Post by anotherdisciple on 2008-09-17
Hey all! I was wanting to test drive VLC 9.2, but it's not in the repositories, nor can I find a .deb of it.

I know that I can compile from source... I tried it, but I'm just a little stupid when it comes to this.

I tried that article "How to Install Anything in Ubuntu" and I unzipped the file and read the INSTALL file... I couldn't figure it out. Can anyone walk me through this. 

It's about time I learned how to do this anyways. I got the file from [_here_]("http://www.videolan.org/vlc/download-sources.html").

---

### Post by dualpretop on 2008-09-17
sudo apt-get remove vlc vlc-nox
sudo apt-get autoremove

add sources list:

deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main

sudo apt-get reload
sudo apt-get install vlc vlc-nox

---

### Post by anotherdisciple on 2008-09-17
Is this a trustworthy repo?

---

### Post by cj2003 on 2008-09-17
There's a guide here:

[Install VLC media player 0.9.2 in Ubuntu]("http://ubuntu-news.net/modules/news/article.php?storyid=5161")

---

### Post by directcharitycontribution on 2008-09-17
u can mark solved now.

---

### Post by anotherdisciple on 2008-09-17
> **directcharitycontribution said:**
> u can mark solved now.
haha... actually ... I was looking to learn how to install if from source.. but I'll mark it as solved anyways since this works.

---

### Post by Johnny K on 2008-09-20
> **anotherdisciple said:**
> Is this a trustworthy repo?

I would also like to know the answer to this question. How do we know that the repository is and will always be legit?

---

### Post by mb_webguy on 2008-09-20
> **anotherdisciple said:**
> haha... actually ... I was looking to learn how to install if from source.. but I'll mark it as solved anyways since this works.

VLC isn't something you want to learn with.  I have tried myself, and it's not pretty (and I have quite a bit of experience compiling on *nix system).  It has many dependencies, including quite a few libraries.  Since the versions of these libraries in the repositories aren't the newest ones which the newest version of VLC requires, you would likely have to compile these from source as well (as well as any libraries those libraries may depend upon, and so on).  There's a term for this: "dependency hell".

Compiling from source isn't really a mystery, nor is it very difficult unless the program has numerous unmet dependencies.  If anything, it's a chore best to be avoided.  All you have to do is extract the archive, then (in the terminal) change to the directory where you extracted the files.  If there is a file called "configure", then the directory does indeed contain compilable source code.  

Type "./configure" (occasionally with some optional arguments) to configure the code for your system and requirements, and go get some coffee or a soda.  Then type "make" to compile the code, and go get something to eat or take a nap.  You might even want to go see a movie.  If you have a slow computer and it's a big program, you might as well go to bed and check back in the morning.  Once that's done, type "sudo make install" to install the compiled application on your computer.

---

### Post by airtonix on 2008-10-13
>                      Originally Posted by **directcharitycontribution**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5806760#post5806760")                 
                 *u can mark solved now.*
No sorry you CANNOT! here is why : 
** the repo is NOT trustworthy, and there is no key for it.**

If you goto the vlc website and look at the main page it says 

> "UBER YAY NEW VERSION OUT PWNAGE!!!!?!?!?!? DOWNLOAD NOW YOU ****"So i click on the download link and oh yea i see...thats right i'm using ubuntu, so i click on that link.

But when i get to that page, there is no mention of this url **anywhere** :

>  deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy mainPlease provide a link to the official website that shows this url.

Its also very annoying that after following links for what you think are for the new version only take to the old version.

---

