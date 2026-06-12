---
title: "Lucid Geforce MX 420 slow scrolling, flash, video"
date: 2010-04-29
forum: Hardware
---

### Post by xDwarf on 2010-04-29
Hi everyone. After trying a few Linux distros throughout the last years and generally using OS X as my preferred OS I am willing to make the transition to Ubuntu. To a large extent because I am getting bored of OS X (its TOO simple) and the in my opinion rightwing/restrictive policies of Apple in general, crazy margins on their sales and more specifically regarding the iPhone OS (Apps, illegalized use of other non-Apple code translated to native iPhone such as flash) - not that I use it but it says a lot about Apple - etc. (much like Germany in the 1940s).

So much for the quick intro.

I have come to love Lucid 10.04 very quickly and this is my new OS of choice, also at work. Here I have an Athlon XP 2200+, 1GB RAM, Geforce MX 420 (64MB AGP4x) and a 1920x1080px screen.

What works:
I have tried visual effects off/minimum and normal and currently have  compiz activated which runs surprisingly well and makes no difference to my problems. The wobbly windows and  cube are very satisfying considering the age of the GPU.

The issue:
in all browsers (I primarily use Firefox but have tried chrome and opera) scrolling is rather slow with xorg hogging 80%+ of my CPU and Firefox has the rest, as soon as the websites are a little more complex the slowdown is even more quite severe. Flash is slow and at full screen utterly useless. Also in other programs like Evolution I notice lag when scrolling.
Any full-screen OpenGL screensavers included in 10.04 run at about 5fps but seem ok in the little preview window. Any fading effects are slow too, such as when demanding the password for Synaptic and other admin tasks.
Scrolling in PDFs is slow as well (I am referring to the document viewer), even relatively simple/text-only ones.

What I've tried:
I am 90% sure this is a GPU age or driver issue. That whole IPv6 issue doesn't explain slow scrolling/OpenGL etc. and anyways, I've disabled IPv6 in Firefox as this was an issue for me. Also on my Macbook I run Lucid in a VM with a nasty GMA950 integrated GPU and things are prefect here (except of course no compiz) in terms of the issues I've described. I understand my screen is a lot smaller on the Macbook but then a GMA950 in a VM is no match for a discrete 64MB GPU either.
I've tried:

[LIST]
[*]that initial pixel=2 thing (doesn't make any difference)
[*]the proprietary nvidia drivers (thanks to these compiz seems to be working great), version 96.43.17
[*]installing the .sh driver from nvidia.com, I got errors and it wouldn't install. I gave up because I figured these are the same as the "Administration/Proprietary Drivers" I am using
[*]uninstalling nvidia-nouveau (doesn't make any difference), reinstalling it, uninstalling the "Administration/Proprietary Drivers" and re-installing nvidia-96 through Synaptic
[*]tried Firefox in Wine and same symptoms
[*]turning detect refresh rate off for compiz (doesn't make any difference) and anyway, compiz seems to be working beautifully anyways
[*]tried flash with and without hardware acceleration - same both ways
[/LIST]
Things I've noticed/want to know:
I am not sure what my actual refresh rate is. I think it is either 0 (impossible) or 60hz (CRT-0 shows 60hz). All is set to auto/default in the nvidia-settings.
Nvidia-settings shows:
Bus Type: AGP 4X
Bus ID: ?@?:?:?
PCI Device ID: unknown
PCI Vendor ID: unknown

is that a problem?

Is it the big screen that's killing my little GPU? But compiz works so well? Is scrolling usually hardware accelerated? And flash should be as I can check/uncheck hardware acceleration (which as mentioned makes no difference).

So I believe that's all I can say for now. I think this is a great community and I'm glad I've made the choice to battle it through and go Ubuntu for good.
Thanks in advance for any help.

---

### Post by xDwarf on 2010-04-29
ok I may have scared people by writing too much :confused:

---

### Post by xDwarf on 2010-04-30
Nobody else with issues of this kind? Today i also tried adding:

Section "Extensions"
    Option "Composite" "Enable"
EndSection
[FONT=monospace]
[FONT=Verdana]to the xorg.conf, no change.[/FONT]
[/FONT]

---

### Post by ifolmedo on 2010-05-04
I am experiencing same problem.
lspci output:
```
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
```

---

### Post by margen on 2010-06-06
I have exactly the same problem except I'm on a slightly different hardware - Athlon XP-M 2500+ with a stable clock to 2500 actual MhZ and a Radeon 9800 Pro.

I've been trying to switch to Ubuntu, but It's been, to say the least, really annoying. Besides this I really enjoy Ubuntu.

I also tried disabling the IPv6 thing (didn't work), and I also removed Compiz and switched to Metacity's compositing. I think it helped a little bit, but the problem is still there.

---

### Post by Arijan on 2010-09-13
I've got the exact same pc configuration (maybe not the same motherboard, but CPU and VGA are the same)

What I am experiencing ever since ubuntu 9.04 is that once Nvidia drivers installed, the Xorg is too slow, week responsive, and cpu expensive.I am using 3d apps though, and what is most interesting is the way how older distros behave completely different than new ones  on the same issue:

From ubuntu 8.10 and backwards (including Debian 5, 4; Suse 11, 10 >, Fedora 6,7) I usually had to disable composite extension in order to have satisfying 3d performance. All was fine and smooth.

But from new kernel and Xorg versions (mostly Ubuntu, starting with 9.04), I have a different situation: Composite Ext. could be on or off - doesn't matter, 3d works (not perfect in speed);
With desktop effects enabled Xorg works fine, but I have no 3d space in 3d apps.
And when desktop effects are disabled - it's the opposite pain: Xorg eats cpu and the feeling is like I work with old 286 pc - windows freeze, moving windows leave white traces, switching desktops hangs 2-4 seconds - and 3d works

I have no idea how this is possible - except to think of bad driver compatibility with Xorg...

I've tried everything - I mean E v e r y t h i n g  to get this to work properly - went to at least 10 000 internet links, read tons of suggestions, reinstalled at least 30 times 5-10 versions of newer linux distros (and who knows how many driver reinstalls per distro) - and I'v got enough of it - I wanna buy SGI!!! I wanna pay 10 000$ for my nerves - ok this was a way too much :) Who doesn't want a SGI?

Anyway, I just think the older hardware isn't supposed do work properly and that smoothly with new distros - we should be happy that it works at all...

---

### Post by odzk on 2010-10-30
Im just going to repeat what everybody said. Any solution on this problem as of yet?

---

### Post by eynestyne on 2010-10-30
I dont kno about the scrolling issue, but i had slow flash video when viewing as fullscreen. Turning off hardware acceleration (right click on the video - setting) solved it.

---

### Post by odzk on 2010-11-02
> **odzk said:**
> Im just going to repeat what everybody said. Any solution on this problem as of yet?

I got mine resolved by installing the official NVDIA driver from the website, 

[http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html)


make sure that you have the latest kernel or else it will fail like what happened to me.

im using kernel 2.6.32-02063225

run in recovery mode, then choose the last option, drop to shell

on the command prompt. type "telinit 3"
it will ask you for your username and pass.

then locate where you save it. i have mine in the downloads
therefore I type:

cd Downloads

then execute the command

sudo sh NVIDIA-Linux-x86-???????.run 

follow the instruction and thats it.

sudo reboot.

it should work.

---

### Post by rohnadams on 2011-08-26
> **odzk said:**
> I got mine resolved by installing the official NVDIA driver from the website, 

This driver version does not support the GeForce MX 420. The legacy driver 96.*** does support the GeForce MX 420, however previous versions were incompatible with the version of X.Org included in Ubuntu 11.04. Luckily for us, nvidia has released an updated version of this legacy driver (96.43.20 - released 8/17/2011) that adds support for this version of the X.Org server. 

Head here to grab the 32-bit driver: [http://www.nvidia.com/object/linux-display-ia32-96.43.20-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.20-driver.html)

or here for 64-bit AMD driver: [http://www.nvidia.com/object/linux-display-amd64-96.43.20-driver.html](http://www.nvidia.com/object/linux-display-amd64-96.43.20-driver.html)

Installation is simple but cannot be done while the graphical interface is running. Ctrl+Alt+F1 to switch to a terminal and then shutdown the graphical server:
sudo /etc/init.d/gdm stop

Change directories to where the driver you just downloaded is located.
cd /PATH/TO/FOLDER

Begin the driver installation with the following:
sudo sh NVIDIA*96.*.run

Follow the instructions; it should be safe to say YES to all prompts. Ignore the "provided install script failed" error as this apparently always happens on Ubuntu systems. If you have the nouveau (or I suppose any other conflicting) driver installed, the installer will provide options for disabling it and may tell you to restart. Upon restart, again follow the above commands to shutdown the graphical interface and drop to a shell. Execute the install script again, say YES to everything, reboot and now the new driver should be installed.

This worked perfectly for me and resolved most of the display issues I had been having: flickering, slow scroll, flash videos, etc. It also provided me with additional (and higher) screen resolutions.

NOTE: If you allow the installer to automatically edit your xorg.conf file & you use Compiz as your window manager (I believe Ubuntu does by default), you will lose some effects, like titlebars, etc. To re-enable them execute:
sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

