---
title: "Ubuntu on ASUS P5Q-EM"
date: 2008-09-09
forum: Hardware
---

### Post by botfish on 2008-09-09
Does anyone have experience running Ubuntu 8.04 on an Asus P5Q-EM?

ASUS P5Q-EM Intel G45 Express Gate ICH10R RAID HDMI DVI LGA775 Micro ATX Intel Motherboard Retail

I've seen on other forums that some people have it running no problem and other have given up because of sound and network driver problems.

---

### Post by pointone on 2008-09-13
I've recently gotten one and am having one hell of a time setting it up.

The SATA controller isn't supported in Hardy Heron, apparently (and live CD freezes during installation as a result) so I've been trying to install Intrepid Ibex alpha 5. 

Unfortunately, with the Ibex live CD, Ubuntu fails to properly configure the video/monitor and it simply flashes the screen a few times (presumably testing various resolutions) before presenting a rather garbled screen.

I got around this by installing via the "alternate" disc. Unfortunately, my installed system falls victim to the same problem.

I am able to get a bit further after running an apt-get update/upgrade, but then fall victim to (I think) [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257450"), where Ubuntu freezes on login.

Tried with kubuntu-desktop as well, just in case... but same result.

---

### Post by whizse on 2008-09-14
It's not Ubuntu, but I'm running Debian unstable on this board. 

Except for [X crashing on login]("https://bugs.freedesktop.org/show_bug.cgi?id=17460") I haven't had any problems at all. The X crash can be worked around by switching to XAA (from the default EXA).

---

### Post by jesper1266 on 2008-10-18
If you set the harddisk controler to achi, then you are able to install ubuntu 8.4 and 8.10b. The network works for me out of the box, but I have been unable to get sound up and running so far.

Cheers 
Jesper

---

### Post by redDEADresolve on 2008-10-22
> **jesper1266 said:**
> If you set the harddisk controler to achi, then you are able to install ubuntu 8.4 and 8.10b. The network works for me out of the box, but I have been unable to get sound up and running so far.

Cheers 
Jesper

Sound should be working. There was a problem with the board and Nvidia cards. Having a Nvidia card isntalled would bork sound. 

The good news is, the g45 freezing on login bug a been fixed with todays, October 22 2008, intel driver and kernel update in Ubuntu 8.10.

You have have 3D.

---

### Post by ebike on 2008-12-03
I have mythbuntu 8.10 (x86_64bit) running on this board and everything is flawless ... even have HD 1080i off a DVB-T card working ...

To my mind this is the ultimate media PC motherboard. Looking forward to the day we get hardware acceleration (due in the 2.6.28 kernel), though even without acceleration I am getting 20% CPU at 720p and 50% CPU 1080i on a E7300 core 2 and my CPU never goes above 45 degC. My case is cold even running 1080i and the power consumption at the wall is only 50 watts, that should fall to 25 watts when we get hardware accell ...

I would recommend this board to anyone thinking of ubuntu 8.10 or mythbuntu 8.10 HTPC.

---

### Post by pablolie on 2008-12-06
> **ebike said:**
> I have mythbuntu 8.10 (x86_64bit) running on this board and everything is flawless ... even have HD 1080i off a DVB-T card working ...

To my mind this is the ultimate media PC motherboard. Looking forward to the day we get hardware acceleration (due in the 2.6.28 kernel), though even without acceleration I am getting 20% CPU at 720p and 50% CPU 1080i on a E7300 core 2 and my CPU never goes above 45 degC. My case is cold even running 1080i and the power consumption at the wall is only 50 watts, that should fall to 25 watts when we get hardware accell ...

I would recommend this board to anyone thinking of ubuntu 8.10 or mythbuntu 8.10 HTPC.

What software are you using to monitor CPU temperate and utilisation? I have the same board, and while everything works -like you say- fine now (I even have Windows 64 and Ubuntu 8.10 64 booting off the same mirrored RAID volume), one thing I miss are the power-saving features in Windows, i.e. the CPU stepping feature.

---

### Post by ebike on 2008-12-08
I installed lmsensors. It only manages to monitor both CPU temperatures, doesn't pick up anything else.

Just using "top" for cpu usage.

---

### Post by orduek on 2009-01-07
> **ebike said:**
> I have mythbuntu 8.10 (x86_64bit) running on this board and everything is flawless ... even have HD 1080i off a DVB-T card working ...

To my mind this is the ultimate media PC motherboard. Looking forward to the day we get hardware acceleration (due in the 2.6.28 kernel), though even without acceleration I am getting 20% CPU at 720p and 50% CPU 1080i on a E7300 core 2 and my CPU never goes above 45 degC. My case is cold even running 1080i and the power consumption at the wall is only 50 watts, that should fall to 25 watts when we get hardware accell ...

I would recommend this board to anyone thinking of ubuntu 8.10 or mythbuntu 8.10 HTPC.

I installed mythbuntu 8.10 with this motherborad and I'm having trouble setting it up to 720p.
He chooses 1080p which is too much for my TV and hence it causes the picture to be very small instead of using the whole screen.
It happens even before OS is up (on BIOS) can I change something to make it OK?

---

### Post by SqRt7744 on 2009-01-24
I got Express Gate to install with Ubuntu! It was actually pretty easy, strange that nobody has posted a how-to yet. I'm using Ubuntu 8.10 x86-64

1. Install wine. I used version  1.1.13, which I got from winehq.org, installation instructions are on the wineHQ site.

2. run the installer from the CD. Accept defaults and click OK, etc. etc until it indicates that it has completed the install successfully.

3. install 'gparted' either through synaptic package manager (System->Administration->Synaptic Package Manager), or open a terminal window and type:
sudo apt-get install gparted

4. start gparted (System->Administration->Partition Editor). Create a new partition on your hard drive, type NTFS. I made mine 1.5GB, labeled it "WINDOWS", and gave it the boot flag to be on the safe side. I created mine at the beginning of the drive. This was probably a mistake since the drive is 500GB and the current partition had to be shrunk and moved, it took 20hrs or so. I suggest making it at the end of the drive where the computer has less work to do.

5. when gparted is finished, open a terminal window and mount the partition. The command will look something like this:
sudo mount.ntfs-3g /dev/sda3 /mnt
where sda3 is the name of the newly created ntfs partition on my computer. It may well have a different name on yours. It is mounted in the directory /mnt.

6. copy the 'fake' wine drive c to the newly created WINDOWS partition.
cp -pr ~/.wine/drive_c/* /mnt

7. if you now look in /mnt, you will find a file called splash.idx. You have to edit this file.
Mine looks like this:

root=UUID=43FE94EC1C4A1BAA
/ASUS.SYS
/ASUS.000

the first line, containing the UUID has to be changed to the UUID of your new ntfs partition. You can find this by typing
ls -l /dev/disk/by-uuid/
the UUID that points to the appropriate partition has be entered into the splash.idx file.

Save everything, close, reboot. If it doesn't work, make sure that the Sata mode in BIOS is set to ide emulation, otherwise splashtop won't work at all (see the mainboard manual)

8. YAY!

---

