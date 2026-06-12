---
title: "3D graphics on HP Compaq 8200 Elite?"
date: 2012-01-19
forum: Hardware
---

### Post by gleedadswell on 2012-01-19
I have successfully installed 11.10 on an HP Compaq 8200 Elite, with a few difficulties which I eventually overcame.  That story is here:

[http://ubuntuforums.org/showthread.php?t=1911886]("http://ubuntuforums.org/showthread.php?t=1911886")

I can't seem to get Unity 3D working.  When I choose "Unity" at login I am definitely getting Unity 2D (e.g. echo $DESKTOP_SESSION returns ubuntu-2d).  I'm aware that this probably has to do with the graphics driver.

When I go to System Settings > Additional Drivers it tells me that no proprietary drivers are installed and gives me no option to install them.  During the install I did tell it to install the proprietary drivers.  Does this just mean there are none available for my graphics card and there's no way I can get 3D working?  Or is there something else I can do?

---

### Post by gleedadswell on 2012-01-22
Still no 3D, but here's an update after I did some further reading.  I tried 
```
geoff@geoff-HP-8200:~$ compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (bailer) - Info: Ensuring a shell for your session
geoff@geoff-HP-8200:~$ 
(metacity:2737): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
....

```

and it gave a string of other Gtk-WARNINGS.

lspci -v shows

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 3395
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel modules: i915

```

I downloaded compiz-check.  It says

```
Gathering information about your system...

 Distribution:          Ubuntu 11.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) Y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) Y

```

Typing that last "Y" just brought up the additional drivers dialogue, which still shows no additional drivers available.  It also game me the same string of Gtk-WARNINGs as before.  

Just in case I tried

geoff@geoff-HP-8200:~$ gconftool-2 --recursive-unset /apps/compiz-1
geoff@geoff-HP-8200:~$ gconftool-2 --recursive-unset /apps/compizconfig-1
geoff@geoff-HP-8200:~$ unity --reset

which also gave the Gtk-WARNINGs.  I installed the gtk2-engines-pixbuf package and now at least the Gtk warnings are gone.  But still no 3D.

The line about the vesa driver not being capable of running Compiz that compiz-check gave seems pretty final.  Is anyone aware of what drivers I can get for this hardware that might do the trick?

---

### Post by gleedadswell on 2012-01-22
...and a further update.

There is a thread on support of Sandybridge graphics (which is what I seem to have) here:

[http://askubuntu.com/questions/65765/does-11-10-support-sandy-bridge]("http://askubuntu.com/questions/65765/does-11-10-support-sandy-bridge")

One person there said it worked for them to do

apt-get remove libdrm-intel1:i386

apt-get install libdrm2 libkms1 i965-va-driver xf86-video-intel

That apt-get remove brought up a set of packages to remove that looked like the entire desktop environment!  So I chickened out.  I did install libkms1 and i965-va-driver.  xf86-video-intel doesn't seem to exist (or its name has changed).  But unity --replace still doesn't work.

---

### Post by MoreOrLess on 2012-01-23
Pastebin your /var/log/Xorg.0.log

---

### Post by gleedadswell on 2012-01-24
> **MoreOrLess said:**
> Pastebin your /var/log/Xorg.0.log

Thanks for the help!  I hadn't come across pastebin before.  That looks very useful.  My Xorg.0.log is at:

[http://pastebin.ca/2105661]("http://pastebin.ca/2105661")

---

### Post by gleedadswell on 2012-01-24
An additional symptom.  I think this is new, so it might have been caused by the installs I mentioned in a previous post.  Or obviously it could be completely unrelated.

My mouse pointer icon tends to disappear a lot.  The places I've noticed it disappear are:

while I hover over any item in the right click menu from the Launcher.
most of the time while the mouse is over the document in a LibreOffice Draw file (which makes Draw very hard to use!!)
While hovering over icons which are links in a webpage displayed by Chromium
after single clicking any file in Nautilus

-------Edit added later---------

If I log into either the gnome shell or the classic gnome fallback I still have the issue with the disappearing pointer, but it is less severe.  It doesn't seem to happen in LibreOffice but it still happens when I hover over icons in the browser or click files in Nautilus.  It also disappears if I hover over an item on the panel, including items in the application menu.

---

### Post by gleedadswell on 2012-01-25
Wow!  Because of the flickering mouse pointer (which is making LibreOffice Draw very hard to use) I've been using Gnome shell when I'm on this machine until I can get these things resolved.  Now that I'm used to Unity and all its great hotkeys I'm finding Gnome really annoying!  When I first started using Unity if anyone had told me I'd eventually find Gnome annoying I probably would have laughed.

---

### Post by MoreOrLess on 2012-01-25
Your symptoms are probably caused by booting with nomodeset. What happens when you boot without that?

---

### Post by gleedadswell on 2012-01-26
> **MoreOrLess said:**
> Your symptoms are probably caused by booting with nomodeset. What happens when you boot without that?

Yeah, I was afraid that might be the root of the problem.  It boots to black screen without nomodeset.  See here

[http://ubuntuforums.org/showthread.php?t=1911886]("http://ubuntuforums.org/showthread.php?t=1911886")

and here

[https://bugs.launchpad.net/ubuntu/+s...el/+bug/887756]("https://bugs.launchpad.net/ubuntu/+s...el/+bug/887756")

Just in case things had changed I just now tried booting without nomodeset, but I got the boot to black screen.

---

### Post by gleedadswell on 2012-01-27
My understanding is that if I can find an nvidia driver for this card then I'll be able to turn off nomodeset and things should work.  Is that correct?

Unfortunately, after a fair bit of looking I haven't come up with a driver.  Might this

[http://intellinuxgraphics.org/2011Q1.html]("http://intellinuxgraphics.org/2011Q1.html")

be what I'm looking for?

---

### Post by Mark Phelps on 2012-01-27
It's not a card; it's a chipset -- and it's attached to the motherboard -- and it's Intel, not Nvidia.  So, I seriously doubt that forcing the installation of Nvidia drivers is going to get the Intel 915 chipset to behave the way you want.

---

### Post by gleedadswell on 2012-01-27
> **Mark Phelps said:**
> It's not a card; it's a chipset -- and it's attached to the motherboard -- and it's Intel, not Nvidia.  So, I seriously doubt that forcing the installation of Nvidia drivers is going to get the Intel 915 chipset to behave the way you want.

OK, I know little enough about hardware that I don't know the distinction.  So I have the following holes in my understanding:

1. What is the difference between a graphics card and a graphics chipset?

2. What the heck is nvidia anyway?  To start with, is it hardware or software?

A quick look at Wikipedia (yes, I know little enough about this that I'm starting there) tells me:

> Modern low-end to mid-range motherboards often include a graphics chipset manufactured by the developer of the northbridge (i.e. an nForce chipset with Nvidia graphics or an Intel chipset with Intel graphics) on the motherboard. This graphics chip usually has a small quantity of embedded memory and takes some of the system's main RAM, reducing the total RAM available. This is usually called integrated graphics or on-board graphics, and is low-performance and undesirable for those wishing to run 3D applications.

I already knew it was integrated into the motherboard.  I guess I thought that was called an "integrated card" or something like that, but I must be misusing the terminology.

So Nvidia is a particular brand of graphics card?  I think I was under the mistaken impression that it was simply a "type" of graphics driver in some vague sense (a protocol or something).  So I'll rephrase:

If I can find a better driver for the integrated intel chipset will I then be able to remove the nomodeset option and have things work?  Does anyone know if such a driver exists for a 

geoff@geoff-HP-8200:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

?  Or am I stuck with no 3D graphics and with misbehaviour of the mouse pointer even in gnome-shell?

I don't know my way around an Xorg.0.log very well.  But if it helps, the only thing that stands out as an error in mine is:

[    10.152] (EE) GLX error: Can not get required symbols.

But if the problem is grub telling the hardware at boot to not even try to use advanced graphics then is the root of the problem happening long before this in the process?

My whole Xorg.0.log is posted on pastebin (see an earlier post on this thread).

---

### Post by gleedadswell on 2012-01-27
I really like the window management in Unity.  So my preference is to figure out how to get 3D (or at the very least a fully working mouse pointer so I can use Unity 2D).  However, if that is impossible, am I likely to have these same issues if I try Xubuntu instead?

---

### Post by MoreOrLess on 2012-01-27
From the log: 
```
[    12.592] (II) LoadModule: "glx"
[    12.592] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    12.592] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    12.592]    compiled for 6.9.0, module version = 1.0.0
```

You tried to install the proprietary ATI driver and that's bad news. The good news is that it's easily reversed: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)

---

### Post by gleedadswell on 2012-01-31
Thanks very much, MoreOrLess.  This feels like progress, but no luck yet.  I followed that set of instructions.  There was no 

/usr/share/ati/fglrx-uninstall.sh

so I wasn't able to run that.  But I ran all the other purges, installs and reconfigures.  I did not do

sudo apt-get install fglrx-modaliases

since that is to install proprietary packages which seemed to be the root of the problem in the first place.  Also, it doesn't seem to exist anymore.  What has it been replaced with and should I have installed it?

I still have the problem with the disappearing mouse pointer and if I try to log into unity 3D my $DESKTOP_SESSION=ubuntu-2d.  If I remove "nomodeset" from my grub.cfg I still get a boot to black screen.

Here are few diagnostics:

The lines you quoted from my /var/log/Xorg.0.log have been replaced with

```
[    10.780] (II) LoadModule: "glx"
[    10.780] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    10.780] (II) Module glx: vendor="X.Org Foundation"
[    10.780] 	compiled for 1.10.4, module version = 1.0.0
[    10.780] 	ABI class: X.Org Server Extension, version 5.0
[    10.780] (==) AIGLX enabled
[    10.780] (II) Loading extension GLX
[    10.780] (II) LoadModule: "record"
[    10.780] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    10.780] (II) Module record: vendor="X.Org Foundation"
[    10.780] 	compiled for 1.10.4, module version = 1.13.0
[    10.780] 	Module class: X.Org Server Extension
[    10.780] 	ABI class: X.Org Server Extension, version 5.0
[    10.780] (II) Loading extension RECORD
```

Is that about what it should be?  It no longer says

vendor="FireGL - AMD Technologies Inc."

which I assume was the tip off that something was wrong.  My new Xorg.0.log is at

[http://pastebin.ca/2108262]("http://pastebin.ca/2108262")

Currently the directory /usr/share/api does not exist, which I assume is a good thing?

Currently if I look in synaptic at what I have installed I see I've got:

jockey-common
jockey-gtk
xserver-xorg-video-radeon
libgl1-mesa-glx
libgl1-mesa-dri
mesa-utils

In particular, I do not have

fglrx
fglrx-amdcccle

-------------------Aside----------------------------------

By the way, shouldn't 

apt-cache search --installed fglrx

list only things I've got installed on my system with fglrx in the name or description?  If so then it's not working.  I see no difference in the lists when I run apt-get search and apt-get search --installed.  But synaptic clearly shows that most of the listed packages are not installed.  Am I misunderstanding the use of the --installed flag in apt-cache?

---

### Post by gleedadswell on 2012-02-07
I decided I'd try some of the previous tests to see what they are saying now that I've removed fglrx.  I get

```
compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session
```

and 

```
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 11.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) Y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) Y
```

Again the last "Y" led to me being prompted for my admin password and then the Add Additional Drivers dialogue came up.  It still shows no additional drivers.

So, currently it stands at:

No additional drivers installed.
Unity 3D doesn't function because of running a vesa driver
Problems with mouse pointer.  The problem is minor in a gnome desktop and bad enough in unity 2D as to make it essentially unusable.

So my outstanding questions are:

1. Does a driver exist for this hardware

geoff@geoff-HP-8200:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

that will make 3D effects available?  i.e. is there such thing as a non vesa driver for this chipset?  What would such a thing be called so I can at least mount a search for it?

2. If not, can I at least make the mouse pointer behave?

---

### Post by gleedadswell on 2012-02-07
Does anyone know whether this is what I'm looking for?

[http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html")

(clearly not item 1 in that list.  Maybe item 2?)

I realize that if I go this route I'll need to build it from source, but I'm up for that.  But is there a precompiled package I can use?  For example is

i965-va-driver

along the lines of what I need?

-----------------------later edit-----------------------------

It doesn't look to me like i965-va-driver will do it.  I think I've got i915.  I think this because

dmesg | grep i915
[   11.199637] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0

but dmesg | grep i965 returns nothing.  Is there another way to be sure, and what difference would this make for what kinds of drivers I should look for?

---

### Post by gleedadswell on 2012-02-07
...and still more questions.

I see that right now I've got 

xserver-xorg-video-radeon

That doesn't seem right.  This link

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch")

which I followed after a previous post said I should install

xserver-xorg-video-ati

and I think the radeon package came along with it.  But now that I know a bit more that seems wrong.  Was that advice specific to another architecture?  Should I purge both of these packages?  My /var/log/Xorg.0.log gives no indication that these are being used so perhaps it is harmless?

---

### Post by MoreOrLess on 2012-02-07
I think what you're looking for is: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric)

As for ati/radeon, those packages are not relevant to your system.

---

### Post by gleedadswell on 2012-02-10
OK, removed the radeon packages.

The xorg-edgers stuff looks likely to cause regressions.  If this was my computer at home I'd be all over it.  But this computer is on my desk at work.  I don't really want to spend an hour at work undoing something that breaks X.

Here's my ignorant theory.  Someone tell me if it's completely wrong, which it probably is.

It looks like I've got all the packages installed that should make mesa available.  I've got libgl1-mesa-glx, libglapi-mesa, libglu1-mesa and libgl1-mesa-dri.  But the computer is using vesa not mesa.  Is that just because of the nomodeset option in grub.cfg which heads off all attempts to use "fancy" graphics?  Unfortunately, without the nomodeset it boots to blank screen.  But I'm guessing no matter what other drivers I stick on here they won't be loaded up as long as the nomodeset option is there.

At least it's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/887756](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/887756)

The last person posting there also says they can only run with vesa.  It is still showing up as "unassigned" on launchpad.

So, is it time for me to throw in the towel and try xubuntu?  Maybe when 12.04 comes out I'll retry unity on this machine.

---

### Post by aDragonfly on 2012-02-13
The problem is a bug in the kernel modules for Sandybridge graphics.  I installed the 3.2.0 Kernel and now the proprietary graphics work.  Apparently the bug in the Sandybridge Kernel modules has been fixed as of 3.2.  I can boot without the nomodeset, etc., and the graphics show as "Intel Sandybridge Desktop".  Unfortunately, I still can't run Compiz, so I'm still stuck with Unity 2d.  If I try to run 3d I get to the desktop, but the panel, launcher, desktop icons, etc. never load, and there's very little functionality.  There is (apparently -- according to a number of forums) an incompatibility between Sandybridge and Compiz.  There's talk of workarounds involving installing xorg-edgers and removing some modules that Compiz currently blacklists (Compiz blacklists a number of Sandybridge modules), but I haven't tried that yet.  Still, for those having trouble with blinking pointers, installing the 3.2 kernel and removing the nomodeset and quiet splash settings will probably be an improvement.

---

### Post by aDragonfly on 2012-02-13
Oh, as far as the "unassigned" status goes, if some of you with blackscreen problems could go over to that bug page and add your information, we could then have the status upgraded to "confirmed" and we might see a little more attention to it...  Thanks!  Here's the link: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/887756](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/887756)

---

### Post by gleedadswell on 2012-02-21
Whoa!

That sounds like fun.  I've never recompiled my kernel before (in Linux circles does this mean I now have to hang my head in shame? ;) ) and I've certainly never worked with an upstream kernel.  So, a bit of advice would be appreciated.

I've looked at a few ways to do this.  I imagine the main difference is how much control you want over the whole thing.  If you're happy to have a kernel compiled by someone else and just install it that is quite different from if you want to compile it yourself for the purposes of debugging and helping with the development efforts, correct?  Here are several ways I've found:

_Easy_

[http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html]("http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html")

summary: add a ppa and just apt-get the new kernel

_Medium_

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

summary: "git" the kernel from git.kernel.org, edit the config files, build the image and header .deb files, install them, update grub, reboot

_Hard_

[http://blog.avirtualhome.com/2012/01/13/compile-linux-kernel-3-2-for-ubuntu-11-10/]("http://blog.avirtualhome.com/2012/01/13/compile-linux-kernel-3-2-for-ubuntu-11-10/")

summary: umm...  I don't understand what all these extra steps are for.

So, I'm inclined to go with the one I've called "medium" if only because then the code comes from a trusted source rather than just a random ppa.  Any advice?

---

### Post by gleedadswell on 2012-03-05
Hooray!!!!

Looking at the git.kernel.org option I noticed it was going to be linux 3.3.  I decided not to go any farther upstream than absolutely necessary.  So I kept looking for other options.  That brought me to here

[https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")

which directed me to the location of the mainline Ubuntu builds.  I grabbed the v3.2-rc4-oneiric/ build and installed it with dpkg -i.  Very straightforward.  Now I appear to have my graphics running properly including Compiz.  So I've got Ubuntu 3D.

Now, how do I mark this thread as solved?

Got it...  Thanks folks!  I learned a lot.

---

