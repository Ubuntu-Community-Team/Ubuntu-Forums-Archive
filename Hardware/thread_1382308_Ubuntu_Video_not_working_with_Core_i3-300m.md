---
title: "Ubuntu Video not working with Core i3-300m"
date: 2010-01-15
forum: Hardware
---

### Post by jmswelch77 on 2010-01-15
During the install I can't get any video at all with ubuntu 9.10 both the 32 and 64 bit versions.  I have also tried kubuntu 9.10 64bit.  The screen is just completely blank.  I have tried installing in both windows with wubi and straight up off of the cd.  The live cd doesn't display any video either.  My setup is:
Asus U50F laptop
core i3-330m
4gb ddr3
500gb sata hdd
dvd burner
15.6in widescreen monitor
windows 7 home premium 64 bit
5 series/3400 series chipset

---

### Post by btechcs on 2010-01-16
I have the same problem with the new core i3 m330 (Arrandale) processors with on-chip graphics (GMA HD). It just does not detect the display. 

I tried i915.modeset=0 to use UMA instead of KMA, but it then just shows the black and white ubuntu logo (with verbose), and then the screen disappears.

If anyone has the same problem, please report. s

---

### Post by metadromos on 2010-01-17
I also have this problem with a new ASUS U50F.  I tried to install 9.10, but get the black screen.

I can't wait to get rid of 7 so hopefully the Ubuntu gurus will have something for us soon!

---

### Post by metadromos on 2010-01-17
While I wasn't able to install Ubuntu 9.10 on my new ASUS U50F, I was able to install Ubuntu 10.04 Alpha 2 release.

---

### Post by jmswelch77 on 2010-01-18
10.04 eh?  I might as well wait until the final candidate comes out.  Sounds like they are addressing the new architecture in the new release.  Pretty promising.

---

### Post by btechcs on 2010-01-18
I tried installing 10.04 Alpha2, it just freezes as soon as it boots to live image.

Any Ideas?

---

### Post by argosreality on 2010-01-18
Have you tried doing the install with the boot parameter fb=false ? That'll disable the framebuffer if your video chipset is not supported in 9.010 (which its probably not since the chipset just came out)

---

### Post by jmswelch77 on 2010-01-18
Oooohhh....I haven't tried that.  I will and will let you know the outcome.  Thanks very much for the post.  :)

---

### Post by jmswelch77 on 2010-01-19
Tried disabling the frame buffer as recommended but am still seeing a blank screen during the install.

---

### Post by iconoclast88 on 2010-01-20
I'm having the same issue with the asus U50f.
I can't get any distro to work right (ubuntu 9.10, 10.4 or SUSE 11.2) except MEPIS, latest distro. But Mepis wireless drivers dont support the U50f.

I'm going to try installing fedora 12 now. I prefer ubuntu, but i'll take anything but JUST windows in the meantime. 

Is UBUNTU going to officially support the i3 processor in the final release of 10.4? Or is that just a rumor and a hope?

Josh

---

### Post by BriceHulse on 2010-01-20
Does this problem have to due with the graphics or the processor?

---

### Post by IrrTrust on 2010-01-20
Is there any word on when this might be supported. It is obviously the on-chip video compatibility. But all I find is this single thread on the subject, nothing else.

And I have a choice of returning a computer within the next 6 days, or sticking with Windows 7 until some type of compatibility appears.

If we are talking April's release, then it is return time.

If sometime fairly soon, then I can hold off and keep the computer, which was a good deal...

So, any word for compatibility appearing and allowing a new install?

---

### Post by iconoclast88 on 2010-01-21
OK, I was able to install 9.10 32 bit on my asus U50f.
I then upgraded to 10.4

All worked well, until...I unplugged the AC power. It froze like it usually would first thing after login.

Anyway to disable the power management module? If i did that, would this break something else?

Hmmm. Perhaps there is no issue with the video or proc.

---

### Post by jmswelch77 on 2010-01-23
I was able to install the pre release of ubuntu 10.04 64bit.  So far it seems to be behaving.  I will keep you posted.  It is just nice to be using Ubuntu again.

---

### Post by jalyst on 2010-01-25
Is i3-530 a viable alternative to GT220 + VDPAU for video decode? 
If not what does it lack in comparison to GT220 + VDPAU? 
I'm hoping I can mostly get away with it, if not I can always add a GT220. 

Thanks!

---

### Post by jmswelch77 on 2010-01-25
Ubuntu 10.04 alpha2 does not like to be used on the battery on the Asus U50F.  The OS locks up as soon as it gets to the desktop.  Seems to work fine on the AC Adapter.

---

### Post by jalyst on 2010-01-26
> **jalyst said:**
> Is i3-530 a viable alternative to GT220 + VDPAU for video decode? 
If not what does it lack in comparison to GT220 + VDPAU? 
I'm hoping I can mostly get away with it, if not I can always add a GT220. 

Thanks!

for those whom may have been wondering the same thing
[http://phoronix.com/forums/showthread.php?p=109520#post109520](http://phoronix.com/forums/showthread.php?p=109520#post109520)

---

### Post by jmswelch77 on 2010-02-01
In regards to the Asus U50F and the Core I3-330m working I may explore virtual box with Ubuntu 9.10.

---

### Post by jalyst on 2010-02-01
righto

---

### Post by cubdukat on 2010-02-06
> **iconoclast88 said:**
> I'm having the same issue with the asus U50f.
I can't get any distro to work right (ubuntu 9.10, 10.4 or SUSE 11.2) except MEPIS, latest distro. But Mepis wireless drivers dont support the U50f.

I'm going to try installing fedora 12 now. I prefer ubuntu, but i'll take anything but JUST windows in the meantime. 

Is UBUNTU going to officially support the i3 processor in the final release of 10.4? Or is that just a rumor and a hope?

Josh

Don't bother. None of the distros seem to like the new chipsets. I think people were expecting them a lot later than Intel sprung them on us, so they haven't had a chance to work support for them into the kernel yet. I am currently having the same problem right now. I can't even get anything out of the live CD. I think I'm going to try the Alpha route, if I can find it.

---

### Post by stacktracer on 2010-02-07
Arrandale gfx can be made to work in Karmic.

Use the xorg-edgers ppa ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)). Add it to your sources.list, then do an update and a dist-upgrade.

You also need kernel >= 2.6.32 (works for me with 2.6.32.7). Get kernel packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). (It's not an apt repository, unfortunately -- you have to download the debs and install with dpkg.)

Those mainline kernel packages seem to be just straight vanilla kernels, with no Ubuntu-izations. The only practical difference I've seen so far is that AppArmor doesn't work, which is no big deal for me.

---

### Post by stacktracer on 2010-02-07
Also, even with xorg-edgers and kernel 2.6.32, compiz is unusably crashy.

You can turn it off with:

```
gconftool-2 --set /desktop/gnome/session/required_components/windowmanager --type string metacity
```

Of course, you first have to be able to log in ... which is tough with a crashy window manager, and bleeding-edge modesetting. You can boot with the "text" kernel parameter, turn off compiz, then reboot as usual.

---

### Post by mkblair on 2010-02-13
Glad I'm not the only one experiencing this. New Dell laptop running Win 7 Home Premium 64 bit, tried to boot Ubuntu 9.10 x64 Live CD in order to set up dual boot, shows Ubuntu splash screen with "try ubuntu without installing, install, memory test, options etc", chose install Ubuntu, and nothing, screen just goes blank, CD spins, and then after a few minutes, nothing, CD stops spinning, and just nothing, blank screen. Does the same thing if I try to boot to "try without installing". I believe it is the Linux kernel not having drivers for this new Intel chipset like a few of the posters stated. I will try the 10.04 Alpha route thogh. I have had success in installing 9.04 x64 in VirtualBox though. Works perfect, but this is not my ideal solution, I want Ubuntu to dual boot properly and Kubuntu to run in VirtualBox.

---

### Post by muay37 on 2010-02-14
I have an Acer AS5740-5780 with a I3-330M and I'm having the same problem.  I've tried Ubuntu 9.10, Mandriva 2010, Fedora 12, OpenSUSE 11.2 and none of them worked.  But, unlike Ubuntu and Fedora, Mandriva and OpenSUSE let me finish the installation before 'crashing'.  The only one that has worked so far has been MoonOS, but I prefer gnome.  Thanks for mentioning the alpha, I'll give that a try now.

---

### Post by cororok on 2010-02-15
Mine is also acer 5740-5780, core i3 330m.

I tried ubuntu 10.XX alpha 2.
I could see the first GUI screen and icons on desktop.
I clicked an icon labeled 'install..'
But after clicking that, It was frozen.

---

### Post by dakotadare2b on 2010-02-17
Any luck? I'm downloading Ubuntu 10.04 alpha 2 now, to see if I can get it installed on a Dell Studio 1747. It has the i7 Intel Q720 & ATI Mobility Radeon 4650 graphic cards. I attempted to install both Ubuntu and Kubuntu 9.10, but had the black screen issue with the live and alternate installs. They run fine in virtual box though, in Win7 Ultimate.

I'll let you know if it is successful.

EDIT: I've installed the Ubuntu 10.04 Alpha 2, using the alternate install, and I now have a working install of Ubuntu. No black screen. It recognized graphics right away.

Location of install files:
[http://cdimage.ubuntu.com/releases/lucid/alpha-2/](http://cdimage.ubuntu.com/releases/lucid/alpha-2/)

Best of luck!!

---

### Post by racer7890 on 2010-02-18
I had this same problem with my Toshiba Satellite Pro U500 (the new model with the i3 processor). I have written a guide for other people who may be struggling with this, hopefully useful to somebody.

[Using the Intel Arrandale with Ubuntu 9.10]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10")

---

### Post by kvmapr on 2010-02-18
After reading all the issues trying to get 9.10 running on the i3, I loaded Virtualbox under Windows 7 onto my new HP dv6 laptop and loaded 9.10 into it. Works great, no issues yet and performance is fine. This will tide me over till i3 support is achieved, hopefully with 10.4 at the latest.

---

### Post by gnarfle on 2010-02-19
> **racer7890 said:**
> I had this same problem with my Toshiba Satellite Pro U500 (the new model with the i3 processor). I have written a guide for other people who may be struggling with this, hopefully useful to somebody.

[Using the Intel Arrandale with Ubuntu 9.10]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10")

Yay! This worked perfectly for me on my Acer Core i3 laptop. I was previously running a nightly of 10.04 that worked graphically but was not terribly stable, now I have a nice install of 9.10 going and I might finally be able to ditch windows.

---

### Post by muay37 on 2010-02-21
Racer7890 - Thanks a lot for your help.  I followed your instructions a few days ago and everything has worked well.

---

### Post by Taylor Franklyn on 2010-02-24
it there another way to do this? im dual booting using wibi, so there is no live cd involved..

---

### Post by Taylor Franklyn on 2010-02-24
no video in safe graphics mode either, ahh sorry im quite the noob.

---

### Post by cororok on 2010-02-26
ubuntu 10.04 alpha 3 ( not II ) works well.

It came out yesterday and I installed it on my acer core i3

It's good. also compiz works well.

but 10.04 is not probably stable itself.

---

### Post by teh603 on 2010-02-26
Works on my Dell Inspiron 1564 as well, and I've been having the same problems on Karmic as everyone else seems to.

Odd thing- Jaunty seems to boot into "safe graphics" mode on mine.

---

### Post by Orographic on 2010-03-03
How is Alpha 3 going with the new i3 chips now? I'm planning on getting an i3 desktop a bit later in the year as they have reviewed well and use so little power. I'm not a gamer so apart from that, they are very good little chips.

---

### Post by teh603 on 2010-03-04
> **Orographic said:**
> How is Alpha 3 going with the new i3 chips now? I'm planning on getting an i3 desktop a bit later in the year as they have reviewed well and use so little power. I'm not a gamer so apart from that, they are very good little chips.

Looks better, but some things are still spotty. Games and Compiz still cause crashes.

---

### Post by Orographic on 2010-03-07
Thanks for that.

Apparently Lynx is shipping with 2.6.32 kernel but 2.6.33 is where i3 and i5 6xx are fully supported.

Has anyone heard more on this?

---

### Post by teh603 on 2010-03-09
Honestly, 2.6.32-16 is working well enough as far as I can tell. I haven't tried it with many 3D games, but the overall chipset is better supported now than it ever has been. When I first started testing Alpha 2, I got a freeze from just trying to use a menu. Several weeks later we're on Alpha 3 and I have fair ACPI support, decent 3D performance, Compiz seeming to be stable enough, and all that.

All we need now is to replace Plymouth with the bootsplash we used to have, and all will be well.

---

### Post by beta.tester on 2010-03-12
> **Orographic said:**
> How is Alpha 3 going with the new i3 chips now? I'm planning on getting an i3 desktop a bit later in the year as they have reviewed well and use so little power. I'm not a gamer so apart from that, they are very good little chips.

Hi

I have just helped a friend with bad withdrawal symptoms :) He only had windows 7 and any attempt to install linux failed with a blank screen.
After trying 10.04 alpha 3 on my own machine and liking the new stuff enough to install it full time :) I installed successfully on his i3 Dell 1564 and it is great! After the updates he is on Kernel 2-6.32.16 and apart from the occasional bug report a program has unexpectedly closed, it is working fine and he is happy and so am I :)

Initially we had a weird problem, as the original partitioning was changed he had a 169G system and a 160G data drive. When we tried to install 10.04 alpha 4 it reported the second partition (160G data) was unusable! I tried deleting it, making it unformatted but no joy. 

The *only* way to get it to install was to reinstall Windows 7 as 1 large partition (the whole of the drive), then install 10.04 alpha 3 and allow it to shrink the partition itself. - Bingo! I suspect that windows 7 has a weird way of writing to the fat table of the end of partition marker, not sure, but can say making it 1 whole disk and allowing Ubuntu 10.04 to shrink it worked great ;)


Hope this helps someone.

Always expecting the best!   john

---

### Post by Orographic on 2010-03-13
Great, thanks guys. I am looking at the i3 chip with 80% to 90% certainty now as I don't play games at all. My wife will probably get this cpu setup first with Windows 7 (she needs it for Sibellius - she's a violinist) and then Lucid Lynx on the spare internal drive. 

I'll set hers up, then I'll buy my system some time mid year or a bit later. May even wait for Ubuntu 10.10

That way, the new motherboards will have a revision or two in them, which can help things a bit.

---

### Post by theviking10 on 2010-04-02
Just thought I'd add that I have much the same problem with my Toshiba Satellite A505 (Intel i3 M330 graphics). However, I cannot get the Lucid Beta to boot. 

Here's hoping for the final release, I would really hate to keep using Win7 for longer than I have to.

---

### Post by sheik.yerbouti on 2010-04-04
Same issue. Tried Karmic 32- and 64-bit all flavors (Ubuntu, Kubuntu, and Xubuntu) and Mint 8, no joy. Switching back to Win7 pending Lucid.

---

### Post by sheik.yerbouti on 2010-04-04
Successful boot with Lucid Beta 1.

---

### Post by nirvale on 2010-05-12
i have a toshiba m505 core i3, ubuntu 10.04, no detect install problems, but, never becomes de first boot only a black screen, i'm have to use win 7... 

any solution?:(

EDIT: i try to install ubuntu studio 10.04, maybe the problem was the rt kernel version..., any idea?

---

### Post by theviking10 on 2010-05-12
Even with the shiny new 10.04 I am unable to boot. :(

Any ideas other than wait for Fedora or SUSE to release their next upgrade?

---

### Post by nirvale on 2010-05-18
> **theviking10 said:**
> Even with the shiny new 10.04 I am unable to boot. :(

Any ideas other than wait for Fedora or SUSE to release their next upgrade?


openSUSE 11.3 "test", boot sucessfully on the intel core i3, but the kernel (2.6.34) only works with one proccesor, mmmm little by little:(, the boot becomes  with: acpi=off in the command line on the grub, my fan works fine.

Good look

---

### Post by pramoad on 2011-01-16
> **nirvale said:**
> i have a toshiba m505 core i3, ubuntu 10.04, no detect install problems, but, never becomes de first boot only a black screen, i'm have to use win 7... 

any solution?:(

EDIT: i try to install ubuntu studio 10.04, maybe the problem was the rt kernel version..., any idea?

Update the kernel

---

