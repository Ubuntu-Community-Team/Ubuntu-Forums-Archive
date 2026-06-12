---
title: "HP HDX 16t Laptop"
date: 2009-03-25
forum: Hardware
---

### Post by seelk on 2009-03-25
I just finished purchasing an [HDX 16t]("http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=Performance+and+entertainment&series_name=HDX16t_series") laptop (will receive it in a few weeks) and I was wondering what is the linux experience like on that system?  Are all the hardware components working?  Any challenges faced?  Thanks!

---

### Post by pmahapatra04 on 2009-05-31
I own a HP HDX 16-1140US laptop and have tried my hands on different versions of Ubuntu (and Mint). With Intrepid (8.10) and later, most of the essential components work out of the box. The sound in the kernels upto 2.6.28 (i.e. Jaunty and earlier) do not have support yet for the IDT audio hardware that came with this machine, although a patch (thanks to chris) might be incorporated in the next kernel update. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332479](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332479) for more details and alsa-base.conf fix.
It is strange that on Intrepid (8.10), even the sound (including recording) works fine, which might be accidental in the sense that the code is not meant for this hardware but "coincidentally" works. So I would go with Intrepid at the moment till a new version of kernel/alsa is released.
Other components that do not work are the finger-print reader, hard drive protection (accelerometer) and the ECE-NIR (Infrared sensor). I can manage my daily computing work without the need for these bells and whistles anyway :)

---

### Post by seelk on 2009-06-01
> **pmahapatra04 said:**
> I own a HP HDX 16-1140US laptop and have tried my hands on different versions of Ubuntu (and Mint). With Intrepid (8.10) and later, most of the essential components work out of the box. The sound in the kernels upto 2.6.28 (i.e. Jaunty and earlier) do not have support yet for the IDT audio hardware that came with this machine, although a patch (thanks to chris) might be incorporated in the next kernel update. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332479](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332479) for more details and alsa-base.conf fix.
It is strange that on Intrepid (8.10), even the sound (including recording) works fine, which might be accidental in the sense that the code is not meant for this hardware but "coincidentally" works. So I would go with Intrepid at the moment till a new version of kernel/alsa is released.
Other components that do not work are the finger-print reader, hard drive protection (accelerometer) and the ECE-NIR (Infrared sensor). I can manage my daily computing work without the need for these bells and whistles anyway :)

Thanks a lot for your response.  I now have the laptop but have not installed Ubuntu 9.04 simply because I get no sound from the Live CD and haven't taken the chance to research the issue.  I did notice the sound in 8.10 works but I would like to use the latest and greatest so I may go with the patch for 9.04.

Question, how did you go by installing Ubuntu?  Did you partition the drive and are now dual-booting?  Or did you completely replaced the two partitions?  The reason I ask is some people have mentioned that installing a new OS could lead to the recovery partition not being recognized by the boot process even though the partition is intact.  Maybe an MBR issue.  If you can shed some light here that will be great.  Thanks again!

---

### Post by pmahapatra04 on 2009-06-17
No problem seelk. Glad I cud help.

I did fresh partitioning of the whole hard disk. I have had lot of experience regarding partitioning and installations on my earlier machines, so to be honest I don't have slightest hesitation removing the "factory junk". I did make the recovery dvd though (in fact that was the first thing I did after the first boot), in case something goes wrong hardware-wise and I have to "unvoid" the warranty. I removed all the partitions and freshly started with 3 primary partitions (in case I decide to go with 3 different OS) and 1 large logical partion (for data). If you plan to go with the new ext4 file system (which I do not suggest at this point), you would have to install ubuntu root in a logical partion.

If I remember correctly, HP keeps the partioning in a wierd order which includes 3 separate partitions for Vista, MediaSmart and Recovery. Just creating a logical drive is a headache, becoz one has to resize the partition and fit in the new one. Creating another partion for linux while keeping rescue & mediasmart partitions intact, would be a nightmare in my opinion. Additionally, just like you said, I think rearranging or adding or messing with the partitions might lead to the recovery partition being not recognized.

If you're frenzy about taking the risk of not being able to recover the data, I would suggest not messing with the original layout. If not, just backup your relevant data and dive in ;) and start afresh. A point to remember is while making new partitions during Ubuntu fresh install, create a couple of primary partitions, to have the flexibility to add windows XP and/or Vista or maybe another linux distro in future.

---

### Post by knife on 2009-06-17
I've got an HDX16t (first relase), and I've finally got it to where I'm happy with it. 

On the partition question, I dumped the recover partition (you don't need it once you make the recovery DVDs), and I let Jaunty shrink the Vista partition.  The Vista disk manager would only let me shrink my 320 GB partition down to 160 or so, even on a fresh install of Vista that only used 25GB (only!).  I told the Jaunty installer to shrink the Vista partition to 60GB, and I can still boot Vista no problem (I think it did some disk integrity checking on the first reboot after the resize, but it ultimately booted up and runs fine).  I've got Jaunty and my swap drive on the remainder of the drive and all is good.

On the hardware, here is what I did:

I compiled and installed alsa 1.0.20, and that fixed almost all my sound issues (recording, mute LED, mismatch between hardware volume controls and software volume), even without upgrading the kernel.  I also upgraded my kernel to 2.6.30, which seems to have smoothed a number of stability problems I had been having.

The ENE-CIR remote will work, but you have to undo whatever the vista driver does to the IR chip that makes it not work under linux. There are two ways reported to work.  1. boot into Vista, go into the hardware manager, and uninstall the ENE CIR driver.  2. Pull the battery out of the computer, wait a minute or so, and put it back in.  I did #1, and now the remote works mostly fine except for a couple of the buttons (most notably the play/pause button).  With #2, it is likely that if you boot into Vista again, then the ENE CIR driver will probably redo whatever it does that makes the remote nonfunctional under linux, so you may have to pull the batter again after every time you boot to Vista.  

For Suspend to RAM to work, you need the latest bios (version F.23A) from HP.  On a brand-new system, you may already have it.

Other things that don't work (yet):

1. Fingerprint reader (it's on the todo list for the fprint project).

2. DVB-T: mine doesn't work, though I think different hardware shipped with different systems (maybe for different markets), and I understand that some people have the DVB-T working in their HDX16's.

3. So far, the bass/treble controls for the sound don't work - maybe Chris will get that working next.

4. I have a strange issue on shutdown where the screen goes all pink, and the system sometimes hangs without shuttinng off, and I have to hold the power key to power it down.  It's intermittent, but it seems to be related to the wireless (it only seems to hang when I'm actually connected to an access point).

---

### Post by oneindelijk on 2010-06-22
Hi, 

I have another HP Notebook but it also has a ene cir driver (I downloaded the vista driver from the HP website for my specific model).
I tried the trick with removing my battery, but I'm not even sure where to test or detect for the driver in Ubuntu.
I've installed the infrared remote control tool, but an autodetect shows my webcam, my AT Keyboard and the sleep button as possible remote receivers.

When I enter ```
lspnp
```I get command not found.
These commands also give nothing as result:
```
lspci | grep cir
lsusb | grep cir
```

---

