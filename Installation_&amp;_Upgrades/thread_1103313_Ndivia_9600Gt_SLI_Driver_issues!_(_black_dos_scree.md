---
title: "Ndivia 9600Gt SLI Driver issues! :( black dos screen when restricted drivers installd"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by iamblue on 2009-03-22
i have a asus m2n-sli,Nvidia 9600gt Sli, and installed the ubuntu 8.10,when i install the restricted drivers for the graphics card it asks for reboot ,which i do then after i do the reboot instead of getting the ubuntu log in screen a get a black-dos screen  like login "$blue-desktop"
       "Pw:"
and i cant get into my regular desktop ive tried all the f1 commands to see if that may be the issue also restarted the x server,manually installed the drivers(which failed to install as well).i think ive installed and uninstalled ubuntu if anything 15 times because of the driver problems.PLEASE can anyone help me:(

---

### Post by tommcd on 2009-03-22
Remove all nvidia drivers you may have installed. If you enabled the nvidia driver from the restricted drivers manager, then disable it. If you instlalled them manually reome them usid the "apt-get remove --purge" option.
Then reboot. Then hit ctrl + alt + F2 to get to a virtual terminal. Login and run these commands:
```
sudo /etc/init.d/gdm stop
sudo apt-get install nvidia-glx-180

```
This will stop the X server, and install the newest nvidia driver from the Ubuntu repos. Then you need to run the nvidia-xconfig utility to enable the driver. See this page for specific options related to SLI:
[http://ubuntuforums.org/showthread.php?t=607385](http://ubuntuforums.org/showthread.php?t=607385)
After running the nvidia-xconfig to enable the driver, run:
```
sudo /etc/init.d/gdm start
```
This will restart X. Then hit ctrl + alt + F7 and you will be back to the Ubuntu desktop. Run:
```
glxinfo | grep -i direct
```
to see if the driver is enabled properly. It should return "direct rendering: yes". Run "sudo nvidia-settings" and you will get the nvidia configuration utility. You should see options for SLI in there if it is set up right.

---

### Post by iamblue on 2009-03-22
thanks for reply :p
nope..it does the exact same thing..when i do <ctrl>+<alt>f7 all i see is a dash blinking..and i get the same picture is saw .

---

### Post by tommcd on 2009-03-22
Since you are having so much trouble, if it were me I would:
1.Remove one of the video cards and run in single (no SLI) mode.
2.Do a clean install of Ubuntu 8.10. Verify that the system boots ok in 2D mode using the "nv" driver. If it doesn't, reboot to recovery mode and choose the option "Xfix fix the X server".
3.Once you get a working  desktop in 2D with the "nv" driver, backup your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
4.Install the nvidia-glx-180 driver as I described in my last post. Run "sudo nvidia-xconfig" (just like that, with no SLI options) and reboot.
5. Verify that the 3D nvidia driver is working with:
```
glxinfo | grep -i direct
```
6.Once you get the nvidia driver working ok, backup your xorg.conf again:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
```
Then consider replacing the 2nd video card and perhaps try SLI again.
This will simplify things so you can proceed step by step. If you have trouble installing from the live CD then use the alternate CD.

---

### Post by MountainMan2000 on 2009-03-23
Hello,

I have exactly the same issue and the same results when I tried to follow the earlier debug help.  I really would prefer to not start disassembling my system to get this issue resolved.  Nor do I like repeatedly reinstalling an OS.  I guess these are both philosophical hangups on my part. . .

Anyway, I have two NVidia cards in my system.  One is a 260 and the other is an 8800GT.  I have one monitor on each.

My initial install hit a problem and wasn't able to display partway through so I went back and selected an option to do a safe graphics install.  That worked and all was well.  The system automatically detected that I should install the Nvidia driver and showed a few, the newest of which was 177.  I ran the install and had the same problems described above.  I followed the recommended actions and it removed 177 and installed 180.  But still no GUI.

Whenever I try to switch to the GUI I just get a blinking cursor.  When I run a command that wants to open a GUI window I get an error such as "cannot open display".

Could it be that gdm needs some hand holding to tell it to use one of my graphics cards and displays as the primary?

Anyway, help would be appreciated.  The last time I tried to use unix (probably around 5 years ago) my attempt was aborted because I could never get my sound card and other hardware working.  I've heard there has been much improvement so I'm hoping I can figure this out.

Thanks.

---

### Post by iamblue on 2009-03-23
ya i still get that black screen. :( its so weird,it only happens when these drivers are installed,besides the video drivers do i have to install motherboard drivers as well?can that be the problem?

---

### Post by MountainMan2000 on 2009-03-23
I think its pretty clear what is going on but the solution is not simple.  The file /etc/X11/xorg.conf contains all the configuration settings that make ubuntu's xwindows GUI work correctly with a particular set of graphics cards and monitors.

You can go to the directory in ubuntu, view it, edit it, etc. to manually configure your hardware but its tough to do so without having a pretty advanced understanding of that files parameters.  Maybe somewhere there is a detailed guide to how the nvidia driver needs to be configured in the xorg.conf file.

I had no problem at all installing the latest nvidia drivers per the instructions above.  But these drivers expect to be told the right settings in xorg.conf.

Nvidia has included a configuration tool to help make these settings easily but it only runs under xwindows.  Since xwindows won't run unless the settings are basically correct, its not a good solution for the initial setup.

I reinstalled to get the gui working again and now I'm going to try to sneak up on a solution by backing up the files and maybe trying to install the nvidia driver and configure it before rebooting.  We'll see.

---

### Post by iamblue on 2009-03-23
blue@blue-desktop:~$ sudo cp /etc/x11/xorg.conf/etc/x11/xorg.conf.bak
cp: missing destination file operand after `/etc/x11/xorg.conf/etc/x11/xorg.conf.bak'

thats what i get when i enter the command in terminal as well in <ctrl> <alt> f2 window

---

### Post by tommcd on 2009-03-23
For those of you wil nvidia driver trouble:
Perhaps boot to recovery mode and choose the option "Xfix Fix Video" (or whatever it says) will help. This may leave you with only the "nv" 2D driver though.
Consider installing the newest driver from nvidia.com. You will need to remove all traces of the nvidia driver from the Ubuntu repos first, plus a few other things. See this:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Before installing the driver from nvidia.com, first try the suggestion in the above link under "Disable Conflicting Software" about blacklisting "nv". Try that first, without nvidia_new". Then perhaps try it with "nvidia_new".

The only other thing I can suggest is digging through /var/log/Xor.0.log to look for errors related to nvidia. You may then be able to google those errors for more specific help.

---

### Post by iamblue on 2009-03-23
OMG....IT WORKED...:D dude you are jesus to me :D..thank you all for the help :D

---

### Post by tommcd on 2009-03-24
> **iamblue said:**
> OMG....IT WORKED...:D dude you are jesus to me :D..thank you all for the help :D
In order to help others, what exactly did you do to get it working? I assume it was blacklisting "nv".  Is that correct? Or did you install the driver from nvidia.com, and blacklist "nv" along with "nvidia_new"?

Glad you got it working! I was starting to think we would not solve this one; and I was running out of ideas.

---

### Post by MountainMan2000 on 2009-03-27
Jeash, I hate it when people do that.  Solicit help on a forum and due to the good will of others figure out how to solve their problem.  But then don't pass on the secret recipe to the rest of the posters because once they have it working they never bother to type it up.

I've made some progress as well.  I broke one of my golden rules and started pulling out hardware to help make the software work.

What I found was that ubuntu does a pretty good job of autodetecting and working with either one of my two Nvidia cards installed (260 or 8800GT) but not both.  It does fine with multiple monitors plugged in to a card, with one defaulting to enabled and the second defaulting to disabled.  Its easy to use the nvidia-settings program to enable and configure the second monitor, setup a large desktop area spanned across the two screens, select the relative positions, etc.

But as soon as I plug the second Nvidia card into my system it causes some error in the xwindows server and it just fails to go to GUI mode (ie black screen with blinking curson).

So far I've not figured out how to make it work with the second card installed.  I've got my xorg.conf populated with all the nvidia settings for my 260 card with two monitors in twinview mode.  Everything is great, although not as fast as under WinXP/Vista/7.  Example: dragging windows around has visible block copy/fill artifacts while on windows its perfectly smooth.

One thing I did do to get a single card working reliably was to install the latest 180 nvidia driver.

---

### Post by Tsula on 2009-04-17
> **MountainMan2000 said:**
> Hello,

I have exactly the same issue and the same results when I tried to follow the earlier debug help.  I really would prefer to not start disassembling my system to get this issue resolved.  Nor do I like repeatedly reinstalling an OS.  I guess these are both philosophical hangups on my part. . .

Anyway, I have two NVidia cards in my system.  One is a 260 and the other is an 8800GT.  I have one monitor on each.

My initial install hit a problem and wasn't able to display partway through so I went back and selected an option to do a safe graphics install.  That worked and all was well.  The system automatically detected that I should install the Nvidia driver and showed a few, the newest of which was 177.  I ran the install and had the same problems described above.  I followed the recommended actions and it removed 177 and installed 180.  But still no GUI.

Whenever I try to switch to the GUI I just get a blinking cursor.  When I run a command that wants to open a GUI window I get an error such as "cannot open display".

Could it be that gdm needs some hand holding to tell it to use one of my graphics cards and displays as the primary?

Anyway, help would be appreciated.  The last time I tried to use unix (probably around 5 years ago) my attempt was aborted because I could never get my sound card and other hardware working.  I've heard there has been much improvement so I'm hoping I can figure this out.

Thanks.

Are you trying to get SLI with a 260 and an 8800GT? >.> If so, you can't even do that on a Windows system. They aren't compatible. You have to have the system cards. A 260 with a 260 or an 8800GT with an 8800GT.. Hope that helps.

---

