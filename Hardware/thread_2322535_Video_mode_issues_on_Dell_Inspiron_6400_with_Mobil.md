---
title: "Video mode issues on Dell Inspiron 6400 with Mobility Radeon X1400 and WSXGA+ display"
date: 2016-04-28
forum: Hardware
---

### Post by dreamlayers on 2016-04-28
I'm trying to use Ubuntu on an old Dell Inspiron 6400 laptop with Mobility Radeon X1400 and 1680x1050 WSXGA+ display. I often see corruption after the kernel switches to the display's native resolution. After logging in, I can make it go away using: xrandr --output LVDS --mode 1400x1050 && sleep 1 && xrandr --output LVDS --mode 1680x1050

Considering how the xrandr mode changes make it go away and how it only temporarily appears and doesn't get propagated by graphical operations, I think this is a video mode issue. The kernel must be outputting a video mode which isn't quite right for the display. I never see those issues in Windows 7, so it doesn't seem to be a hardware problem.

Right now since I found that workaround I'm giving Ubuntu another try on this laptop using Xenial. It would be nice to have a proper fix.

---

### Post by weatherman2 on 2016-04-28
Which version/flavor of Ubuntu?  I've got a couple of these old Dell 6400's (or E1505, same thing) with different video cards and screens, being used by different people.  I'm using Ubuntu 14.04.2 lately with Gnome Flashback and I've interchanged the same hard drive into different laptops - one has the Radeon video card, one the Nvidia, one the integrated Intel card.  None of these have the issue you describe.  I have one WSXGA+ screen and same thing - never an issue with the video modes.  Everything works perfectly upon boot up, without any weird tweaks.  I don't think the Radeon card needed an Additional Driver, onyl the Nvidia card, so I can't really suggest trying that.

Have you updated to the latest BIOS, A17?  If not, I would try that, but you will need Windows I believe.

---

### Post by yoshii on 2016-04-28
Radeon video stuff is currently having issues with the new Ubuntu kernel and Ubuntu versions (16.04).  Search the forums and google, and you'll see similar issues.  
Also there was mention of this in the Ubuntu v16.04 release notes.  Sorry

---

### Post by dreamlayers on 2016-04-28
I'm using Xenial 16.04 with Cinnamon. The open source driver seems to be the only choice nowadays. AMD dropped support for that card in fglrx a long time ago, and I would probably need to use an old unsupported version of Ubuntu to run that driver.

The latest BIOS is installed.

This problem was present in past Ubuntu versions also. I forget which is the version I tried before though.

---

### Post by mörgæs on 2016-04-29
Do you see the same problem in X/Lubuntu?

---

### Post by dreamlayers on 2016-04-29
Is there really any point in trying different desktop environments? They all use the same X server. Furthermore, the corruption even happens if I'm in native resolution graphical text mode via the kernel only, without X running.

---

### Post by him610 on 2016-04-30
Using xrandr to set your monitor's resolution is a temporary fix good only for the current session. You need a permanent fix.

Experienced a similar problem a couple of months ago. Here is how I made the fix permanent. 

_Note: This may or may not work for you._

Using the editor of your choice, open this file... ```
sudo gedit /etc/default/grub
```
Locate the line ```
#GRUB_GFXMODE=640x480
```
Change it to read ```
GRUB_GFXMODE=1680x1050
```
Save and exit
Execute ```
sudo update-grub
```
Reboot your system

You should be able to boot into a stable video graphics environment.

To revert, change the the modified line back to its original setting.

---

### Post by dreamlayers on 2016-05-01
This Ubuntu install was actually copied from my desktop PC, where I had configured GRUB to use text mode and to boot with Linux startup text showing. (I think hiding boot behind graphics dumbs things down and potentially hides problems.) I thought about returning to a more typical configuration, but then I saw that plymouth isn't required via dependencies anymore, and uninstalled it. The problem seems solved. I've booted up 3 times so far without any of those corruption issues.

I also had the Nvidia packages installed from the desktop PC and I uninstalled those recently. Maybe that fixed the problem? Generally in Linux the presence of drivers isn't a problem, because they only become active if the hardware they support is found, but maybe the Nvidia drivers were the problem nevertheless.

I've also uninstalled some other packages, including r8168-dkms and dkms itself, because they're not relevant for the laptop. Those probably didn't make a difference.

There were no recent configuration changes which could have fixed this. It must have been due to the packages I uninstalled, probably either plymouth or Nvidia.

**Edit:** I started using hibernation on the laptop. When hibernating, the desktop disappears for a fraction of a second, and then reappears and is frozen while the data is being written to disk. During that time there is often severe video corruption. That doesn't really matter though. It's just a few seconds while the data is being written to disk, before the computer shuts off.

I also had mild corruption once after resuming from hibernation. I've booted and resumed many times though, so it seems rare, and I have that workaround for when it arises. It seems rare enough that I don't want to spend more time troubleshooting this.

My guess is that corruption can happen if multiple video mode changes happen quickly.

---

### Post by dreamlayers on 2016-05-29
Actually, the problem is not solved. I've had problems both after booting and after resuming from hibernation.

After setting Grub to 1680x1050 graphics mode, I got the problem at the Grub screen. Surely, Grub uses the BIOS to change video modes? Corruption there seems like a BIOS or hardware bug. Yet, it absolutely never happens in Windows 7 or Windows 10.

Sometimes the xrandr mode switching workaround needs to be done multiple times to get a stable mode, but it has always eventually worked. Once the mode is stable, it stays stable, and the problem has absolutely never reappeared later, except after hibernate.

---

### Post by mörgæs on 2016-05-30
How did X/Lubuntu 16.04 come out?

---

