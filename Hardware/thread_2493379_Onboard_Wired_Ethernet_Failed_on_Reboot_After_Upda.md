---
title: "Onboard Wired Ethernet Failed on Reboot After Update"
date: 2023-12-13
forum: Hardware
---

### Post by sdsurfer on 2023-12-13
MSI B560M Pro-VDH
Intel 17-11700K
64GB T-Force 3200 mhz RAM
Ubuntu 20.04 (and my next task was to update that, too)

**The problem: **had a frustrating day yesterday getting a VPS up and running/sites moved, all the while Ubuntu nagging me for a reboot, finally got it done WOO HOO YAY tequila shots for all . . . . . rebooted and no Internet.

Please understand it will be difficult to post output of commands, I'm on my  Laptop posting this, the machine above is not getting anything from the Ethernet. I'll do my best to type out  what you might need to assist. My next step after a nap is to look up my old posts and see what I've forgotten. :-P

I had previously downloaded the Realtek RTL 8125 driver, set it up with ifupdown, the interface was identified as enp3s0. Now any command line queries I do to display the Ethernet interface respond with "sorry man, that doesn't exist, sure you didn't dream it?"

```

sudo ifup enp3s0
[message header]
Cannot find device "enp3s0"
Error getting hardware address for "enp3s0": no such device

```

My thought is if the onboard Ethernet is still good and I can get the name, I could make changes in Network Manager or re-install it.

It still shows up in the GUI Networking connections as Onboard MSI Ethernet -> ifupdown(enp3s0), but I believe it's just not doing anything. It appears all the info is missing (IP addresses, etc.) and all settings in this dialogue are default (connect automatically, all users may connect, MTU auto, etc.) I don't recall doing any special tweaks here.

I believe it's related to the kernel during update and the hardware is probably fine, question 1 is **what could I do to make sure the hardware is good?**

```
sudo lshw -short | grep network
/0/100/1c      [BLANK COLUMN]     **[COLOR=#ff0000]network     [/COLOR]**RTL8125 2.5GbE Controller
```

A few things I don't know about this output:
 - Note the blank column, NO NAME. Code in other posts I've read tell me there's supposed to be a device name there.
 - Is the red significant? That's how it outputs,
 - By the word "Controller," this is software, correct? Doesn't tell me if the hardware is good.

 The second command I "sorta" understand:
```

sudo lshw -C network
*- network UNCLAIMED
    description: Ethernet Controller
    product: RTL8125 2.5GbE Controller
    physical id: 0
    version: 04
    width: 64 bits
    clock 33mhz
    capabilities: pm msi pciexpress msix bus_master cap_list
    configuration: latency=0
    resources: ioport:3000(size-256) memory:a3200000-a320ffff memory:a3210000-a3213fff

```
[SIZE=1][I]
Yes I typed that out lol
[/I][/SIZE]
Again, note the missing ```
logical_name
``` entry, which should be there: ```
logical_name: enp3s0
``` I think I know what unclaimed is - the hardware is no longer bound to anything so it's basically a free agent who works for no one. :-D 

The other thing I don't know is if this is just spec coming from the driver or if it's actually reading the hardware, in which case I would know the onboard Ethernet has not failed.

Reading tons of posts, I also downloaded and installed r8168-8.052.01, which may or may not have been a good idea. It doesn't appear to have applied anyway per the output above. 

I know this is lousy information to go on, not seeking a one off solution, but if anyone could give me pointers on where to look, I'd be very grateful. Next up I'm going to poke around in the bios again and see if I have any old NIC's laying around. Thank you in advance!


Edit: Just checked the bios, again it could be just informational,  there's no tests I cam perform, but **maybe** I can enter the mac  address and get something:
- Driver: RealTek UEFI UNDI Dr
- Version: 2.052
- Release Date: 2019/12/04
- Device Name: RealTek PCI 2.56 BE
- MAC Address (not sure if I shouldn't post it but there's an address here)

---

### Post by #&amp;thj^% on 2023-12-13
Just a thought, is this installed?
```
apt policy build-essential
build-essential:
  Installed: 12.10ubuntu1
  Candidate: 12.10ubuntu1
  Version table:
 *** 12.10ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Yellow Pasque on 2023-12-13
Try booting into the previous kernel version. If you didn't install r8125 with dkms method (or didn't have prerequisite packages like dkms,build-essential linux-headers, etc.), it doesn't get automatically rebuilt when you install a new kernel version.

PPA is probably the easiest way to install: [https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended](https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended)

---

### Post by sdsurfer on 2023-12-13
Thank you for the help. Sorry, I have the lid off and am "wrenching." I attempted to do a boot into both Ubuntu and Unity from USB and once it gets past the selection screen it throws errors and just stops, black screen. I was thinking if I get to boot from USB I could see if the hardware is functioning. My only complaint (aside from the Ethernet now) is I've always had issues with the USB ports, sometimes devices work fine, other times it comes and goes, but that's another topic. 

> **1fallen said:**
> Just a thought, is this installed?
```
apt policy build-essential
```

It sounds familiar. :-D I will check once it's running. 

> **Yellow Pasque said:**
> Try booting into the previous kernel version. ..... [https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended](https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended)

Trying not to make the posts long, that's not only the original way I [resolved these issues]("https://ubuntuforums.org/showthread.php?t=2477541&page=2"), thanks to you (haha, found my thread) it's the same one I use when the Ethernet drops off. Not working right now though. :-(

---

### Post by sdsurfer on 2023-12-13
Hey all, reporting back from a live boot of Ubuntu 23.10 from a USB and can report the hardware is fine with the below observations. Also tested Unity, which I kinda like, but Gnome was far better at giving me details. Both working as (better) than expected.

In Unity it was just giving me "Wired Connection" and all the edit settings appeared to be blank or default. No ifupdown(interface.)

In Ubuntu it's the same, plus giving a path from the desktop icon to Wired->Wired Settings, in there I found IP->my IP Hardware Address, V6 IP, default route, and local DNS address. Maybe now is the time to upgrade, It's almost embarrassing how well it works lol . . . . . back to boot from disk. 


> **1fallen said:**
> Just a thought, is this installed?
```
apt policy build-essential
```

From this demo looks like a nope. Will check again from disk/20.04.
```

sudo apt policy build-essential
build-essential:
  Installed: (none)
  Candidate: 12.10ubuntu1
  Version table:
     12.10ubuntu1 500
        500 cdrom://Ubuntu 23.10.1 _Mantic Minotaur_ - Release amd64 (20231016.1) mantic/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu mantic/main amd64 Packages



```

<totallyofftopic>
Both installs threw System Error has occurred," Unity 3 or 4 as I recall and at least 10 in the Ubuntu install.
It forced me to address the flaky USB setup I have and make sure 3.+ ports are more available, front 5.25 panel coming soon so I can supply BOTH USB 2 and 3 from the front of the computer.
</totallyofftopic>

---

### Post by sdsurfer on 2023-12-13
```

sudo apt policy build-essential
build-essential:
    Installed:    12.8ubuntu.1
    Candidate: 12.8ubuntu.1
    Version Table:
  *** 12.8ubuntu1.1 500
             500 http://us.archive.ubuntu *(etc., remember I'm transcribing lol)*
            100 /var/lib/dpkg/status
       12.ubuntu1 500
       500 http:// .... (archive)

```
```

sudo uname -r
5.4.0-169-generic

```

---

### Post by sdsurfer on 2023-12-14
Good morning all. My last attempt was to boot off the original 20.04 DVD I used for upgrade from 17.04. Unlike the USB installs above, once the demo loads there is no internet, but detects the device with the usual commands. It does not detect any connection (i.e., not in the top menu, in Settings it shows nothing under Network.) A device "edns0" shows up, but any efforts to modify/install it result in "device not found." Ran a few commands, as above detects the device but shows only lo as the interface.

I'm two days behind on all my projects and am burned out from searching and searching for solutions and gettin' nuttin'. At this point I may as well nuke it and upgrade to 23.10, I know it's not an LTS but the Ethernet connects fine from the demo (hopefully . . . not just a demo! :-) )

I've been running Unity from this laptop for a week or so (and I like it so far, compared to Gnome,) no apparent problems so I guess I have to go for it. I was hoping to solve this one just so I'd know, but my head is starting to hurt LOL . . . sometimes the answer is just . . . . 42.

Hopefully this goes smoothly as it did for this Lappie, will report back when done.

---

### Post by Yellow Pasque on 2023-12-14
I got lost really quick in this thread with all the changes. Did you ever boot into the previous kernel to see if it worked? And I was going to ask what happens when you run:
```
sudo modprobe -v r8125
```
But I guess it's late for that now?

---

### Post by sdsurfer on 2023-12-14
> **Yellow Pasque said:**
> I got lost really quick in this thread with all the changes.

You think ***you're*** lost? You have no clue hahahaha :-D 

Summary:
- Lost Ethernet connection
- Various suggestions including a few dozen outside this thread, none working
- Booted from Unity 23.10 USB, Ethernet works
- Booted from Ubuntu 22.04 USB, Ethernet works
- Booted from 20.04 DVD, internet does **NOT** work
- From the first two as mentioned [above, here,]("https://ubuntuforums.org/showthread.php?t=2493379&p=14169173#post14169173") determined onboard Ethernet is fine. The interface has just gone away and Ubuntu no longer recognizes the onboard ethernet
- Realization my life has been on hold for two days and nuked it by installing Unity 23.10 (not an LTS) ***<-- you are here*** :-D

> Did you ever boot into the previous kernel to see if it worked?
Pretty sure (I could be wrong) it was removed by the Ubuntu updater, and that's where the problems began.

 > And I was going to ask what happens when you run:
```
sudo modprobe -v r8125
```
But I guess it's late for that now?

No it's not too late:
- one 500MB for Windows 7 which I never use and am planning on reformatting because last attempt to log in to it it was broken. The problem here is that's where my grub bootloader is and I need to move it.
- One 1TB that originally was intended for OS, containing Ubuntu 20.04
- One 2TB intended for data only that repartitioned and installed Unity on.
[B]
The good news:[/B] I installed Unity 32.10 to the 2TB drive, so I can now dual boot into either Unity or Ubuntu 20.04. I did this because I couldn't let go of the [SIZE=4]***WHYYYYYY?***[/SIZE] :-D I can continue debugging it.

I may reformat the 1.0 TB and change it's role to a data-only drive after the dust settles.
[B]
The bad news:[/B] To use Unity I have an unexpected housekeeping task thrust on me, all my apps and configs over the years are in the 22.04 partition and have to figure out how to migrate them or reinstall. Probably good time to do that as I have a lot of unused junk in there. 

I'm now hung up on the first software update in Unity which is taking forever (it was supposed to do that on install) and my first stop after getting it sorta working is to move grub to a different partition and re-assign startup disk in bios. So this is the third day :-D

---

### Post by sdsurfer on 2023-12-14
What's it been, 3 hours? Unity installed fine and is running on this lappie. In the MSI, hour after hour, black screen, finaly got into the GUI, tried to look around and got various errors opening the partitions, now all of them are gone in Nautilus LOL . . . .  running incredibly slow for a machine with these resources, thank god it's on it's own. Network is still there though LOL . . . there's really a lot of worms in this can, someone get me a bucket!

---

### Post by sdsurfer on 2023-12-14
> **Yellow Pasque said:**
> code]sudo modprobe -v r8125[/code]
But I guess it's late for that now?

```

sudo modprobe -v r8125
insmod /lib/modules/5.4.0-169-generic/updates/dkms/r8125.ko
modprobe: ERROR could not insert 'r1825': Exec format error

```

Still sitting here, [Unity is a fail on this computer.]("https://ubuntuforums.org/showthread.php?t=2493422&p=14169297") I don't get it, installed fine on this lappie. Tried to install Ubuntu 23.10 and it fails with "no valid operating systems found" and there is no "try something else" option as I've read there should be. Downloading 22.04 and will try to install.

---

### Post by sdsurfer on 2023-12-14
> **Yellow Pasque said:**
> Try booting into the previous kernel version.

ERMIGIRD! THIS WORKED! Where can I send a liter of your favorite "beverage" to? -----> \_/

However it took this long to get to it because as I mentioned, the latest update removed it. I had to get and install -167, my current is -169. I'd also deleted my Ethernet connection, it auto set up "wired connection 1" 

What we learned:
**1.** Never give up. [SIZE=1]*(Wife has been commenting for the last 3 days I should just throw it out the window and buy a new Dell. While that was tempting, no.)*[/SIZE]
**2.** For all I know, I don't know jack.
**3.** When the Ethernet fails, look to the kernel first before spending three days chasing your tail.
4. Let go of Unity, it really doesn't work on this computer.
**5.** For everything else, see #1.

In my post [from over a year ago]("https://ubuntuforums.org/showthread.php?t=2477541&page=2&p=14113434#post14113434") I said "off to install 22.04" and well . . . :redface: life happens. Off to do that now.

---

### Post by Yellow Pasque on 2023-12-14
You may want to try this if you boot into -169 kernel.
```
sudo dkms autoinstall
```

I'm glad that the previous kernel worked, though I'm surprised that Ubuntu removed it. I would think they would at least keep one previous version around. Oh well, I guess that's better than the days when Ubuntu left every kernel on the system and filled up peoples' boot partitions.

---

### Post by sdsurfer on 2023-12-15
Oh this is getting better, on day 5 now LOL

- Got in to 22.04 using kernel 5.15.0-19-generic, of course no internet.
- Booted with 5.4.0-167-generic and attempted to update it so it would properly load r8125 [as in this post]("https://askubuntu.com/questions/1423298/ethernet-controller-realtek-r8125-not-working-with-kernel-5-15").
- **Boot partition ran out of space, process stopped.** Cleared some space, moved two .old kernels to a backup drive.
- Reboot, attempted to go into recovery mode with 5.4.0-167-generic,
-  Booted with 5.15.0-19-generic in recovery mode, rebuilt  5.4.0-167-generic initramfs. Tried to enable networking to finish  updating r8125, of course network won't doesn't work.
- Attempts to boot with 5.4.0-167-generic in recovery mode
```

Kernel panic - not syncing: VFS: unable to mount root fs on unknown block(o,0)

```
Can't get to recovery mode with 5.4.0-167-generic.
- Attempt to reboot in normal mode with 5.4.0-167-generic, hangs on loading ramdisk (likely for reason above.)

So, I'm back where I started, 5.15.0-19-generic with no internet, can't get to 5.4.0-167-generic that has internet.

---

### Post by sdsurfer on 2023-12-16
Day 6.

Nothing worked, kept getting "missing operating system."
sda was a Windows drive, I never used Windows but that's where it wanted to put the bootloader/grub. Fresh install of 22.04 from USB drive on sda, reformatted it (default, ext4,) install went fine, reboot . . . 

"Missing operating system."

Tried switching MSI Bios->advanced->BIOS mode to UEFI, it keeps switching back to CSM: "Onboard graphics is not supported in CSM/UEFI mode, will be changed to UEFI."**** I did that, on reboot switches back.

I'm 6 days in and still don't have this thing running. I have TWO 22.04 installs that won't boot. Grub doesn't load. I'm literally sick from searching for solutions, any ideas?

****** Edit:** I don't need the onboard graphics chip, see thread intro, using a card.

**Edit #2: **in BIOS BBS settings, I see the primary drive sda was set to disabled (!!!!!!!!) I know I didn't do that. When enabling it it says "ubuntu: [disk model/id]

Still says missing operating system. What the hell.

**Edit #3:** After seeing "Missing Operating System" again I walked away to avoid throwing stuff, for whatever reason that always winds up costing me money. :-D Came back 10 minutes later, Ubuntu is booting but veeeeery slowly. My goal is to get the original install on the faster disk fixed, it contains all my apps, etc. (No data, that's a different disk.) 

I hope the experts here are getting a decent laugh over this thread, at least that's something! :-D

---

### Post by mnymonyker on 2023-12-17
Check if you have rtl8125 drivers in /lib/firmware/rtl-nic/ . If not, then

download [rtl8125a-3.fw]("https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_nic/rtl8125a-3.fw"),  [rtl8125b-1.fw]("https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_nic/rtl8125b-1.fw"), [rtl8125b-2.fw]("https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_nic/rtl8125b-2.fw") here - [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_nic/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_nic/), then

```
sudo cp ~/Downloads/{rtl8125a-3.fw, rtl8125b-1.fw, rtl8125b-2.fw} /lib/firmware/rtl-nic/
sudo update-initramfs -u
```

---

### Post by mnymonyker on 2023-12-17
Oh, I'm having trouble following the thread. I guess my plan is flawed as you can't download onto an OS without working internet! duh.

But yah, get those files and get them copied to /lib/firmware/rtl-nic/ if you can, then update-initramfs

One other comment, your BIOS may be switching off UEFI because the disk is not a gpt partition table. You have to create the partition table before you format the disk and create partitions.

With gparted you would delete all partitions on the disk, then click "Device>Create_Partition_Table..." and change it from msdos to gpt.

If you don't have it, the [live gparted .iso]("https://gparted.org/download.php") is handy, and you can add it to a [Ventoy USB]("https://www.ventoy.net/en/index.html") too!!

---

### Post by sdsurfer on 2023-12-18
Day 8. Almost there.

@Yellow Pasque, @mnymonyker and @1fallen thanks for  taking the time to look at this, I know how difficult it is to extract  the info you need to help. One thing has led to another and pushed me  further down the rabbit hole from no Internet to no working system to  OMG now not even the monitor is working LOL . . . . as for this Ethernet  issue, going to mark it resolved with the following.

T**he bottom line:**  My MSI wouldn't "stay" in UEFI mode, kept switching it to CSM (BIOS)  mode, and while that should have been fine I'm thinking when I tried to  reinstall from disk it kept borking things up. Why would it switch?

Set  UEFI in BIOS, reboot. Switched back. Over and over until I was staring  at the black screen some text flashed for maybe 1/4 second. It took me  three reboots watching the screen to put half the sentence together,  "this graphics card . . . . . switching to CSM."

This Nvidia card, a GeForce8400,  has always served me well but has presented so many conflicts in  hardware over the years that it is time for it to go. Pulled the card,  plugged monitors into HDMI and VGA, stays in UEFI mode, system installed just fine and now  have a WORKING 22.04 OS. 

I  would not be the least bit surprised  that my Ethernet issues were somehow tied to this card. Way beyond that  though, system is running fine.

**How did I get here?**
- around 2017 I installed 17.04. At that time I had an old 2 core MSI and there were no conflicts with the card. It was, like, bleeding edge man.
- Around 2021 updated to 20.04. I'm guessing because the card was already present, the update just went with it.
- Last year pulled the old MOBO and dropped the disk in it. I was amazed at how everything just worked. 
- Then the latest update came. Most people would just say "the update broke my system" but I can clearly see "I was doing my damnest to break Ubuntu and succeeded!"

New problem: I'm afraid to install anything because I might break it. :-P

---

