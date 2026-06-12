---
title: "Missing /dev/agpgart on an intel 965GM"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by smylie on 2007-05-24
I'm trying to get feisty to run on an HP 6710b laptop w/ x3100 video card (965GM chipset).
It's failing when it tries to start X however, because theres no /dev/agpgart.

(EE) GARTInit: Unable to open /dev/agpgart (No such device or address)
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory

Because this card shares system ram, without agpgart, it can only see 8 meg, so X will only run at 640x480 - anything else and it runs out of memory and barfs.

The agpgart module was loading automatically after the install, but not the intel_agp module. I've try modprobe'ing both of these, and they load without error, but no /dev/agpgart is created.

There's no way in the bios  to specify the amount of VideoRam. So (i'm guessing) that even though I specify the VideoRam in xorg.conf, as there's no /dev/agpgart to see it this value is just being ignored . . .

Anyone got any ideas as to why my /dev/agpgart is missing? (Or even just confirmation that this is my problem, and I'm not barking up the wrong tree)

---

### Post by Ace2016 on 2007-05-25
have a look at your dmesg, it might show the error:

ace@Linux:~$ dmesg |grep AG && dmesg|grep ag

Maybe its something to do with the kernel, i think some changes were made to intel's agp in 2.6.21 so you might have to update your kernel to the newer version.

If you compile the kernel, use make oldconfig with the ubuntu's config file, also run lsmod, look at the modules loaded and when your in menuconfig make sure as many of them are compiled into the kernel, and also make sure to compile in the file systems you use. Make sure to patch the kernel with stuff like suspend2 and stuff if you need it.

---

### Post by smylie on 2007-05-25
Thanks - this fixed it in the end. (After much messing round).
Down side of course being no-more restricted modules until the feisty kernel moves to 2.6.21.
Have to go and sort out wireless drivers myself =)

---

### Post by jollins on 2007-06-01
I'm having the same problem. Could someone explain this process is newbie-friendly terms? A lot of people will be getting laptops with the 965gm (santa rosa) chipset so I'm sure it'll be useful to many others.

---

### Post by smylie on 2007-06-02
try upgrading to the latest ubuntu kernel - 2.6.20.16

When I installed, the default kernel did not give me the /dev/agpgart, so I had to compile the latest kernel (2.6.21.3) + restricted intel modules by hand (which was a **real** pita.) However since then, I've done the ubuntu automatic updates which dragged down a newer version of the ubuntu kernel (2.6.20.16) which seems to work okay as well,. You're much better off sticking with the default ubuntu kernel if you can.

Just try

```
$ sudo apt-get update 
$ sudo apt-get upgrade 
```

It should upgrade a lot of stuff, including linux-kernel. (which is the important bit).

reboot, making sure you're using the new kernel, and hopefully you'll have your agpgart.

Let me know how you get on - I'm particularly interested in your screen clarity - I'm having huge issues try  to get mine to not be fuzzy/blurry, even though it's running at the native resolution - see [http://ubuntuforums.org/showthread.php?t=457876](http://ubuntuforums.org/showthread.php?t=457876)

Cheers
Dave Smylie

---

### Post by jollins on 2007-06-03
Unfortunately that didn't solve the problem. Perhaps I'll just wait until it's updated and my hardware is automatically detected and supported.

---

### Post by smylie on 2007-06-03
Did it create the /dev/agpgart?

---

### Post by jollins on 2007-06-04
> **smylie said:**
> Did it create the /dev/agpgart?
How do I check this?

---

### Post by smylie on 2007-06-04
A simple directory listing:

```
 $ ls -l /dev/agpgart 
```

Given I'm assuming you don't have X if you need agpgart and it's broken, you'll need to do that from the console X dumps you back to when it crashes . . .

---

### Post by jollins on 2007-06-04
You're right - I am being dumped into console when X crashes.

I get 
```
crw-rw---- 1 root video 10, 175 2007-06-05 17:53 /dev/agpgart
```
so I assume yes.

---

### Post by smylie on 2007-06-04
Well, in that case, you shouldn't be getting the "Unable to open /dev/agpgart (No such device or address)" error any more. . . .
If it's still not going, what error are you getting now?

---

### Post by chewearn on 2007-06-07
hi smylie
I'm on the verge of getting the HP 6510b.  I think it's almost identical spec to your 6710b, except for the smaller screen.

I'm very interested to hear about your opinion on your notebook, specifically, how well Feisty run on it.

About the need to update the kernel, will the notebook still boot the livecd and install?  Or did you need to use the alternate cd install?

Is there any other issues you faced?  I saw in a forum somewhere, a person complaint about the fan constantly running, because the bios is not scaling down the cpu while there is no activity.

Thanks! :D

---

### Post by smylie on 2007-06-09
I've actually been very disappointed with this laptop so far.

I had to use to use the Alternate Install CD as it couldn't start X winders in the normal live cd. Even with the Alternate Installer, I couldn't get X to run afterwards. I needed to get the latest intel video drivers from their git repository and compile those + my own custom kernel. (Which also meant had to work out how to do the Intel wireless custom compile as well, which was a real pita .. . . )

But, having finally got X to run, compiz / beryl won't work, and the monitor is blurry. (see [http://ubuntuforums.org/showthread.php?t=464907](http://ubuntuforums.org/showthread.php?t=464907) )

About the only thing that has impressed me is that suspend and hibernate worked out of the box - first laptop I've seen do that.

I think the main problem is that the laptop is too new - the first version of the video driver was only released about 3 or 4 weeks ago, so it's not incorporated into any distributions yet. This should change, (and hopefully one of the newer drivers will resolve my screen issues).

Anyway - I'm downloading Gutsy Gibbon at the moment - I'll give that a try and let you know how that goes . . . 

Cheers
Dave Smylie

---

### Post by jollins on 2007-06-09
> **smylie said:**
> I've actually been very disappointed with this laptop so far.

I had to use to use the Alternate Install CD as it couldn't start X winders in the normal live cd. Even with the Alternate Installer, I couldn't get X to run afterwards. I needed to get the latest intel video drivers from their git repository and compile those + my own custom kernel. (Which also meant had to work out how to do the Intel wireless custom compile as well, which was a real pita .. . . )

But, having finally got X to run, compiz / beryl won't work, and the monitor is blurry. (see [http://ubuntuforums.org/showthread.php?t=464907](http://ubuntuforums.org/showthread.php?t=464907) )

About the only thing that has impressed me is that suspend and hibernate worked out of the box - first laptop I've seen do that.

I think the main problem is that the laptop is too new - the first version of the video driver was only released about 3 or 4 weeks ago, so it's not incorporated into any distributions yet. This should change, (and hopefully one of the newer drivers will resolve my screen issues).

Anyway - I'm downloading Gutsy Gibbon at the moment - I'll give that a try and let you know how that goes . . . 

Cheers
Dave Smylie
Same situation here. Its very disappointing because this 6500 is a good computer but without driver support.  I did get X to work ([instructions]("http://ubuntuforums.org/showthread.php?t=461320")), but I ended up simply removing Fiesty a few days ago because it was such a hassle. X was finally working, but text looked awful and there were so many components that had no drivers because the hardware is so new. I'll give Gutsy a try in the near future I think though. 

The new HP dv6500 series is meant to replace the very popular dv6000. In a few months the 6500 will be a popular computer so the driver support should come about soon i hope.

---

### Post by smylie on 2007-06-09
> **jollins said:**
> 
I'll give Gutsy a try in the near future I think though. 

The new HP dv6500 series is meant to replace the very popular dv6000. In a few months the 6500 will be a popular computer so the driver support should come about soon i hope.

well, just tried gutsy gibbon - same situation with the feisty install cd - it just drops you into a shell. I'm guessing the alternate install cd would let you install it, then you could mess with it and get X going.  (maybe).


I wonder if  it's worth logging
Dave Smylie

---

### Post by chewearn on 2007-06-10
hi smylie and jollins
Thanks for the answers. :popcorn:

While I hate the fact that I will have to live with Windows Vista for a while, I think it will be a good learning experience; from using Vista, and from tinkering with Linux trying to get it to work.

I have already sent out the order for the notebook; it good to know the "trouble" I am going to face when it arrives ;)

---

### Post by tower_ on 2007-07-21
just try :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-video-intel

then edit your xorg.conf and change "Driver" to "Intel"

then add 

intel_agp
agpgart

to your /etc/modules file

finaly: restart xserver or reboot

see also:
[http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html](http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html)

---

