---
title: "Intel's x.org 2.2.0 Driver"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by adityakavoor on 2007-11-16
Finally intels x.org 2.2.0 driver has been released

see [here]("http://www.phoronix.com/scan.php?page=news_item&px=NjE5OA")

Please help me in installing the new driver .. Hope is solves most of the driver issues

I have an Intel 965 platform .. x3000 integrated graphics

---

### Post by JDahl on 2007-11-16
I have also been waiting for this release,  but I will wait for it to enter Debian 
unstable,  then build the packages from the Debian source packages.

---

### Post by adityakavoor on 2007-11-16
> **JDahl said:**
> I have also been waiting for this release,  but I will wait for it to enter Debian 
unstable,  then build the packages from the Debian source packages.

So, U dont recommend doing it now ?

---

### Post by JDahl on 2007-11-16
Waiting for Debian packages will be much less hazzle - then you just build
the packages and install them using the package manager,  and configuration
can be done with the regular Ubuntu/Debian tools.

---

### Post by JDahl on 2007-11-18
The new release is in Debian unstable,  but with all the dependencies I gave up
trying to backport it.

If you want to try backport it yourself,  insert the following into /etc/apt/sources.list:
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) sid main

and run 
sudo apt-get update

Now you can download and compile packages with:
sudo apt-get source --compile xserver-xorg-video-intel

and install the .debs with sudo dpkg -i 

but you cannot install those package without downloading and installing other dependencies, and the list of broken dependencies just kept growing and growing 
for me until I gave up and focused on rescuing Xorg instead.

Normally it's not that difficult to backport a project, but Xorg is probably one of the biggest project to backport;  I  thought it would be possible to just backport the 
intel driver,  but apparently not...

---

### Post by misGnomer on 2007-11-18
I haven't really followed the development of Intel drivers, but as I need to upgrade my current system with the aging but well-supported ATI Radeon 9200 I'd be interested in knowing how well the latest Intel Linux/Xorg drivers support the built-in GMA 3xxx hardware in general? Is there a Wiki or a blog where the advances and the existing deficiencies of current drivers are listed in an understandable manner?

Also the long-delayed G35-based boards (w/ X3500 graphics) appear to be finally hitting the shelves (ASUS P5E-VM HDMI being the first) so it would be interesting to learn if that particular hardware is actually usable with the latest Intel drivers or with Gutsy.

The 2.2.0 release annoucement or trawling through the Xorg mailing list doesn't really give a clear idea about where the level of proper hardware support stands. Bugs get swatted and features added but stability, performace and sheer usability remain somewhat of a mystery to me.

The requirement of X server 1.4.x by these new drivers would also imply that Gutsy won't get these drivers, regardless of Xorg's new modular structure since an upgrade from v1.3 sounds like something Canonical would rather not do.

---

### Post by JDahl on 2007-11-18
In gutsy my integrated X3100 card works well in regular gnome.  But any attempts
at 3d crashes my laptop,  and with the latest Gutsy version of the intel driver,
the external video connector to projectors doesn't work.

Whether newer chipsets than x3100 works,  I don't know.

---

### Post by adityakavoor on 2007-11-18
hmm .. I stay with the older one

---

### Post by misGnomer on 2007-11-20
According to the developers it should be possible to build the new driver against the 1.3 X server, it's just that they haven't tested that combination.

Since X.org is now modular it would be nice if there were even only unofficial builds of the latest official driver releases, and perhaps even weekly builds from git. I mean, wasn't that the whole point behind going modular, i.e. not needing to wait until the next distro (like Ubuntu 8.04) release in order to get bug fixes and improved support for hardware?

Or am I just behind the curve here.

---

### Post by kuse on 2007-11-23
/cry ... so this means that my new motherboard's (p5e-vm hdmi) integrated x3500 (g35) graphics wont work in ubuntu (yet) ?

---

### Post by adityakavoor on 2007-11-27
G33 ... has a lot of problems
X3000 is better than X3100

---

### Post by brundles on 2007-12-11
> **kuse said:**
> /cry ... so this means that my new motherboard's (p5e-vm hdmi) integrated x3500 (g35) graphics wont work in ubuntu (yet) ?

Not good :( I've been looking at this board as the basis for an HD capable upgrade. I thought Intel had pretty good support on Linux?

---

### Post by hanasaki on 2007-12-26
OK... so what is the difference between the g35 and g33?  Can you explain the relationship of the x3000 and x3100 to the G##?  Then there is the g965.  is this a different competing intel chip?

---

### Post by Tommy.Hudec on 2008-01-04
Hi!
Icreated a xserver-xorg-video-intel version 2.2 package for gutsy:

[https://launchpad.net/~tommy-hudec/+archive](https://launchpad.net/~tommy-hudec/+archive)

You can also add a line to your sources.list:

deb [http://ppa.launchpad.net/tommy-hudec/ubuntu](http://ppa.launchpad.net/tommy-hudec/ubuntu) gutsy main

HTH,
Tommy

> **misGnomer said:**
> According to the developers it should be possible to build the new driver against the 1.3 X server, it's just that they haven't tested that combination.

Since X.org is now modular it would be nice if there were even only unofficial builds of the latest official driver releases, and perhaps even weekly builds from git. I mean, wasn't that the whole point behind going modular, i.e. not needing to wait until the next distro (like Ubuntu 8.04) release in order to get bug fixes and improved support for hardware?

Or am I just behind the curve here.

---

### Post by adityakavoor on 2008-01-04
> **Tommy.Hudec said:**
> Hi!
Icreated a xserver-xorg-video-intel version 2.2 package for gutsy:

[https://launchpad.net/~tommy-hudec/+archive](https://launchpad.net/~tommy-hudec/+archive)

You can also add a line to your sources.list:

deb [http://ppa.launchpad.net/tommy-hudec/ubuntu](http://ppa.launchpad.net/tommy-hudec/ubuntu) gutsy main

HTH,
Tommy

any repos for feisty ??? 
I dont like gutsy

---

### Post by isaacj87 on 2008-01-05
> **adityakavoor said:**
> any repos for feisty ??? 
I dont like gutsy

+1 I'm also looking for the latest intel driver...but I'm stuck using the one for Feisty...:(

---

### Post by sberan on 2008-01-05
> **Tommy.Hudec said:**
> Hi!
Icreated a xserver-xorg-video-intel version 2.2 package for gutsy:

[https://launchpad.net/~tommy-hudec/+archive](https://launchpad.net/~tommy-hudec/+archive)

You can also add a line to your sources.list:

deb [http://ppa.launchpad.net/tommy-hudec/ubuntu](http://ppa.launchpad.net/tommy-hudec/ubuntu) gutsy main

HTH,
Tommy

Well thanks for backporting this, although I'm getting an error starting up compiz now. I think I'm going to downgrade to the old version.

Someone else ran into the same thing on the compiz forums [here.]("http://forum.compiz-fusion.org/showthread.php?t=5976")

Here is the output from compiz &:

```
sam@sam-laptop:~$ Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
present. 
Checking for Xgl: not present. 
Starting emerald
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

---

### Post by Tommy.Hudec on 2008-01-06
> **isaacj87 said:**
> +1 I'm also looking for the latest intel driver...but I'm stuck using the one for Feisty...:(

Sorry, It needs Xorg at least version 1.3 AFAIK but in feisty it's 1.2.

---

### Post by Tommy.Hudec on 2008-01-06
> **Tommy.Hudec said:**
> Hi!
I created a xserver-xorg-video-intel version 2.2 package for gutsy:


After testing... my experience:
It crashed several times. I found, that it can have something to do with XV (Xvideo), because it crashed after this: playing a video on desktop 2, stopping it, switching to desktop 1 and then switching back to 2. Then it crashed. It also crashed after wakeup from suspend to RAM or disk (I don't remember now). Most crashes had to do something with playing video.

Jay_Bee also tried it and he states:
"games became very slow and compiz stopped working, so I reverted to the original gutsy driver".

Now I'm using again driver version 2.1.0, it seems more stable to me.

---

### Post by dixon on 2008-01-06
Thanks for backporting the driver.... Is direct rendering working for you with this driver? I get no direct rendering  :(

---

### Post by brundles on 2008-01-24
I don't think it's specific to the backport done by Tommy that's broken DRI - I've run in to the same problem having just built it on Gutsy.

I'm not too keen on the idea of shoe-horning X-Server 1.4 onto Gutsy but might get irritated enough with the tearing to try it!

---

### Post by Yellow Pasque on 2008-01-24
The 2.2.1 driver should be out by tomorrow (Friday 1/25/08), so anyone looking to build from source should probably hold out for that.
[http://www.phoronix.com/scan.php?page=news_item&px=NjI5NA](http://www.phoronix.com/scan.php?page=news_item&px=NjI5NA)

---

### Post by audi100quattro on 2008-01-30
I followed the directions on intel's website to get the current git code driver working: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html) I needed to install git, libtool, autotools, xorg-xserver-dev, and the mesa development package. The directions aren't too hard to follow if you set XORG_DIR=/usr and copy the 3D dri modules to /usr/lib/dri/ just make sure you do it in the right order: drm/libdrm and then the 2D and 3D driver. 

You don't really need to worry about compiling the kernel, and configuring X if like me you're just wanting to use the latest driver for the G35 graphics. I'm wondering when/if xserver 1.4 and/or the new driver will make it gutsy, regardless, the git driver will still work with 1.3. I'll just have to pull in the newest git code when the driver is released and type a couple of things to get it working.

---

### Post by brundles on 2008-01-30
> **audi100quattro said:**
> I followed the directions on intel's website to get the current git code driver working: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html) I needed to install git, libtool, autotools, xorg-xserver-dev, and the mesa development package. The directions aren't too hard to follow if you set XORG_DIR=/usr and copy the 3D dri modules to /usr/lib/dri/ just make sure you do it in the right order: drm/libdrm and then the 2D and 3D driver. 

You don't really need to worry about compiling the kernel, and configuring X if like me you're just wanting to use the latest driver for the G35 graphics. I'm wondering when/if xserver 1.4 and/or the new driver will make it gutsy, regardless, the git driver will still work with 1.3. I'll just have to pull in the newest git code when the driver is released and type a couple of things to get it working.
What are you using for video playback with the G35 chipset and those drivers? I built them recently and found it effectively killed GL and GL2 - both of them unable to use hardware rendering and falling back on the slow software handling instead. At th emoment I'm contemplating upgrading to the next Hardy Alpha/Beta release (judging by the times of the last 3 alphas I don't think it's far off) to get xserver 1.4 and try the latest drivers. The tearing on the playback on the G35 is really irritating.

---

### Post by audi100quattro on 2008-01-31
I jumped the gun a little, only 2D works if you upgrade using git and the instructions on the Intel page (and I didn't get any tearing using mythv or kmplayer, but it is a problem hopefully fixed by 2.2.1: [http://www.phoronix.com/scan.php?page=news_item&px=NjI5NA](http://www.phoronix.com/scan.php?page=news_item&px=NjI5NA)). I just haven't seen it yet.

To get 3D to work, I went back to using debian source packages as this says: [http://ubuntuforums.org/showpost.php?p=3793067&postcount=5](http://ubuntuforums.org/showpost.php?p=3793067&postcount=5) I managed to get through most of the dependencies to upgrade xserver from 1.3 to 1.4. Here's what I had to build: 

apt-get source --compile x11proto-render-dev libpixman-1-dev libdbus-1-dev libhal-dev mesa-swx11-source x11proto-print-dev xserver-xorg-dev xserver-xorg-video-intel xserver-xorg-input-keyboard xserver-xorg-input-mouse x11-common x11-xkb-utils xorg-dev libdrm2

dbus_1.1.2-1_i386.deb                    mesa-common-dev_7.0.2-4_all.deb
dbus-1-doc_1.1.2-1_all.deb               mesa-swx11-source_7.0.2-4_all.deb
dbus-x11_1.1.2-1_i386.deb                mesa-utils_7.0.2-4_i386.deb
hal_0.5.10-5_i386.deb                    x11-common_7.3+10_i386.deb
hal-doc_0.5.10-5_all.deb                 x11proto-print-dev_1.0.3.xsf1-1_all.deb
libdbus-1-3_1.1.2-1_i386.deb             x11proto-render-dev_0.9.3-2_all.deb
libdbus-1-dev_1.1.2-1_i386.deb           x11-xkb-utils_7.3+1_i386.deb
libgl1-mesa-dev_7.0.2-4_all.deb          xbase-clients_7.3+10_all.deb
libgl1-mesa-dri_7.0.2-4_i386.deb         xlibmesa-gl_7.3+10_all.deb
libgl1-mesa-dri-dbg_7.0.2-4_i386.deb     xlibmesa-gl-dev_7.3+10_all.deb
libgl1-mesa-glx_7.0.2-4_i386.deb         xlibmesa-glu_7.3+10_all.deb
libgl1-mesa-glx-dbg_7.0.2-4_i386.deb     xlibs-data_7.3+10_all.deb
libgl1-mesa-swx11_7.0.2-4_i386.deb       xlibs-static-dev_7.3+10_all.deb
libgl1-mesa-swx11-dbg_7.0.2-4_i386.deb   xnest_1.4.1~git20080118-1_i386.deb
libgl1-mesa-swx11-dev_7.0.2-4_i386.deb   xorg_7.3+10_i386.deb
libgl1-mesa-swx11-i686_7.0.2-4_i386.deb  xorg-dev_7.3+10_all.deb
libglu1-mesa_7.0.2-4_i386.deb            xserver-xephyr_1.4.1~git20080118-1_i386.deb
libglu1-mesa-dev_7.0.2-4_i386.deb        xserver-xorg_7.3+10_all.deb
libglu1-xorg_7.3+10_all.deb              xserver-xorg-core_1.4.1~git20080118-1_i386.deb
libglu1-xorg-dev_7.3+10_all.deb          xserver-xorg-core-dbg_1.4.1~git20080118-1_i386.deb
libglw1-mesa_7.0.2-4_i386.deb            xserver-xorg-dev_1.4.1~git20080118-1_i386.deb
libglw1-mesa-dev_7.0.2-4_i386.deb        xserver-xorg-input-all_7.3+10_i386.deb
libhal1_0.5.10-5_i386.deb                xserver-xorg-input-kbd_1.2.2-3_i386.deb
libhal-dev_0.5.10-5_i386.deb             xserver-xorg-input-mouse_1.2.3-2_i386.deb
libhal-storage1_0.5.10-5_i386.deb        xserver-xorg-video-all_7.3+10_i386.deb
libhal-storage-dev_0.5.10-5_i386.deb     xserver-xorg-video-i810_2.2.0-1_all.deb
libosmesa6_7.0.2-4_i386.deb              xserver-xorg-video-intel_2.2.0-1_i386.deb
libosmesa6-dev_7.0.2-4_i386.deb          xserver-xorg-video-intel-dbg_2.2.0-1_i386.deb
libpixman-1-0_0.9.6-1_i386.deb           xutils_7.3+10_all.deb
libpixman-1-0-dbg_0.9.6-1_i386.deb       xvfb_1.4.1~git20080118-1_i386.deb
libpixman-1-dev_0.9.6-1_i386.deb     libdrm2_2.3.0-4_i386.deb  
libdrm2-dbg_2.3.0-4_i386.deb  libdrm-dev_2.3.0-4_i386.deb

Every other dependency is in the gutsy repository. Only xbase-clients has it's dependencies altered to not ask for x11-utils because those are already installed as seperate packages in gutsy. That's pretty pretty much the only special thing I had to do other than install them in the right order to resolve the dependencies. Somebody else here likely knows how wrong that is, but it works. I installed the local packages using dpkg -i <packagename> and I'll upload them to an ftp or something if anybody wants them (40MB w/o the dbg packages). NOT for the faint of heart to try. My ASUS P5E-VM (Intel G35) glxinfo says: 
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965G 4.1.3002 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.0.3

Google Earth works, as does compiz with SKIP_CHECKS=yes according to this: [http://wiki.opencompositing.org/Hardware/Blacklist](http://wiki.opencompositing.org/Hardware/Blacklist) 

I probably should have used the ubuntu source repositories, but I used the debian sid ones instead. I don't have any dependency/configure errors so I should be able to upgrade to 2.2.1, mesa 7.0.3 and/or xserver 1.4 whenever they're pushed to the gutsy repositories. The way to get 3D working with xserver 1.3 might be by installing pixman and x11proto-render from their git repositories with the newest mesa, but I'm not sure, what Intel's page says isn't enough, you pretty much have to upgrade to xserver 1.4.

EDIT: Got the distro version wrong! I'm using gutsy, not feisty. Corrected it :)

---

### Post by adityakavoor on 2008-02-02
**Intel Releases Open 965/G35 IGP Programming Documentation**

see [here]("http://intellinuxgraphics.com/documentation.html")

---

### Post by adityakavoor on 2008-02-22
2.2.1 Driver released. Have a look .

[http://www.phoronix.com/scan.php?page=news_item&px=NjM0Ng](http://www.phoronix.com/scan.php?page=news_item&px=NjM0Ng)

---

### Post by kay_rus on 2008-02-24
did the XV playing issue with the compiz was fixed in 2.2.1 release?

---

### Post by brundles on 2008-02-24
> **kay_rus said:**
> did the XV playing issue with the compiz was fixed in 2.2.1 release?

I've not tried the current drivers, but the [bug for the tearing](http://bugs.freedesktop.org/show_bug.cgi?id=11311) is still open

---

