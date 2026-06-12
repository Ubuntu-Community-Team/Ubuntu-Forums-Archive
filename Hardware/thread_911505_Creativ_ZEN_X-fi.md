---
title: "Creativ ZEN X-fi"
date: 2008-09-05
forum: Hardware
---

### Post by FPrefect42 on 2008-09-05
Hi Forum
I have just installed Hardy Heron and i am really impressed (coming from Debian).
I've just managed to install the Creative ZEN X-fi 8GB.

```
sudo apt-get install libmtp7 mtp-tools
```

In */etc/udev/rules.d/45-libnjb.rules* add:
```
# Creative Zen X-fi
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4162", GROUP="plugdev", MODE="0770"
```

In */etc/udev/rules.d/45-libmtp7.rules* add:
```
# Creative Zen X-fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="770", GROUP="audio"
```

It works with gnomad2 as user.

To mount the X-fi directly to a folder:
```
apt-get install mtpfs
mkdir /home/*username*/*folder*
mtpfs /home/*username*/*folder*
```

I couldn't get it work in Amarok, but i don't care, because normally i use the mtpfs-mount.
Greetz
Fordy

---

### Post by killersnowgoon on 2008-12-25
thanks man. i just got a 32gig zen xfi for christmas, this REALLY helped me out.

---

### Post by InFeh on 2008-12-26
Just got home from celebrating Christmas. Been dreading the mtp hell I'd go through to get it working, do a quick search, find this... I love you.

---

### Post by Si-Ddevil on 2008-12-30
Tried this the other day and "/etc/udev/rules.d/45-libnjb.rules " doesn't exist in my system...

so i created it with just that line (probs a retarded thing 2 do but hey, I was desperate) and I ended up having to reset my player...

can anyone help me here, relative linux noop here, even to i been running ubuntu since gutsy....

Si

---

### Post by jochenh on 2009-01-05
Hey!

You have to install libnjb too.

```
sudo apt-get install libnjb5
```

Greets,

Jochen

---

### Post by gresavage on 2009-01-12
i have a creative zen x-fi 16 GB, and after entering all the information and such, when i run sudo gnomad2 in terminal it sends me this:

Device 0 (VID=041e and PID=4162) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
Segmentation fault

the zen recognizes that its docked, but i can not connect to it

help!

oh yeah and im new at linux

---

### Post by IamI'mMe on 2009-01-20
Thanks for the lead, man!

I followed the steps and some errors occured that I could solve myself and helped me to get MyZen to work with both Amarok and Rhytmbox. Here we go...

I've created two starters to mount and unmount MyZen:

command: sudo mtpfs Zen-Xfi -o allow_other for mounting
command: sudo fusermount -u Zen-Xfi for unmounting

I've used these commands to get MyZen to work with Amarok and Rhytmbox.

In Amarok I've added a MTP Media device and provided the mount command to the pre connect and and unmount command to the post disconnect properties of the device. Connecting en disconnecting works fine. Other features of Amarok are still there for me to explore and to test.

Before starting Rhythmbox I mount MyZen. In Rhythmbox I browse to the appropriate folder at the Rhythmbox preferences, music tab. Closed it, et voila, I can play music with "the box" using MyZen.

Thanks to you and hope to be of any help to you.
Greetz

---

### Post by or4nge on 2009-01-25
Don't know if it could be useful but i've resolved my problem with gnomad mounting in that way:

Open a shell
Logged as root (with sudo su)
Executed gnomad2 in the shell and finally it recognises my zen x-fi :)

---

### Post by alezflute on 2009-02-02
By the way, sudo amarok also connected me to it

---

### Post by BaldAmI on 2009-02-08
I had this same problem (having to run gnomad2 or really any other mp3 syncing program as root). I did some investigating and I think there's a permissions error here

If you look at /etc/udev/rules.d/45-libnjb.rules you'll see that the group for the device is set to "audio". If you change it to "plugdev" for your device gnomad2 should run without root access. A normal Ubuntu user isn't in the audio group, but is in the plugdev group.

I'd assume that this same scenario might apply to an mtp device since it looks like /etc/udev/rules.d/45-libmtp.rules is setup the same way.

---

### Post by alezflute on 2009-02-09
After following all the instructions here (my version of libmtp is 8, not 7) mine works flawlessly with amarok, without needing sudo. However, when trying it with rhythmbox or banshee they didn't found it. When doing mtp-detect it appears but still as unknown device (without error messages, though). I guess it has something to do with the fact that in amarok you add an mtp-device manually while the others are supposed to find it on their own. Has anyone managed to get it to work with any gtk-player?

---

### Post by alezflute on 2009-03-17
Hi again, after some more research, i've been able to make my zen x-fi 8gb work flawlessly under banshee and rhythmbox (only tried a bit with exaile, and there seemed to be problems with pymtp version). I installed the last version of either player and got a libmtp8 0.3.6 from this [PPA]("https://launchpad.net/~glennric/+archive/ppa") Kudos for glennric, since it just works. I guess you can also compile libmtp8 yourself, but i couldn't manage to get it working and since glennric is last version of libmtp i found it easier to add it. Thanks to all

---

### Post by chubbtech on 2009-04-15
I followed instructions form this thread and looked-up another with no success untill I logged-in using gnome instead of kde and voilà gnomad2 works great!!! only 155MB left ;)

thx

---

### Post by Tyndie on 2009-04-22
Is there a definate set of instructions for setting up a x-fi player in ubuntu 8.1.0 and 9.0.4 now please?

---

### Post by alezflute on 2009-04-22
Well, i've switched to Arch so i don't know what the libmtp version in Jaunty is. Anyway, all you need is libmtp8 0.3.6 or superior (in arch it's 3.7, but with 3.6 it was working already) If the X-Fi isn't in the libmtp.rules, you can download the source code, ./configure it and make it, and it should create a new libmtp.rules which worked for me with 0.3.6 (.7 works flawlessly so far) After installing libmtp it should work with rhythmbox or banshee. With amarok you may have to add it (add new device). With exaile there's a problem with pymtp which i can't solve, apparently a new version of pymtp is needed. Hope this helps.

---

### Post by Tyndie on 2009-04-22
Is it possible you can provide a set of commands please, i am pretty new :)

---

### Post by SuperZ on 2009-04-23
Thanks so much guys! Just started out on ubuntu and was a bit dissapointed that it wasnt recognizing it, but now I read this it will be a lot easier. Thanks!

---

### Post by SuperZ on 2009-05-07
still having some trouble... i did what you said... it worked... but then i restarted my computer and it didnt work... going to see what happend wrong.

---

### Post by alezflute on 2009-05-15
As I said earlier, i've switched to Arch, so i'm not sure this will work. Last time I did, in intrepid, it did, so I think there shouldn't be any problem.

    Basically, to get a Zen X-Fi you need a libmtp 8 which version is superior to 0.3.5 and Gnomad2, Banshee, Rhythmbox or Amarok (those are the ones that worked for me). My version of libmtp is 0.3.7 and it works flawlessly. It's the version you will have in karmic. If you can't wait, you will have to either compile it yourself or add a PPA including the packages. I found it best to add a PPA, but it's your choice. The one I was using was Glennric's so the credit goes for him.

    For adding the PPA:

Open System &#8594; Administration &#8594; Software Sources and press Third Party Software.
There you have to add the two repo entries:

deb [http://ppa.launchpad.net/glennric/ppa/ubuntu](http://ppa.launchpad.net/glennric/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/glennric/ppa/ubuntu](http://ppa.launchpad.net/glennric/ppa/ubuntu) jaunty main

Of course, if you are in Jaunty, if not, you have to type intrepid instead ;)
You click Add Source for each one and when you reload, you will see there's an error because the repo isn't signed.

    Next we have to add the repo's key. 
Go [here]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6C843CCE8505D44B") and copy the text into a text editor (gedit, mousepad, kate, there are so many..) and save it to your hard drive. The name is up to you, but something like "glennric repo pgp key" comes to mind :)

Then we go to System->Administration->Software Sources and click the Authentication tab
Click Import Key File, select the key you saved earlier and you're done! 

    All that's left is to update the system packages and install libmtp from launchpad with Synaptic, alongside with mtp-tools and the player of your choice. Exaile won't work AFAIK since the pymtp package is too old and we have to wait for a new one to be released. Banshee in my view performs admirably, but Amarok and Rythmbox are quite good too.

    Since there are other ways some may prefer to add a new repo and its key, i'll give glennric's launchpad [page]("https://launchpad.net/~glennric/+archive/ppa") (also give thanks to him!). Of course, ubuntu backporting a new version of libmtp before karmic release would be quite nice, but i didn't have the slightest problem with PPAs in the past.

    You can test your libmtp by pluging your device and typing mtp-detect in a terminal. Usually it should connect to it without trouble; if your /etc/udev/rules.d/45-libmtp.rules doesn't have the Zen X-Fi in, you can just download the source from their [site]("http://libmtp.sourceforge.net/")
Doing ./configure and make will give you a libmtp.rules file to overwrite your local configuration (so, copying it and pasting where the old one was. Save the old one first!). Then you can retry mtp-detect. 

    Hope it's finally clear and works for everyone!

    Cheers

    alezflute

---

### Post by hbutu on 2009-06-03
First thank you alezflute for your tutorial. But I can't see any libmtp 8 0.3.7 (I have 0.3.0 installed) in system packages update nor in Synaptic Package Manager.
I run Jaunty amd64.

---

### Post by alezflute on 2009-06-04
Indeed, seems like Glennric removed them from his PPA. Until someone finds another PPA, or a way to backport the package, it seems to me that you'll need to download the source and compile. :(

I know there's a 3.7 package for karmic, so maybe there's a way to use it, changing the repos, updating the package information and installing only libmp and its dependencies, and then reverting the sources list. However, I'm not using Ubuntu anymore and I can't test it, so I won't recommend to try such a thing to anyone. Maybe there's some way to ask for people in Ubuntu to backport it to Jaunty, or maybe you can find it on someone else's PPA.

Edit:
I just found Savvas Radevic [PPA]("https://launchpad.net/~medigeek/+archive/experimental") with i383 and amd64 binaries, but it's highly experimental, so use it at your own risk. There are instructions to add it in their launchpad page, so it shouldn't pose any problem. You can, in case you just added the Glennric PPA remove it. Hope it works;)

---

### Post by hbutu on 2009-06-05
I did the trick and now it works as a charm.
Thank you.

---

### Post by I[AM]SMRT on 2009-08-03
I'm having problems with my Zen X-Fi freezing when I try to interact with it using mtp-detect or gnomad2 (banshee doesn't recognize that it's there). Running mtp-detect, it's able to finish but if I try to mtp-detect again afterwards, it's unable to do so:

```
brian@brian-laptop:~$ mtp-detect
libmtp version: 0.3.5

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN X-Fi (041e:4162) @ bus 0, dev 6
Attempting to connect device(s)
Error 2: PTP Layer error 02ff: get_all_metadata_fast(): could not get proplist of all objects.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: get_handles_recursively(): could not get object handles.
Error 2: (Look this up in ptp.h for an explanation.)
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4162
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 6
      Device entry info:
         Vendor: Creative
         Vendor id: 0x041e
         Product: ZEN X-Fi
         Vendor id: 0x4162
         Device flags: 0x00000000
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative ZEN X-Fi
   Device version: 1.04.08_1.03.03
   Serial number: 130300006B749DAF0002D409F474DDAF
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1012: Set object protection
   1016: Set device property value
   1017: Reset device property value
   1019: Move object
   101b: Get partial object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
Events supported:
   0x4006
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
   0xd001: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
   b901: WMA
   3008: MS Wave
   b904: Audible.com Codec
   b982: MP4
   ba03: Abstract Audio Album
   ba05: Abstract Audio Video Playlist
   ba01: Abstract Multimedia Album
   3801: JPEG
   300a: MS AVI
   300c: ASF
   b981: WMV
   bb83: vCard3
   be03: vCalendar2
   b802: Firmware
   3000: Undefined Type
   3001: Association/Directory
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 32127975424
      FreeSpaceInBytes: 6636306432
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 130300006B749DAF0002D409F474DDAF
Special directories:
   Default music folder: 0x00000000
   Default playlist folder: 0x00000000
   Default picture folder: 0x00000000
   Default video folder: 0x00000000
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00000000
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: (NULL)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)
ERROR: Could not close session!
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
OK.
brian@brian-laptop:~$ mtp-detect
libmtp version: 0.3.5

Listing raw device(s)
   No raw devices found.

```

---

### Post by alezflute on 2009-08-03
Well, as I see, your libmtp version is 3.5. Maybe your zen x-fi is freezing because libmtp-detect doesn't close well. I suggest you to try to upgrade to 3.6 version of libmtp (the one coming with ubuntu karmic). Either you [download]("http://packages.ubuntu.com/fi/karmic/libmtp8") and install it manually (maybe you'll have to uninstall your current libmtp first or change your sources.list, upgrade only this package (unless you want to get a hint of karmic alpha :D ) and then put your sources back. I think just downloading the package would be the most sensible idea. To install it, double-clicking should launch the package installer, or you go to its location in a terminal and sudo dpkg -i it. I don't know to what extent it would mess with your pc, but I think it should be just fine. Again, i don't have an ubuntu box to test it, since in Archlinux libmtp is updated almost since it got released. If it still doesn't work, verify you don't have any corrupted files on your creative player.

---

### Post by I[AM]SMRT on 2009-08-03
> **alezflute said:**
> Well, as I see, your libmtp version is 3.5. Maybe your zen x-fi is freezing because libmtp-detect doesn't close well. I suggest you to try to upgrade to 3.6 version of libmtp (the one coming with ubuntu karmic). Either you [download]("http://packages.ubuntu.com/fi/karmic/libmtp8") and install it manually (maybe you'll have to uninstall your current libmtp first or change your sources.list, upgrade only this package (unless you want to get a hint of karmic alpha :D ) and then put your sources back. I think just downloading the package would be the most sensible idea. To install it, double-clicking should launch the package installer, or you go to its location in a terminal and sudo dpkg -i it. I don't know to what extent it would mess with your pc, but I think it should be just fine. Again, i don't have an ubuntu box to test it, since in Archlinux libmtp is updated almost since it got released. If it still doesn't work, verify you don't have any corrupted files on your creative player.
Nope, it still freezes.

---

### Post by alezflute on 2009-08-04
Well, if you updated libmtp, and you have your libmtp rules (as it seems you do since otherwise the player wouldn't be recognized) i think you have a corrupted file which makes libmtp go crazy. I suggest to find a windows machine to try to connect with the creative software to see if there's something wrong like i said, or if you need some firmware upgrade. Mine worked flawlessly since the beginning, but if yours' firmware is different it may be the problem. In any case, keep posting the code you get to see if anyone else can help.

---

### Post by I[AM]SMRT on 2009-08-04
> **alezflute said:**
> Well, if you updated libmtp, and you have your libmtp rules (as it seems you do since otherwise the player wouldn't be recognized) i think you have a corrupted file which makes libmtp go crazy. I suggest to find a windows machine to try to connect with the creative software to see if there's something wrong like i said, or if you need some firmware upgrade. Mine worked flawlessly since the beginning, but if yours' firmware is different it may be the problem. In any case, keep posting the code you get to see if anyone else can help.
I usually update my mp3 player from my windows install and that's the only reason I'm still using windows. I'm pretty sure my firmware's up to date but I'll have to double check that. Maybe I'll wipe everything on the zen x-fi and put the stuff back on in case there are any corrupted files.

---

### Post by I[AM]SMRT on 2009-08-09
So I formatted my zen x-fi and now mtp-detect doesn't show *anything*.

```
brian@brian-laptop:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   No raw devices found.

```

---

### Post by bresdog on 2009-08-09
I've got my zen x-fi being recognised by gnomad2, alls good there. My problem is when transferring media from the x-fi to my laptop it'll transfer 1- 2 songs before gnomad2 then crashes. Anybody come across this before? I thought i was maybe trying to transfer too many files so i tested it using smaller amounts but the same thing keeps happening. Weird. 
Googled it and had a look around the forums but i couldn't see anything relative.
Thanks.

---

### Post by alezflute on 2009-08-09
> **'I[AM]SMRT said:**
> So I formatted my zen x-fi and now mtp-detect doesn't show *anything*.

```
brian@brian-laptop:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   No raw devices found.

```

I don't know how you did this, but your libmtp version is now too low. Before it was ok (0.3.5) although you may still need the libmtp rules for it to work. That you find out by typing mtp-detect and reading the outcome. It's all written before in the post. Hope it helps

---

### Post by I[AM]SMRT on 2009-08-09
> **alezflute said:**
> I don't know how you did this, but your libmtp version is now too low. Before it was ok (0.3.5) although you may still need the libmtp rules for it to work. That you find out by typing mtp-detect and reading the outcome. It's all written before in the post. Hope it helps
Yea, I reinstalled from the repos but it wasn't working before even with 0.3.5. The version of libmtp8 in the repos has support for the zen x-fi already built in.

---

### Post by alezflute on 2009-08-09
> **bresdog said:**
> I've got my zen x-fi being recognised by gnomad2, alls good there. My problem is when transferring media from the x-fi to my laptop it'll transfer 1- 2 songs before gnomad2 then crashes. Anybody come across this before? I thought i was maybe trying to transfer too many files so i tested it using smaller amounts but the same thing keeps happening. Weird. 
Googled it and had a look around the forums but i couldn't see anything relative.
Thanks.

Please post the mtp-detect outcome (open terminal, plug your device, wait a moment for it to get started and then type mtp-detect) as it gives the useful information. I think i've read something like your problem due to a too old version of libmtp (or maybe bad udev rules, can't remember right now) Cheers.

---

### Post by bresdog on 2009-08-09
Heres the info -

>    9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
Events supported:
   0x4006
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
   0xd001: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b901: WMA
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b904: Audible.com Codec
      da01: unknown(da01) UINT32 data type enumeration: 2, 3, 4,  GET/SET
      da02: unknown(da02) array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: unknown(da03) UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b982: MP4
      de99: AudioWAVECodec UINT32 data type enumeration: 41222,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   ba03: Abstract Audio Album
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 24576, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   ba01: Abstract Multimedia Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 3328, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 4992, STEP 1 GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   300a: MS AVI
      de99: AudioWAVECodec UINT32 data type enumeration: 85, 17, 1,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 1536000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 4000000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 844515635, 878070084, 1482049860, 808802372, 1196444237, 1145656920,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 3000000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   300c: ASF
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b981: WMV
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   bb83: vCard3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   be03: vCalendar2
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b802: Firmware
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 8031797248
      FreeSpaceInBytes: 3047424
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 49000001F90E46360002D8D2C6BA4636
Special directories:
   Default music folder: 0x00000057
   Default playlist folder: 0x0000005b
   Default picture folder: 0x00000067
   Default video folder: 0x0000006b
   Default organizer folder: 0x00000063
   Default zencast folder: 0x00000073
   Default album folder: 0x000002cd
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: My ZEN
   Synchronization partner: {00000000-0000-0000-0000-000000000000}
   Battery level 229 of 255 (89%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20090809 18:23:53Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AQAASTZGDvnS2AIANka6xgAAAAA=</UNIQUEID><PUBLICKEY private="1">SZmnRyScwxinEtHGWmZrAZRwAQHCaePNI1ylWBVQvHODBVtM4DMbaQ==</PUBLICKEY><KEYDATA>KPsML9sNGqlWRS/5YAiTGp8g0YY=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>d9o/rFVQAhyLZqsyCR2MWCgY1VmLwlFeo4DUp/4fTqgN/FJqmqseXA==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>ZStwAhlMpxoAXzNvFp+BqvI66LE=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.108.193</SECURITYVERSION><CERTIFICATE private="1">SZmnRyScwxinEtHGWmZrAZRwAQHCaePNI1ylWBVQvHODBVtM4DMbaQIEbMFCPG53k57Z13AcKfCcMqI+Kaf2Ykhy61RtkuJ5UxzPi2yHo0m0NdgD</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative ZEN</NAME>
  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>
  <MODEL>DVP-FL0001</MODEL>
  <SECURITYLEVEL>2000</SECURITYLEVEL>
  <HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR>
  <HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR>
  <FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR>
  <FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR>
  <FEATURES>
    <CLOCK>2</CLOCK>
    <SECURECLOCK>
      <URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL>
      <PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY>
    </SECURECLOCK>
    <METERING>1</METERING>
    <LICENSE_ACQ>0</LICENSE_ACQ>
    <LICENSE_SYNC>1</LICENSE_SYNC>
    <ENCRYPTION>0</ENCRYPTION>
    <SYMMETRIC_OPT>1</SYMMETRIC_OPT>
  </FEATURES>
  <LIMITS>
    <MAXCHAINDEPTH>2</MAXCHAINDEPTH>
    <MAXLICENSESIZE>10240</MAXLICENSESIZE>
    <MAXHEADERSIZE>5120</MAXHEADERSIZE>
  </LIMITS><PUBLICKEY>01jSNo4LLYCkLWpnsvVOxk1wvxbm2krcn20LgpXL9Zf91opCNsMyAQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>DrK/bNN2aO5ImZHdepevdhlT6UePVcdaxTWOMvw/8RYKeQFjSPwWUw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>2085</AUTH_ID><PUBLICKEY>U3xlv/ZHjD1bOwjB+VKpZuAf3UI+x+5XtTYc7TvHKdQeGpyFrOmOEw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>iBzmFZxhy/VC9d2REO5iicO+dguqv8zhB7QPZe0JOj7BNKAwmrQoew==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>Ko25GwcWTT0R8xP4rS9+h4Z/EHX03y7Gb/281mD8U0nQGG3Rk9O+TA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>

Device description WMPInfo.xml file:
<DeviceInfo>
    <WMP DeviceID="{6F98E0BD-C318-4C1F-99A8-734E5D631387}" RelationshipID="{00000000-0000-0000-0000-000000000000}"/>
</DeviceInfo>

PTP: Closing session
OK.


If I remember correctly when i was trying to get it working i installed lib-mtp8. And in the udev/rules i entered these-
/lib/udev/rules.d/45-libmtp8.rules.

# Creative Zen X-fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

# Creative Zen X-fi
ATTRS{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"

/lib/udev/rules.d/45-libnjb.rules

# Creative Zen X-fi
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4162", GROUP="plugdev", MODE="0660"
Then i put both in /etc/udev/rules.d.

Thanks

---

### Post by alezflute on 2009-08-09
It seems to me that you didn't copy the whole outcome of mtp-detect, since i can't see what your libmtp version is. If you're over 0.3.5 it should be ok, and i can only suggest you to try it with banshee or amarok (those are the better working ones in my experience). To make it work with python and pymtp (mtp bindings) you need a patch from [here]("https://bugs.gpodder.org/show_bug.cgi?id=307") . I managed to make it work, but since i couldn't still transfer podcasts, i went back to banshee (does everything for me in an up-to-date Archlinux)

---

### Post by bresdog on 2009-08-09
That was the whole thing, not sure what happened there. Anyways ran it again without the zen plugged in. And it came up, the version is 0.3.0. Im assuming im going to have to get the most recent? I tried both amarok and banshee and it didn't recognise that anything was connected.

---

### Post by xaco1234 on 2009-08-09
Anyone got a good sulotion on how to add videos to this thing yet?

---

### Post by alezflute on 2009-08-10
> **bresdog said:**
> That was the whole thing, not sure what happened there. Anyways ran it again without the zen plugged in. And it came up, the version is 0.3.0. Im assuming im going to have to get the most recent? I tried both amarok and banshee and it didn't recognise that anything was connected.

Yes, you need at least 0.3.5 to make it work (in my experience, i wonder if a really good hacker could make it work :guitar: ) You can read the thread to find out how to get the 0.3.6 version (that's better in my view) by downloading from Karmic repos. You can also search if someone else has it on a ppa, but i think it will be better anyway to use the karmic version. I don't know if someone has backported it to Jaunty, so maybe take a look at backports too.



@ xaco

I transfered some videos with banshee, but you will have to find the correct format and resolution for you creative, otherwise it won't be able to play it.

---

### Post by bresdog on 2009-08-10
Thanks man!

---

### Post by I[AM]SMRT on 2009-08-17
I've actually switched over to Arch (had been planning on doing it for a while) but I still can't get this thing working :(. I have to run mtp-detect as root for it to recognize that the mp3 player is connected. It no longer freezes mid-mtp-detect but I still can't transfer music to it. Here's my mtp-detect output:

```
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN X-Fi (041e:4162) @ bus 0, dev 3
Attempting to connect device(s)
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4162
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 3
      Device entry info:
         Vendor: Creative
         Vendor id: 0x041e
         Product: ZEN X-Fi
         Vendor id: 0x4162
         Device flags: 0x00000000
Microsoft device descriptor 0xee:
	0000: 1203 4d00 5300 4600 5400 3100 3000 3000	..M.S.F.T.1.0.0.
	0010: fe00                                   	..
Microsoft device response to control message 1, CMD 0xfe:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000                    	........
Microsoft device response to control message 2, CMD 0xfe:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000                    	........
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative ZEN X-Fi
   Device version: 1.04.08_1.03.03
   Serial number: 130300006B749DAF0002D409F474DDAF
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1012: Set object protection
   1016: Set device property value
   1017: Reset device property value
   1019: Move object
   101b: Get partial object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
Events supported:
   0x4006
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
   0xd001: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b901: WMA
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b904: Audible.com Codec
      da01: unknown(da01) UINT32 data type enumeration: 2, 3, 4,  GET/SET
      da02: unknown(da02) array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: unknown(da03) UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b982: MP4
      de99: AudioWAVECodec UINT32 data type enumeration: 41222,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type DATETIME FORM GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc42: SyncID STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   ba03: Abstract Audio Album
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 24576, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 180, STEP 1 READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   ba01: Abstract Multimedia Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 3328, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 4992, STEP 1 GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   300a: MS AVI
      de99: AudioWAVECodec UINT32 data type enumeration: 85, 17, 1,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 1536000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 4000000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 844515635, 878070084, 1482049860, 808802372, 1196444237, 1145656920,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 3000000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   300c: ASF
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b981: WMV
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   bb83: vCard3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   be03: vCalendar2
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   b802: Firmware
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc44: Name STRING data type GET/SET
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc07: ObjectFileName STRING data type REGULAR EXPRESSION FORM GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1, 32771,  READ ONLY
      dc0d: Hidden UINT16 data type enumeration: 0, 1,  GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 32127975424
      FreeSpaceInBytes: 6228901888
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 130300006B749DAF0002D409F474DDAF
Special directories:
   Default music folder: 0x0000005a
   Default playlist folder: 0x000c0f7c
   Default picture folder: 0x0000006a
   Default video folder: 0x0000006e
   Default organizer folder: 0x00000066
   Default zencast folder: 0x00000076
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: Brian
   Synchronization partner: (NULL)
   Battery level 229 of 255 (89%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20090312 20:31:38Z#</VALUE><FLAG>DRM_CLK_NOT_SET</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AAADE6+ddGsJ1AIAr9109AAAAAA=</UNIQUEID><PUBLICKEY private="1">Jo4dzwy0Ij3fWPsmykaKk71Lmlj1xJJQC7ZO5+TUlHZ/zF+OKh54UQ==</PUBLICKEY><KEYDATA>e6C/I6Dbs0bE6S0AX9ZFmn5qJvc=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>jOLb0DrARwYxqYL4FfjQqCklC4cXojFxuz+EnPqaxi19F18MRRFTNg==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>qkPlEgbw8jVtWov4q5K+7QJdnbY=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.108.193</SECURITYVERSION><CERTIFICATE private="1">Jo4dzwy0Ij3fWPsmykaKk71Lmlj1xJJQC7ZO5+TUlHZ/zF+OKh54UQIEbMEPhCAoUNEoOURte/OTBoCEakBOVfkhG1I1FzQE6Uyxava6TcLytiF8</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative ZEN</NAME>

  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>

  <MODEL>DVP-FL0001</MODEL>

  <SECURITYLEVEL>2000</SECURITYLEVEL>

  <HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR>

  <HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR>

  <FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR>

  <FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR>

  <FEATURES>

    <CLOCK>2</CLOCK>

    <SECURECLOCK>

      <URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL>

      <PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY>

    </SECURECLOCK>

    <METERING>1</METERING>

    <LICENSE_ACQ>0</LICENSE_ACQ>

    <LICENSE_SYNC>1</LICENSE_SYNC>

    <ENCRYPTION>0</ENCRYPTION>

    <SYMMETRIC_OPT>1</SYMMETRIC_OPT>

  </FEATURES>

  <LIMITS>

    <MAXCHAINDEPTH>2</MAXCHAINDEPTH>

    <MAXLICENSESIZE>10240</MAXLICENSESIZE>

    <MAXHEADERSIZE>5120</MAXHEADERSIZE>

  </LIMITS><PUBLICKEY>01jSNo4LLYCkLWpnsvVOxk1wvxbm2krcn20LgpXL9Zf91opCNsMyAQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>DrK/bNN2aO5ImZHdepevdhlT6UePVcdaxTWOMvw/8RYKeQFjSPwWUw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>2085</AUTH_ID><PUBLICKEY>U3xlv/ZHjD1bOwjB+VKpZuAf3UI+x+5XtTYc7TvHKdQeGpyFrOmOEw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>iBzmFZxhy/VC9d2REO5iicO+dguqv8zhB7QPZe0JOj7BNKAwmrQoew==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>Ko25GwcWTT0R8xP4rS9+h4Z/EHX03y7Gb/281mD8U0nQGG3Rk9O+TA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
OK.
```

EDIT: Hahah, wow, now a lot of the fonts on the zen x-fi are all messed up. They're readable but there are some strange things going on, a few characters (t's and g's) look almost like subscripts and the font itself looks...grainy.

EDIT #2: It auto-detects the zen x-fi now, I added myself to the cameras group:

```
gpasswd -a <user name> cameras
```

Now how do I transfer files to it with banshee?

---

### Post by I[AM]SMRT on 2009-08-18
I don't know what happened but mtp-detect no longer works, here's my output:

```
brian@brian-laptop:~$ mtp-detect
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN X-Fi (041e:4162) @ bus 0, dev 6
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

```

EDIT: Hacked around it, have to unmount the device from nautilus first:

[https://answers.launchpad.net/ubuntu/+question/69910](https://answers.launchpad.net/ubuntu/+question/69910)

EDIT #2: Songs transferred to the device don't actually stay there because I can't actually unmount. Awesome. Plus they don't transfer the correct metadata of the songs, my music folder is formatted Artist -> Album -> Song so it takes the album as the artist name. Really gotdamn annoying.

---

### Post by alezflute on 2009-08-18
Did you add yourself to the relevant groups? you may have to add yourself to audio and storage groups (at least) as well as checking if the udev rules are ok (they should be). You can also read several threads in Archlinux Forums such as [this one]("http://bbs.archlinux.org/viewtopic.php?id=43354") To begin with, which desktop and program are you using to connect? I have mine on xfce and banshee (best support for podcast and transfers for me) You will need a patch if you want to use a python (as exaile) music manager. Gnomad2 (in the AUR, i think) works flawlessly and is a very useful, if rudimentary tool. Amarok 2 works ok as long as you don't mind transfering podcasts (which i wasn't able to do). Mine works under gnome, xfce and kde/kdemod. So:
- check if you can connect as root, which usually means a group problem that you can solve by adding your user to the group and re-login. If it helps you, i'm added to disk,lp,wheel, games, network, video, audio, optical, floppy, storage and hal groups, although i don't think all of them are needed. Always check the device to be ready, not already connected of busy.
-if you can't, you need a correct udev rules or a new libmtp version, but i think that's not the problem :)

Hope it all helps

---

### Post by I[AM]SMRT on 2009-08-18
I've added myself to "storage" and "audio", the corresponding groups in my libnjb and libmtp udev rules files. I've also added myself to the "camera" group because I've found that without it, I can only use sudo mtp-detect. That's not really my issue, now whenever I try to mtp-detect or anything, the device freezes (going from docked -> blank screen and unresponsive) and requires a hard reset, my computer can't do anything with the zen while it's frozen. 

I'm using gnome and banshee.

I have to unmount the device from nautilus before I can do anything with mtp-detect, otherwise mtp-detect says the device is busy.

Sometimes it'll randomly work in banshee but I have no idea when and things will often freeze so I actually get nowhere.

Here's my mtp-detect, it froze in the middle of it:

```
brian@brian-laptop:~$ mtp-detect
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN X-Fi (041e:4162) @ bus 0, dev 6
Attempting to connect device(s)
Error 2: PTP Layer error 02ff: get_all_metadata_fast(): could not get proplist of all objects.
Error 2: (Look this up in ptp.h for an explanation.)
Error 2: PTP Layer error 02ff: get_handles_recursively(): could not get object handles.
Error 2: (Look this up in ptp.h for an explanation.)
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4162
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 6
      Device entry info:
         Vendor: Creative
         Vendor id: 0x041e
         Product: ZEN X-Fi
         Vendor id: 0x4162
         Device flags: 0x00000000
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative ZEN X-Fi
   Device version: 1.04.08_1.03.03
   Serial number: 130300006B749DAF0002D409F474DDAF
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1012: Set object protection
   1016: Set device property value
   1017: Reset device property value
   1019: Move object
   101b: Get partial object
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
Events supported:
   0x4006
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
   0xd001: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
   b901: WMA
   3008: MS Wave
   b904: Audible.com Codec
   b982: MP4
   ba03: Abstract Audio Album
   ba05: Abstract Audio Video Playlist
   ba01: Abstract Multimedia Album
   3801: JPEG
   300a: MS AVI
   300c: ASF
   b981: WMV
   bb83: vCard3
   be03: vCalendar2
   b802: Firmware
   3000: Undefined Type
   3001: Association/Directory
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003 fixed RAM storage
      FilesystemType: 0x0002 generic hierarchical
      AccessCapability: 0x0000 read/write
      MaxCapacity: 32127975424
      FreeSpaceInBytes: 6209175552
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 130300006B749DAF0002D409F474DDAF
Special directories:
   Default music folder: 0x00000000
   Default playlist folder: 0x00000000
   Default picture folder: 0x00000000
   Default video folder: 0x00000000
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00000000
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: (NULL)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)
ERROR: Could not close session!
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
OK.

```

I may be getting somewhere, how do I prevent the device from being automounted in nautilus?

EDIT: I just connect it now and it freezes after about ~10 seconds. It then pops up in banshee after a few minutes but nothing can be done with it because it's frozen. Can't synchronize, can't unmount cleanly. Here's my dmesg:

```
brian@brian-laptop:~$ dmesg | tail
usb 1-3: device descriptor read/64, error -71
usb 1-3: new high speed USB device using ehci_hcd and address 7
usb 1-3: device descriptor read/64, error -71
usb 1-3: device descriptor read/64, error -71
usb 1-3: new high speed USB device using ehci_hcd and address 8
usb 1-3: device not accepting address 8, error -71
usb 1-3: new high speed USB device using ehci_hcd and address 9
usb 1-3: device not accepting address 9, error -71
hub 1-0:1.0: unable to enumerate USB device on port 3
usb 3-1: new full speed USB device using uhci_hcd and address 2

```

EDIT #134234: It's gotta be an issue with libmtp because when I remove myself from cameras and sudo mtp-detect, the player freezes. Here's my 45-libnjb.rules file:

```
SUBSYSTEM!="usb_device", GOTO="libnjb_rules_end"

# Creative Nomad Jukebox
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="0222", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox 2
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4100", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox 3
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4101", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox Zen
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4108", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox Zen USB 2.0
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="410b", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox Zen NX
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4109", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox Zen Xtra
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4110", GROUP="storage", MODE="0660"
# Dell Digital Jukebox
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4111", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox Zen Touch
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411b", GROUP="storage", MODE="0660"
# Creative Nomad Jukebox Zen Micro
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411e", GROUP="storage", MODE="0660"
# Second Generation Dell Digital Jukebox
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4126", GROUP="storage", MODE="0660"
# Dell Pocket DJ
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4127", GROUP="storage", MODE="0660"
# Creative Zen Sleek
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4136", GROUP="storage", MODE="0660"
# Creative Zen X-fi
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4162", GROUP="storage", MODE="0770"

LABEL="libnjb_rules_end"
```

and my 45-libmtp.rules file:

```
# UDEV-style hotplug map for libmtp
# Put this file in /etc/udev/rules.d

ACTION!="add", GOTO="libmtp_rules_end"
ATTR{dev}!="?*", GOTO="libmtp_rules_end"
SUBSYSTEM=="usb", GOTO="libmtp_usb_rules"
# The following thing will be deprecated when older kernels are phased out.
SUBSYSTEM=="usb_device", GOTO="libmtp_usb_device_rules"
GOTO="libmtp_rules_end"

LABEL="libmtp_usb_rules"

# Creative ZEN Vision
ATTR{idVendor}=="041e", ATTR{idProduct}=="411f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative Portable Media Center
ATTR{idVendor}=="041e", ATTR{idProduct}=="4123", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Xtra (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4128", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dell DJ (2nd generation)
ATTR{idVendor}=="041e", ATTR{idProduct}=="412f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Micro (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4130", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Touch (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4131", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dell Dell Pocket DJ (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4132", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Sleek (MTP mode)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4137", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN MicroPhoto
ATTR{idVendor}=="041e", ATTR{idProduct}=="413c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Sleek Photo
ATTR{idVendor}=="041e", ATTR{idProduct}=="413d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Vision:M
ATTR{idVendor}=="041e", ATTR{idProduct}=="413e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN V
ATTR{idVendor}=="041e", ATTR{idProduct}=="4150", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Vision:M (DVP-HD0004)
ATTR{idVendor}=="041e", ATTR{idProduct}=="4151", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN V Plus
ATTR{idVendor}=="041e", ATTR{idProduct}=="4152", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Vision W
ATTR{idVendor}=="041e", ATTR{idProduct}=="4153", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN 8GB
ATTR{idVendor}=="041e", ATTR{idProduct}=="4157", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN V 2GB
ATTR{idVendor}=="041e", ATTR{idProduct}=="4158", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative Zen X-fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="770", GROUP="audio"
# Samsung YP-900
ATTR{idVendor}=="04e8", ATTR{idProduct}=="0409", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-920
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5022", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-925GS
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5024", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-820
ATTR{idVendor}=="04e8", ATTR{idProduct}=="502e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-925(-GS)
ATTR{idVendor}=="04e8", ATTR{idProduct}=="502f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-J70J
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5033", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-Z5
ATTR{idVendor}=="04e8", ATTR{idProduct}=="503c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-Z5 2GB
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5041", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-T7J
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5047", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-U2J (YP-U2JXB/XAA)
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5054", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-F2J
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5057", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-K5
ATTR{idVendor}=="04e8", ATTR{idProduct}=="505a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-U3
ATTR{idVendor}=="04e8", ATTR{idProduct}=="507d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-T9
ATTR{idVendor}=="04e8", ATTR{idProduct}=="507f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-K3
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5081", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-P2
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5083", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-T10
ATTR{idVendor}=="04e8", ATTR{idProduct}=="508a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-999 Portable Media Center/SGH-A707/SGH-L760V
ATTR{idVendor}=="04e8", ATTR{idProduct}=="5a0f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung X830 Mobile Phone
ATTR{idVendor}=="04e8", ATTR{idProduct}=="6702", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung U600 Mobile Phone
ATTR{idVendor}=="04e8", ATTR{idProduct}=="6709", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung Juke (SCH-U470)
ATTR{idVendor}=="04e8", ATTR{idProduct}=="6734", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Intel Bandon Portable Media Center
ATTR{idVendor}=="045e", ATTR{idProduct}=="00c9", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# JVC Alneo XA-HD500
ATTR{idVendor}=="04f1", ATTR{idProduct}=="6105", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD6320/00 or HDD6330/17
ATTR{idVendor}=="0471", ATTR{idProduct}=="014b", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD1630/17
ATTR{idVendor}=="0471", ATTR{idProduct}=="014c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD085/00 or HDD082/17
ATTR{idVendor}=="0471", ATTR{idProduct}=="014d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips GoGear SA9200
ATTR{idVendor}=="0471", ATTR{idProduct}=="014f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips SA1115/55
ATTR{idVendor}=="0471", ATTR{idProduct}=="0164", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips GoGear Audio
ATTR{idVendor}=="0471", ATTR{idProduct}=="0165", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips Shoqbox
ATTR{idVendor}=="0471", ATTR{idProduct}=="0172", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips PSA610
ATTR{idVendor}=="0471", ATTR{idProduct}=="0181", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD6320
ATTR{idVendor}=="0471", ATTR{idProduct}=="01eb", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips SA6014/SA6015/SA6024/SA6025/SA6044/SA6045
ATTR{idVendor}=="0471", ATTR{idProduct}=="084e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips SA5145
ATTR{idVendor}=="0471", ATTR{idProduct}=="0857", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips PSA235
ATTR{idVendor}=="0471", ATTR{idProduct}=="7e01", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa m230/m240
ATTR{idVendor}=="0781", ATTR{idProduct}=="7400", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa c150
ATTR{idVendor}=="0781", ATTR{idProduct}=="7410", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e200/e250/e260/e270/e280
ATTR{idVendor}=="0781", ATTR{idProduct}=="7420", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e280
ATTR{idVendor}=="0781", ATTR{idProduct}=="7421", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e280 v2
ATTR{idVendor}=="0781", ATTR{idProduct}=="7422", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa m240
ATTR{idVendor}=="0781", ATTR{idProduct}=="7430", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa Clip
ATTR{idVendor}=="0781", ATTR{idProduct}=="7432", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa c240/c250
ATTR{idVendor}=="0781", ATTR{idProduct}=="7450", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa Express
ATTR{idVendor}=="0781", ATTR{idProduct}=="7460", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa Connect
ATTR{idVendor}=="0781", ATTR{idProduct}=="7480", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa View
ATTR{idVendor}=="0781", ATTR{idProduct}=="74b0", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Portable Media Center
ATTR{idVendor}=="1006", ATTR{idProduct}=="4002", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Portable Media Center
ATTR{idVendor}=="1006", ATTR{idProduct}=="4003", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver iFP-880
ATTR{idVendor}=="4102", ATTR{idProduct}=="1008", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T10
ATTR{idVendor}=="4102", ATTR{idProduct}=="1113", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T20 FM
ATTR{idVendor}=="4102", ATTR{idProduct}=="1114", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T20
ATTR{idVendor}=="4102", ATTR{idProduct}=="1115", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver U10
ATTR{idVendor}=="4102", ATTR{idProduct}=="1116", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T10a
ATTR{idVendor}=="4102", ATTR{idProduct}=="1117", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T20
ATTR{idVendor}=="4102", ATTR{idProduct}=="1118", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T30
ATTR{idVendor}=="4102", ATTR{idProduct}=="1119", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T10 2GB
ATTR{idVendor}=="4102", ATTR{idProduct}=="1120", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver N12
ATTR{idVendor}=="4102", ATTR{idProduct}=="1122", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Clix2
ATTR{idVendor}=="4102", ATTR{idProduct}=="1126", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Clix
ATTR{idVendor}=="4102", ATTR{idProduct}=="112a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver X20
ATTR{idVendor}=="4102", ATTR{idProduct}=="1132", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T60
ATTR{idVendor}=="4102", ATTR{idProduct}=="1134", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver H10 20GB
ATTR{idVendor}=="4102", ATTR{idProduct}=="2101", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver H10
ATTR{idVendor}=="4102", ATTR{idProduct}=="2102", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dell, Inc DJ Itty
ATTR{idVendor}=="413c", ATTR{idProduct}=="4500", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat MEGF-40
ATTR{idVendor}=="0930", ATTR{idProduct}=="0009", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat
ATTR{idVendor}=="0930", ATTR{idProduct}=="000c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat P20
ATTR{idVendor}=="0930", ATTR{idProduct}=="000f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat S
ATTR{idVendor}=="0930", ATTR{idProduct}=="0010", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat P10
ATTR{idVendor}=="0930", ATTR{idProduct}=="0011", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat V30
ATTR{idVendor}=="0930", ATTR{idProduct}=="0014", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat U
ATTR{idVendor}=="0930", ATTR{idProduct}=="0016", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat MEU202
ATTR{idVendor}=="0930", ATTR{idProduct}=="0018", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat T
ATTR{idVendor}=="0930", ATTR{idProduct}=="0019", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos Gmini XS100
ATTR{idVendor}=="0e79", ATTR{idProduct}=="1207", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos XS202 (MTP mode)
ATTR{idVendor}=="0e79", ATTR{idProduct}=="1208", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 104 (MTP mode)
ATTR{idVendor}=="0e79", ATTR{idProduct}=="120a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 404 (MTP mode)
ATTR{idVendor}=="0e79", ATTR{idProduct}=="1301", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 504 (MTP mode)
ATTR{idVendor}=="0e79", ATTR{idProduct}=="1307", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 704 mobile dvr
ATTR{idVendor}=="0e79", ATTR{idProduct}=="130d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 605 (MTP mode)
ATTR{idVendor}=="0e79", ATTR{idProduct}=="1313", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dunlop MP3 player 1GB / EGOMAN MD223AFD
ATTR{idVendor}=="10d6", ATTR{idProduct}=="2200", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Microsoft Zune
ATTR{idVendor}=="045e", ATTR{idProduct}=="0710", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sirius Stiletto
ATTR{idVendor}=="18f6", ATTR{idProduct}=="0102", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Canon PowerShot A640 (PTP/MTP mode)
ATTR{idVendor}=="04a9", ATTR{idProduct}=="3139", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia 3110c Mobile Phone
ATTR{idVendor}=="0421", ATTR{idProduct}=="005f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N95 Mobile Phone 8GB
ATTR{idVendor}=="0421", ATTR{idProduct}=="006e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia 5300 Mobile Phone
ATTR{idVendor}=="0421", ATTR{idProduct}=="04ba", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N73 Mobile Phone
ATTR{idVendor}=="0421", ATTR{idProduct}=="04d1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N75 Mobile Phone
ATTR{idVendor}=="0421", ATTR{idProduct}=="04e1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N95 Mobile Phone
ATTR{idVendor}=="0421", ATTR{idProduct}=="04ef", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N80 Internet Edition (Media Player)
ATTR{idVendor}=="0421", ATTR{idProduct}=="04f1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Logik LOG DAX MP3 and DAB Player
ATTR{idVendor}=="13d1", ATTR{idProduct}=="7002", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson EM28 Series
ATTR{idVendor}=="069b", ATTR{idProduct}=="0774", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson / RCA Opal / Lyra MC4002
ATTR{idVendor}=="069b", ATTR{idProduct}=="0777", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson RCA H106
ATTR{idVendor}=="069b", ATTR{idProduct}=="301a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson scenium E308
ATTR{idVendor}=="069b", ATTR{idProduct}=="3028", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson / RCA Lyra HC308A
ATTR{idVendor}=="069b", ATTR{idProduct}=="3035", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# FOMA F903iX HIGH-SPEED
ATTR{idVendor}=="04c5", ATTR{idProduct}=="1140", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Palm / Handspring Pocket Tunes
ATTR{idVendor}=="1703", ATTR{idProduct}=="0001", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Palm Handspring Pocket Tunes 4
ATTR{idVendor}=="1703", ATTR{idProduct}=="0002", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# TrekStor Vibez 8/12GB
ATTR{idVendor}=="066f", ATTR{idProduct}=="842a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# TrekStor i.Beat Sweez FM
ATTR{idVendor}=="0402", ATTR{idProduct}=="0611", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Disney MixMax
ATTR{idVendor}=="0aa6", ATTR{idProduct}=="6021", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Tevion MD 81488
ATTR{idVendor}=="0aa6", ATTR{idProduct}=="3011", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Cowon iAudio U3 (MTP mode)
ATTR{idVendor}=="0e21", ATTR{idProduct}=="0701", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Cowon iAudio 7 (MTP mode)
ATTR{idVendor}=="0e21", ATTR{idProduct}=="0751", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Cowon iAudio D2 (MTP mode)
ATTR{idVendor}=="0e21", ATTR{idProduct}=="0801", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Insignia NS-DV45
ATTR{idVendor}=="19ff", ATTR{idProduct}=="0303", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Insignia Sport Player
ATTR{idVendor}=="19ff", ATTR{idProduct}=="0307", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Insignia Pilot 4GB
ATTR{idVendor}=="19ff", ATTR{idProduct}=="0309", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# LG UP3
ATTR{idVendor}=="043e", ATTR{idProduct}=="70b1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sony Walkman NWZ-A815/NWZ-A818
ATTR{idVendor}=="054c", ATTR{idProduct}=="0325", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sony Walkman NWZ-S516
ATTR{idVendor}=="054c", ATTR{idProduct}=="0326", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sony Walkman NWZ-S615F/NWZ-S618F
ATTR{idVendor}=="054c", ATTR{idProduct}=="0327", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SonyEricsson K850i
ATTR{idVendor}=="0fce", ATTR{idProduct}=="0075", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SonyEricsson W910
ATTR{idVendor}=="0fce", ATTR{idProduct}=="0076", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Motorola K1
ATTR{idVendor}=="22b8", ATTR{idProduct}=="4811", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Motorola A1200
ATTR{idVendor}=="22b8", ATTR{idProduct}=="60ca", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Motorola RAZR2 V8
ATTR{idVendor}=="22b8", ATTR{idProduct}=="6415", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Kenwood Media Keg HD10GB7 Sport Player
ATTR{idVendor}=="0b28", ATTR{idProduct}=="100c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Micro-Star International P610/Model MS-5557
ATTR{idVendor}=="0db0", ATTR{idProduct}=="5572", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Isabella Her Prototype
ATTR{idVendor}=="0b20", ATTR{idProduct}=="ddee", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
GOTO="libmtp_rules_end"

LABEL="libmtp_usb_device_rules"
# Creative ZEN Vision
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="411f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative Portable Media Center
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4123", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Xtra (MTP mode)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4128", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dell DJ (2nd generation)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="412f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Micro (MTP mode)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4130", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Touch (MTP mode)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4131", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dell Dell Pocket DJ (MTP mode)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4132", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Sleek (MTP mode)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4137", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN MicroPhoto
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="413c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Sleek Photo
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="413d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Vision:M
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="413e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN V
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4150", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Vision:M (DVP-HD0004)
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4151", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN V Plus
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4152", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN Vision W
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4153", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN 8GB
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4157", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative ZEN V 2GB
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4158", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative Zen X-fi
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="770", GROUP="audio"
# Samsung YP-900
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="0409", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-920
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5022", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-925GS
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5024", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-820
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="502e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-925(-GS)
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="502f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-J70J
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5033", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-Z5
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="503c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-Z5 2GB
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5041", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-T7J
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5047", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-U2J (YP-U2JXB/XAA)
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5054", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-F2J
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5057", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-K5
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="505a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-U3
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="507d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-T9
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="507f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-K3
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5081", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-P2
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5083", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YP-T10
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="508a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung YH-999 Portable Media Center/SGH-A707/SGH-L760V
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="5a0f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung X830 Mobile Phone
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="6702", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung U600 Mobile Phone
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="6709", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Samsung Juke (SCH-U470)
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="6734", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Intel Bandon Portable Media Center
ATTRS{idVendor}=="045e", ATTRS{idProduct}=="00c9", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# JVC Alneo XA-HD500
ATTRS{idVendor}=="04f1", ATTRS{idProduct}=="6105", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD6320/00 or HDD6330/17
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="014b", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD1630/17
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="014c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD085/00 or HDD082/17
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="014d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips GoGear SA9200
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="014f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips SA1115/55
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0164", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips GoGear Audio
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0165", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips Shoqbox
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0172", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips PSA610
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0181", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips HDD6320
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="01eb", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips SA6014/SA6015/SA6024/SA6025/SA6044/SA6045
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="084e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips SA5145
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0857", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Philips PSA235
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="7e01", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa m230/m240
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7400", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa c150
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7410", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e200/e250/e260/e270/e280
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7420", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e280
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7421", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e280 v2
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7422", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa m240
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7430", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa Clip
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7432", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa c240/c250
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7450", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa Express
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7460", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa Connect
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7480", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa View
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="74b0", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Portable Media Center
ATTRS{idVendor}=="1006", ATTRS{idProduct}=="4002", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Portable Media Center
ATTRS{idVendor}=="1006", ATTRS{idProduct}=="4003", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver iFP-880
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1008", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T10
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1113", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T20 FM
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1114", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T20
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1115", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver U10
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1116", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T10a
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1117", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T20
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1118", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T30
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1119", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T10 2GB
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1120", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver N12
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1122", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Clix2
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1126", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver Clix
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="112a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver X20
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1132", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver T60
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="1134", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver H10 20GB
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="2101", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# iRiver H10
ATTRS{idVendor}=="4102", ATTRS{idProduct}=="2102", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dell, Inc DJ Itty
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="4500", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat MEGF-40
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0009", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="000c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat P20
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="000f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat S
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0010", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat P10
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0011", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat V30
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0014", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat U
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0016", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat MEU202
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0018", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Toshiba Gigabeat T
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0019", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos Gmini XS100
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="1207", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos XS202 (MTP mode)
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="1208", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 104 (MTP mode)
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="120a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 404 (MTP mode)
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="1301", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 504 (MTP mode)
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="1307", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 704 mobile dvr
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="130d", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Archos 605 (MTP mode)
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="1313", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Dunlop MP3 player 1GB / EGOMAN MD223AFD
ATTRS{idVendor}=="10d6", ATTRS{idProduct}=="2200", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Microsoft Zune
ATTRS{idVendor}=="045e", ATTRS{idProduct}=="0710", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sirius Stiletto
ATTRS{idVendor}=="18f6", ATTRS{idProduct}=="0102", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Canon PowerShot A640 (PTP/MTP mode)
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="3139", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia 3110c Mobile Phone
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="005f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N95 Mobile Phone 8GB
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="006e", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia 5300 Mobile Phone
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="04ba", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N73 Mobile Phone
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="04d1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N75 Mobile Phone
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="04e1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N95 Mobile Phone
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="04ef", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Nokia N80 Internet Edition (Media Player)
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="04f1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Logik LOG DAX MP3 and DAB Player
ATTRS{idVendor}=="13d1", ATTRS{idProduct}=="7002", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson EM28 Series
ATTRS{idVendor}=="069b", ATTRS{idProduct}=="0774", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson / RCA Opal / Lyra MC4002
ATTRS{idVendor}=="069b", ATTRS{idProduct}=="0777", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson RCA H106
ATTRS{idVendor}=="069b", ATTRS{idProduct}=="301a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson scenium E308
ATTRS{idVendor}=="069b", ATTRS{idProduct}=="3028", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Thomson / RCA Lyra HC308A
ATTRS{idVendor}=="069b", ATTRS{idProduct}=="3035", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# FOMA F903iX HIGH-SPEED
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1140", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Palm / Handspring Pocket Tunes
ATTRS{idVendor}=="1703", ATTRS{idProduct}=="0001", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Palm Handspring Pocket Tunes 4
ATTRS{idVendor}=="1703", ATTRS{idProduct}=="0002", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# TrekStor Vibez 8/12GB
ATTRS{idVendor}=="066f", ATTRS{idProduct}=="842a", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# TrekStor i.Beat Sweez FM
ATTRS{idVendor}=="0402", ATTRS{idProduct}=="0611", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Disney MixMax
ATTRS{idVendor}=="0aa6", ATTRS{idProduct}=="6021", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Tevion MD 81488
ATTRS{idVendor}=="0aa6", ATTRS{idProduct}=="3011", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Cowon iAudio U3 (MTP mode)
ATTRS{idVendor}=="0e21", ATTRS{idProduct}=="0701", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Cowon iAudio 7 (MTP mode)
ATTRS{idVendor}=="0e21", ATTRS{idProduct}=="0751", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Cowon iAudio D2 (MTP mode)
ATTRS{idVendor}=="0e21", ATTRS{idProduct}=="0801", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Insignia NS-DV45
ATTRS{idVendor}=="19ff", ATTRS{idProduct}=="0303", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Insignia Sport Player
ATTRS{idVendor}=="19ff", ATTRS{idProduct}=="0307", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Insignia Pilot 4GB
ATTRS{idVendor}=="19ff", ATTRS{idProduct}=="0309", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# LG UP3
ATTRS{idVendor}=="043e", ATTRS{idProduct}=="70b1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sony Walkman NWZ-A815/NWZ-A818
ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0325", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sony Walkman NWZ-S516
ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0326", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Sony Walkman NWZ-S615F/NWZ-S618F
ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0327", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SonyEricsson K850i
ATTRS{idVendor}=="0fce", ATTRS{idProduct}=="0075", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SonyEricsson W910
ATTRS{idVendor}=="0fce", ATTRS{idProduct}=="0076", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Motorola K1
ATTRS{idVendor}=="22b8", ATTRS{idProduct}=="4811", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Motorola A1200
ATTRS{idVendor}=="22b8", ATTRS{idProduct}=="60ca", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Motorola RAZR2 V8
ATTRS{idVendor}=="22b8", ATTRS{idProduct}=="6415", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Kenwood Media Keg HD10GB7 Sport Player
ATTRS{idVendor}=="0b28", ATTRS{idProduct}=="100c", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Micro-Star International P610/Model MS-5557
ATTRS{idVendor}=="0db0", ATTRS{idProduct}=="5572", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Isabella Her Prototype
ATTRS{idVendor}=="0b20", ATTRS{idProduct}=="ddee", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
GOTO="libmtp_rules_end"

LABEL="libmtp_rules_end"
```

Do I need a libmtp8.rules file or should my libmtp.rules file suffice?

---

### Post by alezflute on 2009-08-19
To me, your rules seem ok. I don't know what may be causing the freezes, but it was at the firmware part it did, apparently. Maybe Creative made an update of their firmware so that their devices wouldn't work with other software than theirs. Try to find the gnome configurations for usb devices and tell gnome not to do anything. Then open banshee (it would seem you already have the mtp plugin on, but check it anyway) and plug the device when it's off, so that the comp switches it on. It works for me like that. If gnome is already accessing the device banshee won't be able to, and if you try mtp-detect on a busy device it will block.

---

### Post by The_Eddster on 2009-08-20
Can anyone tell me where I can get libmtp8 (at least version 0.3.5) for ubuntu jaunty? I can't find it anywhere, on synaptic I have 0.3.0-1 but it doesn't work with my zen x-fi 8GB. 
The glenricc ppa doesn't have it and neither does the other one someone mentioned. Do I just have to install the Karmic version?

---

### Post by alezflute on 2009-08-24
> **The_Eddster said:**
> Can anyone tell me where I can get libmtp8 (at least version 0.3.5) for ubuntu jaunty? I can't find it anywhere, on synaptic I have 0.3.0-1 but it doesn't work with my zen x-fi 8GB. 
The glenricc ppa doesn't have it and neither does the other one someone mentioned. Do I just have to install the Karmic version?


It seems to me that you hadn't read the whole post. I'm not sure how safe it was, but the fastest and easiest way to get an updated libmtp was to download the karmic one. You don't need to upgrade your whole system to karmic. I guess the best way would be to get it backported for Jaunty, but as I no longer use Xubuntu i can't tell if that's done (but i think it's not)

---

### Post by bresdog on 2009-08-26
My zen is now being recognised through Rhythmbox, and i can play the music on it. But when trying to move files it says location not supported. When using gnomad2 it crashes and i have to reset my zen. This is the output from mtp-detect-

> libmtp version: 0.3.5

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN X-Fi (041e:4162) @ bus 0, dev 5
Attempting to connect device(s)
PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Connection timed out
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
usb_claim_interface(): Bad file descriptor
LIBMTP PANIC: Could not open session on device
Unable to open raw device 0
OK.

Any ideas? 
For anyone looking for libmtp8 version 0.3.5, go here-
[http://ppa.launchpad.net/glennric/ppa/ubuntu/pool/main/libm/libmtp/](http://ppa.launchpad.net/glennric/ppa/ubuntu/pool/main/libm/libmtp/)
And download and install-
libmtp8_0.3.5-0ubuntu1_i386.deb,
mtp-tools_0.3.5-0ubuntu1_i386.deb

---

### Post by alezflute on 2009-10-16
Maybe with libmtp 3.6? I think you will get it in a couple of weeks with Karmic. If you can't wait, i guess you could try to navigate their repo and get the relevant packages, installing them manually.

---

### Post by alezflute on 2009-11-01
Well, since Karmic release we have the good version so Zen X-Fi devices are working properly. I guess the thread could be marked as solved.

---

### Post by Dr. Freeze on 2009-11-30
Hey I am about to buy a creative zen xfi just to be clear it should pick it up when plugged into karmic?
or is there anything I need to download?

---

### Post by xadder on 2009-12-27
- same query as above post -

 I also have Karmic installed, and my wife now has a Creative Zen X-fi. It is hard to know from the above discussions which steps are needed. I don't want to do anything to mess up the Zen filesystem.

---

### Post by xadder on 2010-01-04
Help appreciated here as I am not sure what I'm doing....

I have a Creative Zen X_fi, karmic, and libmtp, libnjb5 installed through synaptic. My user in is  the audio and plugdev groups. 

I can see My Zen on /media or through rythmbox, and can play the demo music from there. gnomad2 also sees the Zen, but crashes when I try to add one of the demo songs to playlist with "PDE device NULL, Segmentation fault".  

Still, the setup is different from those described in the above posts:

mtp-detect 
libmtp version: 0.3.7

Listing raw device(s)
   No raw devices found.


45-libmtp7.rules:

# Creative ZEN Vision
ATTR{idVendor}=="041e", ATTR{idProduct}=="411f", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# Creative Portable Media Center
ATTR{idVendor}=="041e", ATTR{idProduct..... etc.... looks okay as far as I understand. 


There is no 45-libnjp.rules file though. Does this matter?

Finally, how do I send files to the Zen? Can I just create a directory by hand and copy mp3's there? Sounds like there should be a better solution. 
Sorry for the noob question, but I am new to both the  music progs  and the Zen.

---

### Post by mrSpaceman on 2010-01-11
This is an old thread (2007) though the date is now 2010 and the release is Karmic Koala (9.10).  This release is (at first) lovely for the Zen X-Fi (I have a 16GB model) - the OS detects it on plug-in and asks you what you want to do with it (open a folder? open Rhythmbox? do nothing?).  The biggest plus (initially) is that the player doesn't crash (well that is nice isn't it?).  The next nice thing is that you can browse it with the OS GUI file explorer, delete files, add files, etc.

After a little playing around, deleting, etc. I have come across a huge problem.  I had just ripped some tracks with Rhythmbox and copied them over using the OS (I couldn't get a satisfactory union between RB and the device to do the copying...or much else...so I left it).  I wanted to test them out: the player now only recognises the artists and tracks from A-C and there are no albums.  If you look in "All Tracks" on the device, then you can browse all the tracks, though I have 2500+, so this isn't fun.

I hooked it up again to linux and the thing that pops up on the desktop as a link gives the filesystem in the properties as "gphoto2" and the capacity as 2.9GB, though when searching though the files it finds 12+GB of files.  

So... I have now corrupted the fs on the device.  How do I get it back?  DO I copy the files onto my HDD and re-format?  How does one re-format an X-Fi?

:Z

---

### Post by alexthunder on 2010-01-11
I can't transfer any files to Creative Zen X-Fi from Ubuntu 9.10.

1. The player is mounted automatically, but when I open it the file browser shows the "gphoto2://[usb:002,002]/" location and I can't see any files on my player. I tried to open Rhythmbox, Banshee to no avail.

2. The latest version of Amarok doesn't have the Media Devices in the Settings, so I can't use it as well.

3. If I launch gnomad2 it reports the following error: "No jukeboxes found on USB bus". In the terminal it shows the following:
```
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
PDE device NULL.
```

4. Tried to use mtptools:
```

sudo apt-get install libmtp mtptools mtpfs
sudo mkdir /media/zen
sudo chmod 775 /media/zen
sudo mtpfs -o allow_other /media/zen
```
The player appear on my desktop as a regular drive, but when I try to access it I get the following error:
```
Transport endpoint is not connected
```

5. gnomad2 doesn't see my mplayer reporting the following error:
No jukeboxes found on USB bus.

I tried to create no-automount.fdi file in /etc/hal/fdi/policy with the following content:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
 <device>
      <match key="info.product" string="ZEN X-Fi">
        <remove key="info.capabilities" type="strlist">portable_audio_player</remove>
      </match>
  </device>
</deviceinfo>
```

My player is no longer mounted automatically and gnomad 2.9.4 can see it. However I can't transfer any files with it. The right panel always stays empty.


I tried so many things, but still have no idea why using Creative Zen X-Fi in Ubuntu 9.10 is so complicated.

---

### Post by Throne777 on 2010-01-28
I used to run Ubuntu 8.10 and got my Creative Zen X Fi working fine by running Gnomad2 in sudo. Now I'm running 9.10 on a fresh install (libmtp and libnjb5 etc, have been installed). When I plug it in the MP3 player goes into docking mode, it comes up on my desktop and I can browse the MP3 player just fine from nautilus. The annoying part is that Gnomad2 won't recognise it (even in sudo), nor will Rhythmbox or Banshee.
Thoughts?

---

### Post by tarahmarie on 2010-04-14
> **alexthunder said:**
> I can't transfer any files to Creative Zen X-Fi from Ubuntu 9.10.

1. The player is mounted automatically, but when I open it the file browser shows the "gphoto2://[usb:002,002]/" location and I can't see any files on my player. I tried to open Rhythmbox, Banshee to no avail.

2. The latest version of Amarok doesn't have the Media Devices in the Settings, so I can't use it as well.

3. If I launch gnomad2 it reports the following error: "No jukeboxes found on USB bus". In the terminal it shows the following:
```
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
PDE device NULL.
```

4. Tried to use mtptools:
```

sudo apt-get install libmtp mtptools mtpfs
sudo mkdir /media/zen
sudo chmod 775 /media/zen
sudo mtpfs -o allow_other /media/zen
```
The player appear on my desktop as a regular drive, but when I try to access it I get the following error:
```
Transport endpoint is not connected
```

5. gnomad2 doesn't see my mplayer reporting the following error:
No jukeboxes found on USB bus.

I tried to create no-automount.fdi file in /etc/hal/fdi/policy with the following content:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
 <device>
      <match key="info.product" string="ZEN X-Fi">
        <remove key="info.capabilities" type="strlist">portable_audio_player</remove>
      </match>
  </device>
</deviceinfo>
```

My player is no longer mounted automatically and gnomad 2.9.4 can see it. However I can't transfer any files with it. The right panel always stays empty.


I tried so many things, but still have no idea why using Creative Zen X-Fi in Ubuntu 9.10 is so complicated.

I am having every last one of the exact same errors you are.  Why?  WTH do I have to do to get it to work?

---

### Post by gresavage on 2010-04-14
> Creative ZEN X-fi and Ubuntu 9.10
I can't transfer any files to Creative Zen X-Fi from Ubuntu 9.10.

1. The player is mounted automatically, but when I open it the file browser shows the "gphoto2://[usb:002,002]/" location and I can't see any files on my player. I tried to open Rhythmbox, Banshee to no avail.

2. The latest version of Amarok doesn't have the Media Devices in the Settings, so I can't use it as well.

3. If I launch gnomad2 it reports the following error: "No jukeboxes found on USB bus". In the terminal it shows the following:
Code:
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
PDE device NULL.
4. Tried to use mtptools:
Code:
sudo apt-get install libmtp mtptools mtpfs
sudo mkdir /media/zen
sudo chmod 775 /media/zen
sudo mtpfs -o allow_other /media/zen
The player appear on my desktop as a regular drive, but when I try to access it I get the following error:
Code:
Transport endpoint is not connected
5. gnomad2 doesn't see my mplayer reporting the following error:
No jukeboxes found on USB bus.

I tried to create no-automount.fdi file in /etc/hal/fdi/policy with the following content:
Code:
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
 <device>
      <match key="info.product" string="ZEN X-Fi">
        <remove key="info.capabilities" type="strlist">portable_audio_player</remove>
      </match>
  </device>
</deviceinfo>
My player is no longer mounted automatically and gnomad 2.9.4 can see it. However I can't transfer any files with it. The right panel always stays empty.


I tried so many things, but still have no idea why using Creative Zen X-Fi in Ubuntu 9.10 is so complicated.

if you try going into nautilus (just open up the file browser) you can probably see Creative Zen X-Fi as a media storage device. It should have a little "Eject" symbol next to it. If you click that to dismount it, then try Rhythmbox or Gnomad2. it should hook up just fine and you should be able to transfer media to and fro without any problem. You just have to remember to dismount the Zen before trying to sync with Rhythmbox or Gnomad2. IDK about Armarok, it's probably the same way.

SO... just dismount the X-fi and THEN open up your media client.

---

