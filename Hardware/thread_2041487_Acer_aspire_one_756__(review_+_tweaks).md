---
title: "Acer aspire one 756  (review + tweaks)"
date: 2012-08-12
forum: Hardware
---

### Post by saou on 2012-08-12
I just got this netbook and put xubuntu on it, dual boot with window 7.   Wifi/LAN/hdmi/xrandr  work out of box (I have not tried VGA).  Suspend also works via the logout menu, but not through the F4 key.  Volume control, speaker mute and wifi on/off work via function keys.

Multitouch works out of box, including two-fingers vertical and horizontal scrolling (you might need to adjust touchpad settings in xfce).  Pinch-zoom does not work.   Right-click is slightly flaky and/or I have not yet found the sweet spot for right click (which I guess means it's flaky :-)

On a freshly charged battery, xubuntu reports/predicts 5:32 of battery life.  I have not tried to drain it, but based on experience with other laptops this is a reasonable estimate for normal use (40% brightness, wifi on, light browsing+emails+editing); take 30% for looping youtubes :-)

The speakers are surpising loud but very tinny.   I watched fullscreen 720p video (using VLC) for about 40min (on AC); the palm rest is warm but comfortable, and both cores stay below 56 degree.  I've been using this all day and the fan is not loud at all (disclaimer:  I don't have good ears!)

Two tweaks (warning:  don't blame me if these brick your machine!):

(1) Common acer problem: Backlight control does not work out of box.   I googled "acer brightness" and found this fix on the ubuntu forum (unfortunately I lost the original URL):  Edit /etc/default/grub  by changing

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

then  sudo update-grub and reboot.

(2)  There is a long delay between logging in and xfce showing up.  This seems to be a xubuntu and/or lightdm problem.     See  post #39  [http://ubuntuforums.org/showthread.php?t=1970326](http://ubuntuforums.org/showthread.php?t=1970326)   for a patch (remember to reboot).

The screen is good (not macbook good) and has good viewing angle.  The keyboard is good (on par with the ultrabooks on display at BB), about 95% of the regular ones.  I've been typing on it all day and have not problem except for the forward slash key (because of the 95% keyboard it's slightly off from where I'm used to finding it; should be okay after a few days).  The arrow keys (and tilde) are small but functional.

All in all this is a very capable, light (< 3lb) and inexpensive travel machine.  I like it a lot.  I plan to put SSD + 8G of ram and make it a poor-man's 'bunbook air, all for all about $400!   Good luck!

PS:  Mine has a celeron 877 -- slightly clockdowned version of sandy bridge i3.   Several people on amazon says that that this is on par and maybe slightly better than the pentium one (I have not tested that).

---

### Post by ahallubuntu on 2012-08-12
~

---

### Post by addlepatedcamel on 2012-08-18
I jumped on the AO756 band wagon as well. I needed something to replace my ancient mac laptop.  I'm planning on downloading Ubuntu 12.04 and I'm assuming I'll need the 64bit version for the celeron 877 processor since the computer comes with the 64bit Windows.  The only reason I ask is because the 32bit version is listed as "recommended" on the download page.

I just want to double check before I download the huge installer file.  I'm also going to up the ram from 2g to 8g.

Thanks.

---

### Post by addlepatedcamel on 2012-08-18
Or perhaps a better way to phrase it, which version would a more experienced Ubuntu user suggest for a relative newbie such as myself?  Given that the intel celeron 877 is a 64bit processor and from my understanding, the 32bit ubuntu version should work as well.  
Thanks.

---

### Post by ahallubuntu on 2012-08-18
~

---

### Post by vickoxy on 2012-08-19
Hi,thanks for reports. I am also interested in this modell-so if someone can describe more accurately the fan behaviour-i will be very grateful. I want to know how much audible is the fan at the lowest speed?

---

### Post by vigi84 on 2012-08-20
I have just ordered a netbook like this, and I am planning to install Ubuntu 10.10, the netbook version.
Maybe it's a naive question, but which version of Ubuntu drains the battery least, hardware-usage-wise etc.??

---

### Post by saou on 2012-08-21
> **vigi84 said:**
> I have just ordered a netbook like this, and I am planning to install Ubuntu 10.10, the netbook version.
Maybe it's a naive question, but which version of Ubuntu drains the battery least, hardware-usage-wise etc.??

xubuntu and lubuntu is more lightweight and a bit more power-efficient than unity 3D.  See  [http://www.phoronix.com/scan.php?page=news_item&px=MTA2NDA](http://www.phoronix.com/scan.php?page=news_item&px=MTA2NDA)   for some benchmarks.

---

### Post by vigi84 on 2012-08-23
Thanks for the answer! Appretiate it!
Yes, according to this chart Lubuntu does seem to take off some weight of CPU and battery usage.

But am so very used to Ubuntu 10.10, and not very keen on changing this habit of mine, because, as it's said Ubuntu is Linux made for human beings. Heh, and I am not very much of a programmer-mind to understand every bit, some installations are still time consuming in Ubuntu, but I like the challenge.

Anyhow, most importantly, the question is if important software would be running on Lubuntu, e.g. Corel After Shot Pro - this is my biggest concern, Libre Office 3.6., that I presume works. Do these OS-es have e.g. a software centre like Ubuntu?

Would the netbook version of Ubuntu 10.10 be still a good option?

---

### Post by saou on 2012-08-24
If you are used to ubuntu 10.10 then I recommend xubuntu 12.04.  I find xubuntu to be the right balance between clean/light-weight install on the one hand and useability on the other (I hate unity and and find lubuntu a bit too spare).  I've been on the road for over a week with my 756 running xubuntu 12.04, often using power saving mode (both CPU clocked at 800MHz) and I have no problem with it except for high res youtube video; the reduced heat is a big plus :-)

If you don't mind wasting bandwidth, download the different version and run them as live USB/CD and see which one you like best.   Oh, I would not recomend using any version of 10.10; it is no longer supported (so no security update -- bad idea!!)

Good luck and let us know how it turns out!

---

### Post by vigi84 on 2012-08-27
OK, so I've got lost a bit. Now, I am in between Xubuntu and Linux Mint Debian Xfce, or even Mate/Cinnamon. 

The most important thing is that I can run Bibble 5 Pro, Darktable, Libre Office 3.6 without any bugs, or deficiencies in design or functionality.

Xfce is different desktop environment which might not support Bibble 5 Pro. I think it works with Darktable, but it might have some bugs.

And another important factor is that it should work with this netbook! And what I found out was that it works nice with Mint 13 Xfce.  According to this review.

[http://www.amazon.com/Acer-Aspire-AO756-2808-11-6-Inch-Netbook/product-reviews/B0083PR78C](http://www.amazon.com/Acer-Aspire-AO756-2808-11-6-Inch-Netbook/product-reviews/B0083PR78C)

---

### Post by vigi84 on 2012-08-27
OK, so I've got lost a bit. Now, I am in between Xubuntu and Linux Mint Debian Xfce, or even Mate/Cinnamon. 

The most important thing is that I can run Bibble 5 Pro, Darktable,  Libre Office 3.6 without any bugs, or deficiencies in design or  functionality.

Xfce is different desktop environment which might not support Bibble 5  Pro. I think it works with Darktable, but it might have some bugs.

And another important factor is that it should work with this netbook!  And what I found out was that it works nice with Mint 13 Xfce.   According to this review.

[http://www.amazon.com/Acer-Aspire-AO...ews/B0083PR78C]("http://www.amazon.com/Acer-Aspire-AO756-2808-11-6-Inch-Netbook/product-reviews/B0083PR78C")

---

### Post by vigi84 on 2012-08-27
OK, I am here at the Xubuntu website, but it does not seem that there is a 64 bit version for Intel.

---

### Post by ahallubuntu on 2012-08-27
There is no "Intel version" for 64 bit.  There is a 32 bit version of Xubuntu and a 64 bit version both both AMD and Intel CPUs.  Since AMD was the first to introduce 64 bit X86-compatible CPUs, their name is on the standard.  "AMD64" works just fine on Intel 64 bit CPUs.

---

### Post by vickoxy on 2012-08-28
Sorry for double-posting;

> And one more question-there is one modell of Aspire One 756 with Celeron 847 (1,1 Ghz) - i like this modell because it has non-glare display. Would there be big difference between Celeron 877 and Celeron 847?
([http://ubuntuforums.org/showthread.php?p=12201059#post12201059](http://ubuntuforums.org/showthread.php?p=12201059#post12201059))

---

### Post by vigi84 on 2012-08-28
> **ahallubuntu said:**
> There is no "Intel version" for 64 bit.  There is a 32 bit version of Xubuntu and a 64 bit version both both AMD and Intel CPUs.  Since AMD was the first to introduce 64 bit X86-compatible CPUs, their name is on the standard.  "AMD64" works just fine on Intel 64 bit CPUs.

Thanks a dozen! I think I'll go with the Xfce DE. So Xubuntu, or Mint DEB Xfce.

Namaste! Peace!

---

### Post by vickoxy on 2012-08-29
Hi again-i bought today the acer aspire one 756 with celeron 847 (1,1 Ghz) because it has non-glare Display.:popcorn:
It is really nice machine. The CPU Fan is very quite, but i have feeling that is almost unnecessary working all the time. I installed lm-sensors but sensors-detect found no fan:
```
linux@linux:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +44.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +44.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +43.0°C  (high = +86.0°C, crit = +100.0°C)

```
This thread doesn´t help me a lot:
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)
Any suggestion how to make fancontrol working under xubuntu 12.04 with celeron 847?
Tried also acerfand and acer_ec.pl but there are not responsive on my ao756...

P.S. One more question: my AO756 has no bluetooth-is it possible to install some bluetooth card or i can use only usb bluetooth adapter?

---

### Post by vickoxy on 2012-09-01
Well-if some one is interested to make some fan control working-please post here:
[http://ubuntuforums.org/showthread.php?t=2050184](http://ubuntuforums.org/showthread.php?t=2050184)

---

### Post by deciocavallo on 2012-10-27
i've buyed an acer 756, i've put a SSD on it and i've installed xubuntu 12.10. 
I've applied the first tweak on first post. Xubuntu works very well and is very fast (maybe for SSD). 

All works very well.:popcorn:

---

### Post by robiwolf on 2012-12-25
I'm planning to buy an AO756, the 987 with 1.5 ghz processor. Anyone can tell me that does it run Minecraft under ubuntu? I have no idea where can i ask this question, so i aks here... Please, if anyone have any experience in this question, just let me know! Sorry for my english...

---

### Post by husam212 on 2013-01-31
I have the celeron 847 edition, wifi keeps disconnecting every 5~10 mins .. all other devices in my home have stable connection using the same router.

I tried the modprobe trick with no success :(

EDIT: solved, installed linux-backports-modules-cw-3.6-precise-generic meta package and everything worked great :)

---

### Post by CiprianL on 2013-05-20
I have just purchased an Aspire One 756 with the newer Ivy Bridge Celeron 1007u processor. Both it's performance and quality are satisfying - well, except the Elantech touchpad, that's a little weird to use, lacking separate buttons. (As a side note, the touchpad driver seems better at detecting multitouch tapping in Ubuntu than the original one for Win 7.)

I've installed Kubuntu 13.04 x64 on it, and it works perfectly, after I've updated the kernel to 3.90, downloaded from 
[URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/"]
http://kernel.ubuntu.com/~kernel-ppa/mainline/[/URL]

(this was necessary because the 3.8.x kernels - both the original that came with the iso image, and the one received from update - were randomly crashing the system, both on Kubuntu and on Ubuntu Gnome Edition). Information on installing the kernel can be  found at 
[URL="http://www.ramoonus.nl/2013/04/30/ubuntu-linux-kernel-3-9-installation-guide/"]
http://www.ramoonus.nl/2013/04/30/ubuntu-linux-kernel-3-9-installation-guide/[/URL]

[FONT=Ubuntu][SIZE=3][COLOR=#333333]The brightness controll still needs to be fixed as described in the first post of this thread.[/COLOR][/SIZE][/FONT]

---

