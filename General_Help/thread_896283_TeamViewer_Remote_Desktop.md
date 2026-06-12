---
title: "TeamViewer Remote Desktop?"
date: 2008-08-21
forum: General Help
---

### Post by Sirugel on 2008-08-21
Teamviewer is a Windows and Mac application that allows you to view another computers screen from your computer and control it from your computer - like many remote assistance programs.

I've tried installing it with Wine and it all worked well, but it wouldnt open.. I would click the .exe and click the .exe link on the Wine menu.. Nothing.

Is there any software like this that can connect a Linux PC to a Windows PC screen? with graphical interface, control, and all of that stuffs?:):)

---

### Post by veloce on 2008-08-29
I use gnome-rdp to connect to Windows PCs using the Remote Desktop Protocol.  Works very well.

---

### Post by jkyahoo101 on 2008-09-03
I use Real VNC. I can control an Ubuntu install from Windows, a Windows install from Ubuntu, Ubuntu to Ubuntu and Windows to Windows. It works very well and all you need is the IP adress of the computer once all of the settings are set up properly. There are several guides on the internet.

---

### Post by veloce on 2008-09-05
> **jkyahoo101 said:**
> I use Real VNC. I can control an Ubuntu install from Windows, a Windows install from Ubuntu, Ubuntu to Ubuntu and Windows to Windows. It works very well and all you need is the IP adress of the computer once all of the settings are set up properly. There are several guides on the internet.

VNC protocol has the advantage that it leaves the session on the remote machine in place.  RDP is a remote login, so it logs off the session running on the remote machine.

On the other hand, I find I get better performance from windows machines with rdp.

---

### Post by alenguav on 2009-07-17
Thinking the same like you I posted an idea in  Ubuntu Brainstorm site here
[http://brainstorm.ubuntu.com/idea/20265/](http://brainstorm.ubuntu.com/idea/20265/)
if you like it vote for it please :)
 
BTW, someone listed a solution based on Reverse-VNC here
[http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

---

### Post by knxville on 2010-02-15
Well, I got it to work with wine, but it seemed kinda laggish and lots of graphical errors, so I just run it through Virtual Machines, its great, though a little bit slower than usual.

---

### Post by pbateman on 2010-03-13
I see they have a web based version. Would I be able to say, install the windows version on a windows pc and then control it remotely from my Ubuntu PC via the web browser?

---

### Post by pehden on 2010-03-25
thanks for pointing that out for me, i had no idea there was a web based one, so now i dont have to fight the exe file in wine anymore, cause the new version of it never sizes correctly on load, i have to constantly keep resizing the window

---

### Post by blackpro on 2010-03-27
Just an FYI I am sure it was posted or should have been posted but if you have a Teamviewer account you can access it from the web and control windows & macs with all features of clients (file transfer chat etcetra) all thru your browser. 

It is a fair and reasonable solution for TV to offer those who run Ubunutu and non supported OS's

Hope this helps :-)

T

---

### Post by Alex_Koekie on 2010-04-04
Don't know if somebody has the same problem, but on my pc (Ubuntu 9.10, Wine 1.1.41) installation of Teamviewer worked but it wouldn't start.

This workaround fixed it (partly) for me.

1. Deinstall Teamviewer.
2. Run the setup again but choose the start teamviewer without installation option.
3. It works! (on my pc)

Hope this will help people.
Greetings,
Alex_Koekie

---

### Post by 2hot6ft2 on 2010-04-15
Teamviewer is available for linux now.
[http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)

---

### Post by maddg3241 on 2010-04-15
can't you use remote desktop viewer somehow but if not remote desktop protocol will work good my friend uses that and it works

---

### Post by maddg3241 on 2010-04-15
OMG i just saw as i posted my thing the post above me says that there is teamviewer for Linux i have waited for this day because of work i can get on Facebook through the blocks lol thank you

---

### Post by maddg3241 on 2010-04-15
forgot the link [http://www.teamviewer.com/download/index.aspx?os=linux]("http://www.teamviewer.com/download/index.aspx?os=linux")

---

### Post by pbateman on 2010-04-17
Thanks for the link and the news!!..downloading now....

---

### Post by pakki on 2010-04-19
great great great news teamvierer as .deb package:P

---

### Post by krige on 2010-04-19
> **2hot6ft2 said:**
> Teamviewer is available for linux now.
[http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)

It still looks like a Windows application though (text and buttons). I wonder why... does it require to have Wine preinstalled?

---

### Post by pbateman on 2010-04-19
I dont think you need Wine for it. I downloaded and installed it and works great. I uninstalled the Wine version I had on, now just running the native .deb one.

---

### Post by Sepiraph on 2010-04-19
Yes it works for Linux w/o wine!

Now does anyone know how to make it autostart upon bootup?  I guess I have to edit /etc/init.d/ and put a new line in /etc/rc3.d but it'd be nice if it comes as a default feature.

---

### Post by krige on 2010-04-19
> **Sepiraph said:**
> Yes it works for Linux w/o wine!

Now does anyone know how to make it autostart upon bootup?  I guess I have to edit /etc/init.d/ and put a new line in /etc/rc3.d but it'd be nice if it comes as a default feature.

Have you tried to add it to
System / Preferences / Startup Applications?

---

### Post by rick_woodham on 2010-04-19
Just curious to see if anyone has any experience with this....but I've just installed the Teamviewer for Linux package for Ubuntu 9.10.  It seems to be working great, native.  Unlike Windows, I am having challenges understanding how to leave Teamviewer running when I close the "window."

---

### Post by Sepiraph on 2010-04-20
> **krige said:**
> Have you tried to add it to
System / Preferences / Startup Applications?

Thanks ... but when I tested it off LAN its speed is not very good so I think I'll look for something like VNC or nomachine.

---

### Post by howefield on 2010-04-20
> **rick_woodham said:**
> I've just installed the Teamviewer for Linux package for Ubuntu 9.10.  It seems to be working great, native.

It isn't native, but wrapped up in a wine installation, although it does work better than the windows version in wine.

>  Unlike Windows, I am having challenges understanding how to leave Teamviewer running when I close the "window."

Hmm. can you explain this a bit more ?

---

### Post by rhonaldmoses on 2010-04-27
Hi Guys,

The wait has come to an end finally. TeamViewer has been released for GNU/Linux.

News: [http://linuxevangelist.blogspot.com/2010/04/teamviewer-for-gnulinux-released.html](http://linuxevangelist.blogspot.com/2010/04/teamviewer-for-gnulinux-released.html)

Download: [http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)

Though it's termed as Beta, that's not going to stop anyone from using it, isn't it?

---

### Post by krige on 2010-04-27
> **rhonaldmoses said:**
> The wait has come to an end finally. TeamViewer has been released for GNU/Linux.

We already knew that. Have you read the previous posts?

---

### Post by howefield on 2010-04-27
> **krige said:**
> Have you read the previous posts?

Why let that stop him plugging his website ?


:lolflag::lolflag:

---

### Post by lumpie on 2010-05-16
> **rick_woodham said:**
>   Unlike Windows, I am having challenges understanding how to leave Teamviewer running when I close the "window."

Does anyone have a solution to this and having TV available after a reboot?

If adding it to System / Preferences / Startup Applications *is* the answer, since I am a Linux noob, I dont know how to do that.

Thank you. Thank you very much.

---

### Post by hornetster on 2010-05-20
Don't think that would work unless you are only going to use it when logged in... If you want to log in to it from another PC, you would need it to run as a service. I'm not quite up to speed on that... :(
   John.

---

### Post by thierrybo on 2010-06-13
Just to share a bug I had hard time to find:
- don't use ```
/apps/metacity/general/reduced_resources = true
``` in gconf editor. It was my setup since several years, it displays only windows borders when you move them. It freeze Teamviewer as soon as you try to move a window.

---

### Post by pehden on 2010-07-06
> **lumpie said:**
> Does anyone have a solution to this and having TV available after a reboot?

If adding it to System / Preferences / Startup Applications *is* the answer, since I am a Linux noob, I dont know how to do that.

Thank you. Thank you very much.


The only way to do this is to create a start up file

Click System>Preferences>StartUp Applications 

Then Click Add, then for name name it what you want

for Command type virtualbox

then save.reboot.

---

### Post by Johann-1.0 on 2010-08-21
[[IMG]http://brainstorm.ubuntu.com/idea/20116/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20116/)

Vote for idea number 3

---

### Post by 7h3d4rk0n3 on 2010-09-23
Just an FYI, there is a Linux version for RPM and DEB based systems. Otherwise, you can compile it from source. 
[http://www.teamviewer.com/download/index.aspx?os=linux](http://www.teamviewer.com/download/index.aspx?os=linux)

---

### Post by Johann-1.0 on 2010-09-26
Hi...there's a package for Ubuntu. You don't need to use wine.

---

### Post by dzsobacsi on 2010-09-28
I have tried to remote control my ubuntu from a windows machine with a browser.
It seems to work fine, I can see the desktop, I can move mouse pointer, etc.
However I cannot use the terminal since I cannot send enter. Actually enter key doesn't work at all (I've tried it with gedit as well)

Any idea?

---

### Post by Johann-1.0 on 2010-10-01
> **dzsobacsi said:**
> I have tried to remote control my ubuntu from a windows machine with a browser.
It seems to work fine, I can see the desktop, I can move mouse pointer, etc.
However I cannot use the terminal since I cannot send enter. Actually enter key doesn't work at all (I've tried it with gedit as well)

Any idea?
I don't know man...I have used Enter key and everything worked fine, even the terminal. You said you have used gedit already...I suppose that you made a script. I venture to suggest that you make a script, but instead that running it through terminal, you treat it like a normal file; double click on it in your preferred graphic file manager. Ubuntu will ask you to run it in terminal or to see its content. You choose run in terminal and it's done.
I can't picture another way without using Enter key.

---

### Post by dzsobacsi on 2010-10-05
I've tried it with the TViewer client (there is a portable version out there) and now it works pretty well.
Still no success if I try to remote control from browser (FF 3.6) but I'm glad with the client.

---

### Post by Wtower on 2010-10-05
Apologies if I miss something here, but doesn't Teamviewer come with a Linux version? 

[http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)
[http://www.teamviewer.com/download/teamviewer_linux_x64.deb](http://www.teamviewer.com/download/teamviewer_linux_x64.deb)
[http://www.teamviewer.com/download/teamviewer_linux.tar.gz](http://www.teamviewer.com/download/teamviewer_linux.tar.gz)

Regards

PS I did miss something, I did :)

---

### Post by Johann-1.0 on 2010-10-05
> **Wtower said:**
> Apologies if I miss something here, but doesn't Teamviewer come with a Linux version? 

[http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)
[http://www.teamviewer.com/download/teamviewer_linux_x64.deb](http://www.teamviewer.com/download/teamviewer_linux_x64.deb)
[http://www.teamviewer.com/download/teamviewer_linux.tar.gz](http://www.teamviewer.com/download/teamviewer_linux.tar.gz)

Regards

PS I did miss something, I did :)
 
Yes, it comes with a Linux Version...but we want an analogue software Linux-native and GPL, this is, free software.

---

### Post by idokus on 2010-10-29
You can download a linux/deb version at the teamviewer website:
[http://www.teamviewer.com/download/index.aspx](http://www.teamviewer.com/download/index.aspx)

It worked for me(tm) to connect from ubuntu 10.04 to windows XP SP3

---

### Post by dlevens on 2011-05-08
I have TeamViewer 6.0.9224 running on Ubuntu 11.04 32bit and have it auto starting on bootup (after login), but it refuses to run if there is no monitor connected to the system.

My goal was to build a remote crahplan server for offsite backups and wanted to run it headless, with only power and network cable. I had everything built and working until I removed the monitor and keyboard and mouse. Ubuntu boots up, auto logs in and crashplan runs great but I cannot get team viewer to run. 

I suspect this is the hardware detection finding no monitor and trying a safe mode type resolution or something?

Because I am installing this remotely I want at least two working remote options. So I have openssh running but would like to get teamviewer working. 

I played around with VNC by turning on allow access to the PC in the remote desktops app, but if I set a password I cannot login because the ubuntu OS prompts for a password saying "enter password to unlock your login keyring"

I am looking for a remote GUI solution that works at the login prompt and shows the actual desktop.

Does anyone know how to turn off and force ubuntu to loading certain display resolution? OR anyone have an idea why teamviewer would only run when a monitor is attached?

Dennis

---

### Post by pehden on 2011-05-09
Why not just install X11-apps and run gnome remote via ssh, connect with 
example
ssh -X yourDYNip

---

### Post by dlevens on 2011-05-09
I had not heard of this option. I checked ubuntu 11.04 and it has x11-apps already installed. I also already have openssh running, but what is needed on the the client side I am connecting from? I am running windows 7 and using putty to SSH into the remote ubuntu server. Seems like I would be missing a client app to handle the gui session? Would this be the actual console desktop gui or another session like RDP?

I need a solution like teamviewer that views and controls the actual console desktop.

I already know teamviewer works great with a monitor attached, would prefer to find out why it wont without a monitor and fix it. The file transfer options, speed, ease of use make it a perfect remote solution, but the need for a monitor is where I am stuck.

Dennis

---

### Post by dlevens on 2011-05-10
I believe this is my issue. 

"Output VGA1 disconnected" 

And this is likely causing teamviewer not to run

```

dennis@rbox2:/etc/X11$ cat /var/log/Xorg.0.log
[    14.359] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.359] X Protocol Version 11, Revision 0
[    14.359] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    14.359] Current Operating System: Linux rbox2 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    14.359] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=02f648ea-7b2b-498f-a498-5f10f4ba2175 ro quiet splash vt.handoff=7
[    14.359] Build Date: 19 April 2011  03:33:17PM
[    14.359] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    14.359] Current version of pixman: 0.20.2
[    14.359]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.359] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.360] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May  9 21:01:58 2011
[    14.410] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.417] (==) No Layout section.  Using the first Screen section.
[    14.417] (==) No screen section available. Using defaults.
[    14.417] (**) |-->Screen "Default Screen Section" (0)
[    14.417] (**) |   |-->Monitor "<default monitor>"
[    14.417] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.417] (==) Automatically adding devices
[    14.417] (==) Automatically enabling devices
[    14.417] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.417]     Entry deleted from font path.
[    14.417] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.417]     Entry deleted from font path.
[    14.417] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.417]     Entry deleted from font path.
[    14.417] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.417]     Entry deleted from font path.
[    14.418] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.418]     Entry deleted from font path.
[    14.418] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.418] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.418] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.418] (II) Loader magic: 0x81ffde0
[    14.418] (II) Module ABI versions:
[    14.418]     X.Org ANSI C Emulation: 0.4
[    14.418]     X.Org Video Driver: 10.0
[    14.418]     X.Org XInput driver : 12.3
[    14.418]     X.Org Server Extension : 5.0
[    14.419] (--) PCI:*(0:0:2:0) 8086:2772:1014:02f6 rev 2, Mem @ 0xd0100000/524288, 0xc0000000/268435456, 0xd0180000/262144, I/O @ 0x000030c0/8
[    14.419] (--) PCI: (0:0:2:1) 8086:2776:1014:02f6 rev 2, Mem @ 0xd0200000/524288
[    14.419] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.419] (II) LoadModule: "extmod"
[    14.449] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.449] (II) Module extmod: vendor="X.Org Foundation"
[    14.449]     compiled for 1.10.1, module version = 1.0.0
[    14.449]     Module class: X.Org Server Extension
[    14.449]     ABI class: X.Org Server Extension, version 5.0
[    14.449] (II) Loading extension MIT-SCREEN-SAVER
[    14.449] (II) Loading extension XFree86-VidModeExtension
[    14.449] (II) Loading extension XFree86-DGA
[    14.449] (II) Loading extension DPMS
[    14.450] (II) Loading extension XVideo
[    14.450] (II) Loading extension XVideo-MotionCompensation
[    14.450] (II) Loading extension X-Resource
[    14.450] (II) LoadModule: "dbe"
[    14.450] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.450] (II) Module dbe: vendor="X.Org Foundation"
[    14.450]     compiled for 1.10.1, module version = 1.0.0
[    14.450]     Module class: X.Org Server Extension
[    14.450]     ABI class: X.Org Server Extension, version 5.0
[    14.450] (II) Loading extension DOUBLE-BUFFER
[    14.450] (II) LoadModule: "glx"
[    14.451] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.451] (II) Module glx: vendor="X.Org Foundation"
[    14.451]     compiled for 1.10.1, module version = 1.0.0
[    14.451]     ABI class: X.Org Server Extension, version 5.0
[    14.451] (==) AIGLX enabled
[    14.451] (II) Loading extension GLX
[    14.451] (II) LoadModule: "record"
[    14.452] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.452] (II) Module record: vendor="X.Org Foundation"
[    14.452]     compiled for 1.10.1, module version = 1.13.0
[    14.452]     Module class: X.Org Server Extension
[    14.452]     ABI class: X.Org Server Extension, version 5.0
[    14.452] (II) Loading extension RECORD
[    14.452] (II) LoadModule: "dri"
[    14.453] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.453] (II) Module dri: vendor="X.Org Foundation"
[    14.453]     compiled for 1.10.1, module version = 1.0.0
[    14.453]     ABI class: X.Org Server Extension, version 5.0
[    14.453] (II) Loading extension XFree86-DRI
[    14.453] (II) LoadModule: "dri2"
[    14.454] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.454] (II) Module dri2: vendor="X.Org Foundation"
[    14.454]     compiled for 1.10.1, module version = 1.2.0
[    14.454]     ABI class: X.Org Server Extension, version 5.0
[    14.454] (II) Loading extension DRI2
[    14.454] (==) Matched intel as autoconfigured driver 0
[    14.454] (==) Matched vesa as autoconfigured driver 1
[    14.454] (==) Matched fbdev as autoconfigured driver 2
[    14.454] (==) Assigned the driver to the xf86ConfigLayout
[    14.454] (II) LoadModule: "intel"
[    14.454] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.455] (II) Module intel: vendor="X.Org Foundation"
[    14.455]     compiled for 1.10.1, module version = 2.14.0
[    14.455]     Module class: X.Org Video Driver
[    14.455]     ABI class: X.Org Video Driver, version 10.0
[    14.455] (II) LoadModule: "vesa"
[    14.455] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.455] (II) Module vesa: vendor="X.Org Foundation"
[    14.455]     compiled for 1.10.0, module version = 2.3.0
[    14.455]     Module class: X.Org Video Driver
[    14.455]     ABI class: X.Org Video Driver, version 10.0
[    14.455] (II) LoadModule: "fbdev"
[    14.456] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.456] (II) Module fbdev: vendor="X.Org Foundation"
[    14.456]     compiled for 1.10.0, module version = 0.4.2
[    14.456]     ABI class: X.Org Video Driver, version 10.0
[    14.456] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    14.458] (II) VESA: driver for VESA chipsets: vesa
[    14.458] (II) FBDEV: driver for framebuffer: fbdev
[    14.458] (++) using VT number 7

[    14.461] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.461] (WW) Falling back to old probe method for vesa
[    14.461] (WW) Falling back to old probe method for fbdev
[    14.461] (II) Loading sub module "fbdevhw"
[    14.461] (II) LoadModule: "fbdevhw"
[    14.461] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.462] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.462]     compiled for 1.10.1, module version = 0.0.2
[    14.462]     ABI class: X.Org Video Driver, version 10.0
[    14.462] drmOpenDevice: node name is /dev/dri/card0
[    14.462] drmOpenDevice: open result is 9, (OK)
[    14.462] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    14.462] drmOpenDevice: node name is /dev/dri/card0
[    14.462] drmOpenDevice: open result is 9, (OK)
[    14.462] drmOpenByBusid: drmOpenMinor returns 9
[    14.462] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    14.462] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.462] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    14.462] (==) intel(0): RGB weight 888
[    14.462] (==) intel(0): Default visual is TrueColor
[    14.462] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
[    14.462] (--) intel(0): Chipset: "945G"
[    14.462] (**) intel(0): Relaxed fencing disabled
[    14.462] (**) intel(0): Tiling enabled
[    14.462] (**) intel(0): SwapBuffers wait enabled
[    14.462] (==) intel(0): video overlay key set to 0x101fe
[    14.484] (II) intel(0): Output VGA1 has no monitor section
[    14.504] (II) intel(0): EDID for output VGA1
[    14.504] (II) intel(0): Output VGA1 disconnected
[    14.504] (WW) intel(0): No outputs definitely connected, trying again...
[    14.504] (II) intel(0): Output VGA1 disconnected
[    14.504] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    14.504] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.504] (II) intel(0): Kernel page flipping support detected, enabling
[    14.504] (==) intel(0): DPI set to (96, 96)
[    14.504] (II) Loading sub module "fb"
[    14.504] (II) LoadModule: "fb"
[    14.504] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.505] (II) Module fb: vendor="X.Org Foundation"
[    14.505]     compiled for 1.10.1, module version = 1.0.0
[    14.505]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.505] (II) UnloadModule: "vesa"
[    14.505] (II) Unloading vesa
[    14.505] (II) UnloadModule: "fbdev"
[    14.505] (II) Unloading fbdev
[    14.505] (II) UnloadModule: "fbdevhw"
[    14.505] (II) Unloading fbdevhw
[    14.505] (==) Depth 24 pixmap format is 32 bpp
[    14.505] (==) intel(0): VideoRam: 262144 KB
[    14.505] (II) intel(0): [DRI2] Setup complete
[    14.505] (II) intel(0): [DRI2]   DRI driver: i915
[    14.505] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    14.505] (II) UXA(0): Driver registered support for the following operations:
[    14.505] (II)         solid
[    14.506] (II)         copy
[    14.506] (II)         composite (RENDER acceleration)
[    14.506] (II)         put_image
[    14.506] (II)         get_image
[    14.506] (==) intel(0): Backing store disabled
[    14.506] (==) intel(0): Silken mouse enabled
[    14.506] (II) intel(0): Initializing HW Cursor
[    14.506] (EE) intel(0): Couldn't create pixmap for fbcon
[    14.506] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.506] (==) intel(0): DPMS enabled
[    14.506] (==) intel(0): Intel XvMC decoder disabled
[    14.506] (II) intel(0): Set up textured video
[    14.506] (II) intel(0): Set up overlay video
[    14.506] (II) intel(0): direct rendering: DRI2 Enabled
[    14.506] (==) intel(0): hotplug detection: "enabled"
[    14.506] (--) RandR disabled
[    14.506] (II) Initializing built-in extension Generic Event Extension
[    14.507] (II) Initializing built-in extension SHAPE
[    14.507] (II) Initializing built-in extension MIT-SHM
[    14.507] (II) Initializing built-in extension XInputExtension
[    14.507] (II) Initializing built-in extension XTEST
[    14.507] (II) Initializing built-in extension BIG-REQUESTS
[    14.507] (II) Initializing built-in extension SYNC
[    14.507] (II) Initializing built-in extension XKEYBOARD
[    14.507] (II) Initializing built-in extension XC-MISC
[    14.507] (II) Initializing built-in extension SECURITY
[    14.507] (II) Initializing built-in extension XINERAMA
[    14.507] (II) Initializing built-in extension XFIXES
[    14.507] (II) Initializing built-in extension RENDER
[    14.507] (II) Initializing built-in extension RANDR
[    14.507] (II) Initializing built-in extension COMPOSITE
[    14.507] (II) Initializing built-in extension DAMAGE
[    14.507] (II) Initializing built-in extension GESTURE
[    14.527] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    14.533] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    14.533] (II) AIGLX: enabled GLX_INTEL_swap_event
[    14.533] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    14.533] (II) AIGLX: enabled GLX_SGI_make_current_read
[    14.533] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    14.533] (II) AIGLX: Loaded and initialized i915
[    14.533] (II) GLX: Initialized DRI2 GL provider for screen 0
[    14.550] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.565] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.565] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.565] (II) LoadModule: "evdev"
[    14.566] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.566] (II) Module evdev: vendor="X.Org Foundation"
[    14.566]     compiled for 1.10.0.902, module version = 2.6.0
[    14.566]     Module class: X.Org XInput Driver
[    14.566]     ABI class: X.Org XInput driver, version 12.3
[    14.566] (II) Using input driver 'evdev' for 'Power Button'
[    14.566] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.567] (**) Power Button: always reports core events
[    14.567] (**) Power Button: Device: "/dev/input/event1"
[    14.580] (--) Power Button: Found keys
[    14.580] (II) Power Button: Configuring as keyboard
[    14.580] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.580] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.580] (**) Option "xkb_rules" "evdev"
[    14.580] (**) Option "xkb_model" "pc105"
[    14.580] (**) Option "xkb_layout" "us"
[    14.582] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.582] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.582] (II) Using input driver 'evdev' for 'Power Button'
[    14.582] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.582] (**) Power Button: always reports core events
[    14.582] (**) Power Button: Device: "/dev/input/event0"
[    14.596] (--) Power Button: Found keys
[    14.596] (II) Power Button: Configuring as keyboard
[    14.596] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input0/event0"
[    14.596] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.596] (**) Option "xkb_rules" "evdev"
[    14.596] (**) Option "xkb_model" "pc105"
[    14.596] (**) Option "xkb_layout" "us"
[    14.604] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event2)
[    14.605] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    14.605] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    14.605] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.605] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    14.605] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
[    14.624] (--) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[    14.624] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    14.624] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[    14.624] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    14.624] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    14.624] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    14.624] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    14.624] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.624] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2/event2"
[    14.624] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[    14.625] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    14.625] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    14.625] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    14.625] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    14.625] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    14.626] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    14.626] (II) No input driver/identifier specified (ignoring)
[    14.627] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event3)
[    14.627] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.627] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[    14.627] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.627] (**) BTC USB Multimedia Keyboard: always reports core events
[    14.627] (**) BTC USB Multimedia Keyboard: Device: "/dev/input/event3"
[    14.644] (--) BTC USB Multimedia Keyboard: Found keys
[    14.644] (II) BTC USB Multimedia Keyboard: Configuring as keyboard
[    14.644] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3/event3"
[    14.644] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD)
[    14.644] (**) Option "xkb_rules" "evdev"
[    14.644] (**) Option "xkb_model" "pc105"
[    14.644] (**) Option "xkb_layout" "us"
[    14.646] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event4)
[    14.646] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.646] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[    14.646] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.646] (**) BTC USB Multimedia Keyboard: always reports core events
[    14.646] (**) BTC USB Multimedia Keyboard: Device: "/dev/input/event4"
[    14.668] (--) BTC USB Multimedia Keyboard: Found keys
[    14.668] (II) BTC USB Multimedia Keyboard: Configuring as keyboard
[    14.668] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input4/event4"
[    14.668] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD)
[    14.668] (**) Option "xkb_rules" "evdev"
[    14.668] (**) Option "xkb_model" "pc105"
[    14.668] (**) Option "xkb_layout" "us"


```

---

### Post by linuxyogi on 2011-05-10
<Deleted> #-o

---

### Post by mrjerryk on 2011-07-05
> **dzsobacsi said:**
> I have tried to remote control my ubuntu from a windows machine with a browser.
It seems to work fine, I can see the desktop, I can move mouse pointer, etc.
However I cannot use the terminal since I cannot send enter. Actually enter key doesn't work at all (I've tried it with gedit as well)

Any idea?

I am having the same issue.  Enter key and Backspace does not work.  This only happens when I use the Web login feature, which is what I need to use while I am at work.  If I use the client from my windows box to login everything is fine.

Did you ever find a fix for this?

---

### Post by mogging on 2011-07-19
I got a black screen when I connect to ubuntu using windows xp.

But connection established successful.

Any one could help?

Thanks.

---

