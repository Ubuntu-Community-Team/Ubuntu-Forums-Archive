---
title: "Trying to make laptop faster 1.5ghz CPU dual core both 100%"
date: 2018-06-21
forum: Hardware
---

### Post by jimijives on 2018-06-21
Hi, I've made a bit of a mistake buying a new laptop.  10 years ago I bought a 15.6in Samsung dual core that was 2.2ghz and it recently broke down so I purchased an Acer Aspire ES1 for £250 and as it had Windows 10 installed I just assumed it would be much better or at least as capable as the Samsung.    It turns out it's an AMD E1 dual core 1.5ghz and Ubuntu 16.04 uses 100% of both CPUs when I have 10 tabs open in Firefox and basically slows to a stop for a while.  One tab is YouTube, the rest are just sites like this without many graphics.    This never happened on the Samsung which I had no problems with at all using either Win10 or Ubuntu 14.  I have tried to make it faster by installing a Samsung Evo SSD but it's still slowing to a stop.  For instance when I type text it takes about 10 seconds for it to appear on screen.    I have 4gb DDR3L 16000 Ram and it's using 94% Memory and 6% swap.  In Start Up Applications all that is running is a VPN, snap user application helper and Gnome SSH Keyring.  None of those are showing up under Processes in System Monitor.    Is there anything I can do to make this machine faster?    I really can't understand why the 10 year old Samsung was much better and that didn't have an SSD in it.    I tried to install Lubuntu (erase everything, clean install) but RKHunter went crazy and came up with about 20 warnings and 2 Rootkits present even though the SHA256SUMS matched.  I have tried to make separate paragraphs but for some reason the post isn't formatting them???

---

### Post by TheFu on 2018-06-22
Performance isn't always related to Ghz or Cores or age.  Video processing today - especially viewing videos - is almost always determined by the GPU and/or GPU driver support for hardware decoding of the video format and has almost nothing to do with the CPU anymore.

So, that is why a $90 Chromebook can playback all youtube videos perfectly - they have hardware + driver support to decode hidef h.264 video streams.  If the GPU + drivers don't support that, a higher end CPU can make up for the lack, but most CPUs new enough to handle hidef video also include iGPUs that handle mpeg2 and h.264 videos nicely.  H.265, OTOH, will be an issue for many laptops until the drivers and HW support that newer v-codec at all.

Clear as mud?

Windows really needs an i3 or better CPU to work, except in very limited situations.

Firefox since last fall has shown a number of performance problems, especially on low-end GPUs.  I have a system where firefox can't be used - takes 30 seconds for pretty much any user input to be seen. Chromium on the same machine works like you would expect.

RAM that isn't used is a waste. That is common in the Linux and Windows worlds.  Unused RAM is used for disk and network buffers automatically in Linux.  You can see that with **top** or **free -m** commands.

Snaps will use much more RAM than non-snap applications as their core libraries move farther and farther apart.  Snaps are a bad idea for RAM restricted systems like yours and mine.

The standard Ubuntu will be slow on lower-end laptops with low-end  GPUs.  Lubuntu should perform well on those systems.  I've never seen anything from rkhunter except false positives. NEVER.

So, after all that, I'm unsure if you want advice about replacing the computer and help selecting a better, faster, cheaper laptop that won't perform so poorly (hint, avoid cheap acers) - start with comparing CPU passmark scores
 or
do you want to make the current system as fast as possible and understand the limitations?

BTW, if you could post the **inxi -Fz** output that would be very helpful.  Nothing personal in that, with those options and we will have facts, not interpretations.

---

### Post by Yellow Pasque on 2018-06-23
> **jimijives said:**
> I have 4gb DDR3L 16000 Ram and it's using 94% Memory and 6% swap. 
When the system slows down like that, look at free and htop:
```
free -m
htop
```

> I tried to install Lubuntu (erase everything, clean install) but RKHunter went crazy and came up with about 20 warnings and 2 Rootkits present even though the SHA256SUMS matched.
rkhunter often spits out false positives. It's a very "paranoid" program aimed at server admins and power users. I wouldn't let it deter me from trying a lighter distro.

---

### Post by Autodave on 2018-06-23
My first thought was why you would need 10 tabs open at once: that will slow anything down. My second thought would be to try Xubuntu 18.04. It is much lighter than Ubuntu, but not a bland desktop. I run Xubuntu on a 700 ASUS EEEPC single core and it is not bad at all.

---

### Post by jimijives on 2018-06-29
Hi, thanks everyone for your advice.  

I have 10 tabs open sometimes because of wikipedia and it's endless links within a page or searching for answers to questions on Google and keeping all different answers open etc.  

I think it might be the GPU card because it's a Radeon and I read Ubuntu/Linux doesn't have/get the specific drivers like it does with Intel GPUs?  

Also I'm sure it's quite a basic GPU.  

I did notice Chromium is much much faster than Firefox when opening pages but I don't know if that's because I have 5 addons in Firefox including Ghostery, HTTPS Everywhere and NoScript?  

I installed inxi and this is the output:
```
inxi -Fz
System:    Host: jimi Kernel: 4.13.0-45-generic x86_64 (64 bit)
           Desktop: Unity 7.4.5  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Acer model: TRICERA_CZL v: V1.02
           Bios: Insyde v: V1.02 date: 09/19/2016
CPU:       Dual core AMD E1-7010 APU with AMD Radeon R2 Graphics (-MCP-) cache: 2048 KB 
           clock speeds: max: 1500 MHz 1: 1497 MHz 2: 1497 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Mullins [Radeon R2 Graphics]
           Display Server: X.Org 1.19.5 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.97hz
           GLX Renderer: AMD MULLINS (DRM 2.50.0 / 4.13.0-45-generic, LLVM 5.0.0)
           GLX Version: 3.0 Mesa 17.2.8
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.0-45-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (10.4% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB
Partition: ID-1: / size: 107G used: 8.2G (9%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 472M used: 136M (31%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 3.72GB used: 0.00GB (0%) fs: swap dev: /dev/dm-3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.4C mobo: N/A gpu: 51.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 213 Uptime: 1:20 Memory: 1711.1/3404.1MB
           Client: Shell (bash) inxi: 2.2.35 
```

With 13 tabs open (I was searching for info regarding encryption and wiping a usb to get rid of malware) this is the output of 'free m': (I installed htop but I don't know how to copy and paste it as it seems to be open in nano?  I only know how to use gedit.)

```
free m
              total        used        free      shared  buff/cache   available
Mem:        3485780     1884768      294280       59068     1306732     1250548
Swap:       3628540           0     3628540]
```

I really appreciate you all taking time to reply to my query.  

I think I'll just try and get used to this cheap laptop for a while.  Maybe try to keep the tabs down to a minimum.  It's just when typing input, I have to wait 5-10 seconds sometimes to see what I've input.  Quite annoying on a 'modern' laptop.  

As you already mentioned, for the basic use I need it for I probably should have bought a Chromebook but I like Ubuntu.  

Maybe as you advised I should install Lubuntu or Xubuntu.  

I did read that Ubuntu 18 LTS offers a 'minimal install'?  

Anyway, with your advice I have a few avenues to go down that should speed up performance so thanks again.

---

### Post by TheFu on 2018-06-29
That is a slow CPU relative to systems 4 yrs old. It has a passmark of 1000, so it is basically a chromebook-like machine trying to run a full OS.  I use chromebooks running Ubuntu, but always have gotten models that are 50% faster than the machine you have - passmark over 1500. I've seen refurbished versions of that model for $80, BTW. Saw a refurbished Dell 11 Chromebook with the same CPU last week for $90. My current chromebook has a passmark near 3200, but it isn't low-end.  

The free command shows that you aren't out of RAM and that no swap is being used.  I'm guessing if firefox is slow that you have the same firefox issues I'm having.  If you disable all the addons for firefox, is it still slow?   I have about 4 addons running in mine but keep it limited to avoid performance issues.

Definitely don't use Unity on a computer like that.  You can swap out Unity for a lighter desktop. No reinstall needed.  I'd recommend the Mate desktop. It is polished,  but still fast and has GUI programs for most Admin needs, unlike LXDE.  **sudo apt update && sudo apt full-upgrade && sudo apt install mate-desktop** will install it.  Then you'll reboot, pre-login, click on the "gear" and select the Mate desktop, then login normally. The entire GUI should look different.  If not, sometimes the "gear" selection doesn't actually get selected. Just logout and try to select it again.  You'll know when it has changed.  Use it for a few days or a week and if you like it, you can remove the Unity later.   Doing this will free up a little more RAM and will free up some GPU and CPU cycles that Unity wastes being extra pretty.

If Mate isn't to your liking, we all have different tastes, then you can try xfce4 or lxde just as easily.  It is best to try new DEs (desktop environments) using a guest or temporary account to avoid configuration setting conflicts.

BTW, The free command you used is missing the switch to make it pretty.  **free -m** not *free m*. No big deal, but details do matter.  If you could remove the "html code" tags for the text, that would make it easier to read the text in the last post.  It isn't wrapping in the forums.  But that you very much for posting the **inxi** output with code tags, very good for readability.  Also, good-on-you for using LVM. We can resize your swap if needed pretty easily because of  that.  I don't think it is needed, though I prefer 4.1G for swap on all non-server installs.  I'd check that the swap is "zswap" by running **dmesg |grep zswap**. We want to see something like 
```
[    1.026125] zswap: loaded using pool lz4/zbud
``` in the output. I think it is the default.

A system with 4G of RAM shouldn't have any problems having 10 tabs open.  I'm using one now and have 16 tabs open in the browser and 12 different windows open with different programs, but  only 3 of those are *heavy* processes. Most are xterms into  different computers. xterms are very light, unlike the fancy other terminals installed by default.

On Linux GUIs, you can  *select & paste* anywhere there is text thanks to X/Windows.  **htop** opens a terminal and begins putting updated system information into it every 2 or 5 seconds.  You can just select it with the mouse, then paste it using the middle mouse button into the Reply area here (or into any text entry field anywhere, inside any program). On a laptop, the middle mouse button is usually emulated with a 3 finger touch. No keyboard needed. No right menu needed. Just select then paste. The selection is placed into the x-buffer (a part of X/Windows). It might take practice to get the timing for all 3 fingers or the specific area on the touchpad where that works.  For example, mine is picking and the "paste" only works in the upper left area of the touchpad.  This is one of those things that is easy to understand in video, but hard to explain in words. ;(  I've been using select-paste for 25+ yrs. Copy-paste is 4x slower to me.  With a mount, it is really easy.   This works on any computer running X/Windows regardless of the OS.

I'm not very good with GPU drivers, so hopefully someone else will be able to advise based on the data provided already, but it appears you have a Radeon GPU. The output from  ** lshw -C video** will show clearly which drivers are being used.

[https://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/](https://www.makeuseof.com/tag/install-proprietary-graphics-drivers-ubuntu-fedora-linux/) has steps to load "Additional Drivers" which might be all you need.  IDK.  I'd be certain to have a bootable flash drive with Ubuntu installer ready before doing that so I could undo any issues. And I'd run a backup before doing it too.  And I'd keep track of the packages that were installed, so if I needed to remove them later, I could.  But having the correct GPU drivers is VERY important, so the risks are well-worth it, IMHO.

Or it could be something completely different.

A tip for future computer purchases, always check the passmark scores to compare values of different CPUs.  It is common for there to be $20 price difference between a terrible CPU and a mid-level one in similar laptop lines.  4 yrs ago, 1500 was the minimum for a happy desktop experience. I'd say 3000 is the min passmark today.

---

### Post by wildmanne39 on 2018-06-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please do not put text in HTML tags or PHP tags.

Thanks

---

### Post by jimijives on 2018-06-29
Hi TheFu,

thanks very much for replying again so soon.  I can't get the three fingers to work on my touchpad, two fingers right click is all I can manage.  I tried to copy and past htop before but I couldn't select the moving text for some reason.

How do I make paragraphs neat and tidy like you have?  In Preview Post it all looks good but when I post it's just a big mush.  Maybe I should be more concise.

Thanks for the info regarding Additional Drivers.  Unfortunately non were recognised so the GPU is as good as it's going to get I think.  I appreciate knowing that function is there though for the future, I'm kinda new to Linux and learning something new is always good.

I just read on a site that I don't need any anti virus or rootkit checkers because they make things worse by letting users get used to false positives and then not noticing real ones when they appear but more importantly the nature of anti virus software being able to access every file makes a huge attack surface so they're almost counter intuitive and can't stop zero day attacks anyway.  Ubuntu developers would patch any vulnerabilities just as fast as any anti virus provider.  I love the thought of this because rkhunter and chkrootkit freak me out a lot.  ClamAv just says 0 Infected but 20 million errors. 

It's difficult after being hacked in Windows to leave the OS completely free of protection even though it's intrinsically built in Linux.

Regards my CPU, yes I was very naive when I purchased it.  I just assumed a modern machine would provide a modern experience.  When I seen how low the CPU mark was I did laugh a bit because the graph almost found it hard to draw a line that small.

Maybe I'll just buy second hand, as you say I should be able to get something relatively cheap.  I could use this to practise on.  I'd like to learn how to use VMs as they are supposed to be very secure.

I disabled the Guest account because of paranoia so I can't install Mate just now.  I'm going to do a fresh install of Xubuntu or Lubuntu though because this CPU can't handle the full OS.  I was quite happy with the Lubuntu desktop as it is exactly all I need, a link to Firefox and I'm happy.  Ctrl Atl T is the only other important thing.  Oh yeah and the Dash button for updating even though that's automatic for security issues.  I have no idea why rkhunter seen so many errors in Lubuntu.  I verified the ISO with SHA256SUMS. 

I have a problem with my SSD.  I checked it using GParted and I get two results for the exact same size of partition. 

/dev/sda2/ says extended and size 111.31gb and looks fine but underneath that there is /dev/sda5 'crypt-luks' with a red exclamation mark.  The size is 111.31gb but the warning says 'Linux Unified Key Setup encryption is not yet supported.'  I do get asked for two passwords when booting up though, one for the disk and one for Home.

I don't understand that.

I have went on a tangent.  Thanks again for your informative reply.

[PHP]free -m
              total        used        free      shared  buff/cache   available
Mem:           3404        2256         123          60        1024         802
Swap:          3543           2        3540[/PHP]

[PHP]dmesg |grep zswap
[    2.353494] zswap: loaded using pool lzo/zbud][/PHP]

Should the text 'zswap' be in red letters?  You don't need to reply again, I don't expect you to answer all my noob questions.  They will all be different after I install a lighter OS anyway...

---

### Post by TheFu on 2018-06-29
Seems like you've understood the key things I'd hoped to convey.  That's excellent.

The machine you have should make a nice media payback system, if you connect it to your TV/projector and load Kodi.  Or it could be a server (without a GUI) for all sorts of uses.  Perhaps a backup server and/or Nextcloud for the house and/or remote access or VPN server?   All these things (non-gui) should happily run on a system like that.  For nextcloud and/or backups, I'd assume an external USB3 disk or two would be used for storage.  The GigE ethernet makes this much better than specialized, more expensive, items, BTW.

The zswap in red letters is just highlighing the search from the grep command.

The gparted stuff is because the system was installed with whole disk encryption.  That uses LUKS and LVM to accomplish.  Gparted can't see anything but the partitions. All the encrypted stuff and LVM stuff is unknown to gparted.  IMHO, all laptops (actually all portable storage devices) need to be LUKS encrypted.  The downside to encryption is that any disk issues can only be corrected by having excellent backups.  Trying to fix logical or physical errors  on an encrypted disk is often useless. So if you don't have daily or at least weekly, automatic, backups, please get some ASAP.  And be certain to validate that the restore actually works the way you need it BEFORE you need it.

For testing new DEs, you don't have to use a guest account.  Just make a new account in the normal way and login using it.  When you are done, delete that new test account.  No harm done. Just don't leave it lying around without an extra strong password (25+ characters).

AV for Linux is mostly about searching for Windows virus signatures. If the system is frequently on a network with Windows machines, it is nice if you run AV.  If you use WINE on Linux, it is possible to get some Windows virii.  Not all, but some work under WINE and can be damaging.

3-fingers on the touchpad can mean that the driver isn't configured for it.  I have this configured in my "autostart" file which is run only when login physically on the laptop:
```
synclient TapButton1=1 &
synclient TapButton2=3 &
synclient TapButton3=2 &
```
Run it manually in a terminal and see if that helps.  If it breaks anything, a reboot will make it go away.

---

### Post by jimijives on 2018-06-29
Apologies to wildmanne39, I didn't see your post.  Thanks for the advice.

TheFu, I just added a new user and then entered the command:
```
usermod -aG sudo jives
```

but it said usermod wasn't allowed in the passwd file or something similar.  

When I logged into the account it said I wasn't in the sudoers folder.

So I couldn't enter the command you provided to install Mate.

Before that I tried to get the 3 fingers functioning using the commands you provided but the first command just output a number then
the next two output a number but the word 'Done' after the number.

Still didn't get the three fingers working for some strange reason because it obviously made two changes at least.

Thanks for the alternative usages of this laptop.  I like the idea of it being a link to the tv via HDMI because I have Amazon Prime.

Maybe with Kodi I could learn some penetration testing to see how to learn how to harden Linux.

Nextcloud sounds interesting although I'd have to look it up to fully understand it but if it's a personal cloud then that would be nice.

Thanks for putting my mind at ease regarding GParted output.

---

### Post by TheFu on 2018-06-29
If your touchpad uses different drivers,  you may need totally different commands. You'll need to hunt down that info.Sorry. Many systems use synclient.  Also, check if your system supports 3 mouse button emulation.
The numbers displayed were just because the program were placed into the background.  Standard Unix job control stuff. It is worth knowing those techniques, BTW.

Installed programs are available (generally) system-wide.  Use your sudo account to do everything except actually login and test.  The settings that can conflict are per-userid, not per-system.  Linux is multi-user, so we have to think multi-user. ;)

---

