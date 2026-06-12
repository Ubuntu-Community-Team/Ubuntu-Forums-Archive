---
title: "Installing Ubuntu on HP DV2"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by eigenman on 2009-05-31
I recently purchased an HP dv2-1028 with AMD neo cpu, and an ATI 1250x, without a CD player. This was surprisingly a painless install, but there were few issues that arose, which I'm posting here (along with few solutions).

First off, since this laptop does not have a cd-player, I needed to setup a usb boot disk. Quick search brought me up to [http://www.pendrivelinux.com](http://www.pendrivelinux.com). I followed the instruction for installing 9.04, but for some odd reason that failed (the USB key claims that it can't find the mounted partition. Seems to be the duplicate of [https://bugs.launchpad.net/ubuntu/+bug/366678](https://bugs.launchpad.net/ubuntu/+bug/366678)), so I installed 8.10 instead which went ahead with a hitch. In fact, I was impressed on how quickly it could install the whole thing.

After the installation, the laptop was fully functional: sound, suspend/hibernation, nice video, they were all working fine. The only issue showed up when I was trying to test the webcam. Apparently the ati driver for 8.10 doesn't support xvideo extension, and as result, cheese would crash upon start. Installing fglrx solved that problem, however that broke the hibernation/suspend issue (hmm... I'm pretty sure my laptop was not functional after wakeup, but it's possible that it was just the display. If someone has any experience in that regards, they can correct me). I didn't stay in 8.10 for that long, but it seemed like a solid system (minus the issues mentioned, which I'm sure one can fix if they spend a bit of time on it).

After noticing the problem with hibernation/suspend issues, I upgraded to 9.04. To my surprise, my laptop would crash upon startup with garbeled display. Searching the web a litte, I find out that fglrx and 9.04 are not quite compatible (I can't find the wiki page that says that, but it was from ubuntu's website), and it was strongly suggested to remove fglrx before upgrading. So, I remove fglrx, and switch back to the open source driver, and reboot, and it works like a charm. xvideo extension is working now, so cheese is functional. In fact almost everything is working without a hitch: webcam, video card, video replay, wireless, suspend/hibernation (although, see below). The only issue was the lack of sound from the internal speakers. This is apparently a known problem, and following the suggestion at 
[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090) 
solved the speaker issue.

The only issue left, is not everything starts up automatically after a suspend/wakeup cycle. Specifically, the monitor is initially off, and I have to switch to text and back to graphic mode to make it work again (minor annoyance), and the wireless needs to be enabled manually afterward. I'm not sure if anyone has any suggestion how to fix these issues, or if it is unique to my setup. However, aside from these, the laptop seems functional, and I am a very proud user. I am in the euphoric state that makes me pity the people using other OS'es right now. :)

Thanks Ubuntu,
eigenman

UPDATE: I spoked too soon. In the default setting, after waking up from suspend, vbetools is using ~90% cpu, as well as the issues mentioned above, and I could not suspend again. The workaround in [https://bugs.launchpad.net/ubuntu/+source/vbetool/+bug/130979](https://bugs.launchpad.net/ubuntu/+source/vbetool/+bug/130979) solved the problem. Specifically adding
```

      <match key="system.hardware.product" contains="HP Pavilion dv2">
        <merge key="power_management.quirk.none" type="bool">true</merge>
      </match>

```
just under the prefix="Hewlett-Packard" fixed the problem.

---

### Post by mr_raider on 2009-06-15
Thanks for the post. I just bought a dv2-1043ca with the 3410 HD Radeon GPU. I hate the pre-installed Vista so I will try Windows 7 and Ubuntu. I'll see if I hav ethe same issues.

---

### Post by mr_raider on 2009-06-16
I managed to boot 9.04 to Live install. I used a USB stick and connected it for boot. Then removed the stick and reconnected it during the splash screen and went to live install.

Did you get the touchpad side scroll function to work?

---

### Post by eigenman on 2009-06-21
The side scroll (for moving up and down) seems to work out of the box as well. I haven't tried the scroll for left and right. I don't use it, so I haven't looked into it at all. In general, I find the touchpad to be one of weakest point of this laptop on ubuntu. It seems a bit too sensitive at times for my taste, and I don't know how to fix that.

---

### Post by babber on 2009-08-11
Hey guys, i just ordered a dv2-1028 for my fiance.  i'd like to install ubuntu on it for her, as my experiences with vista haven't been pleasant.  do you mind if i pick your brains when it arrives?  i'm not a novice comp user, but am totally new to ubuntu.  Thanks.
Babber

---

### Post by alfu on 2009-09-22
Shrinking Vista, Installing Ubuntu 9.04 as dual-boot on HP dv2-1030us.

**1) Create a set of Vista recovery DVDs first.**  On this HP computer, creating a recovery disk may result in "No DVD drive capable of creating a recovery disk" error if there is not yet loaded a DVD or CD into the external USB drive. The recovery program writes the file to optical disks, not a connected USB HDD with a partition large enough to hold it. 

[INDENT]This operation is *jaw-droppingly slow*.  **After spending an entire afternoon with the Vista recovery disk manager I was able to get to the 6% verified position on two DVDs, both of which then ended up coasters.** The HP phone rep (from India, where else?) informed me that I could use any other brand of DVD to do backups *except Memorex*.:lolflag: With HP DVDs the process went OK.
[/INDENT] 
**2) Shrink Vista**  If you try to do this within Vista, it will want to retain way too much space for its drekware (190GB).  "Size of available shrink space can be restricted if snapshots or pagefiles are enabled on the volume" may cause this, but so far I can find no way to disable them. 

So it is better to shrink the Vista partition with GPartEd (I gave Vista a generous 55GB, probably not enuf space for Windows 7 :) ).  This is only possible from the LiveCD, not a GPartEd within a Ubuntu install. 

**3) Run Ubuntu from the Live CD.** Hold <F10> or <FN>+<F10> on power up to get into the HP setup and make the external DVD bootable.

Unfortunately booting both Ubuntu 9.04 live AMD64 and i386 36bit CDs fail with a "modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: no such file or directory" and then drops into the BusyBox built-in shell on this computer (which I have no clue how to use).  

This may just be a [USB plugging/unplugging]("https://bugs.launchpad.net/ubuntu/+bug/366678") issue, so try this:

1) Arrow-key down to select "Install Ubuntu".  Hit <F6> then <ESC> to reveal the boot options command line.
2) Replace "quiet splash--" with "debug break=mount".  Hit <ENTER>.
2) Once the busy box prompt appears, wait for the CD to stop spinning and unplug the external CD drive.
3) Plug the drive back in. It will start up, log more pages of text, then halt.  Hit <ENTER>.
4) At the "(initramfs)" prompt type "exit" to allow the cd to finish booting. 
5) The first time I tried this resulted in the Black Screen of Death.  The second time it worked.

Under 'System/Administration/Partition Editor', select the Vista partition and use the 'Resize/Move' option to set the C: partition to whatever you are comfortable with.  Look closely, and you can see a graphic representation of the amount filled (pale buff) versus the amount free (white).

Boot back up into Vista, and you get a scary "Windows is loading files ..." message and then attempts repairs for about an hour with some restarts.  But when you access the "Start/Control Panel/System & Maintenance/Administrative Tools/Computer Management/Storage/Disk Management (local)" dialog you will see you in fact have shrunk the C: drive. While you are at it, re-label C: to "Vista" or something useful.

[INDENT]Hopefully, you will never have to recover Vista from the D: RECOVERY partition.  <ALT-F11> at startup launches this grindingly slow process.  This involves a re-formatting (and a land-grab for any space you freed up with GPartEd) of the C: partition, at least 4 lengthy but uninformative loops of "Software is being installed" dialogs and restarts, and a clobbering of the Ubuntu bootloader.  Nor does this procedure let you opt out of the many gigs of drekware that MegaHard Corp and H-P want you to host on your own computer.
[/INDENT] 
[INDENT] Recovering Vista from the 13GB RECOVERY partition does not clobber Ubuntu itself, but it is lost for all practical purposes.  The various means I found on the web using the Terminal to repair Grub did not work ("fdisk -l" returned null in all permutations I could think of, and >grub commands also returned null).  I had to do a full Ubuntu re-install into the same partition.
[/INDENT] 
  
**4) Boot into the Ubuntu live CD again.**  I used gparted to wipe one of the ext3 partitions, then Installed Ubuntu into the unallocated space (this creates an extended partition). **Much better is to have your /home and /usr directories install on separate partitions**, so when you re-install Ubuntu, your user data is not wiped as well!  In using the "advanced" option (on another computer), I made ext3 partitions mounting in mountpoints "/", "/home" and "/usr".  Unfortunately, the Ubuntu installer ignored the latter two, and put everything into "/" for me.  The Gnome desktop does not even see these partitions, let alone mount them.  

*So I have not succeeded in being able to do this yet, but will offer step-by-step instructions when I get it working.  This should be part of the Ubuntu documentation somewhere, but I have not been able to find it yet.*

**5) Boot into your new Ubuntu install.** 

Using the Applications/Add/Remove menu, if you install the Gnome Partition Editor from an on-line download, you can see the now-shrunken Vista partition.  Altho the Ubuntu desktop generally sees M$-formatted partitions, it can't see the Vista RECOVERY partition (NTFS).  GPartEd can SEE it, but cannot mount it nor unmount it, nor do anything with the recovery file on it (like save it to another medium).

When you boot into Vista, with the Vista Disk Management tool you can see the partitions the Ubuntu install created, but they do not show up on Vista's desktop directory listing.

**6) You will have issues with your new install:**  

**Booting from a USB flash drive** After going into this computer's setup and changing all possible USB devices to a higher boot priority than the HDD, Ubuntu still boots from the hard drive rather than the USB stick. *Not sure yet if this is a H-P or a Ubuntu issue.*

**Disk and partition labels** cannot be set from the Gnome desktop (a pop-up 'Rename...' option exists, but is always grayed-out).  As a workaround, go into GPartEd and unmount a partition.  Then you can re-name it in GPartEd.  Also, there is no way in selecting "properties" for a partition in the Gnome desktop to determine which physical drive it is on.  You also need to go into GPartEd to do that.  Micro$oft fans will be delighted, however, that file listings are cutsieable with 'Emblems'.

**Evolution e-mail client** has a host of problems, including not recognizing its own backup file, importing an .ldif @ddress book file, allowing random line length wrapping or representing 'text' as just text.  Thunderbird is much better; it includes a dialog box in which you can set all the program variables that are read on startup.

**"File Save ..."** Ordinarily, a program will prompt you to save a file on the last media on which you saved.  The Gnome Image Viewer (and perhaps others) does not do this, always defaulting to the directory the image was loaded from, making copying/renaming fotos rather tedious.  However, the Image Viewer does a more satisfying job of dealing with fotos than does the default Ubuntu image organizer, the F-Spot Photo Viewer, which can't show a slide show on this computer without crashing.

**"File Save As ..."** The first time you save a document in Ubuntu, the filename is hilighted in the File Save dialog box.  However, if you begin typing and expect what you type to replace the highlighted text, you will find you are actually issuing some sort of random commands.

**Flashcard multi-reader support** for the multi-reader on the right side is a bit dodgy in Ubuntu 9.04: you have to insert a USB flash drive after putting in an SD card in order for Ubuntu to see the former.  Generally, Ubuntu support for USB is more robust than support for multi-card readers.  To read an SD card reliably, I suggest you insert it into an external USB card reader adapter.

**Internet Radio** is not currently available on the DV2-1030 with Ubuntu. Attempting to download the [flash player plug-in from Adobe]("http://get.adobe.com/flashplayer/") results in an architecture error.

**Multiple windows for the same directory** Unlike even the oldest Macintosh O/S, windows are not 'owned' by directories in Ubuntu. This gets some getting used to, since if you are not careful, you can have windows all over the place showing the same info.

**Permissions** At random, Ubuntu declares a medium a "read-only file system", locking everything on it, and there is nothing you can do about it (opening the "properties" dialog and choosing "Permissions" just results in a "Sorry, could not change the permissions of <mediaName>: Error setting permissions: Read-only file system" error).  I'm glad I still have an old iBook, since I can then put in 2 USB flashdrives and copy from one to the "read-only" one in either Mac OS 9.4 or OS X.

[INDENT]Actually, this is a 'feature' in Ubuntu, not a bug; the O/S is designed to lock access to a drive if there is a hint of corruption (i.e., written to by alien O/S).  The Micro$oft NTFS format is not compatible with Ubuntu, but Fat32 is.  Fat32 has limits: 4GB per file and 32GB per partition.  [More info here]("https://answers.launchpad.net/ubuntu/+question/2436")[/INDENT]
*I will post the solution to this apparent problem when I define it better.  I have downloaded the [System Rescue CD]("http://www.sysresccd.org/") and will report here on what it can do for making disks writable.*

**Sound support for the built-in speakers** is not yet available, but the headphone jack works.  *I will document how to get sound working later.*

---

### Post by teuffel2 on 2010-01-29
Is anybody having difficulty with the wireless connection? I could not get it to work with 9.10 so I loaded 9.04. With 9.04 the wireless connection works but only intermittently. It will work then disconnect and then come back on again. Any suggestions would be appreciated.

---

### Post by ozorba on 2010-02-03
> **teuffel2 said:**
> Is anybody having difficulty with the wireless connection? I could not get it to work with 9.10 so I loaded 9.04. With 9.04 the wireless connection works but only intermittently. It will work then disconnect and then come back on again. Any suggestions would be appreciated.

I get problems once in a while. Especially when I download largish files during update or somewhere else for other use. 

I then cannot get it back with ifdown -a and ifup -a as su.

It is really puzzling.

---

### Post by leonlauncher on 2010-03-02
hi, i have just installed ubuntu on my  dv2, but the problem now is i dont know how to turn on the wireless, even after pressing the wireless button on the side the light is still orange.

any help would be great

---

### Post by alfu on 2010-06-21
Ubuntu 10.04 now supports sound out to the speakers of the DV2-1030us, but does not support wireless networking.

---

### Post by bangmalley on 2010-10-29
> **teuffel2 said:**
> Is anybody having difficulty with the wireless connection? I could not get it to work with 9.10 so I loaded 9.04. With 9.04 the wireless connection works but only intermittently. It will work then disconnect and then come back on again. Any suggestions would be appreciated.

I suggest using WICD.
WICD is pretty confusing to use for those familiar with Network-Manager
Unlike the preinstalled Network-Manager, you must type wireless key (WEP/WPA) before you click Connect. Network-Manager will ask you for the wireless key if you want to connect to particular AP, but WICD doesn't.

What you do is, on the WICD Network Manager, click on the "Properties", and type the wireless key, Apply, and you shall connect.

---

### Post by bangmalley on 2010-10-29
> **leonlauncher said:**
> hi, i have just installed ubuntu on my  dv2, but the problem now is i dont know how to turn on the wireless, even after pressing the wireless button on the side the light is still orange.

any help would be great

boot into vista/7 if you still have it.
use the Wireless Assistant to turn it on.

If you don't have Wireless Assistant, download the installer below (Compatible with Vista and 7, 32-bit and 64-bit):
[Wireless Assistant]("ftp://ftp.hp.com/pub/softpaq/sp48001-48500/sp48392.exe")

---

