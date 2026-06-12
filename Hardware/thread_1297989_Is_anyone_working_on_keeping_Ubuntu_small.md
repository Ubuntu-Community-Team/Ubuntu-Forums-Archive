---
title: "Is anyone working on keeping Ubuntu small???"
date: 2009-10-22
forum: Hardware
---

### Post by wirelessguy on 2009-10-22
Hi,
 
I'm a pretty happy user of Ubuntu (Jaunty) but I was curious if there are any existing projects to keep Ubuntu from getting to bloated for simple netbook use.
 
(I see no real reason why a base OS with web capability and email should have to be larger than 1 GB or so on a netbook).
 
Some quick background. I was an avid user of my Nokia N800 but traded up for a Dell Mini 9 netbook running Ubuntu. The orig shipping copy of Ubuntu was nuts. Dell must have been smoking something to sell a 4GB SSD with less than 200mb free.
 
I upgraded to 9.04 remix and instantly gained close to a gig of space. I've only added on a few apps I like (thunderbird, pidgin ...) and the disk space has been somewhat managable. The only thing I dislike is the fact that Evolution Mail is somehow tied to the OS and can't be uninstalled.
 
I've been thinking about the new Moblin 2.0 but I'm a bit hesitant as it took me some time getting the ubuntu script worked out to get Blutooth passthrough working with my cell phone. I hope mobiln masks the OS but still allows for shell access.
 
I don't intend to use my netbook as a developers workstation I want it to be an easy web terminal.
 
 
Any thoughts, experiences or suggestions on the subject would be greatly appreciated.
 
~ WG.

---

### Post by Giblet5 on 2009-10-22
I'm sure that it's a consideration, but it's probably a low priority.

Disk is cheap - $0.08/gig is easy to find and 8 cents is only two or three day's pay in the US, after taxes.

---

### Post by John Bean on 2009-10-22
> **Giblet5 said:**
> Disk is cheap - $0.08/gig is easy to find
Not in SSD form it isn't... which is what most of the smallest netbooks use.

---

### Post by IcarusR on 2009-10-22
> The only thing I dislike is the fact that Evolution Mail is somehow tied to the OS and can't be uninstalled

Strange, I am running 9.04 NRM live cd on my eeepc 901 & have just uninstalled evolution successfully.

I have uninstalled evolution from all my hdd installs for sometime in favour of thunderbird.

Also I believe Pidgin is installed by default.

---

### Post by Giblet5 on 2009-10-22
> **John Bean said:**
> Not in SSD form it isn't... which is what most of the smallest netbooks use.

That SSD can be ripped out of there, tossed onto the pile of forgotten 720KB floppies behind the monitor, and replaced with a 500G hard drive. Cheap.

Just sayin' that it's a matter of priorities.

SSD is yet another very popular bad idea, IMO. Flash dies quickly. VERY quickly. Netbook owners will discover this in 3.....2...

---

### Post by lukeiamyourfather on 2009-10-22
While you can use Ubuntu on a netbook with a 4GB SSD, that's not really what the target user is. Most users of Ubuntu probably have at least a 40GB (if not 500GB+) disk drive so a 4GB operating system is not that big of a deal. Ubuntu is also a fully featured operating system with many applications and features (that take up space). Moblin and other netbook operating systems are not as flexible and robust because they're designed to take up very little disk space and resources while performing only a few tasks (playing music, browsing the web, simple office tasks). In other words, I'm sure size is a concern for Ubuntu but not on the level you're looking for. Cheers!

---

### Post by Mighty_Joe on 2009-10-22
> **Giblet5 said:**
> SSD is yet another very popular bad idea, IMO. Flash dies quickly. VERY quickly.

[no it doesn't]("http://www.storagesearch.com/ssdmyths-endurance.html")

---

### Post by John Bean on 2009-10-22
> **Mighty_Joe said:**
> [no it doesn't]("http://www.storagesearch.com/ssdmyths-endurance.html")

Quite. Saved me the effort of responding ;-)

Too many people equate "SSD" with "flash card" (as used in numerous consumer devices) and jump to completely wrong conclusions about life expectation. I've used SSDs for years in harsh, 24/7 environments that would kill a laptop hard disk in weeks. And  I killed quite a few during extended real-world trials...

---

### Post by wirelessguy on 2009-10-22
Thanks for all the replies.

While doing some research I found out that uninstalling evolution does not uninstall netbook-remix and render your PC useless. It uninstalls some sort of meta files that say it's a "standard netbook remix" install. Wish I would have known that sooner. I reclaimed a lot of space today.  :-)

I'm curious about this whole SSD thing though.
First let me say that I don't care how cheap HD space is huge base OS is simply wasteful.

My Mini 9 has the SD slot for added storage and no shortage of USB ports, so what I'd really like is a small and fast SSD (and as others pointed out those guys aren't cheap!).

I'm not aware of being able to swap out the mini 9 SSD for a real HD in this machine. If this is the case I'd be curious who's done this successfully so please feel free to post some URLs for that.

Thanks.
- WG

---

### Post by lukeiamyourfather on 2009-10-22
> **wirelessguy said:**
> 
First let me say that I don't care how cheap HD space is huge base OS is simply wasteful.


You're missing the point. Its not a huge operating system relatively speaking (I'd say its on the smaller side of things), you say its not because you have only 4GB of storage. Use something intended to be minimalistic, not a fully featured distribution like Ubuntu if you're concerned about storage space.

That's like driving a truck and complaining about the gas mileage and how it won't fit in your small garage. The solution is get a small car or motorcycle that's more fuel efficient and will fit in the garage. Its not the trucks fault, its the driver who picked the wrong car.

Ubuntu has more features, which means its bigger. Moblin, Chrome OS, and the like have relatively few features and are smaller to fit on netbook storage devices. Sure you can use Ubuntu but don't try to force Ubuntu into a minimalistic operating system when its not and the majority of users wouldn't want that anyway.

If you're compelled to use Ubuntu anyway then maybe try Xubuntu or uninstall whatever you don't need to free up some space (games, GIMP, extra wallpapers and media, etc.). Cheers!

---

### Post by wirelessguy on 2009-10-23
I appreciate your comments about Ubuntu's size since I was unaware that it was meant to be a larger (full featured) distro. I had assumed that since it shipped with my netbook, and the 4GB was the base unit, that it was intended to run on such a device.

However, I'm not new to the concept of installing unix OSs on machines and I still hold that 4gb is A LOT of room. I remeber installing FreeBSD out of 40 floppies back in college. I've also worked with just about every copy of redhat (commercial unix OSs) and even embedded linux.

My point is that until the last few years OS shipped on CDs not DVDs and their size was much smaller. Atom processor netbooks are not the platform for high performance gaming or video acceleration etc.. They also don't really need to be running things like web servers, email servers, etc...  (and again, that's not to say I haven't played with a 4MB embedded linux system that HAS a web server). So why shouldn't I expect my netbooks software to be as compact as the hardware? Email, web browser, IM, word processing and perhaps some music.

Today, we see BIG IRON computers starting to use SSD and RAM to cache the entire OS as well as databases to avoid disk swapping. Thus I think it makes very good sense to try and keep the OS at a manageable level so that this remains a possibility.

---

### Post by snowpine on 2009-10-23
Hi there, Ubuntu is not bloated... a base install ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) uses less than 500mb disk space, and a full install (with office suite, games, multimedia, graphics, etc.) uses less than 4gb (8gb recommended). (As a comparison, Windows 7 requires 16gb, I believe, and that's without an office suite or any other applications.)

Sorry, but 4gb is pathetically small for a primary storage device in this day and age (1TB hard drives are less than $100). Many netbooks have 160gb drives, and that would have been a better option if you wanted lots of storage. Dell has been criticized many times on these forums for offering the useless 4gb drive.

I personally have a Dell Mini with an 8gb drive. I did a base install (Ubuntu, Debian, and currently Arch) and installed only what I needed, and managed to keep the system between 1 and 2gb. If that's still too bloated for you, I recommend either Puppy or SliTaz, either of which is less than 100mb.

The bottom line is, if you let someone else choose what software goes on your system, there will always be* something* you don't need that makes it seem bloated. Do a minimal install, and then add what you need, and you'll always get exactly what you want. :)

---

### Post by IcarusR on 2009-10-23
You could alway build your own tailor made distro from Linux From Scratch, & learn a lot about Linux internals to-boot.
Then you can have the exact programs you want & no extra ones !!

[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

Not sure how small an install you could make this way, but would be an interesting project.

---

