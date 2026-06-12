---
title: "Help! Ubuntu won't boot!"
date: 2008-08-02
forum: General Help
---

### Post by weweboom on 2008-08-02
when i boot up ubuntu, it shows the tty or a black screen with a terminal like app running screen, and i can't get out of it, i tried repairing the x server in recovery mode, but nothing happened, I think i screwed up my xorg.conf but i'm not sure. help please

---

### Post by Diabolis on 2008-08-02
If you messed with your xorg.conf you can try to fix it with this command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by phidia on 2008-08-02
You can open another tty by pressing the Alt+Ctrl+F1 keys (F2 thru F7 also works in place of F1)  
Login and enter > sudo nano /etc/X11/xorg.conf to edit you xorg. You can try using the "vesa" driver in place of what's there an type "startx" to see if x will run. 
If xorg is too messed up you should be able to generate a new xorg by entering "sudo dpkg-reconfigure xserver-xorg" 
If you are using hardy be aware that [xorg is changed in hardy]("https://help.ubuntu.com/community/Video").

---

### Post by weweboom on 2008-08-02
thank you for responding but when i enter in sudo dpkg-reconfigure xserver-xorg
it responds with xserver-xorg is broken or not fully installed
and when I open up xorg.conf with nano the nano screen is blank, does that mean I deleted my xorg.conf

---

### Post by Diabolis on 2008-08-02
Reinstall the package:
```

sudo apt-get --reinstall install xserver-xorg
```

---

### Post by weweboom on 2008-08-02
again, thank you for responding but when i enter that i get a bunch of failed to fetch... then a unable to fetch some archives,maybe run apt-get update or try with --fix missing, neither work

---

### Post by Diabolis on 2008-08-02
```

sudo apt-get update
sudo apt-get --reinstall install xserver-xorg

```

---

### Post by weweboom on 2008-08-02
thanks but it didn't work either I think it's because my computer isn't accessing the internet for some reason because I tried to download a different package with the same result: a bunch of failed to fetches, can i somehow download it on my vista partition and install it? or is there a command to connect ubuntu to the internet i could type in? could i get the files off of the ubuntu live cd?

---

### Post by tom66 on 2008-08-02
If you use a wifi router, try getting an ethernet cable and connecting your computer or laptop through a cable, then you might have internet.

---

### Post by Diabolis on 2008-08-02
I think that you can install the packages that you need from the live-cd.

Yes, you can configure your internet connection through a terminal. It just depends on the type of connection, wireless or ethernet.

---

### Post by weweboom on 2008-08-02
it is connected via ethernet cord

---

### Post by noobuntu35 on 2008-08-02
> **weweboom said:**
> thanks but it didn't work either I think it's because my computer isn't accessing the internet for some reason because I tried to download a different package with the same result: a bunch of failed to fetches, can i somehow download it on my vista partition and install it? or is there a command to connect ubuntu to the internet i could type in? could i get the files off of the ubuntu live cd?

Hope this will help, Please forgive the M$ analogies I'm a recent Ubuntu convert, Just switched from M$ recently... try the command line and enter ifconfig it will list your Internet configurations (ipconfig M$) add the -a and it will show you all connections (ipconfig/all) this will tell you if you are connected, next, are you running a dual boot and able to connect from Vista? if so then download the Drivers you need to run the device to a Flashdrive. reboot into your *nix program and install the Driver from there. If you can post back the results of your ifconfig It might help some of the uber geeks lead you in the right direction to fix said connection

---

### Post by weweboom on 2008-08-02
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0  (0.0 B)  TX bytes:0  (0.0 B)

---

### Post by TreeFinger on 2008-08-02
What run level are you in?

```

runlevel

```

---

### Post by weweboom on 2008-08-02
I do have a vista partition but I am a giant noob and have no idea what the nix thing is

---

### Post by Diabolis on 2008-08-02
This is too messy, just go for a clean install. This is very strange, in your case, the internet connection should work out of the box.

*nix, means a unix based operating system.

---

### Post by weweboom on 2008-08-02
I'm in level N S

---

### Post by TreeFinger on 2008-08-02
I believe you are in single user mode. I never typed the command runlevel so I don't know what the output would be. From the man page N means there is no history of previous run level and I am guessing S means single user mode.

try switching run levels

```

telinit 2

```

--edit

oh, crap. i see now you went into recovery mode on purpose. I don't believe you have network access when in single user mode. Although, someone can verify this because I am not totally sure.

If you are trying to reinstall packages you would need network services.

---

### Post by weweboom on 2008-08-02
thanks but telinit 2 just restarted the terminal thing

---

### Post by Diabolis on 2008-08-02
Thats fine, changing your runlevel is supposed to enable networking services.

---

### Post by TreeFinger on 2008-08-02
> **weweboom said:**
> thanks but telinit 2 just restarted the terminal thing

now try to run the commands to uninstall and reinstall x as someone previously stated.

---

### Post by TreeFinger on 2008-08-02
> **TreeFinger said:**
> now try to run the commands to uninstall and reinstall x as someone previously stated.

if you went back to recovery mode, I believe the following command will start your network services

```

service network start

```

then run the commands to reinstall and install x, hopefully it will work out for you.

---

### Post by noobuntu35 on 2008-08-02
> **weweboom said:**
> Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0  (0.0 B)  TX bytes:0  (0.0 B)

you are not connected. Obviously, Sorry I should have explained *nix but its been done, so many Flavors (versions) of the Linux/Unix installs that *nix is a generalization. 127.0.0.1 is your computer or linbox. the default mask is also a sure sign that the connection is missing. are you using a router? I can also see that your system does not show a card installed it would have shown as eth0 or eth1 I will help you to find the right CLI to get this up and running. you need to verify the card is installed. I am off to read for a few minutes check back in about 5 minutes or follow the UBERGEEKS. (the really old hacker guys, actually whitehat crackers is the right term but who's counting :p )

---

### Post by Diabolis on 2008-08-02
No, actually the right term is hacker for the good guys and cracker for the bad guys.

And It would surprise me if the problem was his card, as the posts above have proved. He was in recovery mode and the networking services were off.

---

### Post by noobuntu35 on 2008-08-02
> **Diabolis said:**
> No, actually the right term is hacker for the good guys and cracker for the bad guys.

And It would surprise me if the problem was his card, as the posts above have proved. He was in recovery mode and the networking services were off.

fair enough, so let it be written so on so forth Hacker then we're all good guys/gals (to me Cracker sounds horrible anyway...) however where is his eth card in his ifconfig, its not listed. beyond that I missed if the internet is connected through vistan and not linux if its a dual boot or what have you, lastly did you try ifconfig -a , Still reading (college books are good for something)

---

### Post by noobuntu35 on 2008-08-02
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:## <-- not important 
          inet addr:192.168.1.101 <-- router assigned (linksys)
          Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe06:71d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1209788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:722200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1724689685 (1.6 GB)  TX bytes:63698999 (60.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5947 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304825 (297.6 KB)  TX bytes:304825 (297.6 KB)

john@ubuntu:~$ 
this is what mine looks like, just ifconfig

---

### Post by weweboom on 2008-08-02
i enabled network services, then did apt-get --reinstall install xserver-xorg and still is says failed to fetch...

---

### Post by noobuntu35 on 2008-08-02
are you logged on as root? if not use the sudo (Super user do) command at the beginning of your command I.E. sudo apt-get install... 
it will ask for the password for your sudo (you) if you have administrative control it will go through try this if you havn't yet.The sudo will keep things from going through if you are not signed on as the root user.

---

### Post by weweboom on 2008-08-02
thanks, all of you I FIXED IT!!!!!!!

---

### Post by Diabolis on 2008-08-02
Great, don't forget to mark the thread as solved.

---

### Post by TreeFinger on 2008-08-02
could you mark the thread as solved and tell us what you did that made it work again?

---

### Post by Diabolis on 2008-08-03
He changed his runlevel by typing the command that you gave him or by booting into normal mode and then he executed the commands that I gave him.

to summarize:
```

telinit 2
sudo apt-get update
sudo apt-get --reinstall install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mahela007 on 2008-08-03
hello guys........
I have a similar problem where ubuntu wont boot.
i tried booting it in safe mode. It proceed up to a certain point and then is gives a repeating bunch of errors about "sda6". what does this mean?

---

### Post by Diabolis on 2008-08-04
errors that say "sda" are related to a partition problem. Maybe a drive is not mounting correctly.

Please be more specific with your problem so we can help you.

---

