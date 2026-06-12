---
title: "ubuntu on lenovo u350 from usb drive"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by mwub on 2009-08-16
Hi guys,

When I got any questions regarding ubuntu I usually find answers really quick in the forums here. But this time I couldn't find one so here's my question:

I just bought a lenovo U350 and want to install ubuntu on it. Since it does not have a CD drive I used unetbootin to create a bootable usb drive so I can install ubuntu.
When I boot from usb everything starts normal, I get the unetbootin screen asking me what version of ubuntu i want to install (default or OEM) and then I see the splash screen with the bar showing me that it's working and loading.
But when it reaches 100% the only thing I get afterwards is a blank (or black) screen and nothing is happening.
I suppose it is some kind of problem with the graphics but I have no idea what to add in the command line when I'm booting the installer to make it work.

Did anyone have similar problems?

---

### Post by mwub on 2009-08-17
Maybe I should also mention that I tried the ubuntu netbook remix but I had the same problem (black screen after loading)

Here are the specs of the laptop by the way:

Intel® Pentium® SU2700 processor ( 1.30GHz 800MHz 2MB )
Intel Integrated Graphics X4500
3 GBPC3-8500 DDR3 SDRAM 1066MHz
320GB

---

### Post by skipjackrc4 on 2009-08-22
I had the same problem (though I was using an external optical drive).  This laptop is so new that older versions of Ubuntu (or other distros) won't work.  I installed 9.10 alpha without a problem (installation wise).  Fedora 11 also worked.

I will warn you that brightness control and headphones don't work.  Everything that I have tried seems to.  Hopefully in a few months, these features will be working.

---

### Post by mwub on 2009-08-23
Thank you for your help.

Well, I guess I'll install Fedora and eventually switch to Ubuntu 9.10.
And I don't really care about the brightness or the headphones as long as I get Linux to work on my lenovo.

---

### Post by ionospheric on 2009-09-08
blank screen problem:

When the Ubuntu live CD (on USB stick) boot menu comes up, press F4 for Modes. Then select "Graphics Safe Mode".

---

### Post by nampala on 2009-09-09
I´ve also tried to install ubuntu 9.10 on a lenovo u 350. Graphics work fine, but my wireless card and ethernet card both do not work out of the box. Did anybody else here get them to work?

---

### Post by mwub on 2009-09-09
Hi guys,

it's me again.

Like I previously mentioned I tried to install Fedora 11 which kind of worked, but not really.
I was able to install Fedora, but the grub installation failed every time (grub couldn't be installed on my primary partition, the one with Vista on it). Which means I had Fedora installed but couldn't boot it since I always got straight to Vista, no grub involved. I tried to make my own bootloader with EasyBCD (or VistaBootloader, I don't remember) but that didn't work at all.

Well, then I downloaded the newest alpha of Ubuntu 9.10 and I was actually able to start the Live CD and use Ubuntu and all that stuff, but when I wanted to install it permanently the installation stopped saying that the installer was unable to mount the partitions that I wanted to install Ubuntu on.

What's going on here? Is there anything I should check regarding my harddrive or my partitions that I want to install Ubuntu on?

@ionospheric: at what point do you want me to press F4? I don't really get to the Ubuntu boot menu. The only boot menu I get is the one from unetbootin. I could add something in the command line, but I don't now what to write to start Ubuntu in "graphics safe mode".

@nampala: Well, at least you got it installed. How exactly did you do that? From an USB flash drive or an external drive?

---

### Post by nampala on 2009-09-10
I did it with an external drive. But it also crashed my hard drive once, so you might have the same problem. Seems like the partition manager doesn´t work too well. 

The hitting F4 thing is right at the start when you boot the cd and it asks you whether you want to try the live cd or install directly or do a memory test. The safe graphics install also worked on my computer for Ubuntu 9.04, but then of course you also don´t have the right graphics working after the installation and have to keep on hacking.

---

### Post by ionospheric on 2009-09-16
mwub, you are right: with the unetbootin method, you do not get the menu at the bottom of the screen.

If you download the image file, and install it according to the Ubuntu method, you do get the menu at the bottom of the screen (after answering the question about the language preference).

[COLOR="Blue"][COLOR="DarkOrange"][https://help.ubuntu.com/community/Installation/FromImgFiles]("https://help.ubuntu.com/community/Installation/FromImgFiles")[/COLOR][/COLOR]

If you choose the netbootin method, you can still enter boot options by hitting the TAB key and trying xforcevesa or vga=771.

So I got NBR 9.04 to work with this method, but after running the updates, the new kernel did not run at all.

The good news is that Karmic Koala 9.10 alpha 5 works great, so there is no need to worry about 9.04 any more. The display works out of the box. 

There are some little things that need to be adjusted. The touchpad mouse click is disabled by default, it can be enabled through System->Preferences->Mouse. Also, Grub did not have an option to boot the Windows partition after the install. This could be fixed by running 

```
sudo update-grub
```

In all, I love this little machine. I don't know what all the whining is about when it comes to performance. On my U350, supertuxkart runs faster than on my HP nc6400 which has the Intel dual core 2 CU and Intel 945 graphics chip.

The only annoyance is that the fan runs a lot, but hopefully somebody will provide a fan control eventually..

---

### Post by srdjo on 2009-09-20
I also got it installed using unetbootin and usb drive.

I installed Ubuntu 9.10 and all is working except both network devices.

Does anyone has any hint ?

---

### Post by alprakas on 2009-09-22
for me, fedora 11 works perfectly fine, except that brightness control is not available and the heaphone jack sense doesnt work! 

The fan is really irritating, anyone any suggestions?

---

### Post by mwub on 2009-09-24
So, I finally got it installed.

Here's how:
I got the newest alpha of 9.10 (since I already tested the Live CD and that worked) and this time I let ubuntu choose the partition for the installation.
I had already partitioned some space on my hdd but everytime I chose the manual installation and pointed ubuntu to these partitions, the installation always failed (see my previous posts)

Well, this time I chose the side-by-side installation since I still didn't wanna loose Vista (I know, I know, but hey, I paid for it). It turned out that ubuntu thought my partition that stores the backups for Vista IS Vista and deleted the other partition.
So in the end I have ubuntu running and lost my Vista and all the data that was on that partition.

But I don't really mind, honestly. There was nothing on there that was that important.

The most important thing is that ubuntu works and it's fantastic. It's so much faster than Vista was!

But, nothing is perfect, so I also have a short list of things that don't work (compared to earlier ubuntu versions on my old laptop):

-no two-finger-scrolling. doesn't work, don't know why, I already tried changing the .conf myself, but that didn't change anything. I would appreciate it if someone could help me with that because I miss the two-finger-scrolling :(
-the brightness control doesn't work (other people already mentioned that so that's nothing new)

I haven't tested the headphone jack yet, so I don't know if that one doesn't work also.
As to the fan, I don't think it's too loud.


Thanks to everyone for helping me and coming up with suggestions!

---

### Post by alprakas on 2009-09-25
hey mwub, thanks for these updates, :-)

though I would like to ask a couple of things... Which desktop manager are you using? KDE or the default GNOME or any other one?

Also please check the headphone jack and let us know...thanks in advance!
For me in fedora 11, the headphone jack works, but the sound comes from both the headphone as well as the integrated speakers even with the headphone connected, which is a big problem when I use my laptop in my office...

by the way, has anyone else tried any other distro on this laptop?

alprakas

---

### Post by mwub on 2009-09-28
I'm using GNOME. I somehow can't get used to KDE, don't know why.

I tested the headphone jack and got the same problem like you: the sound comes from the headphones AND speakers when the headphones are plugged in. Weird...

Hopefully there's a workaround cause that's kind of annoying.


mwub

---

### Post by alprakas on 2009-10-04
Just wanted to let you guys know, that I tried the latest version of sabayon 5 (both KDE and GNOME) on the U350. Its good to see that almost everything worked right out of the box, including the display brightness control :-) The only problem I am still facing is the sound coming from both the headphones and the laptop speaker. Somehow this problem is still not addressed.

The KDE version as usual has good eye candy but it felt like slowing the system a little more than the GNOME one....So I finally installed the GNOME version. There are couple of bugs here and there as it is a new version, but overall, it looks quite polished and the laptop runs fairly cool.

in the meantime I have problems in the hibernation of VISTA, somehow it comes back to login screen after I send it to hibernation...wierd problem...hope this can be solved in the Windows 7 upgrade... :-) I havent tried hibernating in sabayon yet.

By the way I would like to ask you people about the battery life and the normal temperature at which ur U350 (or any laptop with low voltage processor) runs? Mine can last for about 3 hours max with the supplied 4 cell battery......that is sad, given its a CULV processor...the normal temperature is about 48 or 49 C...Is it normal?

thanks,
alprakas

---

### Post by nomnex on 2009-10-22
> **ionospheric said:**
> 
The only annoyance is that the fan runs a lot, but hopefully somebody will provide a fan control eventually..

Perhaps, you could try this?
[http://www.notebookforums.com/post3074321.html](http://www.notebookforums.com/post3074321.html).

Fan and heat are recurrent complains on notebook forums for this model running the native crap Vista/Win7. It might not be OS related and I am afraid there won't be a magical fix from Canonical.

---

### Post by Sukolzs on 2009-11-08
Regarding simultaneous sound on headphones and laptop speakers there is bug reported on Launchpad.
[https://bugs.launchpad.net/ubuntu/+bug/477226]("https://bugs.launchpad.net/ubuntu/+bug/477226")
Please confirm this bug so that we can get solution as fast as possible.;)
Sorry for a bit offtopic post.

---

### Post by ReuseablePlastix on 2009-11-13
> **mwub said:**
> 
I tested the headphone jack and got the same problem like you: the sound comes from the headphones AND speakers when the headphones are plugged in. Weird...

Hopefully there's a workaround cause that's kind of annoying.


mwub

mwub,

HunterThomson, Wyth and co. put together a thorough tweaking of the Lenovo Y510 ([Lenovo Ideapad Y510 is Go]("http://ubuntuforums.org/showthread.php?t=870681")).  Not sure of the similarities of the Y510 to the U350 but we had the same issues with sound.  Check it out; I hope it helps, it's pretty well summarized on the first page.

---

### Post by mwub on 2009-12-02
> **nomnex said:**
> Perhaps, you could try this?
[http://www.notebookforums.com/post3074321.html](http://www.notebookforums.com/post3074321.html).

Fan and heat are recurrent complains on notebook forums for this model running the native crap Vista/Win7. It might not be OS related and I am afraid there won't be a magical fix from Canonical.


Wow, thanks a lot! I actually did that and it definitely helped. I also had a sticker stuck in between the CPU and the heat sink! I removed it and put some grease on the CPU and GPU. The fan is a lot quieter now and doesn't run that often. Plus my battery lasts now at least 6.5 hours!

---

### Post by nomnex on 2009-12-02
> **mwub said:**
> Wow, thanks a lot! I actually did that and it definitely helped!

Glad if it helped. The issue has been addressed to Lenovo US,  but obviously there is no much communication with the Chinese assembly line.

---

### Post by nomnex on 2009-12-16
Need info regarding the brightness.

Can you set brightness through the panel applet or through the Power manager (eventually through the BIOS)? Any info welcome.

Does anyone have open a bug about brightness (FN keys) on this model on Launchpad? Thanks

---

### Post by gonville on 2010-02-09
Hi, I've just bought a Lenovo U350 with Vista pre-installed. I used Wubi to install Ubuntu 9.10 and now have a dual boot machine. Ubuntu working well except it will not detect wireless internet. I have no problems detecting and connecting to my home wireless from Vista. Have tried disabling the network connection in Vista but still nothing in Ubuntu. Have you had a similar problem? Do I need a different driver for Ubuntu to detect the network?
Thanks

---

### Post by Robert Leithe on 2010-05-11
> **nampala said:**
> I´ve also tried to install ubuntu 9.10 on a lenovo u 350. Graphics work fine, but my wireless card and ethernet card both do not work out of the box. Did anybody else here get them to work?

Did you get the wireless and ethernet to work? Because that's were I've been stuck (and gave up) with my U350. Running Windows 7 now, but miss Ubuntu sorely... :)

Robert

---

