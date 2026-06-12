---
title: "Known Intrepid Ibex bugs and workarounds"
date: 2008-11-01
forum: General Help
---

### Post by frodon on 2008-11-01
[COLOR=DarkOrange]**Disclaimer : The purpose of this thread is just to list known [SIZE=3][B]Intrepid Ibex**[/SIZE] bugs [SIZE="5"]_and give the corresponding workarounds and launchpad entries_[/SIZE]. All discussions about the bug itself should go in the thread dedicated to the bug.[/B][/COLOR]

[SIZE="4"][COLOR=Red]**_Please do not list here bugs without any workaround_**[/COLOR][/SIZE]

-------------------------------------------------

**_Official Release Notes :_**
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

**_No sound effects play when "play sound effects when buttons are clicked" is enabled_**
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)
- Workaround : [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

**_Bluetooth mouse does not re-establish connection after reboot_**
- Bug report : [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/249448](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/249448)
- Workaround : [http://ubuntuforums.org/showpost.php?p=6086632&postcount=5](http://ubuntuforums.org/showpost.php?p=6086632&postcount=5)

**_Thinkfinger does not appear to work in Xorg_**
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429)
- Workaround : Explained in bug report.

**_Losing keyboard and mouse control when changing screen brightness with fn + arrow under intrepid_**
- Bug Report : [https://bugs.launchpad.net/ubuntu/intrepid/+source/acpid/+bug/285323](https://bugs.launchpad.net/ubuntu/intrepid/+source/acpid/+bug/285323)
- Workaround : [http://ubuntuforums.org/showpost.php?p=6096699&postcount=16](http://ubuntuforums.org/showpost.php?p=6096699&postcount=16)

**_Shutdown hangs at the ALSA modules_**
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274995)
- Workaround : [http://ubuntuforums.org/showpost.php?p=6216439&postcount=58](http://ubuntuforums.org/showpost.php?p=6216439&postcount=58)
[http://ubuntuforums.org/showpost.php?p=6099553&postcount=18](http://ubuntuforums.org/showpost.php?p=6099553&postcount=18)

**_Webcam issues with some apps like skype_**
- Bug Report : [https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)
- Workaround : [http://ubuntuforums.org/showpost.php?p=6115686&postcount=30](http://ubuntuforums.org/showpost.php?p=6115686&postcount=30)

**_gedit loading takes very long and 100% CPU load_**
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/280411](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/280411)
- Workaround : [http://ubuntuforums.org/showpost.php?p=6136071&postcount=38](http://ubuntuforums.org/showpost.php?p=6136071&postcount=38)

**_usb modem bugs_**
- Bug Report : [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/291351](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/291351)
- Workaround : [http://bugzilla.kernel.org/show_bug.cgi?id=11767](http://bugzilla.kernel.org/show_bug.cgi?id=11767)
[https://bugs.launchpad.net/ubuntu/+bug/292105](https://bugs.launchpad.net/ubuntu/+bug/292105)

**_USB Storage device Not Accessible_**
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)
- Workaround : [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983)

**_SCSI disk issues_**
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244608)
- Workaround : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244608)
[http://ubuntuforums.org/showthread.php?t=915171](http://ubuntuforums.org/showthread.php?t=915171)

-------------------------------------------------

Fell free to propose other known Intrepid Ibex bugs to be listed here but **[COLOR=Red]think to provide a link to the workaround and a link to the  corresponding launchpad entry.[/COLOR]**

Other ubuntu version known bugs :
[Hardy Heron known bugs]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by TheExplorer on 2008-11-01
Sorry if it's restricted to share links, but I've found an interesting article [here]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html") with solutions. Hope it helps people with NVidia cards. Frodon, you may copypaste it and delete my post if you want.

---

### Post by frodon on 2008-11-01
As long as there's no associated launchpad entry to track the bugs it can't be added to first post, some of these issues can be due to tweaked configs and some may have been fixed already too.

---

### Post by empty_tank on 2008-11-01
I had problems with no login sounds with upgraded intrepid amd64.  I found a bug report at: [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)


Bug #273507: No sound effects play when "play sound effects when buttons are clicked" is enabled

The workaround is to install latest libcanberra 0.10.

"Check this page: "https://launchpad.net/~gkulyk/+archive" with the latest libcanberra 0.10 (the one used in intrepid is the outdated 0.6).
Include the line: "deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main" in synaptic and reload.
Immediately the new 0.10 will show up as an upgrade, marked all upgrades, and reboot!"

The workaround fixed the problem.

---

### Post by and.duncan on 2008-11-02
Bug: Bluetooth mouse won't work after a restart/standby etc.

Workaround: In Bluetooth manager change visibility setting away from 'Always visible' and then back to 'Always visible', mouse should be automatically detected again.

Alternatively, delete mouse pairing from the bluetooth manager and reacquire.

Link: [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/249448](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/249448)

---

### Post by frodon on 2008-11-02
Both added, thanks a lot for your feedback.

---

### Post by WrathofthePenguin on 2008-11-02
Cannot browse samba shares

Bug is reported: [https://bugs.launchpad.net/ubuntu/+bug/292836](https://bugs.launchpad.net/ubuntu/+bug/292836)

I've now found a (lousy) workaround:

The share can be opened in firefox - the last character of every directory or file is still dropped, but can be added to the url line manually - you can eventually drill down to your files and get them, but it is very tedious.

---

### Post by iris-n on 2008-11-02
That's a cosmetic bug only, but quite visible.

In the Places menu of the gnome-panel, any icons other than the default theme don't show up. It is actually a gnome-icon-theme bug, but as it affects Intrepid, I think it would by nice to put here. It's [[COLOR="DarkOrange"]_launchpad entry_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/278033").

The workaround: 

```
sudo rm -f /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm -f /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/16x16/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/icon-theme.cache
sudo gtk-update-icon-cache -qf /usr/share/icons/gnome
```

It's due to [[COLOR="DarkOrange"]_perfectska04_[/COLOR]]("http://ubuntuforums.org/member.php?u=352049").

---

### Post by WrathofthePenguin on 2008-11-02
> **iris-n said:**
> That's a cosmetic bug only, but quite visible.

In the Places menu of the gnome-panel, any icons other than the default theme don't show up. It is actually a gnome-icon-theme bug, but as it affects Intrepid, I think it would by nice to put here. It's [[COLOR="DarkOrange"]_launchpad entry_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/278033").

The workaround: 

```
sudo rm -f /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm -f /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/16x16/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/icon-theme.cache
sudo gtk-update-icon-cache -qf /usr/share/icons/gnome
```

It's due to [[COLOR="DarkOrange"]_perfectska04_[/COLOR]]("http://ubuntuforums.org/member.php?u=352049").

Which bug are you talking about? It almost (based only on that you mention the Places menu) sounds like the one I reported, but I can't tell for sure. If you're referring to that, then I'm a worse writer than I thought. In the one I reported the last character of the directory or file name is dropped in the actual packets being sent out on the wire.

---

### Post by iris-n on 2008-11-02
Well, it's hard to tell who writes or reads badly (i'm foreign, so not able to decide), but my bug certainly does not have anything to do with yours. Mine is just that the custom icon themes don't change the icons that appear in the Places menu.

---

### Post by WrathofthePenguin on 2008-11-02
> **iris-n said:**
> Well, it's hard to tell who writes or reads badly (i'm foreign, so not able to decide), but my bug certainly does not have anything to do with yours. Mine is just that the custom icon themes don't change the icons that appear in the Places menu.

Ah- that explains it! I thought you were commenting on one of the previous bugs! I apologize - and I hope that my feeble attempt at humor didn't come across the wrong way. I would not have guessed that english was your second, third or fourth language - you write quite well.

---

### Post by der_joachim on 2008-11-03
**Issue**: Thinkfinger does not appear to work in Xorg. Swiping your finger and then pressing enter does the trick. This problem does not appear in the CLI environment (although I did not try to reproduce).

**Launchpad ticket**: [Click here]("https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429").

**Workaround**: Add the PPA in post #21(-ish) of the launchpad ticket. Update, upgrade and restart X.

---

### Post by laney_1 on 2008-11-03
there seems to be alot of trouble with fan control (or the fan starting at all) in 8.10.

heres my bug report: 
[https://bugs.launchpad.net/bugs/292374](https://bugs.launchpad.net/bugs/292374)

and the forum post:
[http://ubuntuforums.org/showthread.php?t=964320](http://ubuntuforums.org/showthread.php?t=964320)

currently no known work around (maybe stay with "hardy"?)

laney_1

---

### Post by frodon on 2008-11-03
As stated in first post this thread is for know bugs which have an existing workaround.

---

### Post by laney_1 on 2008-11-03
oh sorry, my bad ](*,)

---

### Post by Ozor Mox on 2008-11-03
[https://bugs.launchpad.net/ubuntu/intrepid/+source/acpid/+bug/285323](https://bugs.launchpad.net/ubuntu/intrepid/+source/acpid/+bug/285323)

Bug: Losing keyboard and mouse control when changing screen brightness with fn + arrow under intrepid

This problem has affected my Dell Latitude D600 laptop. If the Fn+Brightness controls are used to adjust screen brightness, the keyboard becomes completely unresponsive and it is not possible to type anywhere. Also, the mouse continues to move normally, but right click is not possible, and left click behaves strangely, becoming unable to open menus. The Applications, Places, System menu for example becomes "depressed" (highlighted blue), but the menu does not appear. CPU usage will rise while this problem is present, and there are several other weird side-effects.

Workaround: Use Ctrl+Alt+F1 to switch to a terminal, then Ctrl+Alt+F7 to switch back to X. All problems will then disappear. Avoid using the function keys to control display brightness.

---

### Post by mr_raider on 2008-11-03
Problem: Intrepid doesn't have the PAND tool that I used in Hardy to connect to the internet via bluetooth on my Windows Mobile phone.

Solution:

1. Use synaptic package manager to get the following package; bluez-compat

2. Edit the file /etc/default/bluetooth and add the following lines:

```

PAND_ENABLED=1
PAND_OPTIONS="--role=PANU"
```


3. Edit the file /etc/network/interfaces and add the line
```

iface bnep0 inet dhcp

```

4. Create the following file: /etc/bluetooth/panup

Add this;
```

#!/bin/bash
sudo pand --connect 00:17:E8:2F:8C:42 -n
sleep 1
sudo ifup bnep0

```


replace with your phone address


5. Create the following file: /etc/bluetooth/pandown

Add this;

```
#!/bin/bash
sudo ifdown bnep0
sudo pand -K
```



6. Make panup and pandown executable

7. Pair the phone, start the connection and sharing software on your phone.

8. run the script /etc/bluetooth/panup to start and you should acquire DNS address

9. run the script /etc/bluetooth/pandown to terminate


It boggles the mind that you have to do all that crap on a modern OS where the GUI should handle it.

This procedure is modified from an older one in this thread:

[http://ubuntuforums.org/showthread.php?t=598890](http://ubuntuforums.org/showthread.php?t=598890)

---

### Post by dcstar on 2008-11-03
Shutdown hangs at the ALSA modules:

[http://ubuntuforums.org/showthread.php?t=964177&highlight=shutdown](http://ubuntuforums.org/showthread.php?t=964177&highlight=shutdown)

Basically you have to shut down networking before the ALSA stuff is shut down. "Workaround" originally from:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274995)

open terminal

```
sudo gedit /etc/init.d/alsa-utils
```

scroll down to where you see **stop**

insert this line at the top (right after the **stop**) :
```
ifconfig eth0 down
```

or if you use wireless/both at times, insert this instead/in addition:
```
ifconfig wlan0 down
```

---

### Post by shane19174 on 2008-11-04
CD/DVD drive closes immediately after ejecting.

Official bug report: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316").

Workaround: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316").

(Note that the workaround discussed in the bug is now available through intrepid-proposed. In order to get the update [the package affected is udev, the new version being 124-9], I had to temporarily change from the German mirror to the US repos.)

---

### Post by shane19174 on 2008-11-04
Bug: After upgrading from Hardy, clicking on folders in the "Places" menu opens up the wrong application (for example, VLC, Totem, Rhythmbox, etc. instead of Nautilus).

Launchpad: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492").

Workaround: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492").

(Basically, the solution is simply to right click on a folder in nautilus > open with app > file manager. Afterwards, "places" folders should open normally again.)

---

### Post by frodon on 2008-11-04
This bug is marked as fixed it seems.

---

### Post by shane19174 on 2008-11-04
> **frodon said:**
> This bug is marked as fixed it seems.

Which bug do you mean? If you mean the "places" folders, then yes, it apparently got "fixed" at some point, but I've seen at least 10 new threads on this both in "Absolute Beginners" and "General Help" over the past days, so it seems in fact to be very much alive.

---

### Post by frodon on 2008-11-04
No, updates takes times to reach all the mirrors and some users may have not the update available yet or just don't have an up to date ubuntu box.

So this explains why some users are still reporting this and will continue reporting this for some weeks.

---

### Post by shane19174 on 2008-11-04
> **frodon said:**
> No, updates takes times to reach all the mirrors and some users may have not the update available yet or just don't have an up to date ubuntu box.

So this explains why some users are still reporting this and will continue reporting this for some weeks.

Sorry, I see now that I gave you the wrong launchpad thread. The correct one (with regard to the "places" folders) is here: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/260492]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/260492"). Note that this has the same bug number as the one I posted before, but it's filed against gnome-panel instead of nautilus. You'll notice that this one is still "in progress," with a fix uploaded to intrepid-proposed just yesterday. The reports on this thread show that upgrades from Hardy to Intrepid are still affected.

---

### Post by Trelane on 2008-11-04
Further bug, gnome-session-remove is missing.

---

### Post by jerrylamos on 2008-11-04
Intrepid Compiz hangs on login for Intel i830MG and i845 video cards
[https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/259385](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/259385)
Install or upgrade to Intrepid 8.10 can't boot.
Symptoms: after login, pc hangs with nothing but cursor black or brown or tan or orange screen (depending on the display?)
Workaround: remove compiz as detailed in the bug report.  Boot in rescue mode and in root shell prompt sudo apt-get remove compiz compiz-core

Jerry

---

### Post by zeigfried on 2008-11-04
[URL="https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316"]
CD-ROM tray closes automatically after eject[/URL] - **status:** [simple fix]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316/comments/34")

Sorry, I doubled shane19174 post.

Cheers

---

### Post by Handssolow on 2008-11-05
Regarding the bluetooth mouse bug, since removing avahi-daemon and avahi-autoipd, my Acer Aspire One netbook finds my MS 5000v1.0 bluetooth mouse possibly with every fresh boot. Insidentally the atheros driver I'm using is from madwifi not the default driver in 8.10 which I disabled. I've also posted my findings on this bluetooth bug thread in Launchpad. I'm not sure if there is a cause and effect or it's just a chance finding.

Subsequently report: One warm restart no working bluetooth mouse, one cold restart and it's working again.

---

### Post by HyperHacker on 2008-11-05
Apparently, Totem is installed by default in Xubuntu, but not any codecs. I just tried about 15 random videos and it didn't have audio or video codecs for any of them. Why include a movie player that can't play any movies? >_> (For that matter, why not include mplayer?)

As I've mentioned before, the keyboard is messed up. Down, Left, Numpad Down, Numpad Left (when Num Lock is off), End, Page Down do nothing, and Page Up types a slash.

The Xfce panel weather plugin doesn't seem to be showing any icons, unless the "fog" icon is just a white blob.

I can't install the Flash player for Firefox either. It either hangs at 0% or times out.

[edit] Why is Thunderbird the default image viewer when an actual image viewer is installed?

---

### Post by spiderbatdad on 2008-11-06
webcams not working with various apps like skype and IM's or even cheese. The bug affects more than just gscpa devices.
[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

That is; try: ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype  
**OR**
 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

---

### Post by frodon on 2008-11-06
your bug report is marked as fixed spiderbatdad. Almost any webcam apps seems to have been fixed but i will add the bug to first post since skype is closed source and ubuntu devs can't fix it.

Hope skype devs will consider implementing a fix in their code.

---

### Post by spiderbatdad on 2008-11-06
> **frodon said:**
> your bug report is marked as fixed spiderbatdad. Almost any webcam apps seems to have been fixed but i will add the bug to first post since skype is closed source and ubuntu devs can't fix it.

Hope skype devs will consider implementing a fix in their code.

I'm also still having to use this fix for gyachi.

Also, to my knowledge it is fix committed only in Debian. So the version of libv4l in the repos still doesn't work. So still a bug in many other packages...kopete, gst, mplayer, vlc and amsn.

---

### Post by mr_raider on 2008-11-06
> **HyperHacker said:**
> 

The Xfce panel weather plugin doesn't seem to be showing any icons, unless the "fog" icon is just a white blob.

yes it is :)

---

### Post by sharkster2007 on 2008-11-06
Deleted due to no known workaround sorry :-(

---

### Post by loell on 2008-11-07
> **spiderbatdad said:**
> I'm also still having to use this fix for gyachi.

Also, to my knowledge it is fix committed only in Debian. So the version of libv4l in the repos still doesn't work. So still a bug in many other packages...kopete, gst, mplayer, vlc and amsn.

gyachi specific:

the developer is now using libv4l API to access webcams. hope you can contribute feedbacks with webcam detection in [gyachi forum]("https://sourceforge.net/forum/forum.php?forum_id=533966")

you can install the latest build from my [ppa]("https://launchpad.net/~loell/+archive").

---

### Post by kevdog on 2008-11-08
Anyword on a actual solution for the Intel 830MG graphics driver debacle?  The last time this driver actually functioned appropriately for me was with the Gutsy release.

---

### Post by loell on 2008-11-09
[low mic sound with intel audio]("http://ubuntuforums.org/showthread.php?t=963801")

---

### Post by Panarchy on 2008-11-09
I had to unplug my IDE drive before the installer could detect my SATA drive.

BTW: Burnt the image to a DVD for speed.

BTW2: Am using 64-bit ubuntu

BTW3: Downloaded and burnt it today

Please fix this bug.

Thanks in advance,

Panarchy

---

### Post by Andreas1 on 2008-11-09
gedit loading takes very long and 100% CPU load

Bug: [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/280411]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/280411")

Workaround: Just disable the "browser pane" plugin

---

### Post by frodon on 2008-11-09
First post updated.

To everyone, for a report to be taken into consideration for the first post, launchpad entry and workaround description/link are mandatory.

---

### Post by davidmaxwaterman on 2008-11-09
> **spiderbatdad said:**
> webcams not working with various apps like skype and IM's or even cheese. The bug affects more than just gscpa devices.
[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

That is; try: ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype  
**OR**
 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

Didn't work for me - tried both. I tried the compat one under strace to make sure it was using it, and it was...but I still get solid green video in skype. Using x86 linux on amd64 (got fed up with doing 32-bit workarounds)...skype worked just fine on 8.04.

I'm now using gyachi (ie Yahoo! IM with video) as a work around, but the quality isn't as high - but it doesn't 'hang up' as much as skype either. Maybe I'll just stick to yahoo! I only use the video bit...not the audio.

---

### Post by zero777zero on 2008-11-09
i dont know if this is a bug or what, but i'm going to post it here.

a few days ago grub freaked out and i tried to do a re-install of 8.10, but i kept getting a 'initramfs' error. luckily i had a copy of 8.04 nearby or i'd be without OS right now. the 8.10 cd is perfectly clean, scratch free, etc and it worked fine the other day when i installed it, but no matter what option i chose from the live cd i always get the initramfs error after the ubuntu load screen.

edit: i redownloaded 8.10, burned with brasero on slow speed, no errors occured, the issue is still happening!

edit2: did a clean install with vista, installed 8.10 over that with cd

---

### Post by hanzomon4 on 2008-11-09
Sound does not come back after suspend:

1 Workaround: ```
sudo alsa force-reload
```

Alternate Workaround: Just switch to a VT console(Ctrl+Alt+F1) then switch back(ctrl+alt+F7)

[Launchpad entry]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275630")

---

### Post by frodon on 2008-11-09
I won't add this one as it is an old and known one especially if you own an intel chipset.

In such case you don't even need to bother with such ugly fix as adding your soundcard infos to the right modprobe file fix it :
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

I had this issue on hardy too on my acer laptop and adding my soundcard infos just killed the annoyance for good.

---

### Post by psyke777 on 2008-11-10
Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/150515](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/150515)

Easier Fix: add **nohz=off** to your kernel parameters. This makes your kernel no longer tickless which then causes the module to stop ksoftirqd looping without pause.

Complex Fix: Download the module source code from [http://sourceforge.net/project/platformdownload.php?group_id=179406](http://sourceforge.net/project/platformdownload.php?group_id=179406) and add this fix: [http://sourceforge.net/tracker/index.php?func=detail&aid=2045610&group_id=179406&atid=889023](http://sourceforge.net/tracker/index.php?func=detail&aid=2045610&group_id=179406&atid=889023) 
I am not a programmer but I added **pAdapter->ErrorTimer.expires=jiffies+HZ;** prior to **add_timer( &pAdapter->ErrorTimer );** and compiled and installed. Someone with more experience should verify this fix before you use it.

---

### Post by frodon on 2008-11-11
The bug report is for gutsy psyke777, if this apply to intrepid too then you should update the bug report.

---

### Post by psyke777 on 2008-11-11
> **frodon said:**
> The bug report is for gutsy psyke777, if this apply to intrepid too then you should update the bug report.

Ok, I added my comments there. I didn't know how to update the rest so I gave up.

---

### Post by philinux on 2008-11-11
Google Earth GUI has tiny fonts. using the preferences tool does not change them.
Fix is to edit /home/username/.config/Google/google/GoogleEarthPlus.conf

[https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/293628](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/293628)

---

### Post by directcharitycontribution on 2008-11-11
usb modem bugs [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/291351](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/291351)

fix - [http://bugzilla.kernel.org/show_bug.cgi?id=11767](http://bugzilla.kernel.org/show_bug.cgi?id=11767)

FIX - [https://bugs.launchpad.net/ubuntu/+bug/292105](https://bugs.launchpad.net/ubuntu/+bug/292105)

---

### Post by Gary.M on 2008-11-11
This is widely reported and a fix/workaround has been posted on the Launchpad entry today. I have tried this and it fixed the problem for me.

Bug reported here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)

Fix in this entry

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983)

---

### Post by mess_enger_guy on 2008-11-12
I know there was a post regarding nvidia restricted drivers at the start of this thread. To be explicit, all nvidia restricted drivers work with intrepid except the legacy 71 drivers (96 drivers are working now). This problem won't be solved until nvidia releases new 71 drivers compatible with the new xorg of intrepid. Also the release of new drivers isn't going to happen soon, check this out:

[http://www.nvnews.net/vbulletin/showthread.php?p=1833180](http://www.nvnews.net/vbulletin/showthread.php?p=1833180)

Launchpad: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107)

Workaround: Use NV drivers for nvidia cards that use the 71x legacy drivers until the release of new drivers :(

---

### Post by frodon on 2008-11-12
> **mess_enger_guy said:**
> I know there was a post regarding nvidia restricted drivers at the start of this thread. To be explicit, all nvidia restricted drivers work with intrepid except the legacy 71 drivers (96 drivers are working now). This problem won't be solved until nvidia releases new 71 drivers compatible with the new xorg of intrepid. Also the release of new drivers isn't going to happen soon, check this out:

[http://www.nvnews.net/vbulletin/showthread.php?p=1833180](http://www.nvnews.net/vbulletin/showthread.php?p=1833180)

Launchpad: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107)

Workaround: Use NV drivers for nvidia cards that use the 71x legacy drivers until the release of new drivers :(listed in first link in the first post (ubuntu intrepid ibex official release notes)

---

### Post by mess_enger_guy on 2008-11-12
> **frodon said:**
> listed in first link in the first post (ubuntu intrepid ibex official release notes)

I know that this information is there in the release notes but it is incomplete. This is what the release notes say:

*The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.*

As I mentioned the beta 71 & 96 drivers that were supposed to be compatible with the intrepid xorg have released. But only 96 drivers work perfectly at present, also the packages for the 96 drivers are available in intrepid repo. So the intrepid users who have nvidia cards which use 96 drivers, they don't need to use nv drivers anymore. The compatible nvidia drivers are available now. Thought I might update the information included in the release notes, if it helps anybody...

---

### Post by kleeman on 2008-11-12
scsi disks do not boot. Users are dumped into a busybox terminal. This bug is confined to intrepid and is apparently a 2.6.27 kernel problem. A workaround is posted in the forum and launchpad links

[http://ubuntuforums.org/showthread.php?t=915171](http://ubuntuforums.org/showthread.php?t=915171)
[https://bugs.launchpad.net/bugs/244608](https://bugs.launchpad.net/bugs/244608)

---

### Post by mbeierl on 2008-11-12
Did not see this one here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168)

pptp and NetworkManager don't work if you cache the password.  A suggested workaround is to manually enter keys in gconf and don't cache the password, or alternatively use kvpnc.

---

### Post by gkrules on 2008-11-12
There is an issue with HP notebooks [maybe desktops too] that causes the boot screen to hang. All you have to do is hold down a key and the computer will boot up.

No permanent fixes have been made yet.

Some people have gotten it to boot by adding "acpi=noirq" at the end of the following line
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=c877e76e-7e7f-4b47-aec7-6ae28d1ab767 ro quiet splash
on /boot/grub/menu.lst

BUT, there are side effects, such as your remote not working and X not correctly starting at time.

---

### Post by frodon on 2008-11-13
> **mbeierl said:**
> Did not see this one here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168)

pptp and NetworkManager don't work if you cache the password.  A suggested workaround is to manually enter keys in gconf and don't cache the password, or alternatively use kvpnc.Hopefully the bug is Triaged which means devs have all in hand to fix this bug, i hope we won't have to wait too long for an update to hit the repo.

Will add this one to first post today.

---

### Post by lordfoul on 2008-11-16
Getting A2DP Bluetooth in 8.10 working.

[http://ubuntuforums.org/showthread.php?t=969527](http://ubuntuforums.org/showthread.php?t=969527)

---

### Post by WrathofthePenguin on 2008-11-18
Fix available for Samba Shares not working bug - I'm copying my post from another thread to save time:

The bug I submitted:

[https://bugs.launchpad.net/bugs/292836](https://bugs.launchpad.net/bugs/292836)

was marked as a duplicate of another:

[https://bugs.launchpad.net/bugs/282298](https://bugs.launchpad.net/bugs/282298)

The patch which fixes this bug is posted here:

[https://launchpad.net/~tcarrez/+archive](https://launchpad.net/~tcarrez/+archive)

And it resolved the problem completely for me.

To install:

In Synaptic Package Manager, go to Settings->Repositories

Under the Third-Party Software tab, click on Add.

Enter the following:

deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main

and Click on Add Source.

You can reload and the update shows up for samba (there will be a little star showing for Samba. You can click and upgrade. Do all the upgrades and make sure there aren't others for Samba afterward.

---

### Post by BrionS on 2008-11-20
Alternate and possibly better workaround for shutdown/restart hang on ALSA originally suggested here: 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/202](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/202)

Run the following in a terminal window:

sudo ln -s /etc/init.d/NetworkManager /etc/rc0.d/K40NetworkManager
sudo ln -s /etc/init.d/NetworkManager /etc/rc6.d/K40NetworkManager

This will shut down the Network Manager before ALSA on reboot and shutdown. Using the ifdown fix your network will be lost any time you stop or restart ALSA and does not get automatically restarted with the ALSA.

This alternative is also easy to roll back by simply deleting the symlinks in /etc/rc0.d and /etc/rc6.d for NetworkManager.

---

### Post by andrew.46 on 2008-11-26
Hi,

There is a bug with checkinstall that is affecting Intrepid Ibex, although also seen sporadically in other Ubuntu versions as well. With this bug checkinstall fails claiming it cannot find files or directories that are actually in existence. The bug is a little random as it is an inability of checkinstall to cope with newer gnu coreutils so depends on *which* coreutils are actually utilised. The workaround is to run checkinstall as:

```
checkinstall --fstrans=no
```

Discussion of this bug on the checkinstall pages can be seen here:

[http://checkinstall.izto.org/cklist/msg00319.html](http://checkinstall.izto.org/cklist/msg00319.html)

and the Launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/78455](https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/78455)

All the best,

  Andrew

---

### Post by shaunburrows on 2008-11-27
pwmconfig not able to save file to /ect/fancontrol

saved to home directory and copied across

Also weird behavior when using ```
sudo gedit /ect/fancontrol
```
Blank file coming up and unable to save without doing new save as.

Not sure if its just a Ibex bug but not found any previous mention of it.

---

### Post by akahige on 2008-11-29
> **shaunburrows said:**
> pwmconfig not able to save file to /ect/fancontrol

saved to home directory and copied across

Also weird behavior when using ```
sudo gedit /ect/fancontrol
```
Blank file coming up and unable to save without doing new save as.

Not sure if its just a Ibex bug but not found any previous mention of it.

Maybe it's because you're trying to save to "ect" and not "etc"...?

---

### Post by boombox1387 on 2008-12-01
Sorry if this was mentioned before, I read over the last 6 pages and didn't see anything.

For some ATI video cards, the default driver was switched to the free driver with no option to use the restricted driver in Ibex.  Using the free driver, all video players crash when they start to play a video if Compiz is enabled.  The fix for this is to add ```
Option "AccelMethod" "EXA"
``` to Section "Device" in xorg.conf.

Details can be found here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/269357]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/269357")

---

### Post by Metralha on 2008-12-07
Thanks but with my ATI video cards x1700 i still have the problem that can't see any film, serie without appearance set as none. Bah...this sucks,it's a really bad bug!!!
Thanks anyway

---

### Post by _sebastian_ on 2008-12-11
Wireless can't be activated after disabling kill switch

> If the system was booted with an enabled kill switch, then I can't reactive the wireless interface any more after I disabled WLAN with the kill switch. Only a reboot with deactivated kill switch enables the interface again.

Bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/193970](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/193970)
2 workarounds are included in bug description and more options in the post

---

### Post by ripps818 on 2008-12-11
> **boombox1387 said:**
> For some ATI video cards, the default driver was switched to the free driver with no option to use the restricted driver in Ibex.  Using the free driver, all video players crash when they start to play a video if Compiz is enabled.  The fix for this is to add ```
Option "AccelMethod" "EXA"
``` to Section "Device" in xorg.conf.


If your desktop starts freezing with EXA (like mine did) it can probably be fixed by adding ```
Options "AGPMode" "1"
``` to your xorg.conf right below the EXA entry.

---

### Post by Arup on 2008-12-11
For those having issues specially with Intel G31 series and other video cards like system booting to a blank screen after logging out and logging in, here is a simple solution. This bug is caused by compiz and turning effects to none in Appearance solves the problems, those who need a less buggy effects can opt for Metacity which is built into Gnome, it doesn't use your graphics card, however effects are stark compared to compiz but no issues. Also desktop is much faster.

---

### Post by seaq on 2008-12-16
Hi, i've put in the wiki a list for known bugs with webcam cameras. 


[https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams](https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams)

---

### Post by JohnPhys on 2008-12-17
This bug existed in Hardy as well (and probably previous releases).

Bug: [https://bugs.launchpad.net/inkscape/+bug/55273](https://bugs.launchpad.net/inkscape/+bug/55273)
Workaround:  [https://bugs.launchpad.net/inkscape/+bug/55273/comments/49](https://bugs.launchpad.net/inkscape/+bug/55273/comments/49)

This has worked great for me on my 2 hardy installs and my intrepid install (the bug is still present in Intreipd).

---

### Post by Favux on 2008-12-18
Bug:  When trying to connect to WPA/WPA2, NetworkManager (0.7) keeps asking for the password.

Launchpad:  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963")

Workaround:  [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

### Post by dcstar on 2008-12-19
**Network disconnected when resume from suspend**

This seems to be affecting a fair few people from this thread I just read with this workaround (sorry, I don't know if there is a Launchpad entry):

[http://ubuntuforums.org/showpost.php?p=6264243&postcount=8](http://ubuntuforums.org/showpost.php?p=6264243&postcount=8)

---

### Post by Hello_World on 2008-12-20
> Re: Known Intrepid Ibex bugs and workarounds
webcams not working with various apps like skype and IM's or even cheese. The bug affects more than just gscpa devices.
[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

That is; try:
Code:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype  
OR
 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

__________________

[http://unmundane.etsy.com](http://unmundane.etsy.com)

I guess, that is worst necroposting i ever did - answering an 3 year old post ...
However, this solution still works (worked for me with my webcam, a Trust cp-2250d) on Ubuntu 8.10
There is also a way to workaround to start the application (in this case: skype) over and over via the terminal. You can find it here: 
[http://www.atokar.net/index.php/topic,236.msg464/topicseen.html#msg464](http://www.atokar.net/index.php/topic,236.msg464/topicseen.html#msg464)

---

### Post by kleeman on 2008-12-21
The latest kernel update 2.6.27-11 fixed my webcam issues. Mine uses the uvcvideo kernel module.

---

### Post by Colt45 on 2008-12-25
HOWTO: Bug workaround for slow responsiveness of Ubuntu 8.10 (display refresh bug)

[http://ubuntuforums.org/showthread.php?t=1021773](http://ubuntuforums.org/showthread.php?t=1021773)

Launchpad entry..
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972)


**UPDATE**: This seems to help desktop responsiveness, but does not totally fix random VLC playback skipping in Ubuntu.



Posted this to launchpad and over at videolan.org earlier tonight. Hopefully this workaround can help some people who may be experiencing a very laggy/slow desktop in Ubuntu 8.10 or are experiencing problems with video playback using XVideo or VLC.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972)



The issue of "General System Sluggishness" may be due to a bug with autodetection of display refresh rate in Compiz or Ubuntu. This would explain why both Nvidia and ATi users are effected.

Example: If refresh rate is being polled at 59.88Hz, Ubuntu or Compiz is rounding down to 50Hz instead of setting refresh to 60Hz.

The Nvidia steps only need to be done by Nvidia users to fix tearing/VSync issues for video playback. Follow the steps and see if it solves the problem...




Credit goes to shaundennie 
[http://www.nvnews.net/vbulletin/showthread.php?t=106746](http://www.nvnews.net/vbulletin/showthread.php?t=106746)


**UPDATE**: *12/26/08*
The steps in this post fix tearing in XVideo/X11 and improve desktop responsiveness, but they do not fix the skipping issue in VLC.



Problems with desktop responsiveness mainly appear to be attributed to Compiz or Ubuntu's autodetection of refresh rate.  Compiz or Ubuntu will round down display refresh from 59.99Hz to 50Hz instead of setting it to 60hz.  This rounding down of 10Hz seems to cause  the slowdown that many people are experiencing with Ubuntu desktop performance.   To overcome this, you need to manually set your display refresh rate to 60Hz in CompizConfig Settings Manager.


**Fore note**:
----------------------------------------------------------------------------------------------------------------------
A few days before executing the steps below, I reverted to Nvidia 173.14.12 and VLC 0.8.6h
It's entirely possible that you may be fine using Nvidia 177.80 or 177.82 with VLC 0.9.4
or later after following the steps below.  I have not tested further. If you encounter success
with newer drivers or newer vlc, please post results.



----------------------------------------------------------------------------------------------------------------------
**STEPS**: *Compiz Configuration*

1. Download CompizConfig Settings Manager from Ubuntu repository.
2. Navigate to.. System --> Prefences --> CompizConfig Settings Manager
3. Navigate to.. General --> General Options
4. Click "General Options" to open window
5. Click "Display Settings" tab
6. Uncheck "Detect Refresh Rate"
7. Move "Refresh Rate" slider to 60, or set 60 in the box
8. Check "Sync to VBlank"
9. Click back button to move back to main CompizConfig window
10. Navigate to.. Utility --> Video Playback
11. Uncheck "Video Playback" then exit the CompizConfig Settings Manager.


**STEPS**: *Nvidia Configuration*

1. Pull up nvidia-settings
.. Navigate to.. Applications --> System Tools --> nvidia-settings
.. or open a terminal, type "nvidia-settings" , press enter
2. Click "X Server XVideo Settings"
3. Check "Sync to VBlank" _IF_ not checked
4. Click "OpenGL Settings"
5. Uncheck "Sync to VBlank" _IF_ checked
6. click quit button
7. click quit button
8. Reopen nvidia-settings to verify that config changes were saved.
.. IF they were saved, you are done with step 8.
.. IF they were not saved, ~/.nvidia-settings-rc in your home directory
.. may be under root permissions. You will need to chown chgrp for the file.
.. Then you will need to start back at Step 1 and repeat all steps.

**IMPORTANT**: Reboot your machine when finished. The driver changes won't function correctly until you reboot

---

### Post by 2hot6ft2 on 2008-12-26
hpet clocksource causing freezes 507 hits in launchpad
[https://launchpad.net/+search?field.text=hpet&field.actions.search=Search](https://launchpad.net/+search?field.text=hpet&field.actions.search=Search)

Found an interesting blog with fixes earlier here.
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell)

And another by the same author (not exactly sure how to search launchpad for this one) that fixes freezes caused by ati drivers here.
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f)

Maybe this will help someone. I apologize for my lack of info.

---

### Post by dcstar on 2008-12-30
**Kompozer crashes**

Workaround (until new version released in Jan 2009):

[http://ubuntuforums.org/showthread.php?t=988682](http://ubuntuforums.org/showthread.php?t=988682)

---

### Post by thingy87654321 on 2009-01-03
yep

---

### Post by ropers on 2009-01-09
**Canon BJC-85 prints colours all wrong when trying to print images**

I had a problem where my Canon printer (BJC-85) would print the colours all wrong, and it turned out that it was just an incorrect default setting in the printer driver. Going to System -- Administration -- Printing -- BJC-85 -- Printer Options -- Printer Features Common and setting the Ink Type to CMYK Color instead of Photo CcMmYK Color fixed the issue. The only print heads that are available for the BJC-85 are either black ink only or CMYK; this printer does not support CcMmYK at all -- so arguably the user should never be given that choice, nevermind it being the default. Yeah, this is a long shot, but maybe this helps somebody.

---

### Post by mwillams73 on 2009-01-09
Im having a problem with the no sound effects thing, you know I set up sound preferences to play sounds when i clik on something ( i call it a soundscheme) anyways the bug fixs and work arounds that are posted at the top of the page are, well, incomplete, I need some one to post step by step instuctions so that i can get this fix, is it really that hard, im tired of cliking on the links posted and being taking to a place that doesnt explain what im supposed to do with the files they offer, I know how to use the terminal but if i dont know what im supposed to do to install it then what good is this post for, It sure hasnt helped me so far. 

This is the last bug that needs to be fixed on my system and has taken the most time to track down an answer for, all my other problems were fixed cause the people posted concise instructions along with what to do, why not on this post? You cant just post a link that leads to another link and then not explain what needs to be done! at the last link when you clik on the the file it takes you to another place so you can download it, the bug post at launchpad just says install this and it works, but not how to install it.Im not a programer here ok? I dont know how to do all that, supposedly its in synaptic but i cant find it even when i paste what they say to paste. Please help!!!!!

---

### Post by mwillams73 on 2009-01-09
Here is the actual fix for the libcanberra bug, unlike all of you im going to post it here instead of posting a link,




  If you are on Intrepid then you need to add the repository

"deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main"

by going to System > Administration > Software Sources

Third Party Software tab.

Click on Add and give the above line without the quotes

Click Close .

It will ask to reload, let it do fetch.

In the updates you will get the new canberra 0.10
--

---

### Post by oygle on 2009-01-13
The bug in Kompozer, where it closes if you use the mouse ..

I found out this problem only a few days ago. Searched around and although tht bug has not been fixed, I was able to try a few tips and use Kompozer, without it closing.

1. It can open files okay, as long as you use the menu with the keyboard.
2. You can use the mouse to 'position' in a cell, table, row, column, or any other part of the html document.
3. BUT, don't use the mouse on the menu, and don't left or right click the mouse.

So, how can one 'navigate' then ?  Just use the keyboard to navigate the menu. For example to add a row

Alt - B - I - R

use your keyboard left and right arrows to navigate some of those menu options.

HTH

Oygle

---

### Post by madyogi on 2009-01-22
> **iris-n said:**
> That's a cosmetic bug only, but quite visible.

In the Places menu of the gnome-panel, any icons other than the default theme don't show up. It is actually a gnome-icon-theme bug, but as it affects Intrepid, I think it would by nice to put here. It's [[COLOR="DarkOrange"]_launchpad entry_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/278033").

The workaround: 

```
sudo rm -f /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm -f /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/16x16/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/icon-theme.cache
sudo gtk-update-icon-cache -qf /usr/share/icons/gnome
```

It's due to [[COLOR="DarkOrange"]_perfectska04_[/COLOR]]("http://ubuntuforums.org/member.php?u=352049").
Thank You!

---

### Post by haneya on 2009-01-24
Cant open computer or trash and cant mount drives 

workaround:-[http://ubuntuforums.org/showthread.php?p=6592089]("http://ubuntuforums.org/showthread.php?p=6592089")
bug:-[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/320498]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/320498")

---

### Post by amlucent23 on 2009-01-28
Description: Receive a system-tools-backends error anytime your install/update/remove software. package system-tools-backends 2.6.0-1ubuntu1.1 failed to install/upgrade: subprocess post-installation script returned error exit status 1 


Bug: [https://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389]("https://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389")

Workaround: [https://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389/comments/34]("https://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389/comments/34")

---

### Post by tegnoto89 on 2009-02-09
Not sure if this has been solved, but I found a few threads regarding Intrepid's apparent inability to stay connected with WPA 2 networking.  I was unable to find an answer, and have since downgraded to Hardy.

---

### Post by davidmaxwaterman on 2009-02-09
> **tegnoto89 said:**
> Not sure if this has been solved, but I found a few threads regarding Intrepid's apparent inability to stay connected with WPA 2 networking.  I was unable to find an answer, and have since downgraded to Hardy.

Interesting. I've noticed this too, but had thought it was just a reception problem. Perhaps it isn't...

Max.

---

### Post by Gary.M on 2009-02-11
I'm running a Linksys Draft-N adapter with driver via ndiswrapper, WPA2 (which I found I needed to get the full speed) and it is rock solid. Running Linux Mint Felicia, which is in effect Intrepid...

---

### Post by polobreaka on 2009-02-13
how come nobody mention anything about clocksource tsc unstable? seems like a known linux problem. i know i encounter it everytime im using ibex. its getting to the point where i want to get rid of ubuntu because of this random hang ups. i would be working on a document and all of a sudden it would freeze and ill have to wait couple of minutes for it revive. its quit annoying.

---

### Post by Arup on 2009-02-14
> **polobreaka said:**
> how come nobody mention anything about clocksource tsc unstable? seems like a known linux problem. i know i encounter it everytime im using ibex. its getting to the point where i want to get rid of ubuntu because of this random hang ups. i would be working on a document and all of a sudden it would freeze and ill have to wait couple of minutes for it revive. its quit annoying.

On most cases setting the CPFREQ governor to performance takes that problem away.

---

### Post by polobreaka on 2009-02-14
> **Arup said:**
> On most cases setting the CPFREQ governor to performance takes that problem away.

will it work on intel pentium D duo core 3.0ghz? i read up on how to setup cpufreq, but it looks like people are setting up with their laptop. im using a desktop.

---

### Post by Arup on 2009-02-14
> **polobreaka said:**
> will it work on intel pentium D duo core 3.0ghz? i read up on how to setup cpufreq, but it looks like people are setting up with their laptop. im using a desktop.

Yes, CPUFREQ is working in the background, the panel is a GUI for controlling it. Give it a try.

---

### Post by polobreaka on 2009-02-14
i was able to set cpu0 to performance, but i dont know how to set cpu1 to performance also. right now cpu1 is set to ondemand. 

also, is there a way to start in performance on both cpu during start up?

---

### Post by Arup on 2009-02-14
If you use CPUFREQ panel then its a core wide setting.

---

### Post by frodon on 2009-02-16
Please let this thread go back on topic. No talk about bugs here, just report those who have a known workaround.
Discussions about the bug itself belongs to the related support thread.

Thanks.

---

### Post by aakash602 on 2009-02-16
1. **Studio theme**- The Ubuntu studio theme has a colour problem. for eg., in the shutdown menu, when u just place the mouse over an option like Shutdown, Hibernate etc., the colour of highlighting and the font colour are just too similar, making the font unreadable.

2. **Playing VCD**-When a Video CD is placed in the DVD writer, it is not played automatically. Also, if i try to play it manually, it says i don't have the rights. I cannot even copy the contents of the CD to my hard drive.

It is a desktop computer.

---

### Post by aakash602 on 2009-02-16
one more thing

3. **USB start-up disk**-This tool starts the process but never finishes it.

---

### Post by octavianus on 2009-02-17
XFS reading issue.

I created an XFS partition but my Intrepid can not read/write there. That also applies when I use Ubuntu Live CD.
 When I formatted my 1G USB memory to XFS  in my Mobile phone , yet Ubuntu ( even on live CD mode )failed to read/write there.

I tried the same with SLAX live cD and it could read/write my XFS partion without any issue. what is the catch here ?

---

### Post by digitalmonk on 2009-03-30
I have two issues,
first: whenever I open firefox 3.0.8 on my intrepid,it always opens in the offline mode.
second: Empathy is always offline,never managed to connect it to the yahoo and gtalk accounts,pidgin on the otherhand works fine.

any help will be much appreciated :)

---

### Post by suresh_vandiyur on 2009-03-30
I do let it run and It says...
*checking root file system...
1075
Fsck 1.41.3 (12-oct-2008 )
/Lib/init/rw/rootdev contains a file system with errors, check forced.
/Lib/init/re/rootdev: unattached inode 286889

/lib/init/rw/rootdev: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
Fsck died with exit status 4

{red colored}* an automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintinence mode with the root filesystem mounted in read only mode.
{green or orange (I'm colorblind)}* the root filesystem is currently mounted in read only mode.
A maintinence shell will now be started.
After performing system maintinence press CONTROL-D to terminate the maintinence shell and restart the system.
Bash: no job control in this shell
Root@ubuntu:~# _

This pops up every time... I am at a loss I have no idea what to do... Again any help is appriciated.

---

### Post by boombox1387 on 2009-03-30
> **frodon said:**
> Please let this thread go back on topic. No talk about bugs here, just report those who have a known workaround.
Discussions about the bug itself belongs to the related support thread.

Thanks.

It's a shame that this needs to be stated every three or four posts, but again, this thread is for known bugs *with known workarounds*.  There are many good places to talk about (or report) open bugs.  Launchpad comes to mind...

But this thread is supposed to be a place to talk about known ways to fix common problems.  Please, please try to keep it that way.

---

### Post by digitalmonk on 2009-04-02
well how do you expect ubuntu beginners to know what is a known issue and what is a bug?
finding the right thread his this huge maze of threads is too much of a task to ask for, isn't it ?

---

### Post by boombox1387 on 2009-04-02
> **digitalmonk said:**
> well how do you expect ubuntu beginners to know what is a known issue and what is a bug?

There isn't really a difference between a known issue and a bug.  There is a difference, though, between a workaround and no workaround.  While there are thousands of people in these forums who want to help new users with any issues they have, this thread is specifically for workarounds, as stated in the title.

> **digitalmonk said:**
> finding the right thread his this huge maze of threads is too much of a task to ask for, isn't it ?

It's true that there is an obscene number of threads here, but searches (both forum searches and Google searches) tend to work pretty well if people are really trying to find the best place to discuss their problem.

Anyway, I'm definitely not trying to be the forum police, and I certainly wouldn't want to be too hard on users who get mixed up in the forums, but it would be nice to try to keep this thread as relevant as possible.

---

### Post by smallrabbit on 2009-04-09
> **TheExplorer said:**
> Sorry if it's restricted to share links, but I've found an interesting article [here]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html") with solutions. Hope it helps people with NVidia cards. Frodon, you may copypaste it and delete my post if you want.

Thanks TheExplorer. I had problems with Ubuntu on my laptop running Nvidia 8400 GT. And btw I am really happy for Ubuntu. Everytime Windows leaves me behind, Ubuntu gets very useful. I am even starting to write about linux on [my computer blog]("http://www.pcterritory.net"). If anything is reliable in computer sphere, than this is linux.

---

### Post by bsmith1051 on 2009-04-16
> **Gary.M said:**
> This is widely reported and a fix/workaround has been posted on the Launchpad entry today. I have tried this and it fixed the problem for me.

Bug reported here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)

Fix in this entry
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983)
I don't think this entry belongs here (it's been added to the original post).  It was a kernel bug in 8.04 which is fixed in 8.10.  There are other USB bugs in 8.10 but without fixes :(

---

### Post by amd-64 on 2009-09-17
> **and.duncan said:**
> Bug: Bluetooth mouse won't work after a restart/standby etc.

Workaround: In Bluetooth manager change visibility setting away from 'Always visible' and then back to 'Always visible', mouse should be automatically detected again.

Alternatively, delete mouse pairing from the bluetooth manager and reacquire.

Link: [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/249448](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/249448)


There is a better solution here [https://lists.ubuntu.com/archives/ubuntu-bluetooth/2008-November/002928.html](https://lists.ubuntu.com/archives/ubuntu-bluetooth/2008-November/002928.html)

---

