---
title: "Strange session problem on Acer Travelmate 364 ECi"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by karmik on 2006-09-04
Hi forumers. I come from a Gentoo 2006.0 Fvwm 2.15 envinronment on my desktop machine but i wanted to try Ubuntu on this old laptop which i recently obtained. I never used gnome nor any complex DM so if the answer to this question seems pretty obvious to you please forgive me in advance.
Also, i'm not too sure on the forum's policy about logs and images size so i'll post mine as links.
I've a TM364 ECi (namely PIII M 1,2 GHz, 512 MB Ram, Chipset Intel 830, 30 Gb HD) and i'm experiencing this strange and annoying problem:
Both in the live-cd envinronment and in the regularly installed version, at start i got nothing but the X server on screen.

[http://img172.imageshack.us/my.php?image=screenshotao5.jpg]("http://img172.imageshack.us/my.php?image=screenshotao5.jpg")

I suspect some gnome component hang up during the boot because from a 
```

karmik@carrot:~$ ps aux
```
I receive this

[http://silenceisdefeat.org/~karmik/process.txt]("http://silenceisdefeat.org/~karmik/process.txt")

I can clearly see that a lot of GUI-related processes are running but nothing appear on the screen. Please note that in the beginning even the xterm window wasn't running, i had to switch to console and run an xterm -display :0. 

I then tried to start the session-manager cause i figured it was a good try in order to start the installed desktop envinronment, but all i get is this:
```

karmik@carrot:~$ gnome-session
SESSION_MANAGER=local/carrot:/tmp/.ICE-unix/6526
```
So it sets its env variable but nothing happen.


I thought that even a pci list might come in handy:

[http://silenceisdefeat.org/~karmik/lspci.txt]("http://silenceisdefeat.org/~karmik/lspci.txt")

Hope these aren't stupid questions but both surfing and browsing your nice forum didn't work for me. 

Any suggestion would be MUCH appreciated, thanks :)

---

