---
title: "[SOLVED] cant get gnome only term"
date: 2008-11-10
forum: General Help
---

### Post by hydrohead on 2008-11-10
I am a newbie.  I have no idea what i did the last time i used ubuntu, but now I can not get the gui to boot.  I just get a brown-ish  screen that does nothing.(not the desktop, but the color that surrounds the log in screen)

if i try to boot to failsafe gnome, I get this error:

could not find the GNOME installation, will try running the "Failsafe xterm" session.

if I click on OK, I get a terminal.

Did I break it permanently, or is there a way to fix this in the terminal?


I believe that I am using the release before the one that just came out.  I am using Parallels on a Mac.

thanks

---

### Post by EXCiD3 on 2008-11-10
Try running this in terminal
```
sudo apt-get remove --purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

That will remove and reinstall the Gnome desktop for you and should fix your problems. I'm not sure what happened, did you do an upgrade recently or anything?

---

### Post by hydrohead on 2008-11-11
I am fairly certain that the last thing I did was upgrade Open Office to 3.

I will go give your suggestions a try

---

### Post by hydrohead on 2008-11-14
the command (sudo apt-get remove --purge ubuntu-desktop) tells me that the Ubuntu desktop is not installed and wont be removed.  It also tells me that there are three packages that where automically installed and are no longer required and to use apt-get autoremove to remove them.

I did use the autoremove to remove them.

the second code (sudo apt-get install ubuntu-desktop) gives me a lot of errors and and W:Failed to fetch messages.  They all appear to contain one of the fallowing:
     Could not resolve 'us.archive.ubunu.com'
     Could not resolve 'security.ubuntu.com'

I am guessing this is because I need to make an internet connection from the terminal before using that second code.  Am I reading the errors correctly?

---

### Post by geirha on 2008-11-14
Yes, that is what it means, it is unable to contact those servers, which is most likely because your network isn't set up. What kind of network connection do you have?

---

### Post by hydrohead on 2008-11-14
It is Parallels shared networking set to connect at start up.  That makes the connection between the VM and my Mac active.  Once Ubuntu was up and running, I had to click on the network icon in the upper right corner and actually make the network conncection.

My Mac is connected mostly wirelessly, although simetimes wired for security reasons to a router which is connected to my cable modem.

I do know that I could switch between wireless and wired with out effecting the connection within ubuntu.

I hope that gives you enough info, but feal free to ask for more if needed.

---

### Post by geirha on 2008-11-14
I'm afraid I have no idea how parallels work, but it might be as simple as running ```
sudo dhclient 
``` to have dhcp set up the network properly.

---

### Post by hydrohead on 2008-11-14
yes, that got me connected to the internet, thanks

---

### Post by hydrohead on 2008-11-14
thank you EXCiD3 and geirha, your help fixed my problem.  Once I got connected to the net, I had to run 'sudo apt-get install ubuntu-desktop' restart, then run it again, but I now have a desktop again.

---

### Post by EXCiD3 on 2008-11-14
> **hydrohead said:**
> thank you EXCiD3 and geirha, your help fixed my problem.  Once I got connected to the net, I had to run 'sudo apt-get install ubuntu-desktop' restart, then run it again, but I now have a desktop again.

Awesome! glad you got it working, having an internet connection is kind of important for using apt-get ;)

---

### Post by haplo_dk on 2008-11-25
I also want to say thanks !
I've worked all night to solve this problem.
I was installing lamp-server, and the installation halted/failed, and I found the desktop acted a little weird, so I rebooted.
I got to the login screen, and at first the mouse and keyboard didn't work - this solved it:
[http://www.linuxine.com/2008/10/uubuntu-810-betano-mousekeyboard-response.html#comment-104](http://www.linuxine.com/2008/10/uubuntu-810-betano-mousekeyboard-response.html#comment-104)
But then after typing username and passwords ubuntu just stopped/froze with the Ubuntu light tan colored background - nothing happened.
If I choose the failsafe gnome session it would say "gnome installation could not be found" and I would get a terminal and nothing else.
But the command for getting me on the internet "sudo dhclient" and then "sudo apt-get install ubuntu-desktop" saved my night - thank you so much !!! :-)

---

