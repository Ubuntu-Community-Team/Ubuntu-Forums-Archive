---
title: "Trying to install drivers for Nvidia RTX 2070 Super"
date: 2020-01-04
forum: Hardware
---

### Post by jukingeo on 2020-01-04
Hello All,

I am having a bitch of a time trying to install the Ubuntu drivers for a new video card I purchased.  Here is the info:

New Card:  Nvidia RTX 2070 Super

System:

Gigabyte MB with 8 meg ram Intel 6700k Quad core processor 4.0ghz running a dual boot system Windows 7 and Ubuntu 16.04

Driver:

The driver file is NVIDIA-Linux-x86_64-410.66.run

Now right off the bat I run into an issue that the .run file is not standard, however, I did some research and found it can be run in the terminal.  So the instructions were to go into the terminal and enter this info:

Cd to Downloads directory

chmod +x NVIDIA-Linux-x86_64-410.66.run

Sudo ./ NVIDIA-Linux-x86_64-410.66.run

So I run that and the program runs fine, however it then gives me an error message saying I have to close 'X'.  Again more reading and I found out that it is best to boot into terminal mode directly.  This is where things get sticky.   Since I boot right into the graphical interface, I needed to access the Grub menu.  I found out that holding the 'ESC' key on boot up does this.  Quess what?  There is NO boot to terminal prompt option.  I did notice there was a recovery mode and I entered that and from there I get a menu and from that point there is an option to select the root terminal prompt.   So I click on that and finally get to where I want to be....or so it seems.

So I enter all of the terminal information again and then I get an error message saying, "Unable to create a temporary directory".

So now I am back to square one with a low resolution display and cannot do much of anything without the drivers installed.

Any assistance would be appreciated.   Any directions need to be in EXACT step by step format with as little hoop jumping as possible.  (I despise hoop jumping as there is too much of it going on in Linux).

Thank you,

Geo

---

### Post by CatKiller on 2020-01-04
> **jukingeo said:**
> The driver file is NVIDIA-Linux-x86_64-410.66.run

Don't use that. Don't even try to use that. This isn't Windows. Those files are for package maintainers, not end users. 

Use the [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) and use your package manager to install the driver.

---

### Post by CatKiller on 2020-01-04
Also Ubuntu Studio 16.04 has technically reached its [End Of Life](https://ubuntustudio.org/2019/04/ubuntu-studio-16-04-lts-reaches-end-of-life-eol/). The parts that are shared with the main Ubuntu release will probably still work fine, but Studio-specific stuff won't get updated.

---

### Post by Autodave on 2020-01-04
I doubt that 16.04 will have the drivers available.......you may have to upgrade to 18.04 first.

---

### Post by CatKiller on 2020-01-04
> **Autodave said:**
> I doubt that 16.04 will have the drivers available.......you may have to upgrade to 18.04 first.

The ppa builds up to the 430 branch for Xenial, which does support the 2070 Super. OP will probably need the HWE stack, though; the older releases seem to get less testing, so the newer kernel would likely be helpful.

Upgrading to 18.04 would be a good idea in general, though, for the official Ubuntu Studio support, if not for the other changes from 16.04 to 18.04.

---

### Post by jukingeo on 2020-01-04
> **CatKiller said:**
> Don't use that. Don't even try to use that. This isn't Windows. Those files are for package maintainers, not end users. 

Use the [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) and use your package manager to install the driver.

Really?  Why was it on the Linux driver download page on the Nvidia site?  What file should I be using on that page?

> **Autodave said:**
> I doubt that 16.04 will have the drivers available.......you may have to upgrade to 18.04 first.

S--t.  That's not cool. Upgrade = Problems...especially since I am on dual boot.  Grub likes to mess with the boot sector and the last thing I need is to see my windows partition obliterated.

---

### Post by CatKiller on 2020-01-04
> **jukingeo said:**
> What file should I be using on that page?

You shouldn't be using any file on that page. Or any page. Downloading and running random files from random websites is a Windows thing. Using Windowsisms in Linux will bite you, hard.

Use your package manager to install software. That's what it's there for.

---

### Post by Autodave on 2020-01-04
You need to completely change the way you are thinking: Linux and Windows are miles apart in a lot of things.  The *Software *center has thousands of free programs: just about anything you can think of.  You will find programs to replace what you used in Windows.  Some work better, some not quite as good.  But, they are free and work well for 99% of users.  LibreOffice will replace MS Office, Gimp will replace Paint Shop Pro.  (I use both of these and actually prefer them over the MS ones that I have used in the past.)

Before you ever decide that you need to d-l a program, ask here if someone has a suggestion on one of the free programs already in Linux.

---

### Post by jukingeo on 2020-01-04
Hello All,

Thank you  all for assisting me in this situation, but it turned out that the video card isn't suiting my needs and thus I am going to return it to the store.  So everything goes back the way it was and thus I am not going to have to do the driver update at this time.

As for Software Center, yes, I am familiar with it, but sadly, it rarely has the most current driver posted since the RTX 2070 Super is still very new.

---

### Post by Autodave on 2020-01-04
The 430 driver is indeed there: it is what I am using for my RTX 2070: same driver that you need.

---

### Post by CatKiller on 2020-01-04
> **jukingeo said:**
> As for Software Center, yes, I am familiar with it, but sadly, it rarely has the most current driver posted since the RTX 2070 Super is still very new.
... which is why you'd add a PPA, so that your package manager knows where to find more recent packages.

---

### Post by jukingeo on 2020-01-07
> **Autodave said:**
> The 430 driver is indeed there: it is what I am using for my RTX 2070: same driver that you need.

I switched gears and I sent the RTX 2070 Super back.  What I am getting instead is a GTX Black Gaming 1080 TI.  For certain this card should have drivers that work with Ubuntu Studio 16.04, correct?   I went with the 1080 Ti because I found out that despite being older, it is still slightly better and has more Cuda Cores than the RTX 2070  Super.  But the main thing is that it has 3gig more on memory at 11gig instead of 8gig.  That might be enough to get my renders in.   Going back and looking at my renders while many of them wouldn't fit into 8gig, they were close.    I think with a bit of render optimization they should fit into the 11gig of the 1080ti.

So now I need the driver for the GTX 1080 Ti instead.

---

### Post by Autodave on 2020-01-07
Same one: the 430.xx driver.  IF there is a newer one there, choose the newer one.  440 is the latest and greatest, but not sure if it is in the repository yet or not.

---

### Post by CatKiller on 2020-01-07
> **Autodave said:**
> Same one: the 430.xx driver.  IF there is a newer one there, choose the newer one.  440 is the latest and greatest, but not sure if it is in the repository yet or not.

The Ubuntu *restricted* repository goes up to 384 for xenial. The PPA goes to 430 for xenial. Given that 440 was built for the bionic PPA on the same day as that 430 xenial build I don't think that they're planning to build a newer branch for the old release unless something fundamental changes. Maybe if there's another HWE update for xenial?

---

### Post by jukingeo on 2020-01-10
> **CatKiller said:**
> The Ubuntu *restricted* repository goes up to 384 for xenial. The PPA goes to 430 for xenial. Given that 440 was built for the bionic PPA on the same day as that 430 xenial build I don't think that they're planning to build a newer branch for the old release unless something fundamental changes. Maybe if there's another HWE update for xenial?

So this would mean 430 is the one to go with for the 1080TI?

---

### Post by CatKiller on 2020-01-10
> **jukingeo said:**
> So this would mean 430 is the one to go with for the 1080TI?

Yes. It's the newest branch that you can get for 16.04.

---

