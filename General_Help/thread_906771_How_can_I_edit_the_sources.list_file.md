---
title: "How can I edit the sources.list file?"
date: 2008-08-31
forum: General Help
---

### Post by Vanillalite on 2008-08-31
I'm trying to update KDE 4.03 to KDE 4.1. On Kubuntu's website it has [upgrade instructions]("http://www.kubuntu.org/news/kde-4.1")


Submitted on Tue, 2008-07-29

KDE 4.1 has been released and packages are available for Kubuntu 8.04, the Hardy Heron. These packages install to /usr/lib/kde4 and can be installed along side your existing KDE 3 installation.
Instructions

The updated packages for Kubuntu 8.04 are located in the Kubuntu Member's KDE 4 Personal Package Archive (PPA) repositories. To update to KDE 4.1, please follow these instructions:

   1. Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main to your /etc/apt/sources.list.
   2. If you already have the kubuntu-kde4-desktop packages installed, simply type sudo apt-get update && sudo apt-get dist-upgrade and answer the questions in which you are prompted. If you do not have kubuntu-kde4-desktop installed, simply type sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop and answer the questions. Both of these options are to be typed at the command prompt.

kdeplasma-addons contains new Plasma fun.

Thanks to Harald, Guillaume, Steve, Jon and Arby for preparing these packages.


Anyways so I can do step 2 fine I think but can't figure out what to do with step one. If I navigate to it graphically I can open the file, but I'm not sure exactly where to type the line and even if I just add the line to the end it won't left me save because I'm not root.

I can navigate in the terminal to the actual folder etc/apt but then I'm not sure what I'm suppose to type in the terminal to open the file so I can type the line in and save. I assume it's sudo something but frack if I know.

Sorry I'm a total newb, and thanks in advance! :)

---

### Post by mb_webguy on 2008-08-31
Well, you could type "kdesu kate /etc/apt/sources.list" in the terminal and edit the file using Kate, or you could simply type "sudo echo deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main >> /etc/apt/sources.list" to add the line to the end of the file.  (And make sure you use >>, because a single greater-than will replace the contents of the file with the line, rather than append the line to the end!)

---

### Post by Vanillalite on 2008-08-31
When I try the first way it says the command is not found.:(

The second way seems like it would work, but it tells me permission is denied?

Any ideas on either of that?

---

### Post by RedSquirrel on 2008-08-31
> **mb_webguy said:**
> ... or you could simply type "sudo echo deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main >> /etc/apt/sources.list" to add the line to the end of the file.  (And make sure you use >>, because a single greater-than will replace the contents of the file with the line, rather than append the line to the end!)

The sudo applies to the echo, but not to the redirection. Hence, you have to use tee for this situations like this. 

```
echo "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list
```See:
[https://help.ubuntu.com/community/RootSudo#Downsides%20of%20using%20sudo](https://help.ubuntu.com/community/RootSudo#Downsides%20of%20using%20sudo)

---

### Post by mb_webguy on 2008-08-31
> **RedSquirrel said:**
> The sudo applies to the echo, but not to the redirection. Hence, you have to use tee for this situations like this. 

```
echo "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list
```See:
[https://help.ubuntu.com/community/RootSudo#Downsides%20of%20using%20sudo](https://help.ubuntu.com/community/RootSudo#Downsides%20of%20using%20sudo)

*blink blink*  Oh, yeah.  I knew that.  Sorry.  I wasn't thinking...

The reason the first method might not have worked is if you've uninstalled Kate (which should be the default text editor in Kubuntu).  I assumed since you said you're using Kubuntu that you'd have Kate.

---

### Post by Vanillalite on 2008-08-31
> **mb_webguy said:**
> *blink blink*  Oh, yeah.  I knew that.  Sorry.  I wasn't thinking...

The reason the first method might not have worked is if you've uninstalled Kate (which should be the default text editor in Kubuntu).  I assumed since you said you're using Kubuntu that you'd have Kate.

What's funny is I looked up in the package manager and it says Kate is installed. No clue why that way didn't work. I'm about to try the new suggestion above though now and will let you all know. Thanks a ton for the help!

---

### Post by Vanillalite on 2008-08-31
Money! Thanks a ton guys. The new line worked first try, and then I just did what it told me to do in the first part of step 2 and on my way we went. I just rebooted and bam KDE 4.1! This is actually the first thing I'm doing. Now to check things out and see the differences between 4.03 and 4.1. :)

Seriously thanks again! :D

---

