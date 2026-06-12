---
title: "Intrepid randomlly locks up"
date: 2008-11-03
forum: General Help
---

### Post by Phantom784 on 2008-11-03
I'm having issues with my Intrepid install randomly locking up.  Usually, this happens when I'm away from the computer and the screen saver is activated, although once it was while reading a page on Firefox. Ctrl+Alt+BackSpace, Ctrl+Alt+Del, and Alt+SysReq+REISUB all have no effect, leading me to think the issue is in the kernel. I set up a fully encrypted system, and I also have a TrueCrypt volume being mounted by PAM mount. This is the first time I've used either of these, so is it possible they have to do with the problem?

My system is a Dell Inspirion 1720.
Processor: Intel Core 2 Duo T9300 @ 2.50GHz
Memory: 3GiB of DDR2, 512MB Video Memory
Video Card:  nVidia Corporation GeForce 8600M GT (using proprietary driver version 177)
Storage: SAMSUNG HM320JI - 298.02 Gigabyte Hard Drive (SATA connection)
Optical Drive: TSSTcorp DVD+/-RW TS-L632H
Ethernet: Broadcom BCM4401-B0 100Base-TX
Wireless: Intel Corporation PRO/Wireless 4965
Bluetooth: Broadcom BCM2045
Battery: DELL GK47984, 52000mWh capacity

---

### Post by geedew on 2008-11-03
I am noticing the same thing.  No keystrokes are registering, and any and all objects on the screen are frozen, it's almost as if we are entering bsod territory!  Ick.

But on mine, I have noticed one thing, it's occuring mostly during screen loads of some sort.  So far it has happened to me when:
Coming out of Suspend, screen loads and then freezes, 
Opening up a new Tab in FF3, 
Using alt+tab.

So it definitely seems kernel related and it definitely random in my un-extensive knowledge of the OS.  

Intrepid Ibex 64-bit upgraded from Hardy 64-bit
Lenovo X61 tablet full install.
xorg.conf IS being used, because I love my pen and I will not let HAL take it away from me!

I'm going to figure out how to get some sort of mem dump or something, to see if I can track it down.

---

### Post by Phantom784 on 2008-11-03
I remembered having a similar problem back on Feisty, and that was caused by the Nvidia driver.  Therefore, I uninstalled the proprietary driver, but I still had it crash after a few hours of use, leading me to believe this problem isn't related to those drivers.  I'm using the 32 bit version, and since geedew is having the same problem on the 64bit version, this isn't just a problem on one architecture.

---

### Post by crunchyblack on 2008-11-04
This exact same garbage was happening with hardy for many MANY people. there was multiple 40+ page threads regarding it which ruled out video card drivers, ethernet / wifi cards and many other factors.  

This forced me to use gutsy until intrepid came out which I thought would fix it, and it didn't, so now i have to format and lose all my **** once again.  I'm about to use another distro.

---

### Post by geedew on 2008-11-05
Well, I didn't have this issue in Hardy.
I am VERY inclined to believe that this has more to do with flash than anything.... I will report back if I can figure anything else out.

---

### Post by adamdddave on 2008-11-06
I've got the same thing happening to me. Had the same problem in Hardy. The problem only started sometime around 3 weeks before Intrepid was released. I did a fresh install and still have the problems. I've noticed that the hard drive light is solidly on for the period of time when the computer is locked, then it all goes away after about 20-30 seconds. Something makes me think it's firefox 3, but that's just me.

---

### Post by haylocki on 2008-11-12
Hi,
    just a shot in the dark, but I have been having this problem on my computer after upgrading to Intrepid.

I ran the System monitor (System -> Administration -> System Monitor)

and clicked on the "Resources" tab. There I noticed I had 0 MB of swap memory enabled :shock:

So I enabled swap memory, and the problem seems to have gone away.

Maybe this will be the case with someone else.

Cheers, Ian

---

### Post by mohtasham1983 on 2008-11-17
I'm having this problem with one of my laptop since I installed several updates a few days ago. My other laptop works fine, even after installing those updates.

My laptop that works fine is a Dell Latitude D505 and the one that crashes is a Dell Latitude D630. They both use Intel graphic cards. The only difference between them is that my D630 laptop has a broadcom wireless card, while the other one has an intel one. 

I guess it's a problem with Broadcom drivers.

---

### Post by Joe on 2008-11-19
> **mohtasham1983 said:**
> I'm having this problem with one of my laptop since I installed several updates a few days ago. My other laptop works fine, even after installing those updates.

My laptop that works fine is a Dell Latitude D505 and the one that crashes is a Dell Latitude D630. They both use Intel graphic cards. The only difference between them is that my D630 laptop has a broadcom wireless card, while the other one has an intel one. 

I guess it's a problem with Broadcom drivers.

Same thing started happening to me since those recent updates as well but I'm not using a broadcom card.

---

### Post by Phantom784 on 2008-11-20
Well, I don't have a broadcom card and I have swap enabled, so those two things probably aren't the cause of my problems.  And it's not a recent update, at least not for me, since it's been going on for a while.  I also tried booting with "noapic", because another post somewhere said that could help, but it didn't.

---

### Post by Phantom784 on 2008-12-02
I just wanted to bump this and say I'm still having this issue, even after the latest kernel update.  I also found a post from Hardy about the same issue.  Somebody narrowed down their issue to the wireless drivers, which are the same as mine (although others having the issue had different wireless).  Assuming the wireless is my problem (the only way to really check is to use the serial port to watch console output on a different system, and my laptop doesn't have a serial port), is there a place where I can find another drive to use for wireless?  (I'd rather not resort to NDISwrapper if possible.)  One weird thing though is that I had Hardy on the same laptop with no issues, where the other people were having the problem.

Here's the thread I found: [http://ph.ubuntuforums.com/showthread.php?t=832383](http://ph.ubuntuforums.com/showthread.php?t=832383)

---

### Post by jdorenbush on 2008-12-02
> **haylocki said:**
> Hi,
    just a shot in the dark, but I have been having this problem on my computer after upgrading to Intrepid.

I ran the System monitor (System -> Administration -> System Monitor)

and clicked on the "Resources" tab. There I noticed I had 0 MB of swap memory enabled :shock:

So I enabled swap memory, and the problem seems to have gone away.

Maybe this will be the case with someone else.

Cheers, Ian

Dumb question - How do I enable that?

I too have random system lock ups and sometimes just random software lock ups. I love the look and feel of ubuntu, but jeez Windows XP was running smoother than this. :redface:

---

### Post by s1nful on 2008-12-03
I have been seeing this since the intrepid update. My observations:

[LIST]
[*]It seems to be related to FF3 or an addon because it doesn't happen if I don't opem the browser.
[*]I monitor the machine state remotely using pings and it stops responding to them with a request timed out message (sounds like kernel/network problems?)
[*] VNC sessions are terminated (connection reset)
[*]The time between outages and the time to recover seems completely random. Sometimes it will go for hours and other times minutes. Sometimes the outage is a hicough, sometimes it is down for tens of minutes
[/LIST]

I've tried pretty well all I can think of. Is there a reasonable alternative browser I can try?

---

### Post by jdorenbush on 2008-12-03
> **s1nful said:**
> I have been seeing this since the intrepid update. My observations:

[LIST]
[*]It seems to be related to FF3 or an addon because it doesn't happen if I don't opem the browser.
[*]I monitor the machine state remotely using pings and it stops responding to them with a request timed out message (sounds like kernel/network problems?)
[*] VNC sessions are terminated (connection reset)
[*]The time between outages and the time to recover seems completely random. Sometimes it will go for hours and other times minutes. Sometimes the outage is a hicough, sometimes it is down for tens of minutes
[/LIST]

I've tried pretty well all I can think of. Is there a reasonable alternative browser I can try?

Opera
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

---

### Post by s1nful on 2008-12-05
Thanks for that. For me it was definitely FF3 or one of the addons.

Opera installed and working. No lockups since last night. Prior to that it was down 25% of the time.

If you need it, the synaptic package is here:

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free #Opera

(add this line to your /etc/apt/sources.list, fire up package manager, refresh it and opera will magically appear in the list)

I can even listen to BBC iplayer (worked in opera with no tinkering at all) while I'm working without it stuttering every few minutes.

When I get time I'll reload firefox and uninstall the addons one by one until I can pin it down to either one of them or the app itself.

Glad I got it sorted. I thought I was going to have to try  Fedora 10.

---

### Post by haylocki on 2008-12-05
[QUOTE=jdorenbush;6296789]Dumb question - How do I enable that?

A swap partition should have been created when you installed Ubuntu. 

If you run the partiton editor :

System > Administration > Partiton Editor

(If the option is not there, just run :

sudo apt-get install gparted

in a terminal).


You should then be able to see what the location of your swap partition is, on my computer it is /dev/sda3.

Next you can close the partition editor, and run :

sudo gedit /etc/fstab

in a terminal. and add a line similar to :

/dev/sda3  none  swap  sw  0  0

(replacing /dev/sda3 with whatever location you found with the partition editor)

Save the file, Then type :

sudo swapon -a

and swap memory should be enabled.


If you don't have a swap partition follow these instreuctions :

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


Cheers, Ian

---

### Post by jdorenbush on 2008-12-05
Ian does this look right to you? Swap is sda5 (3.08gb)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e75fa73f-3da8-4c63-9bb2-a721228cc02b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=3d81340b-b500-4a16-89fc-701a50b88547 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5 none 	swap sw 0 0
```

Now what differences should I notice?

---

### Post by haylocki on 2008-12-06
> **jdorenbush said:**
> Ian does this look right to you? Swap is sda5 (3.08gb)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e75fa73f-3da8-4c63-9bb2-a721228cc02b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=3d81340b-b500-4a16-89fc-701a50b88547 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5 none 	swap sw 0 0
```

Now what differences should I notice?

Hi, looking at your fstab, you already had swap setup on this line :

UUID=3d81340b-b500-4a16-89fc-701a50b88547 none            swap    sw              0       0

So you need to either delete that line, or the new line you just added.

After running sudo swapon -a, looking at the system monitor resources tab, should show how much swap memory you have and how much is being used.

The difference you should see is that the computer no longer runs out of memory, and stops the computer being usable.

Did you check if you already had swap memory working, by looking at the system monitor, before editing the /etc/fstab file ?

Cheers, Ian

---

### Post by jdorenbush on 2008-12-06
Yeah I saw that, but I didn't get it because it said, "UUID=3d81340b-b500-4a16-89fc-701a50b88547". I removed the recently added swap. System Monitor says its using 2.1MB (0.1%) of 3.1GB - that sound normal?

---

### Post by haylocki on 2008-12-07
> **jdorenbush said:**
> Yeah I saw that, but I didn't get it because it said, "UUID=3d81340b-b500-4a16-89fc-701a50b88547". I removed the recently added swap. System Monitor says its using 2.1MB (0.1%) of 3.1GB - that sound normal?


Hi, Yes the UUID's are a PITA when you want to find out what device they are.

Wow! you have 3.1 GB of swap.

Looks like it's ok, so your problem with locking up must be somewhere else.

I've had this no swap problem on 2 different computers now, seems like I'm the only one.

Good luck with finding the cause of your lockup's.

Cheers, Ian

---

### Post by jdorenbush on 2008-12-07
> **haylocki said:**
> Hi, Yes the UUID's are a PITA when you want to find out what device they are.

Wow! you have 3.1 GB of swap.

Looks like it's ok, so your problem with locking up must be somewhere else.

I've had this no swap problem on 2 different computers now, seems like I'm the only one.

Good luck with finding the cause of your lockup's.

Cheers, Ian

"Wow"? I assume that's a good thing. Haha.

Thankfully Intrepid hasn't locked up lately. Previously I had Wubi/Hardy installed along with Windows XP on the same HDD. After all my Hardy problems I removed Ubuntu completely. I then reinstalled it from a CD onto a separate HDD. I haven't had many problems since. I just wanted to make sure this memory swap was setup correctly to avoid any future problems.

---

### Post by Phantom784 on 2008-12-09
Well, it's not firefox 3 or lack of swap for me.  Since the only way to see the output from the kernel panic is to have a console open when it happens, I decided to use my system in VNC with the console open on the 'real' screen to see what happens.  I'll post back with my results.  If anyone else wants to try this, please do and post what it says when it crashes.

---

### Post by Kevbert on 2008-12-09
Phantom784. Does the screen lock up on a particular screensaver (if you've set to random)? This could be a screensaver issue as well as another problem, maybe a memory check (memtest) is also in order. Locking up in Firefox may be due to a missing plug-in. Can you replicate it by going to the same web address ?
I've encountered both problems (braid in screensaver, disabled it) and Firefox when surfing to a Samsung web page (screen goes grey and just sits there indefinitely).

---

### Post by Cherylita on 2009-01-13
> **haylocki said:**
> Hi,
    just a shot in the dark, but I have been having this problem on my computer after upgrading to Intrepid.

I ran the System monitor (System -> Administration -> System Monitor)

and clicked on the "Resources" tab. There I noticed I had 0 MB of swap memory enabled :shock:

So I enabled swap memory, and the problem seems to have gone away.

Maybe this will be the case with someone else.

Cheers, Ian

Hi Ian,
I am very much a newbie here - how do you enable swap memeory?
Thanks!
Cheryl

---

### Post by haylocki on 2009-01-14
> **Cherylita said:**
> Hi Ian,
I am very much a newbie here - how do you enable swap memeory?
Thanks!
Cheryl

Hi, first check that you do not have swap memory enabled already.

try :

Applications -> Accessories -> text editor
UUID=d4e6292f-958e-46d8-91b6-9e2941662c23 none            swap    sw              0       0
Then open a file called /etc/fstab

look in this file for a line that contains the word 'swap'.

mine looks something like this :

UUID=d4e6292f-958e-46d8-91b6-9e2941662c23 none            swap    sw   0 0

If you have this then swap is already enabled on your system

If you do not, have a look further back in this thread where I explained enabling swap to another user.

Cheers, Ian

---

### Post by Xyem on 2009-02-01
I've been experiencing lock-ups since I upgraded my Hardy install to Intrepid. I thought it had something to do with Truecrypt as it only seemed to happen when I had something mounted through it.

However, I checked top and gnome-system-monitor and NetworkManager had pegged one of the CPUs and RAM usage was increasing constantly. I killed NetworkManager and memory usage has leveled off and it hasn't locked up yet ( with a Truecrypt volume mounted ).

Perhaps something to look for?

Good luck

---

### Post by Ubuntiac on 2009-02-02
I've been getting hanging since Intrepid, too. I've noticed that the hard drive starts to access constantly, and while the mouse keeps moving, no clicks or keyboard inputs (alt+ctrl+del, sysrq+*) seem to register.

I did notice the last time that it happened just as I clicked in Firefox, so there may be a clue there.

While the system uses the proprietry Broadcom 43XX driver now, the issue was happening even before that was installed.

I did once manage to see some kind of error when it hung about blocks on sda2 (my swap partition). This is hard to check though as fsck doesn't seem able to check swap partitions.

---

### Post by Xyem on 2009-02-03
Unfortunately my previous post wasn't the cause of the lockups and it had locked up shortly after I had posted it, even in a LiveCD.

However, I think I have now found the issue. A PCI wireless card ( that I wasn't using ). I've removed it and everything has stabilised ( lasted all evening with no issue plus the whole system became more responsive ).

AFAIK the card is an ACX111 chipset ( I can check if needed ). Perhaps try removing wireless drivers ( and card if possible )?

Hope this helps.

---

### Post by bibliophage on 2009-02-10
I have the same problem, but everything locks up. Mouse, keyboard, screen, everything. I've been watching the system monitor, and when it happens, both CPUs are at 100%. I'm not sure what is causing this, when I look at the processes, nothing appears to be taking up cycles. I've been tinkering with xorg.conf to see if anything helps, but it doesn't seem to. I can get CPU2 to less than 100%, but never CPU1.

Anyone have any ideas?

Ubuntu 8.10 Intrepid
2.0 Gigs RAM
AMD Athlon 64 X2 6000+
Nvidia GeForce 8600 GT

---

### Post by Xyem on 2009-02-11
Sounds very much like what I had..

Try stopping/killing NetworkManager.

---

