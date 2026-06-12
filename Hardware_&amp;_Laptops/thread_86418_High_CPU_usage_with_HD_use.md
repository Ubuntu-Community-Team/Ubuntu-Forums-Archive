---
title: "High CPU usage with HD use?"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by GoA on 2005-11-05
Hi. I have the following problem with breezy and it the same problem actually exists also in hoary. Everytime when using a lot of the harddrive. Like big copying operations or unrarring big files my cpu usage goes to 100 %. This makes sense because the unrar program uses it all, right? No, unrar program uses about 10 % of power and system monitor doesn't show what takes about 80 % of the rest. So now you say that DMA isn't enabled. Wrong, DMA is on and when I test the speeds with hdparm I get about 55 mb/s reading and about 1000 mb in the another test so by tests the hd seems to preform well. Then another example. If I copy files from my fat32 partition to my EXT3 partiotion CPU-usage goes again into 100 %. So this seems like using a lot filesystem/hd-performance uses way too lot of cpu-power. Here's my system specs:

DFI Infinity NFII Ultra
Athlon 2800+@2205 mhz
1024 mb of DDR 400 memory 
Nvidia GeForce 5200
120 gb seagate 7200.7 hd in IDE
Beta Bios for overclocking. (stable and good)

I have tried different settings with bios but now effect. Currently there are disabled almost everything useless such as intengrated sound, network, sata, paraller and serial ports.

So any thought? In windows side this doesn't happen so it seems to be a driver/kernel issue. When I was using my own compiled kernel with the option to make all ide-devices to use DMA the situation was the same. This is quite depressing. I'm not swtiching awazy from ubuntu but maybe I have to do a hardware update or something?

---

### Post by Teroedni on 2005-11-05
hmm so what kernel are you using now?

---

### Post by spizkapa on 2005-11-05
[QUOTE=GoA]
DFI Infinity NFII Ultra
Athlon 2800+@2205 mhz
1024 mb of DDR 400 memory 
Nvidia GeForce 5200
120 gb seagate 7200.7 hd in IDE
Beta Bios for overclocking. (stable and good)

So any thought? In windows side this doesn't happen so it seems to be a driver/kernel issue. When I was using my own compiled kernel with the option to make all ide-devices to use DMA the situation was the same. This is quite depressing. I'm not swtiching awazy from ubuntu but maybe I have to do a hardware update or something?[/QUOTE]

Dude, don't be alarmed. You don't need a hardware upgrade.

What you probably do need is to install the right kernel with synaptic (the 686 is the right one for your Athlon) and get all the nice optimisations that come with it. It makes a huge difference.

You also need to remember that reading from one partition of a drive and writing to another means that the same drive is reading and writing at the same time. This is inevitably slow. If your fat32 partition was on a different drive (but preferably on the same IDE channel), the copy would be much faster.

HTH.

---

### Post by GoA on 2005-11-05
I'm currently running 686 kernel. Have tried K7 kernel also and 2.6.14 compiled with c1 optimations and custom 2.6.12 kernel. Same thing with all.

And yes, I know it's slow to read/write at the same time but for unrarring a dvd tooks a lot more time on ubuntu than on windows.

hmmm.. maybe I should try these: [http://www.nvidia.com/object/linux_nforce_1.0-0306.html](http://www.nvidia.com/object/linux_nforce_1.0-0306.html)

Those have something for nforce2 ide disk controller?

---

### Post by spizkapa on 2005-11-05
[QUOTE=GoA]I'm currently running 686 kernel. Have tried K7 kernel also and 2.6.14 compiled with c1 optimations and custom 2.6.12 kernel. Same thing with all.

And yes, I know it's slow to read/write at the same time but for unrarring a dvd tooks a lot more time on ubuntu than on windows.[/QUOTE]

What are you unrarring with? If you're using the non-free version of unrar then your complaint on speed should be directed to the people who write unrar. What I mean is that you can't expect the alpha/beta Linux version which has been around only for a short while to be as fast as the stable mature Windows version. Those are the breaks...

If you're using the free version (which I suspect you're not since it doesn't support rar v3) then you have to allow some speed deficiencies when software is written without proper specs.

Unrarring CD/DVD images has always worked for me. It surely does take up a lot of processor time and "effort", as you say. I don't think that fiddling with your kernel (since you have the right one from what you say) will further speed things up. It's not a kernel issue as far as I can see, it's a software issue.

---

### Post by GoA on 2005-11-05
I'm using the free version. But the problem isn't the rar program. Something else tooks up the cpu-usage and it seems that is linked directly to heavy disk usage. I'll try to install those nvidia nforce2 drivers.

EDIT: It had drivers only for sound and ethernet which I don't use.
EDIT2: Here's a screenshot about how it looks from my computer

[http://80.221.63.65/cpuusage.jpg](http://80.221.63.65/cpuusage.jpg)
[http://80.221.63.65/resources.jpg](http://80.221.63.65/resources.jpg)

In the usage picture you can see how the cpu-usage goes to 100 % after the copy process starts. 
In the resources picture you can see the apps that use most of the cpu-power. 

And it doesn't make sense that what could take almost 2.2 ghz of processor speed for a simple copy operation?

---

### Post by GoA on 2005-11-11
Ok, I bought new sata drive and the problem still exists even if I don't anymore have any ide-drive on my computer. My sata-chip is sil3114. Kernel 2.6.12-k7 should support that by default because everything is working. However, it seems  like all the data is going through the processor when using harddisk because the processor use goes to 100 % still.

---

### Post by GoA on 2005-11-20
Still no leads? When doing the copy thing and using top command I can see about 78 % in the cpu wa part. Little googling told me this:

Presumably "wa" indicates CPU wait states, which are different from idle. Currently, whenever
I do a disk access, the "top" command reports something like this:

Cpu(s): 10.9% us, 9.2% sy, 0.7% ni, 0.0% id, 78.5% wa, 0.7% hi, 0.0% si

The "78.5% wa" is a very bad thing, as for reasons yet unknown my CPU is waiting on something, maybe the ISA bus. This is slowing my system down to a crawl. Perhaps I can tell you more about "wa" when I figure out how to correct this problem. 

Any suggestions or thoughts would be nice, even very little ones. I have already tryed to disable floppy disks, motherboards ethernet, sound, paraller and printer ports, fireware and game controller ports but no help. I could try buuting the system without any ide devices and use only the sata harddisk.

EDIT: I tried to remove all ide devices and all pci devices from my computer but still the same problem. :(

---

### Post by cylon359 on 2005-11-20
[QUOTE=GoA]Still no leads? When doing the copy thing and using top command I can see about 78 % in the cpu wa part. Little googling told me this:

Presumably "wa" indicates CPU wait states, which are different from idle. Currently, whenever
I do a disk access, the "top" command reports something like this:

Cpu(s): 10.9% us, 9.2% sy, 0.7% ni, 0.0% id, 78.5% wa, 0.7% hi, 0.0% si

The "78.5% wa" is a very bad thing, as for reasons yet unknown my CPU is waiting on something, maybe the ISA bus. This is slowing my system down to a crawl. Perhaps I can tell you more about "wa" when I figure out how to correct this problem. 

Any suggestions or thoughts would be nice, even very little ones. I have already tryed to disable floppy disks, motherboards ethernet, sound, paraller and printer ports, fireware and game controller ports but no help. I could try buuting the system without any ide devices and use only the sata harddisk.

EDIT: I tried to remove all ide devices and all pci devices from my computer but still the same problem. :([/QUOTE]

wa is I/O wait time.  Basically, your CPU is so much faster than your disk, that it has to wait for it before continuing to copy more... this is totally normal.

So your CPU isn't actually at 100%, it's just waiting for I/O to complete.

---

### Post by GoA on 2005-11-20
So basically all the time  the system monitor has showed the 100 % cpu usage it has been only wating time so all this time all my problems has been useless? :D

---

### Post by cylon359 on 2005-11-20
[QUOTE=GoA]So basically all the time  the system monitor has showed the 100 % cpu usage it has been only wating time so all this time all my problems has been useless? :D[/QUOTE]

Yes, system monitor does not show I/O wait time.  You need to use either top or vmstat in a terminal to see that.

---

### Post by AlmaTlust on 2008-04-25
I have the same problem. My question is: why should my system responsiveness become so slow when all the time the cpu is just waiting for input from the hd? Shouldn't it have enough resources to still react to my mouse, switch windows or the like?
My main problem is with updatedb and rdiff. When those are running, my system gets VERY unresponsive up to the point that mouse clicks take a minute or longer to do something...

---

### Post by paoletto on 2008-05-10
It's because what the guy above said is completely wrong.

If you want to try yourself just put some cpu intensive process with nice -n 20 togheter with your disk intensive process. You will see that those %WA cpu cycles does not translate to %NI, and your cpu intensive process will be very slow. 

That means %WA is not the same as %IDLE, but they are used cpu cycle for the I/O

(oh, for instance, i got your same problem in gutsy and hardy now, after a dist-ugrade, before my system was fine. And no damn one knows why ubuntu does this.. Im sincerely considering  to switch to gentoo, considering the high support quality ubuntu is getting..)

---

### Post by paoletto on 2008-05-10
i want to add that this forum is getting full of threads about troubles with disk performances, and no damn one gives an authoritative answer..

Ubuntu, u want the $$$ without working, hah?

---

### Post by Joeb454 on 2008-05-10
Well perhaps if you stop and think about it, you may realise that we don't know **everything** :)

And how does Ubuntu get $$$ ? it's distributed for Free

---

### Post by paoletto on 2008-05-10
possible, but when the forum starts getting populated by posts with the same problem, maybe some ubuntu engineer should start investigating, dont you think?

---

### Post by cudjoe on 2008-06-02
Did you guyz sorted something about that problem ?

Somebody said it was related to available space on partitions.
[http://ubuntuforums.org/showthread.php?t=399316](http://ubuntuforums.org/showthread.php?t=399316)


Mines are pretty but could be worse !
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                502M  264K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   56K  502M   1% /dev
devshm                502M  668K  501M   1% /dev/shm
lrm                   502M   38M  465M   8% /lib/modules/2.6.24-17-generic/volatile
/dev/sda3              73G   63G  6.6G  91% /home
gvfs-fuse-daemon       19G   13G  5.3G  72% /home/mathieu/.gvfs

```

Could it be related to my swap partition ? I don't think so because it's never used...I have 1Go of RAM.

Pretty annoying... Miro is very slow, VirtualBox forget it, Copying file completely eats cpu (mouse & keyboard unresponsive !!)

Please let us informed of you investigated !
Thanks a lot !

---

