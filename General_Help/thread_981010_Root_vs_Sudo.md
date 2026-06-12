---
title: "Root vs Sudo"
date: 2008-11-13
forum: General Help
---

### Post by drcoracle on 2008-11-13
I have a program that MUST be installed as root, it will not install with sudo.

It also must be run as root.

How do I do this?

---

### Post by taurus on 2008-11-13
```
sudo su
```

---

### Post by Coreigh on 2008-11-13
What program? Have you *tried* sudo?

Information on sudo vs root:
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by BenAshton24 on 2008-11-13
It will not install with sudo :S well sudo is basically root. Have you checked that the program has executable permissions. right click on file --> properties --> Permissions tab --> check the button that says execute file as program (assuming it is one file and doesn't require configuration / making etc.). Then try install it again.

If you really are fusses about root then you can type "sudo su" in terminal and that should give you root. or, "sudo apt-get install su" then just run su from terminal.

Hope this helps :D

--Ben.

---

### Post by Portmanteaufu on 2008-11-13
If you do:

```
sudo -i
```

it will drop you into a root shell. (Be sure to type 'exit' when you're finished.) However, sudo effectively makes you root for the one command so your problem sounds strange to me. If you don't mind my asking, what exactly are you trying to do? Could you post your commands and their output?

---

### Post by Coreigh on 2008-11-13
Ben has a good point it is more likely a permissions problem. If the program in question is asome type of binary installer you need to make it executable.
```
sudo chmod +x /path/filename
```

so if the file is in your home folder and it is named GameInstaller the it would be this:
> sudo chmod +x ~/GameInstaller

---

### Post by drcoracle on 2008-11-13
I will when I get home in a couple of hours. I am trynig to install a program that monitors a MMORPG program across the network. 
In reality it is a packet sniffer but it is not malicious. It takes data being received by the other program, parses it, and displays that same data in a different format. There is a Windows version but it sucs. I finally got Ubuntu two work on 3 of my machines, after all the trouble a couple of months ago. a Gateway Laptop, A Gateway Desktop and a HP 310W.

Basically I have been experimenting with it, at the user level, nothing that would not install using the Package installer.

This is my first attempt to get this involved.
I also fialed at getting Java installe deven though I followed the instructions line by lin.

Thanks.

---

### Post by drcoracle on 2008-11-13
Yes I did.
The program is ShowEQ

---

### Post by iponeverything on 2008-11-13
> **drcoracle said:**
> I have a program that MUST be installed as root, it will not install with sudo.

humm.. I would like know what program must be installed as root but will not install as root. ;) ahh ok ShowEQ.

> 
It also must be run as root.

ditto

> 
How do I do this?

if you add a - to your su, you'll take the root environment along.

---

### Post by drcoracle on 2008-11-13
> **BenAshton24 said:**
> It will not install with sudo :S well sudo is basically root. Have you checked that the program has executable permissions. right click on file --> properties --> Permissions tab --> check the button that says execute file as program (assuming it is one file and doesn't require configuration / making etc.). Then try install it again.

If you really are fusses about root then you can type "sudo su" in terminal and that should give you root. or, "sudo apt-get install su" then just run su from terminal.

Hope this helps :D

--Ben.



Did not try thhis will look when I get home.

---

