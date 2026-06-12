---
title: "Playing Videos Via External HDD Keeps Freezing"
date: 2016-12-08
forum: Hardware
---

### Post by ThePowerpuffGirls on 2016-12-08
This has started happening for a couple of days now. At first, I thought it was a video I was watching that was 1080p, and that it was VLC, because it used to do that 1080p, but not for awhile.
Then, I watched some episodes of "Highway To Heaven", which is standard, meaning not hi-res. So, tonight I tried a different media player, the default media player, Totem, and it still freezes.
What happens is every minute or few minutes, it would freeze for for about 10-20 seconds, both audio and video.

I first noticed it the other day when watching the latest episode of The Walking Dead. When I was copying the files over, from a SSD via USB 3.0, I noticed that the files took a really long time to copy over, it would copy over like 100MB or more, freeze for a few seconds, copy over some and freeze for about 10-15 minutes, copy some more and freeze for another, it took at least a half hour to copy 2 files of The Walking Dead over, one was 1+GB and another was 3.2GB.

The next day or two after that, I've noticed that while downloading stuff via torrent, which I have set for the files to go directly on the HDD which the movies are on. I got an error which said the it didn't have the permission. I tried to change them via 'gksudo nemo' and couldn't because of an error. After running 'fsck -r' I was able to download without trouble. It may gives some clues on what is happening or what happened.

BTW, the files I copy over worked, at least one of them does because I watched it via the SSD that I use as a jump drive, and it worked without freezing.
The drive is a Western Digital 6TB; EXT4 format.
Another interesting thing is, ever since I got it, when stuff was copy to the drive, it would always freeze. Like you'd only get a few seconds of video, it'll freeze for 20 seconds and a few more seconds of video would play. I assuming that it's because it was is like 5400RPM.

---

### Post by ThePowerpuffGirls on 2016-12-11
Bump.

---

### Post by SeijiSensei on 2016-12-11
Try using SMPlayer and playing with its buffer size: Options > Preferences > Performance > Cache. Use mpv as the player engine.

```

sudo apt-get update
sudo apt-get install smplayer mpv

```

Also what video hardware do you have?  Does it support hardware decoding of H.264-encoded content?  Do you have the same problems with 720p content?  If you don't have a video adapter with hardware decoding, then the CPU has to handle that.  Decoding a 1080p H.264 video is very processor intensive.  Try opening a terminal window and running the "top" command, then play the video.  What kind of CPU load do you see?

---

### Post by ThePowerpuffGirls on 2016-12-12
> **SeijiSensei said:**
> Try using SMPlayer and playing with its buffer size: Options > Preferences > Performance > Cache. Use mpv as the player engine.

```

sudo apt-get update
sudo apt-get install smplayer mpv

```

Also what video hardware do you have?  Does it support hardware decoding of H.264-encoded content?  Do you have the same problems with 720p content?  If you don't have a video adapter with hardware decoding, then the CPU has to handle that.  Decoding a 1080p H.264 video is very processor intensive.  Try opening a terminal window and running the "top" command, then play the video.  What kind of CPU load do you see?

Space-bar-ins't-working-in-message-box-for-some-reason

I have an ASUS Z97-K motherboard and using the IGPU, and a I have a Intel Core i5-4670K processor.
It's a problem on all video, despite it being 1080, 720 or standard. It started after I had trouble copying two media files (2 episodes of The Walking Dead). Since it was happening on both media players and not on a different drive, I was assuming it was the drive that was causing it. I will try to media player of your choice tonight and will let you know how it goes.

Update:
I'm copying over the latest episode The Walking Dead, and it frooze and said error copying and that it was a read-only file system.
I did the check again for errors:

```
alexa@Alexas-PC:~$ sudo fsck -r /dev/sdafsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


/dev/sda: status 8, rss 3148, real 0.063142, user 0.000000, sys 0.000000
alexa@Alexas-PC:~$ sudo fsck -r /dev/sda1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
6TBHDD: recovering journal
6TBHDD contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
6TBHDD: 6505/183140352 files (6.2% non-contiguous), 1056380600/1465122048 blocks
/dev/sda1: status 0, rss 62388, real 73.910146, user 6.572000, sys 0.200000
alexa@Alexas-PC:~$ 

```

Now I get 'No object for D-Bus interface' when I click on it.

Update 2: I restarted the computer, of course I got to long in, it hangs, and the drives don't appear in the side bar, so I restart again, and it works and I'm able to access the drive.
I copy over the latest episode of The Walking Dead, it it hangs on 0% for a few seconds, slowly go to 69% and hangs for a minute or two and then the dialogue box disappears. It was much quicker then last time though.

Update 3: I forgot to use the media player you mentioned but it doesn't haven't skipped once.

---

