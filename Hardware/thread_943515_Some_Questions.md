---
title: "Some Questions"
date: 2008-10-10
forum: Hardware
---

### Post by andras artois on 2008-10-10
I have a few questions that would make my Ubuntu somewhat easier to use :)

1) Is it possible to mount a external hard drive directly to my /home location and for it to then show up on my desktop? I want to do this with two external hard drives and what will be the best way to format them? ext3, swap etc.

2) I have two internal hard drives, a 60GB one with Ubuntu currently installed and a 40GB one with XP currently installed. The 60GB hard drive is set as master and the 40 GB as the slave. At the GRUB menu XP doesn't show up unless I choose to boot from the 40GB hard drive and then the screen just flashes blue and the computer restarts. Is this because the 40GB is set as slave? If so, what do I need to set the jumper as?

3) I may want to install Vista on the 40GB hard drive, will 40GB be enough space for Vista and will it run on a Pentium 4 (2.4GHZ) and 700ishMB of RAM? I don't have a graphics card and I don't want glassy fancy effects.

4) I have a Sony Mp3 player, model NWZ-A828. How do I get this to show up as A removable device but so I can just cut/copy/paste music on to it?

5) Can all computers boot from a external hard drive? And will all linux distro's install onto a external hard drive?

Thank you to anyone that can help :)

x

---

### Post by cl0ckwork on 2008-10-10
1) yes, it is possible to have it automatically mount and show on your desktop but im not sure about the /home part.  do you want to use it as your /home partition or just have it mount on startup?

2) sorry, not much experience here :???:

3)my vista install takes up about 25-30 gigs but there is a program called vlite that can take extra programs out if you dont use them, eg. notepad if you use notepad++ etc.
700 meg of ram is cutting it close, recommended is 1 gig but if u arent running any visual effects it shouldnt be a problem

4) most mp3 players are quite picky with any linux distro, usually a media program is needed (rhythmbox, exaile, etc.) to recognize the player.  i have a few creative media mp3 players and 2 ipods and none of them show up as a removable disk, maby there are appropriate drivers out there for yours

5) they can as long as their BOIS allows them. depending on what brand name, M/B, age, etc.
most distros can install on an externa drive, but theres a bit more setup involved that just on an internal disk

hope that helps :)

---

### Post by andras artois on 2008-10-10
Sorry I wasn't very clear what I meant in 1). I want one hard drive for my Video's and one hard drive for my music and then I would like both them to mount into the home directory.

So would Vista be okay being installed onto the 40GB hard drive? It's premium home edition BTW. I would remove IE, Microsoft Office, Windows media player etc.

With booting from a external hard drive does it need a specific way of installing it like Dreamlinux's pen drive installer?

Thank for the help so far it's very appreciated!

---

### Post by Paul41 on 2008-10-10
> 
1) Is it possible to mount a external hard drive directly to my /home location and for it to then show up on my desktop? I want to do this with two external hard drives and what will be the best way to format them? ext3, swap etc.
Since you are using both Windows and Linux I would use FAT32 so both of them can read it (it is also the default for most external drives). To mount it in your home first find where it is by opening the terminal and typing

```
df -h
```

You should see a list of drives. Find your external drives, they will be listed as something like /dev/sdb1, /dev/sdc1. Make a directory in your desktop and name it whatever you like

```
sudo mkdir ~/Desktop/external1
```

Then to mount the drive on your home (this assumes it was /dev/sdb1 and formatted as FAT32) type

```
sudo mount -t vfat /dev/sdb1 ~/Desktop/external1
```

> 2) I have two internal hard drives, a 60GB one with Ubuntu currently installed and a 40GB one with XP currently installed. The 60GB hard drive is set as master and the 40 GB as the slave. At the GRUB menu XP doesn't show up unless I choose to boot from the 40GB hard drive and then the screen just flashes blue and the computer restarts. Is this because the 40GB is set as slave? If so, what do I need to set the jumper as?

Windows does not like to be installed on a slave drive (Linux doesn't care) so that may be your problem.

---

### Post by andras artois on 2008-10-10
Thank you! I'll try that now.

So if I just set windows as master and linux as slave it should be alright to dual boot? What happens if both of them are set to master?

EDIT: Few problems, I can drag and drop files into but I can't right click and paste files into the folder. Also the drive shows up on the desktop as well as the folder and the name of the drive, sbc1 etc, changes depending on which drive is switched on first so it doesn't connect to the folder if they're detected in the wrong order.

Would it be a better idea to just name the drive and let it be like when you plug a Memory stick into your pc and it pops up on the desktop?

---

