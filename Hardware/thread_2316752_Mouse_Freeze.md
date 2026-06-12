---
title: "Mouse Freeze"
date: 2016-03-10
forum: Hardware
---

### Post by lile001 on 2016-03-10
I searched in these forums for a solution, but could not identify anything that seemed relevant.  There is a thread [here]("http://askubuntu.com/questions/489907/ubuntu-14-04-frequent-mouse-freeze") that seems relevant, but I've had little luck in following the advice found there.  Here goes:

I am running Ubuntu 14.04 LTS on a Dell T5500 with dual processors and 24G memory, relatively new install on a new box.  Running Gnome, not Unity. I am running a Logitech M705 wireless mouse.  Also running a logitech wireless keyboard on the same bluetooth connection, no problems.    I run for days at a time with no issue.  

Then occasionally, the mouse, although the cursor moves, does not respond to a button click.  Left click does not pick anything, Right click doesn't do what it is supposed to do in context.  Keyboard seems to work, mouse cursor moves around,  things that respond to mouse cursor focus like autohide top menu respond normally.  Turning the mouse on and off doesn't fix the issue, nor is it fixed by plugging in a wired mouse. Conky reports that I am using 1% of my CPU, so the CPU isn't taxed.  TOP reports that the usual suspects are running at a low hum:  Chrome, and a few other things at less than 1%, nothing seems to be hogging the CPU.   

The Big Hammer solution I have been using is to reboot. Usually I can bail out of whatever program I am in using keyboard shortcuts to save work, not always (remember kiddoes: Control S is your friend!)  I was using sudo service  lightdm restart, but lately that just hangs, so I've ended up doing a hard reboot.  

Xev reports keyboard activity, and mouse focus activity, however does not report that I have pressed a mouse button once I get The Freeze.  

Reinstalling mouse drivers hits a wall, as follows: 

```
 sudo apt-get --reinstall install xserver-xorg-input-mouseReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xserver-xorg-input-mouse : Depends: xorg-input-abi-20
                            Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.



```


I'm kind of stuck after that.  This dependency thing may or may not have anything to do with the problem.  I've tried to dig into this dependency thing but swiftly get in over my depth.


[/EDIT]  Some added info, possibly relevant: 


[COLOR=#111111][FONT=Consolas]```
 dpkg --get-selections | grep hold  
```
reports nothing. I have only a vague understanding of what this should accomplish. From  [here]("http://askubuntu.com/questions/596045/mouse-and-keyboard-freezes-after-suspend-in-can-not-install-xserver-xorg-unme")
Other suggestions on that page are a bit out of my depth and likely only semi-relevant so I am afraid to try them.  

[/EDIT]

here is the output of apt-get -f install

[/FONT][/COLOR]```
sudo apt-get -f install[sudo] password for lawrence: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.

```

I'm not sure but I think the 22 "not upgraded" are a problem (once again out of my depth here.) 

[/EDIT]

Tried following [this]("http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa"): 

```
  sudo apt-get -u dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-locale-en gdm gir1.2-gdm-1.0 libbind9-90
  libdns100 libgdm1 libisc95 libisccc90 libisccfg90 liblwres90 libmm-glib0
  libnautilus-extension1a libnss3 libnss3-nssdb modemmanager nautilus
  nautilus-data usbutils xserver-xorg-core-lts-vivid
22 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.6 MB of archives.
After this operation, 676 kB of additional disk space will be used.
Do you want to continue? [Y/n] y

```

which proceeded to install a number of packages - could this be the fix?  Don't know yet.  


Now we have: 

```
 sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Does this mean that these 22 packages were fixed?  Perhaps xserver-xorg-core-lts-vivid was one of the bad actors?  Or am I on a wild goose chase?  As the problem only occurs every several days I won't know for a while if this is really the issue or a sideshow.  



[COLOR=#111111][FONT=Consolas]

 



[/FONT][/COLOR]

---

### Post by jbMacAZ on 2016-03-15
I'm running Cinnamon over Ubuntu15.10 (Asus T100-CHI 2GB RAM, Z3775) and I've seen the same mouse click issue.  I've seen it on wireless and bluetooth mice.  Sometimes, if I leave it idle for a few minutes, the mouse buttons start working again, but rebooting is more reliable.  Sometimes the touchscreen still works and a few taps on the screen restores the mouse.  The mouse freeze doesn't happen very often, and I can't provoke on demand.    It's a small comfort to know I'm not the only one.  I was beginning to think that my mouse buttons were getting worn out.

---

