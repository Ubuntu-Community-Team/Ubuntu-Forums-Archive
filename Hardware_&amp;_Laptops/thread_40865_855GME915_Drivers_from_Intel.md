---
title: "855GME/915 Drivers from Intel"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by Vertical on 2005-06-10
There are official drivers from Intel for theese chipsets. Are there any ubuntu precompiled packages with this stuff?

Is it worth installing this drivers?

---

### Post by jerome bettis on 2005-06-11
the 2.6 kernel already has drivers for that chipset in there.  if you're reading this from your laptop with said chipset and running ubuntu, it's working fine right now.

not sure if you mean that intel released different ones but i'm not aware of any and there's nothing on their website. if this is what you're getting at can you post a link or something about it?

wait

[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=922&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=922&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng)

is that what you're talking about?  i just downloaded it and i think it's something for the 2.4 kernel.  hold on one second let me try this out ...

here is the readme file for that: [ftp://aiedownload.intel.com/df-support/8211/ENG/readme.txt](ftp://aiedownload.intel.com/df-support/8211/ENG/readme.txt)

---

### Post by jerome bettis on 2005-06-12
well it won't compile with ubuntu ... (just a bunch of errors)

i'm trying to just move the files that came in there into my kernel tree and it's compiling now .. we'll see what happens.

---

### Post by jerome bettis on 2005-06-12
nope that didn't work.  so i have no idea what these are all about.  i've asked on a few other forums so we'll see what's going on shortly hopefully.

it would be cool if they're actually better than what the kernel has.  and if we could get it working.

---

### Post by Vertical on 2005-06-12
They are better, cause they fully support the 855/915 chip (i810 doesn't). Also, they have support for TV-out and dualhead.

---

### Post by kiddyfurby on 2005-06-12
would be very nice if it pump up my glxgear fps.
I was not even able to find all dependencies to start building the module in my attempt.

---

### Post by X3N on 2005-06-12
I compiled these on my Samsung X05, then i read the documentation when X broke, and it says these drivers are for 2.4.x kernels 
..always read the label 

I'm a bit confused as to how the opengl works with these drivers, as apparently the drivers don't make use of hardware acceleration.. ? which is a shame because i can't run quake without it.

---

### Post by tflovik on 2005-06-12
The driver support the 2.6 kernel.
I had Suse 9.2 installed on my laptop(Inspiron 6000) before, and i got it working running a 2.6.9 kernel.

---

### Post by Vertical on 2005-06-12
Yes, Intel have some patches for Suse 9.2 Kernel, FC2 kernel and RHEL 3, MDK 10. Maybe some other (I don't remeber). But no support for future distributions (FC3-4, MDK 10.1, Suse 9.3)

Thats the main problem (I think), cause kernel must be patched before using Intel drivers. Where to get patches for new kernels?  :neutral:

---

### Post by jerome bettis on 2005-06-12
alright i've got some good news

i think the ones on the intel site are just ones that can be found at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) only they're a little old now.  i actually bothered to read the text of the intel install program and noticed dri.sourceforge.net at the top.  so they're not developed by intel.

i downloaded the latest version of the i915 driver from that link and install worked perfectly.   i don't play games or anything so i can't really say if the video is better but glxgears now gives ~850 fps as compared to 640 without the i915 module loaded.

that file also has a different version of the i810 for xorg but when i tried moving it into /usr/X11R6/lib/modules/drivers i just got a blank screen when xorg started and had to do ctrl alt del to get out.  maybe this is something worth pursuing further .. maybe not

---

### Post by Vertical on 2005-06-12
What chipset are on your laptop?
I wonder if this driver can make Tv-out possible :)

---

### Post by jerome bettis on 2005-06-12
855 gme

i've tried the tv out a few months ago and it flickered when i turned the laptop on but nothing else.  it worked in windows but the resolution was horrible on my giant tv.

i'll try that again with this module later tonight .. but i'm not optimistic

---

### Post by Vertical on 2005-06-12
I recieved this message today from one user, owner of 855gme/tvout laptop
didn't try it yet. Going to test it soon

[b]> Hi!
> I was browsing through the xorg archives and saw your message about
> tv-out.
> I'm using nvtv to change resolutions and to change from NTSC to PAL.
> I'm attaching the patch i made needed to have basic support for the 
> card. Apply with:
> cd nvtv ; patch -p1 < ../nvtv-i855.diff
> 
> To use nvtv you need:
> - go to the "Config" section of nvtv and choose the videocard with
> the 
> busID 00:02.0. It will detect the tv-encoder.
> - Choose "TV on" on the bottom
> - Choose "AutoApply"on the bottom.
> - Go to the "Mode" section and choose the TV System and then choose
> the 
> resolution you want.
> This resolution selection only changes the tv-encoder resolution, EX:
> if 
> you have configured the screen to be 1024x768 and select 800x600 it
> will 
> show part of the screen. If your screen is 800x600 and you choose 
> 1024x768 it will show the 800x600 screen and some garbage on the
> right 
> and below (not visible framebuffer memory).
> You also need to use:
> Option "MonitorLayout" "TV,LFP" instead of
> Option "MonitorLayout" "LFP,TV" in Xorg.conf
> 
> Hope this helps!

The patch he attached is attached to this message. I would highly
recommend you use nvtv with the attached patch instead of fiddling with
Intel's binary-only driver. Although that driver enables all
functionality of the Intel graphics hardware, including odd video modes
that have historically been trouble for the open-source i810 driver,
configuration was a hassle for me (you had to compile part of the config
file!) and it turned out the sacrafice in system stability was not worth
it.

HTH,
Andrew[/b]

---

### Post by MetalMusicAddict on 2005-06-12
Im kinda glad to see other people are having problems with the i810 driver. I had to go to the vesa driver to get a screen. Is there gonna be a fix for this? I have a Dell inspiron 2200 notebook. Im not sure if the chipset is the same as ones mentioned but I know that Ubuntu wants to use the i810 driver for my screen. It would be nice to get some acceleration.

---

### Post by gsalinas on 2005-06-24
[QUOTE=jerome bettis]alright i've got some good news

i think the ones on the intel site are just ones that can be found at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) only they're a little old now.  i actually bothered to read the text of the intel install program and noticed dri.sourceforge.net at the top.  so they're not developed by intel.

i downloaded the latest version of the i915 driver from that link and install worked perfectly.   i don't play games or anything so i can't really say if the video is better but glxgears now gives ~850 fps as compared to 640 without the i915 module loaded.

that file also has a different version of the i810 for xorg but when i tried moving it into /usr/X11R6/lib/modules/drivers i just got a blank screen when xorg started and had to do ctrl alt del to get out.  maybe this is something worth pursuing further .. maybe not[/QUOTE]
 
I've got the same problem with my Presario M2000, it comes along with a intel i915 video card.
Hoary's X detection uses by default i810 driver which turned the screen blank.

I downloaded the i915 from freedesktop and tried to run it by "sudo sh..." without luck... it says cannot compile/find the kernel modules..

How did you got the i915 driver working??? anyway... I'm sure I'm missing something but cant figure out what!!.

---

### Post by pillow on 2005-06-25
On that site, I followed the guide on [building from scratch.]("http://dri.freedesktop.org/wiki/Building") After much frustration, many google/ubuntu forums searches, and a few apt-gets, it's up and running! (Acer 1690WLCi laptop.. Intel 915PM chipset) Now just to get it running 1280x800 grrr. 

I couldn't get DRM to compile, it doesn't like the kernel source.. (I decompressed it and make errored out on a kernel setting it didn't like). Ubuntu comes with DRM already, so I hoped if I didn't compile DRM it wouldn't matter. 

glxgears from ~500 fps to ~1100 fps


Some problems I ran into.. 

Xorg compile died on "Couldn't find Xlibint.h" .. had to **sudo apt-get install xlibs-dev**
Xorg compile died on "Couldn't find freetype.h" .. had to **sudo apt-get install libfreetype-dev**
Mesa compile died on "Couldn't find expat.h' .. had to **sudo apt-get install libexpat1-dev**

I'm pretty new at this, did I even have to re-compile Xorg?

---

### Post by foxy123 on 2005-08-18
[QUOTE=jerome bettis]alright i've got some good news

i think the ones on the intel site are just ones that can be found at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) only they're a little old now.  i actually bothered to read the text of the intel install program and noticed dri.sourceforge.net at the top.  so they're not developed by intel.

i downloaded the latest version of the i915 driver from that link and install worked perfectly.   i don't play games or anything so i can't really say if the video is better but glxgears now gives ~850 fps as compared to 640 without the i915 module loaded.

that file also has a different version of the i810 for xorg but when i tried moving it into /usr/X11R6/lib/modules/drivers i just got a blank screen when xorg started and had to do ctrl alt del to get out.  maybe this is something worth pursuing further .. maybe not[/QUOTE]
how did you actually install it? I tried to run install.sh and got error:
```
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
```

---

### Post by sneax on 2005-08-19
I also have intel 855gme, isn't there a better driver available then the i810 one? I get exactly 500fps in the gears test and people say that's not realy good. CS1.6 is also running pretty slow under Cedega compared to WIndows (though with windows I get network error due to my wireless and can't play at all :/ ).

---

### Post by foxy123 on 2005-08-20
Well, I fixed it. For those who may have the same problem, you should follow the Savage card howto: [http://www.ubuntuforums.org/showthread.php?t=32043](http://www.ubuntuforums.org/showthread.php?t=32043), but replace savage driver with 915i driver (or any other [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) driver).

My glxgears jumped from 460 to 880 fps, which is excellent!

EDIT: actually I have now around 5700-5900 fps which is WOW!

---

### Post by sneax on 2005-08-20
On the page where you can download those snapshots it says you have to use i915 driver for 855gme graphics card. The i810 is just what it says, for i810. Now I think I installed the driver, but I don't know how to change from i810 to i915? When I change it in my xorg.conf it says module/driver not found!

This is what I had to do:
Install 686 kernel instead of 386
Delete kernel 386 through synaptec
Download the latest 'common' page from that snapshots directory
Download the latest driver from that snapshots directory
Unzip both in same directory (first common then specific driver, i915)
Then do make, which went OK.

And then what? How can I use that i915 driver?

Thank you for your help, these are very friendly forums for beginners too! You made me a linux fan  :)

---

### Post by foxy123 on 2005-08-21
[QUOTE=sneax]On the page where you can download those snapshots it says you have to use i915 driver for 855gme graphics card. The i810 is just what it says, for i810. Now I think I installed the driver, but I don't know how to change from i810 to i915? When I change it in my xorg.conf it says module/driver not found!

This is what I had to do:
Install 686 kernel instead of 386
Delete kernel 386 through synaptec
Download the latest 'common' page from that snapshots directory
Download the latest driver from that snapshots directory
Unzip both in same directory (first common then specific driver, i915)
Then do make, which went OK.

And then what? How can I use that i915 driver?

Thank you for your help, these are very friendly forums for beginners too! You made me a linux fan  :)[/QUOTE]

it's a good question. I tried to replace i810 with i915 and it failed to boot into gdm. Also I tried gl-117, which I usually use to test 3D acceleration, and good low fsp message. However, before i have installed a new i925 driver it was a bit slow but fine. I wonder if my xorg.conf is configured properly...

---

### Post by sneax on 2005-08-21
This is what i found out after last night's trial and error:
There are 2 files taking care of your video card. First we have the DRI part and we have the x driver, which you specify in your xorg.conf.

If you install from that snapshot url a few posts back, then even if you install the i915 driver, in xorg.conf you STILL have to use i810 - for a real i915 card too! The x driver is the same though the DRI driver is different for i810 and i915.

Since I installed this yesterday I didn't have extra fps in glxgears - about 760 is the max i get out, but cedega refused to work correctly (its very very slow). I tryed replacing my new i810_drv.o and i810_dri.so with the old ones but that didn' fix things either. That driver installs way more then just those files, since I don't know how to unisntall I just went ahead and reinstalled ubuntu (now with the idea in mind that i will stay as close to the 'official' repositries as possible ;) ) though half way through the installation it quit, after running md5 check it seems my cd has a scratch (after checking it, there is indeed a huge scratch, damn dog probalby!). I say no problemo, i boot into windows! I restart pc and grub refuses to load with an error!!! omg!

So now im on a different pc downloading ubuntu again but you know what? i don't have any cd-r's anymore! and its sunday, shops are closed! omg!!!!! im going to try writing those files on a dvd and hope its bootable ... what a weekend!

---

### Post by foxy123 on 2005-08-21
It is quite strange because if I run lsmod I've got:
```
i915                   21856  1
drm                    74808  2 i915
``` 
glxinfo:
```
 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
``` 

so it looks like dri is enabled, but I do not have 3D acceleration at all.

BTW, if you want to boot into Windows, try fix_mbr command to get rid of grub...

---

### Post by foxy123 on 2005-08-21
I installed a previous version of the driver i915-20050714-linux.i386 and my 3D acceleration is back. I guess something wrong with 20050718. 

I wonder now if it is possible to change 1024x768 resolution to a higher one.

---

### Post by sneax on 2005-08-21
I wrote a new CD-R (my last one!) and installed ubuntu over my whole hard drive. No more windows! You say those older drivers work better? I don't dare installing them because If I lose graphics completely (it works now but very slow) what can I do to uninstall?!

---

### Post by sneax on 2005-08-21
[QUOTE=sneax]I wrote a new CD-R (my last one!) and installed ubuntu over my whole hard drive. No more windows! You say those older drivers work better? I don't dare installing them because If I lose graphics completely (it works now but very slow) what can I do to uninstall?![/QUOTE]
 Everything's fixed now. What made Cedega so slow was my SOUND driver confilicted in the background! I did what I posted in my 'howto' in the beginners forum for my sound and it all worked! (sorry not gona search for the link, i went over my bandwidth limit and am now on smallband, like a 56k :/ ).

Phew, I'm realy happy now. I also got all my desired resolutions working under x ALL my problems are fixed and I can finaly start enjoying ubuntu to its fullest! In those past days setting everything up with trial and error I already learned a lot about linux!

THough that's the major flaw of linux on desktop too. I don't think mainstream users want to go through all this just to get things working.

---

### Post by prox2far on 2005-09-17
[QUOTE=Vertical]I recieved this message today from one user, owner of 855gme/tvout laptop
didn't try it yet. Going to test it soon

> Hi!
> I was browsing through the xorg archives and saw your message about
> tv-out.
> I'm using nvtv to change resolutions and to change from NTSC to PAL.
> I'm attaching the patch i made needed to have basic support for the 
> card. Apply with:
> cd nvtv ; patch -p1 < ../nvtv-i855.diff[/QUOTE]

this just doesn't work for me :(
what do you mean with "cd nvtv" that part does not make any sense

---

### Post by John.Michael.Kane on 2005-09-17
[QUOTE=prox2far]this just doesn't work for me :(
what do you mean with "cd nvtv" that part does not make any sense[/QUOTE]
 Search in synaptic for i855-crt... this should help..

---

### Post by chunk on 2005-10-22
> **Vertical]I recieved this message today from one user, owner of 855gme/tvout laptop
didn't try it yet. Going to test it soon

[b]> Hi!
> I was browsing through the xorg archives and saw your message about
> tv-out.
> I'm using nvtv to change resolutions and to change from NTSC to PAL.
> I'm attaching the patch i made needed to have basic support for the 
> card. Apply with:
> cd nvtv  said:**
> 

So what exactly does this patch do? Does it modify nvtv for use with the 855gme or does it modify nvtv for PAL instead of NTSC?

I'm going to try it. I hope it modifies nvtv for 855gme because this is what I want.

[QUOTE=prox2far]this just doesn't work for me :(
what do you mean with "cd nvtv" that part does not make any sense[/QUOTE]

I think he means go to the directory where the "nvtv" source code is located, then run the command "patch -p1 < ../nvtv-i855.diff". Then compile the source and set the configuration files as described. It doesn't seem easy.

---

### Post by casainho on 2005-10-30
[QUOTE=chunk]So what exactly does this patch do? Does it modify nvtv for use with the 855gme or does it modify nvtv for PAL instead of NTSC?

I'm going to try it. I hope it modifies nvtv for 855gme because this is what I want.

I think he means go to the directory where the "nvtv" source code is located, then run the command "patch -p1 < ../nvtv-i855.diff". Then compile the source and set the configuration files as described. It doesn't seem easy.[/QUOTE]

I download the source of "nvtv-0.4.7" from SourceFourge and then I aplied the patch.

I compiled after the "nvtv-0.4.7". Now reconize some encoder, but gives gives a message on console:
"CH7009 family not yet supported"!! -> So I think that this is some new version of Chrontel TV encoder that program can not handle yet :( 

I googled all the internet and I didn't find a way to put the TV out (Intel 855) working on Linux - blame on Intel for not make an Open driver :mad:

---

### Post by Vertical on 2005-11-03
Hello
This is the source of nvtv-0.4.7 with applied i855 patch
Can anyone make binary .deb package from this source?
It would be great

Thanks!

---

### Post by Vertical on 2005-11-03
I'm trying again intel drivers

Everything is ok, Xserver runs, but screen on my laptop is black.
I think it happens cause I didn't put string 
Option "PortDrivers" "lvds"
in my xorg.conf (in Device section)
But then I add this string, X doesn't run says that can't find module lvds! (or any other also).

All modules are present in my /usr/X11R6/lib/modules

What is wrong?

My xorg.conf and X server log are located here:
[http://cabbage.nm.ru/intel/xorg.conf](http://cabbage.nm.ru/intel/xorg.conf)
[http://cabbage.nm.ru/intel/Xorg.0.log](http://cabbage.nm.ru/intel/Xorg.0.log)

---

### Post by chunk on 2005-11-11
[QUOTE=Vertical]Hello
This is the source of nvtv-0.4.7 with applied i855 patch
Can anyone make binary .deb package from this source?
It would be great

Thanks![/QUOTE]

Does it work?

Are you using a Fujitsu laptop by any chance?

---

### Post by AndreAPL on 2005-11-13
[QUOTE=foxy123]It is quite strange because if I run lsmod I've got:
```
i915                   21856  1
drm                    74808  2 i915
``` 
glxinfo:
```
 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
``` 

so it looks like dri is enabled, but I do not have 3D acceleration at all.

BTW, if you want to boot into Windows, try fix_mbr command to get rid of grub...[/QUOTE]

same problem here.... what is wrong ???:confused:

---

### Post by foxy123 on 2005-11-13
[QUOTE=AndreAPL]same problem here.... what is wrong ???:confused:[/QUOTE]
What version of the driver have you installed?

---

### Post by AndreAPL on 2005-11-14
built-in in kubuntu 5.10...
dri loaded, says direct rendering enable...

---

### Post by foxy123 on 2005-11-14
[QUOTE=AndreAPL]built-in in kubuntu 5.10...
dri loaded, says direct rendering enable...[/QUOTE]
you can follow this guide [http://www.ubuntuforums.org/showthread.php?t=75393](http://www.ubuntuforums.org/showthread.php?t=75393). Just replace savage driver with i915 and use 20050714 version rather than 20050718, which did not work for me.

---

### Post by PeaceMessenger on 2005-11-29
I have a Dell Inspiron 1100 that uses the 845GL integrated graphics chip.  Unfortunately Ubuntu only gives me 600x480 screen resolution.  After a lot of struggle, I'm now at the point of believing it is the driver.  Intel says I need the 915G driver, but my xorg.conf file tells me that my ocmputer is trying to use the i810 driver.  I downloaded the driver from Intel's website but haven't figured out how to install it yet.  
This is a link to that discussion [http://ubuntuforums.org/showthread.php?p=529903#post529903]("http://ubuntuforums.org/showthread.php?p=529903#post529903")
Since you guys seem to know something about drivers it would be great if you guys could lend a hand.
Thanks,

---

### Post by foxy123 on 2005-11-30
[QUOTE=PeaceMessenger]I have a Dell Inspiron 1100 that uses the 845GL integrated graphics chip.  Unfortunately Ubuntu only gives me 600x480 screen resolution.  After a lot of struggle, I'm now at the point of believing it is the driver.  Intel says I need the 915G driver, but my xorg.conf file tells me that my ocmputer is trying to use the i810 driver.  I downloaded the driver from Intel's website but haven't figured out how to install it yet.  
This is a link to that discussion [http://ubuntuforums.org/showthread.php?p=529903#post529903]("http://ubuntuforums.org/showthread.php?p=529903#post529903")
Since you guys seem to know something about drivers it would be great if you guys could lend a hand.
Thanks,[/QUOTE]
you can use the link I gave above to Savage card HOWTO. Please note that they put 20070714 version, which works with X11R6.8 in archives folder. Download i915 driver and common files and follow the guide. Also although it is i915, you will have i810 in you xorg.conf, which is fine.

Let us know if you have any problems. Also do not use recent drivers from dri, they are for X11R6.9/7.0.

---

### Post by AndreAPL on 2006-03-23
[QUOTE=foxy123]you can follow this guide [http://www.ubuntuforums.org/showthread.php?t=75393](http://www.ubuntuforums.org/showthread.php?t=75393). Just replace savage driver with i915 and use 20050714 version rather than 20050718, which did not work for me.[/QUOTE]
inded i'm using 20050718, will try the other,thanks

---

### Post by foxy123 on 2006-03-23
[QUOTE=AndreAPL]inded i'm using 20050718, will try the other,thanks[/QUOTE]
or switch to Dapper where DRI for Intel chips works out of the box (on clean install though).

---

### Post by AndreAPL on 2006-03-26
[QUOTE=foxy123]or switch to Dapper where DRI for Intel chips works out of the box (on clean install though).[/QUOTE]
Not a solution to me :mrgreen: 
will work around :rolleyes: anyone using recent snapshot's ?
20050714 isn't even in the server :neutral:

---

### Post by foxy123 on 2006-03-26
[QUOTE=AndreAPL]Not a solution to me :mrgreen: 
will work around :rolleyes: anyone using recent snapshot's ?
20050714 isn't even in the server :neutral:[/QUOTE]
should be there, look in the archives

---

### Post by AndreAPL on 2006-03-26
[QUOTE=foxy123]should be there, look in the archives[/QUOTE]
no, already search there...

---

### Post by foxy123 on 2006-03-27
[QUOTE=AndreAPL]no, already search there...[/QUOTE]
if you like I can look into my archives and if it's still there send it to you... I'm not sure though and can do it only in the evening when back to my laptop...

---

