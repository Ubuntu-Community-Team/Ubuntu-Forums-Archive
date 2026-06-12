---
title: "For VIA/S3G Unichrome Pro IGP Driver laptop owners."
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by butlershouse on 2006-10-03
If you have , like me , purchased a modern fairly cheap laptop such as the Fujitsue Seimens LG7310 Amilo . Then it may have the Unichrome Video Adapter.  You may curent be running with a Wide Screen or widescreen laptop which is using a mode of 1024x768 instead of the preferred 1280x800. Now you may have already visited this link 

[S3 and VIA Unichrome Drivers]("http://www.ubuntuforums.org/showthread.php?t=264650")

And edited your xorg.cong file and experienced a wierd blank screen or just a plain old crashing. If that is the case then I would suggest you read and apply the following ( having tried the above ) since I can confirm that the OpenChrome driver has fixed the problem with screen layout on my laptop.

[OpenChrome]("https://help.ubuntu.com/community/OpenChrome") 

Thanks ...

[Nik Butler]("nikbutler.wordpress.com")

---

### Post by Speedy on 2006-11-13
Nik

I to have the Fujitsu Seimens LG7310 Amilo & the 2D performance was terrible, until I found you article.

Thank you
Steve

---

### Post by VividHazE on 2006-12-06
Thanks Butlers House! I have one of these cheapish laptops with the Graphics driver your talking about.  I haven't risked installing Ubuntu on the laptop (only got it yesterday) as I'm compiling information on compatibility, such as your thread here.

thanks a bunch I'll let you know if it works for me too.

---

### Post by VividHazE on 2006-12-06
Hey guys its me again, I got to the point where it tells you to run autogen.sh command with the prefix after it, and it runs fine for a while but then this comes up at the end.
> 
checking for XORG... configure: error: Package requirements (xorg-server xproto xvmc fontsproto libdrm ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xvmc' found
No package 'fontsproto' found
No package 'libdrm' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I tried checking on the repo's for xorg-server but it wasn't there, any ideas on how to help me? I'm very new to this stuff.

Thanks

EDIT: Phew, that was difficult, I had to install a lot more packages like libdrm and xproto etc to get the compiling and make install to work, but I got it working eventually and this is still a good guide.

---

### Post by ryan76 on 2006-12-23
I'm getting the same error and the packages aren't in the repository. Does anyone know where they are?

Thanks

---

### Post by countryparson on 2007-03-09
Hi vividhaze: I'm having the same trouble, could you tell exactly what you did.  I'm really new to this and can't figure out how to get my resolution to 1280x768.
I've tried to look for the packages it said were not found, it installed all except xorg.server which it couldn't find.
I tried working through the steps again and got the same error message.
Thanks,

---

### Post by Bonner on 2007-03-13
I also have a FSC Amilo K7610(AMD 3300+, 512MB, 80GB), Via/S3G Unichrome Pro IGP Graphics Adapter and have been trying for 2 days to run the 6.10 LiveCd, but only get the Blank screen after selecting Run/Install from the CD Boot menu.

I have tried all the various changes proposed here in the forum to no avail. I have run this CD successfully on my Desktop PC.

It sounds as though this is more an issue with the LiveCD than whether 6.10 will run on my Laptop. 

My question is then should I just create a partition (I currently have XP Home) and install the "alternate install" CD  ?
My goal is to go away completely from Windows. If the install works are there tools I can use to then reclaim the Windows disk partition?

---

### Post by Bonner on 2007-03-14
Finally, after 3+ days, SUCCESS!!.

After so many different combinations of configuration options, I simply changed the
driver from "via" to "vesa" in xorg.conf and I got my screen.

I am a little confused though. Through all the reading I have done here on the forum, I thought 6.10 had functioning support for VIA. 

For direct VIA support, do I need to install the openChrome driver?

By the way, this is my first venture into the world of Linux, and I must say it is fascinating.
I can say goodbye to windows.

Bye from Bonn, Germany.

---

### Post by newsman on 2008-01-22
I got s3g unichrome pro igp in my uni lab ...and i just installed kubuntu (the kde4 live cd version on to the hard drive)... I just followed the manual install instructions for 2d ....... so far no crashes.... no i am going to lull myself into a false sense of security by installing gnome desktop before going on with 3d acceleration bit.....p.s. is there any way to check if it is already enabled..... from my perspective, kde4 is still pretty slow... (but marginally quicker)

---

### Post by newsman on 2008-01-22
Ok for the 3d part at the end i get error on the glxinfo | grep render command


direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

so where to go from here???

---

### Post by newsman on 2008-01-23
i installed 7.10 ubuntu... although i loved the kde4 but it was just not snappy, (i.e. it was slow). but now if i do:

glxinfo | grep render 

I get:

direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710 x86/MMX+/3DNow!+/SSE2

Without having done anything...... wow.

---

### Post by effenberg0x0 on 2008-01-23
After many months trying everything that is possible with VIA Official Driver and the drivers released by Openchrome and Unichrome projects,  I have started a petition asking VIA to release decent Linux Drivers, as other manufacturers do or help the community by opening specifications, which would allow developers to work on opensource drivers. 

If you would like to help, please visit [http://ubuntuforums.org/showthread.php?t=676143](http://ubuntuforums.org/showthread.php?t=676143) or go directly to [http://www.petitiononline.com/vialinux/](http://www.petitiononline.com/vialinux/) .

Thanks,
Effenberg

---

### Post by newsman on 2008-01-24
after using it for a while. i now realise, it still annoying and slow... hahaha.

---

### Post by davidgutu on 2008-05-02
does 3d work? Whenever I install any drivers, my screen is black on reboot and I have t reinstal again

---

### Post by starcannon on 2008-05-05
I'm using the latest drivers from:
 [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)


The Good:
So far I have Compiz working, 896fps in glxgears.

The Bad:
Screen is flickering, and has a purplish hue to it, this is on an Everex Cloudbook, I will try an external monitor tomorrow to see if its something specific to the Cloudbook WVGA LCD or the driver.

Any other Cloudbookers out there messing with the latest drivers?
Got a working xorg.conf for them?

---

### Post by sofamensch on 2008-05-16
Openchrome is not working well. I cant watch any videos for any reason. The offered VIA driver from the Reps only gives me a black screen, maybe i will be able to fix that with some LCD setting. But using Vesa is the only way for now.

I am also on a Amilo K7610. I doubt that Compiz will ever run on that thing since it doesnt support some texture features. But Mpeg2 Mpeg4 Acceleration would be neat though...

---

### Post by uhappo on 2008-05-16
Well, on my laptop, I chose openchrome for driver, and changed the screen for LCD-screen 1024-768 (just tried it for the heck of it), restarted X-server and voilla!!!

Try it

---

### Post by sofamensch on 2008-07-14
Yeah but without MPEG Acceleration and everything

---

