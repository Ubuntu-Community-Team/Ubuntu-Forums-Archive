---
title: "Not Optimum Mode GTX1070"
date: 2016-09-10
forum: Hardware
---

### Post by deedee8 on 2016-09-10
Hi everyone. I've just completed my new PC build and decided to give Ubuntu a shot. While I was installing the OS (Ubuntu 16.04), my monitor would turn black after I started the installation and displayed the following message:

"NOT OPTIMUM MODE
Recommended mode 1920x1080 60hz"

I have a Gigabyte GTX1070 graphics card. After troubleshooting for hours I finally fixed this by going into grub and adding "nomodeset" in the command line, as explained in this post:
[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132).

The installation was successful, but unfortunately now that the system rebooted I am getting the same problem, but that fix is no longer working. My monitor goes to black and I get the same error message.

I tried going into recovery mode, and typing ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` to get the drivers

I made sure to enable networking, and I am connected to ethernet, however I get a series of error messages along the line of: "Failed to fetch http://us.archive.ubuntu/..."
I tried pinging Google's DNS and that worked fine, so my internet connection should be working.

If anyone has any idea how to fix this, please please please help a noobie who just wants to get away from proprietary software :)

---

### Post by CantankRus on 2016-09-10
The networking option didn't used to work in recovery.
Thought would have been fixed by now.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("https://ubuntuforums.org/showthread.php?t=2253852&p=13172632#post13172632") to enable networking in recovery mode.
Run ifconfig to get your network interface. (or iwconfig)

**[COLOR="#FF0000"]Edit[/COLOR]**: Can't get this to work in 16.04.
When you get to the login screen or a blank screen, try pressing ctrl+alt+F1 to get a tty login prompt.

---

### Post by deedee8 on 2016-09-10
Thanks for the quick reply!

I tried enabling networking in recovery using dhclient, but that didn't seem to do anything. I still got the "failed to fetch" errors. 
Unfortunately, I can't do the ctrl-alt-F1 trick because I can't actually reach a login screen (when I do its simply a purple background without anything on it, and I'm forced to reboot my computer).

Would it be possible to download the necessary driver(s) onto a USB from my macbook, then insert the USB into my desktop and install them from there? If so, how could I do it in recovery mode?

---

### Post by CantankRus on 2016-09-10
> **deedee8 said:**
> Thanks for the quick reply!

I tried enabling networking in recovery using dhclient, but that didn't seem to do anything. I still got the "failed to fetch" errors. 
Unfortunately, I can't do the ctrl-alt-F1 trick because I can't actually reach a login screen (when I do its simply a purple background without anything on it, and I'm forced to reboot my computer).

Would it be possible to download the necessary driver(s) onto a USB from my macbook, then insert the USB into my desktop and install them from there? If so, how could I do it in recovery mode?

I can't get networking in recovery either. Used to work.

If you only edited the grub screen to add nomodeset you will have to do it again as it only lasts for that boot.
To make permanent you would need to edit the file /etc/default/grub

---

### Post by Bashing-om on 2016-09-11
deedee8; Hello;
Start Networking from rescue mode 16.04 - systemd:
```

systemctl enable NetworkManager.service
systemctl start NetworkManager.service

```
see if that does it.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by CantankRus on 2016-09-11
> **Bashing-om said:**
> deedee8; Hello;
Start Networking from rescue mode 16.04 - systemd:
```

systemctl enable NetworkManager.service
systemctl start NetworkManager.service

```
see if that does it.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

Does this work for you?
After dropping to root shell and remounting in rw, the first command returns me to the command prompt but
second command doesn't.

---

### Post by deedee8 on 2016-09-11
Thanks to both of you for helping! I finally got it to work and I can't wait to start ubunting (and move on to the next challenge i guess).

Here's what worked for me in the end, using bits and pieces from all over the internet:

First I temporarily added a temporary DNS server to my system: ```
[COLOR=#111111][FONT=Consolas]echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null[/FONT][/COLOR]
```
This allowed me to run "sudo apt-get update" and "sudo apt-get upgrade" without the "failed to fetch" errors. However, there were still a few errors popping up, so I tried resuming the normal boot, and I got to the login page successfully. From there I could do ctr-alt-F1 to access tty and connect to the internet. Then I ran apt-get update and upgrade, and got all the packages installed successfully.

All of that seemed to have done the trick. I'm not sure exactly which bits contributed and which were redundant, but I'm glad I made it past the login screen.

Now I'll make sure to download all the necessary drivers and adjust the screen resolution / Input timing to make sure that it doesn't happen again. Will follow up if anything comes up.

Thanks again!

---

### Post by Bashing-om on 2016-09-11
CantankRus; Hey ..

I am not fluent in systemd . but
I have tested this procedure in my 16.04 test install and indeed it does work for me to enable networking (wired) .

I do think that I also started the GUI :
```

systemctl isolate graphical.target

``` I am under advisement :
> 
That does much more than just start the GUI, it also stops everything that is not a dependency of graphical.target.

We have a lot to learn .

[INDENT][INDENT]is this fun or what
[/INDENT][/INDENT]

---

### Post by CantankRus on 2016-09-11
> **Bashing-om said:**
> CantankRus; Hey ..

<-------------->

We have a lot to learn .



....and I have plenty of empty space to store it. :P

---

