---
title: "Dawicontrol (fake-)RAID1 shown as seperate disks"
date: 2009-03-08
forum: Hardware
---

### Post by delirium83 on 2009-03-08
Hi there,

I recently installed a (fake-)RAID controller from Dawicontrol (DC-300e), as I wanted to have a RAID1 of two discs that was accesible from my kubuntu as well as my Windows Vista. I set up the RAID in the RAID BIOS and can use it properly in Vista. In Kubuntu however, the RAID is shown as two seperate discs in Dolphin.

I have done some forum and google research and it seems like writing to one of the discs with kubuntu sends the RAID out-of-sync. This is consistent with my own experience, hence I suppose the discs are really accessed as the HDDs instead of the RAID.

Is there anything I can do to see and use the RAID1 instead of the included discs?

```
$ sudo dmraid -s
*** Active Set
name   : sil_aibicacaaibc
size   : 625140400
stride : 0
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
```

---

### Post by delirium83 on 2010-03-17
I never solved the problem and now (after updating to the current Kubuntu version and still wanting to tackle the problem) the raid controller is not found at all, meaning 

```
sudo dmraid -s
no raid disks
```

The two physical discs are still found as /dev/sdd and /dev/sdc and I can mount both of them without problems, but not as the RAID1 (see first post)

As I really want to be able to use these HDDs in Ubuntu as well as Windows, could anybody please help me with my problem?

The fakeraid controller uses a Sil3132 chipset, btw.

All ideas are welcome,
del

---

### Post by Lundis500 on 2010-03-17
I have a RAID-1 as well using my nForce motherboard.
What you are asking is not possible.

---

### Post by delirium83 on 2010-03-18
Is there any specific reason why do you think so? Or maybe even a link that explains the problem? I was unable to find anything using google/forum searches.

The chipset (Sil3132) of my fakeraid controller is supported in Ubuntu (afaik) and should therefore be accessible as the RAID instead of the single discs.

---

### Post by Lundis500 on 2010-03-18
Don't really have a link for you, I no longer track the message I got for the same question.
But it's the same for me, the Raid is not visible or usable, only as separate disks.

I just have a separate FAT32 and NTFS partition on a single drive where I move files between them.

Maybe some day the linux people decide to make proper drivers for the simple raid controllers that we have.

---

### Post by jrssystemsnet on 2010-03-18
> **delirium83 said:**
> 
```
$ sudo dmraid -s
*** Active Set
name   : sil_aibicacaaibc
size   : 625140400
stride : 0
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
```

Try **ls /dev/mapper**.  You're looking for something like **/dev/mapper/pdc_feddabdf** or some similar crap.  Once you've found it, you should be able to simply **sudo mkdir /mnt/fakeraid** and **sudo mount /dev/mapper/pdc_feddabdf** (or whatever) to mount your fakeraid partition.

---

### Post by delirium83 on 2010-03-19
in /dev/mapper I only have 'control'. Do I need to run any command to add the entries there?

The part you quoted is not the current situation any more, as dmraid does not see the RAID any more (see second post).

---

### Post by jrssystemsnet on 2010-03-19
Well, unfortunately if dmraid can't find the array, you can't mount the array.  So you need to drop back to figuring out what's wrong with dmraid.  If you can get THAT sorted, you'll find the array in /dev/mapper and you can mount it.

Try **sudo dmraid -r**, or even **sudo dmraid -r /dev/sdc** and see if that gets you any output - and if it does, try looking in /dev/mapper again afterward.

---

### Post by mauryg on 2010-03-24
I have been struggling with a similar problem with the ICH10R controller on an ASUS P6T mobo. I have a 4 x 1 TB RAID5 set under Windows 7 which I want to access via Ubuntu. 
Here's what worked for me:
1. You have to have dmraid and ntfsprogs installed.
2. boot into ubuntu and start a terminal session
3. run sudo dmraid -ay to activate the RAID set
3. run sudo gparted. It will open a GUI window; just close it
4. close terminal session.
5 run disk manager (palimpsest) from the menu and mount the NTFS partitions.

Right now I'm trying to work out how to have ubuntu do all this automagically on bootup.

hope this helps.

Maury

---

