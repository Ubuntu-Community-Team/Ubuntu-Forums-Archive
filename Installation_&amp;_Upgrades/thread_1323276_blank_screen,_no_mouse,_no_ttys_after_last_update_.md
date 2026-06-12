---
title: "blank screen, no mouse, no ttys after last update 9.10"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by josvanr on 2009-11-11
Have been running kubuntu 9.10 with kde and gnome (on laptop
packard bell bg46). After  running the last update and 
rebooting, I see the blue kubuntu logo with progress bar, but 
then only a blank screen. I tried to switch to a text terminal
(alt-fn) but that doesn't work. When I choose the previous 
kernel in grub (2.6.31-14-generic) I see the same. Using the
kernel before that to start up (2.6.27-14-generic) kubuntu 
starts in a low graphics mode (hence I can write this mail). 
Then kdm start up and I can start kde or gnome.
But still I have no mouse, but my wacom graphics tablet does
work. What is the way to proceed in a case like this? Is there
some way to repeat the update (in case something went wrong?)

Here I some error messages I see when kubuntu is saying it is 
starting in low graphics mode:

(EE) intel(0): [drm] Failed to open DRM device for: No such file or directory
(EE) intel(0): [drm] Failed to open DRM master
(EE) intel(0): [drm] Failed to initialize kernel memory manager
(EE) SynPS/2 Synaptics touch pad: Unable to query/initialize Synaptics hardware
(EE) PreInt failed for input device "SynPS/2 Synaptics TouchPad"
(EE) config/hal: New input device request failed (8 )

---

### Post by josvanr on 2009-11-11
hello, I just managed to download the live cd for kubuntu 9.10, and I can boot up the system from the cd with no trouble.. (is this any help?)

josvanr

---

### Post by moomooranch on 2009-11-12
I have the same problem...I've deleted the 2.6.27 kernels so I can't try what you did, but I have the same symptoms on my Kubuntu system using both the 2.6.31-14 and 2.6.31-15 kernels (generic). I had enabled the 

deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) karmic main

repository before this happened. This started happening after an update two days ago. Yesterday, I was able to log into Kubuntu after booting once into Vista, shutting down, and starting Kubuntu. Today, after installing some more updates, I am not able to get a graphical interface at all. Not sure what is going on but I seriously need to access my work :(

After the blue Kubuntu bar fills up and the black screen appears, pressing Alt+Ctrl+F1 brings me to a screen with a gray cursor, and Alt+Ctrl+F2 then brings me to a terminal. The combination must be in this order. But it is only a snapshot of a terminal; typing does not register. To do anything in the Alt+Ctrl+F2 terminal, you have to switch back to the Alt+Ctrl+F1 terminal, type what you need to, and then switch back to Alt+Ctrl+F2 to see the results. I have tried, using this method, to reconfigure the xserver, but it did not help. I've also uninstalled mysql to prevent it from starting up during boot, but it didn't fix this problem.

I've removed the quiet option in the grub menu but I still don't see any messages during boot.

Another thing unique on my system is that I have uninstalled network-manager in favor of wicd.

---

### Post by moomooranch on 2009-11-12
I've solved the problem; kdm is to blame.

Using the technique of logging into a terminal that I described above, type:

dpkg-reconfigure gdm

Then, select gdm and press enter. If you don't have gdm, install it first. After the install, the installer should ask you whether you prefer kdm or gdm; choose gdm.

Sigh, now off to reinstalling/reconfiguring everything I uninstalled in trying to fix this problem.

Ubuntu again proves that its a Gnome-centric distro :(

---

### Post by josvanr on 2009-11-14
bah what a pain! I ended up just reinstalling the entire distribution (ubuntu/gnome this time)....

---

### Post by ppietryga on 2009-11-16
josvanr:
Are You using proposed-updates repository?
If Yes the issue was with **kdm** from that repository (v. 4.3.2_ubuntu7.1 AFAIK).

I had the same issue (I even filed a bug #482143 on Launchpad, with no response). The proposed-updates repository is marked as providing packages that can cause some instability, so should be used only by users willing to help in testing packages, before they appear in updates repository.

Regards
ppietryga

---

### Post by drpjkurian on 2009-11-18
> **moomooranch said:**
> I've solved the problem; kdm is to blame.

Using the technique of logging into a terminal that I described above, type:

dpkg-reconfigure gdm

Then, select gdm and press enter. If you don't have gdm, install it first. After the install, the installer should ask you whether you prefer kdm or gdm; choose gdm.

Sigh, now off to reinstalling/reconfiguring everything I uninstalled in trying to fix this problem.

Ubuntu again proves that its a Gnome-centric distro :(

Dear Moomooranch

Thank you very much.Your advice helped me a lot.

With regards
dr kurian

---

### Post by AtesComp on 2009-11-18
I had the "low-graphics" problem (low-graphic warning, OK, OK, OK, then KDM starts OK--if I did it fast enough) on three completely different system, including a laptop.  This includes one upgrade and two fresh installs.   Here is my story:

What I got to apparently work on two systems was to edit the GRUB2 default file (/etc/defaults/grub).  I changed the following two vars to be as follows: 
```
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="splash"
```It had "splash" in each line for some dumb reason FOR EVERY SYSTEM!  It also had a "vga=" something for 640x480 mode that was reporting the vga option as deprecated.  I took out the "quiet" option so I could see what was going on.  I don't know why these options would cause the problem, but it cleared up the laptop.  However, I think that was just a fluke in the startup timing.

As stated previously, the real problem seems to be the new KDM in the new KDE from the proposed-updates.  The laptop worked fine until I added the proposed-updates and updated KDE.  The laptop didn't have an Nvidia graphics controller, so it probably moved the problem by offsetting a timing problem present in KDM.

The other system that "worked" with the GRUB2 fix still has a problem starting which is why I think it is a critical timing problem in KDM.  Sometimes it would start, other times not...and I would get an annoying, very rapid beeping from the motherboard.  This system has an on-board Nvidia graphics controller.

The last system has an Nvidia graphic card.  The GRUB2 fix didn't do anything for this system.  The KDM->GDM fix did!

The best fix so far is to switch from KDM to GDM--at least for now.

---

### Post by Larik on 2009-11-26
Hi,

I think I got the same or at least a similar problem. After a few weeks (dont remember exactly), I also got this "low graphic mode" error on kdm. A click on "ok" and "cancel" makes kdm start somehow.
When I switch to gdm everything works fine. So this timing thing might be a cause for it.

kdm.log says:


[LIST=1]
[*]ddxSigGiveUp: Closing log
[*]Warning:  Failsafe mode was already attempted within 30 seconds.
[*]Warning:  Falling back to gdm to report the issue.
[/LIST]

Full logs can be found here:

 kdm.log [http://pastebin.com/d3dd48317](http://pastebin.com/d3dd48317)
xorg.0.log [http://pastebin.com/d4b047286](http://pastebin.com/d4b047286) 

xorg.conf [http://pastebin.com/d1471cb3b](http://pastebin.com/d1471cb3b)


Graphics card is a NVIDIA 6600GT. Tried all drivers (also the original from NVIDIA).

---

### Post by AtesComp on 2009-12-01
There is a timing problem.  KDM doesn't wait long enough.

SOLUTION:
Edit the file /etc/kde4/kdm/kdmrc with your favorite editor:
```
sudo nano /etc/kde4/kdm/kdmrc

```
Under the [X-*-core] section (careful, there are several very similarly named sections) add or change the "ServerTimeout" parameter:
```
ServerTimeout=120

```
Save it and reset your "gdm" to "kdm":
```
sudo dpkg-reconfigure kdm

```
  Then select "kdm" and "ok".

Reboot and your golden!

---

### Post by AtesComp on 2009-12-02
Ok, not so golden.  The first reboot worked well.  The second reboot STILL gave me the "low graphics" messages.  This is REALLY getting old.

---

### Post by depeha on 2009-12-02
Hi... I´ve got same problem...
I updated KDE to 4.3.4 today (there was also 9 bug fixes), reboot laptop, kubuntu splash showed up for few seconds, and fater that just black. when I press ctrl+alt+F1(-F6) still nothing... I tried recovery mode, older kernel... just black screen :(  Is there some another way, instead of reinstalling whole ubuntu??

---

### Post by Larik on 2009-12-02
@AtesComp

Also didn't work for me. :(
GDM has some bad influence on the fonts in KDE (at least for me), so I really would appreciate KDM working as intended again. KDM worked until an (evil) update, but as I said I don't know when it was

---

### Post by wnelson on 2009-12-02
It is not a fix. I think it has something to do with Dbus. 
Try Alt-PrtScr R E this might drop you to a prompt to login. Login. The su to root and run gdm/kdm?

---

### Post by seascape on 2009-12-03
and if you can't get to the login screen, here is the complete sequence for shutting down:

Alt+SysRq+R+S+E+I+U+B

[http://www.botskool.com/forum/computer-programming/linux/unix/restartshutdown-frozen-linuxubuntu](http://www.botskool.com/forum/computer-programming/linux/unix/restartshutdown-frozen-linuxubuntu)

---

### Post by manishsk on 2009-12-06
Check out, hope that helps. I have filed a bug for the same.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483)

---

### Post by AtesComp on 2009-12-08
The problem I had was solved. It is related to GDM being installed, but using KDM. The fix is now in karmic proposed updates as a GDM update.

Yes, the 491483 bug is the problem!

See [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483)

---

### Post by Larik on 2009-12-15
For me the problem has gone after the update. Using latest Nvidia driver. No more complains from kdm.
Who ever fixed it, thank you a lot!

---

