---
title: "Creative Zen not recognised by computer"
date: 2010-04-21
forum: Hardware
---

### Post by abelito8 on 2010-04-21
I am using ubuntu 9.04 on a Sony Vaio Laptop. I had installed an application that allowed me to connect a Zen creative player (30 GB) and for some time it worked. 
Now, as I connect the player, the computer fails to recognise it. At first I thought this was due to improper unmounting from a windows system (do not know why, it does not appear among the other USB devices in use)
However I tried it on a Ubuntu 9.10 and it recognised it...however I was unable to write on the device nor to copy any information from the device into the computer...

is there anything I would need to know?

thank you

---

### Post by lykeion on 2010-04-21
> **abelito8 said:**
>  I had installed an application that allowed me to connect a Zen creative player (30 GB) and for some time it worked.

What application?

I have a Creative Zen 4GB and use gnomad2 to transfer files to it from PC.
One thing I have to do to make gnomad recognize it is to unmount the Creative ZEN device in nautilus before I launch gnomad. 
Otherwise it works flawlessly.

Hope this helps...

---

### Post by abelito8 on 2010-04-26
Thank you for your reply, I am afraid I cannot unmount the device as far as the system cannot find it....
otherwise I have installed gnomad2, maybe a miracle will happen and the computer will start recognising my ZEN

---

### Post by lykeion on 2010-04-27
You say that when you connect your zen via usb it doesn't mount?
It may be some problems with old libmtp package or missing udev rules for your model, but I need some more info to help you further:

1. what is your creative zen model?

2. what os version are you running:
open a terminal and paste the output of this command:
```
echo `uname -a`
```
3. what libmtp version is installed:
paste the output of this terminal command:
```
dpkg -s libmtp8
```
4. (after connecting your zen) paste the output of this command:
```
lsusb
```
5. (also after connecting) paste the output of this command:
```
mtp-detect
```

---

### Post by abelito8 on 2010-04-28
Thanks for this, here you have

1) I am using a Creative Zen Vision 30GB

[http://www.google.com.tr/imgres?imgurl=http://ec1.images-amazon.com/images/I/4112S7AQPWL._AA280_.jpg&imgrefurl=http://mp3-p.blogspot.com/2007/07/creative-zen-visionm-60-gb-portable.html&h=280&w=280&sz=12&tbnid=9jkB83TEBaiHpM:&tbnh=114&tbnw=114&prev=/images%3Fq%3Dcreative%2Bzen%2B30%2BGB&usg=__z6TPeuv5D1yAOFDXoqird71FvL4=&ei=3uHXS-W1KsqOOOrC1O8G&sa=X&oi=image_result&resnum=8&ct=image&ved=0CCoQ9QEwBw](http://www.google.com.tr/imgres?imgurl=http://ec1.images-amazon.com/images/I/4112S7AQPWL._AA280_.jpg&imgrefurl=http://mp3-p.blogspot.com/2007/07/creative-zen-visionm-60-gb-portable.html&h=280&w=280&sz=12&tbnid=9jkB83TEBaiHpM:&tbnh=114&tbnw=114&prev=/images%3Fq%3Dcreative%2Bzen%2B30%2BGB&usg=__z6TPeuv5D1yAOFDXoqird71FvL4=&ei=3uHXS-W1KsqOOOrC1O8G&sa=X&oi=image_result&resnum=8&ct=image&ved=0CCoQ9QEwBw)

(this one is 60GB, otherwise it's the one I have)

2) os version
Linux ernesto 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

3) libmtp

Package: libmtp8
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 564
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libmtp
Version: 0.3.0-1ubuntu3
Depends: libc6 (>= 2.4), libusb-0.1-4 (>= 2:0.1.12)
Recommends: udev
Breaks: udev (<< 136-1)
Description: Media Transfer Protocol (MTP) library
 A library for communicating with MTP aware devices.  MTP (Media
 Transfer Protocol) is necessary to communicate with some USB portable
 devices like mp3 players, video players or digital camera.
 .
 While some portable device will use USB mass storage protocol or PTP
 (picture transfer protocol), some device can only communicate through
 MTP [ see [http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol) ]
Homepage: [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/)
Original-Maintainer: Rafael Laboissiere <rafael@debian.org>

4) lsusb

Bus 002 Device 005: ID 041e:413e Creative Technology, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


5) mpt detect

that was more complicate...

at first I found out I had not it, so I installed, then I tried immediately after install and it said:
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN Vision:M (041e:413e) @ bus 0, dev 5
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

I switched the Zen off and tried again 

this time I got 

libmtp version: 0.3.0

Listing raw device(s)
   No raw devices found.


....is it so bad???

---

### Post by abelito8 on 2010-04-28
A small discovery, whilst stating that the device is busy, I was still able to play the music from my MP3 Player in my computer...the albums are simply among the ones in Amarok (but the player is listed nowhere else)

---

### Post by grege on 2010-04-28
Zens will not mount as a normal USB drive, they use a different protocol.

I use Gnomad2 or Amarok to move music back and forth. Sometimes Gnomad2 will fail to see the Zen, especially the first time you use it, run it as superuser once and the problems usually disappear. 

The most reliable for me in recent times is to use Amarok which automatically recognizes and loads the Zen on startup (it takes a few seconds to appear at top of left hand column).

---

### Post by abelito8 on 2010-04-28
Thank you but I seem to have an anarchic gnomad2, even when I log in as superuser does not find anything connected to a usb port

Amarok, now I see the music but I was unable to understand how to transfer music from there

and what will happen once I finish? I do not see any way to unmount the volume...shall I brutally unplug it?

---

### Post by grege on 2010-04-28
To add a song or album.

Plug in Zen and start Amarok

Find song in your Amarok library and right click on it. In the menu toward the bottom you will see Copy to Collection, move mouse down and Creative Zen will appear as a choice. Click on Zen and the music is copied across. The status bar for the copying is bottom right of Amarok (one track will be too fast to see, but you can follow progress of album).

When finished adding songs close Amarok and you will see the display on the Zen change from docked to either the normal display of the Zen or the Zen's updating library display. You can unplug at this point, it was never mounted in a normal sense.

The only hassle I have had is copying albums of various artists that Amarok spreads across the library, but you can work around that by using the search function to only show the tracks you want in Amarok before trying to copy.

Hopefully this will get you going.

EDIT: These instructions are for the latest version of Amarok, if you are using an older version the principals are the same although the layout might be different.

---

### Post by abelito8 on 2010-04-28
I found out how to move music into and from the Zen but it seems only a palliative. 
HDD MP3 have several directories and I do not see where I am copying the files. what if I want to copy a movie? Finally I have my Zen partitioned and 3GB are to be used as a normal USB stick, I do not have access to them through Amarok...

any help?

---

### Post by abelito8 on 2010-04-28
Ah grege thank you, we were writing our threads at the same time so I saw it only now
well at least the music issue is solved...it remains the mistery of why I cannot see it (Ubuntu 9.10 sees it but does not allow to copy)

---

### Post by grege on 2010-04-28
I use Kubuntu 10.04 and the system never acknowledges the existence of the Zen. I remember in older versions using Gnome it showed as an icon on the desktop, but you could do nothing with it.

I have a newish Zen 32gb and I can add an extra SD card, when I want that card to mount I must go through the Zen's menus and tell it to allow it to be seen as a normal drive. It then appears as you would expect. Only trouble is the extra space of the SD card is not used by the Zen's internal library and media can only be played from the Zen's file manager. I use it for Audio books, so keeping all those chapters out of the music library is not a bad thing.

cheers

---

### Post by abelito8 on 2010-04-28
I have checked my Zen's menu and could not find the option "show yourself as a common device" maybe this is an option only in new generation zens?

---

### Post by grege on 2010-04-28
That function only applies to the extra SD card, the internal Zen memory where the music is stored is always an MTP device, requiring it to be controlled differently - in this case by Amarok. Rhythmbox might work as well, I have never tried.

Yours has some of it's space separated as a storage device, there must be a way to access that. My old Zen, similar to yours, died when I foolishly tried replacing the battery with the wrong one. I am sure I could access that extra space - see if you have all the MTP libraries installed. I am out of ideas at this point.

btw if you are interested Creative have been dropping prices on the new Zens and throwing in high end buds on some models. Mine will run for 30 hours (music) on a charge, is the size of a thick credit card and weighs virtually nothing. And it works fine with Amarok. Add an SD card for videos and your done.

[http://us.store.creative.com/category/19937529081/1/ZEN-MP3-Players.htm](http://us.store.creative.com/category/19937529081/1/ZEN-MP3-Players.htm)

The latest model  Zen X-Fi Style 32gb Solid state drive is only $US170

---

### Post by lykeion on 2010-04-29
**about the "busy device" message from mtp-detect:**
you'll have to close down all applications accessing the zen device (i.e. amarok, gnomad2, etc) and also make sure the zen device is 'unmounted' in nautilus. 
then before you'll try mtp-detect again you'll might have to run this command in a terminal:
```
sudo /etc/init.d/udev restart
```
after this you can launch gnomad2 (as super user is not necessary, at least not for me) and the gnomad2 should be able to find the zen device.
[B]
about transferring videos to zen:[/B]
you'll first have to make sure the video has the right format. 
for my creative zen i use 240x320 xvid video codec, mp3lame audio codec. and i use mencoder to convert the video to this format
(if you'd like i could post a bash script that performs this conversion). 
maybe your zen model accepts other formats/resolution - you should check the specs on creative's homepage.

i've noticed that when i transfer videos using gnomad2 there's seems to be a problem with no timelengths for the transferred videos (and seeking is not possible). 
my solution was to use banshee to transfer the videos (actually i think banshee is much better than amarok, but that's just my opinion).

one could ask oneself why so much fiddling is needed to be able to do simple transferring to a creative zen device? 
one answer to this is that the MTP protocol "is part of the 'Windows Media' framework and thus closely related to Windows Media Player." (quoted from wikipedia).
but personally i don't mind this as a long-time linux user, it's just the way things are.

---

### Post by abelito8 on 2010-05-01
For some reasons the computer recognised my creative and I was able to move some music simply by dragging icons 
then I tried to delete films (also graphically) and it would not allow me, then the Zen icon disappeared as it had appeared 

I typed the command you suggested....and

I guess I shall try with bashee now..but thank you for your help

abel@ernesto:~$ sudo /etc/init.d/udev restart
[sudo] password for abel: 
 * Stopping kernel event manager...                                      [ OK ] 
 * Starting kernel event manager...                                      [ OK ] 
abel@ernesto:~$ mtp-detect
libmtp version: 0.3.0

Listing raw device(s)
   Found 1 device(s):
   Creative: ZEN Vision:M (041e:413e) @ bus 0, dev 3
Attempting to connect device(s)
PTP: Opening session
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 413e
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 0
      Device number: 3
      Device entry info:
         Vendor: Creative
         Vendor id: 0x041e
         Product: ZEN Vision:M
         Vendor id: 0x413e
         Device flags: 0x00000001
Microsoft device descriptor 0xee:
    0000: 1203 4d00 5300 4600 5400 3100 3000 3000    ..M.S.F.T.1.0.0.
    0010: fe00                                       ..
Microsoft device response to control message 1, CMD 0xfe:
    0000: 2800 0000 0001 0400 0100 0000 0000 0000    (...............
    0010: 0001 4d54 5000 0000 0000 0000 0000 0000    ..MTP...........
    0020: 0000 0000 0000 0000                        ........
Microsoft device response to control message 2, CMD 0xfe:
    0000: 2800 0000 0001 0400 0100 0000 0000 0000    (...............
    0010: 0001 4d54 5000 0000 0000 0000 0000 0000    ..MTP...........
    0020: 0000 0000 0000 0000                        ........
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative Zen Vision:M
   Device version: 1.62.02_0.00.23
   Serial number: 00023C028FF9935B0BF2A063F73CD0AA
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
   1016: Set device property value
   1017: Reset device property value
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
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
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
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b901: WMA
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
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
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
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
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b904: Audible.com Codec
      da01: unknown(da01) UINT32 data type enumeration: 2, 4,  GET/SET
      da02: unknown(da02) array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: unknown(da03) UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
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
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba01: Abstract Multimedia Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba03: Abstract Audio Album
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 80, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 24576, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 80, STEP 1 READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 3328, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 4992, STEP 1 GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   300a: MS AVI
      de99: AudioWAVECodec UINT32 data type enumeration: 80, 85, 17, 1,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 1536000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 576, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 844515635, 1482049860, 808802372, 1196444237, 1446137933, 1395937357, 1195724877, 1145656920,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 720, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   300c: ASF
      de99: AudioWAVECodec UINT32 data type enumeration: 80, 85, 352, 353, 17, 1,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 1536000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 576, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 1482049860, 808802372, 1196444237, 1446137933, 1395937357, 1195724877, 861293911, 1145656920,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 720, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b982: MP4
      de99: AudioWAVECodec UINT32 data type enumeration: 80, 85, 17, 1,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 1536000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 576, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 808802372, 1196444237, 1446137933, 1395937357, 1195724877, 1145656920,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 720, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   300b: MPEG
      de99: AudioWAVECodec UINT32 data type enumeration: 80, 85,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 384000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 480, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 1446137933, 1195724877,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 2500000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 720, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b981: WMV
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 430000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 20, MAX 30000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 850000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 861293911,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 802000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 8192, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 96, STEP 1 READ ONLY
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   bb83: vCard3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   be03: vCalendar2
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b802: Firmware
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 29952966656
      FreeSpaceInBytes: 4794843136
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 00023C028FF9935B0BF2A063F73CD0AA
Special directories:
   Default music folder: 0x00000058
   Default playlist folder: 0x0000005c
   Default picture folder: 0x00000068
   Default video folder: 0x0000006c
   Default organizer folder: 0x00000064
   Default zencast folder: 0x00000074
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: My Zen
   Synchronization partner: {00000000-0000-0000-0000-000000000000}
   Battery level 244 of 255 (95%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   MPEG video stream
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20100501 12:27:20Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AjwCAFuT+Y9joPILqtA89wAAAAA=</UNIQUEID><PUBLICKEY private="1">37Cdj3oWBDpv8+kAyHqC1OlrpETJa/ns0g/EjXrwK9JfVsLFroJwUQ==</PUBLICKEY><KEYDATA>ue4rJ1t4WLm9a5m1Yaeu4pIGKNY=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>Wdl7AD4SRALbfkSTSgYk0ZjxX1oFhkcVtCsw3rAxP1dmvgISLio6DQ==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>+uo4h/WDnDCJtx14YS1vuI10VFk=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.103.61</SECURITYVERSION><CERTIFICATE private="1">37Cdj3oWBDpv8+kAyHqC1OlrpETJa/ns0g/EjXrwK9JfVsLFroJwUQIEZz2JMJo+Nec9r/2XCgtQ64YDA9WnJYLP3QEC4UETuWEhmCKouyYHCNcG</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative Zen Vision:M</NAME>
  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>
  <MODEL>DVP-HD0003</MODEL>
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
  </LIMITS><PUBLICKEY>Zyqn8gWDO+E0O5uFWAITnXpHrzfRKPtanLWS4c0CWBv4HVL8VMm0QQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>g27HSbQgG+GZO2dlcOK0qdK/Ql+5HU7kWCXnqSDDHko5fruJpT/pVQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>673</AUTH_ID><PUBLICKEY>apoWlp0LevRxXWHcSskvn/VSsG5YjXoM7Bya7bMdc0GO3VM9fxhIgw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>MJmLft7Asiwh9iDeM/VogDjM4G5U6x0E1Vws11mQN0yJjBMkGWRZVQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>dhVs0/oSDCgWs5g9yvEdkRatr1eLsaMe7Kws0MwaOWWebmtq1TZABQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>

Device description WMPInfo.xml file:
<DeviceInfo>
    <WMP DeviceID="{B2050696-92DB-452D-9824-B521CF6B4E55}" RelationshipID="{00000000-0000-0000-0000-000000000000}"/>
</DeviceInfo>

PTP: Closing session
OK.
abel@ernesto:~$

---

### Post by abelito8 on 2010-05-01
Update, I tried banshee and my zen is recognised, I could also delete a video (finally!). I was unable to upload any video file but I guess I just have to learn how to do it with banshee so I am playing a bit with it at the moment

thank you!

---

