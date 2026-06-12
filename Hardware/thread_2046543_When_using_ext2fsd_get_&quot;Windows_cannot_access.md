---
title: "When using ext2fsd get &quot;Windows cannot access ...&quot;"
date: 2012-08-23
forum: Hardware
---

### Post by mind_exploit on 2012-08-23
Hello,

I have a linux partition on my laptop, that I access from both Ubuntu and Windows 7. The problem is that for only some exe files when I try to run them from Windows I get

"Windows cannot access H:\....exe

Check the spelling of the name. Otherwise, there might be a problem with your network. To try to identify and resolve network problems, click Diagnose."

And below:

"Error code: 0x800704b3
The network path was either typed incorrectly, does not exist, or the network provider is currently unavailable. Please try retyping the path or contact your network administrator."

Clicking on Diagnose doesn't can not find the problem. Changing the letter that this common drive is mounted under in Windows didn't change anything.

Can you help me please? ... thanks in advance :)

---

### Post by mind_exploit on 2012-08-24
Hello,

I found out that when I enter in the windows in safe mode - then I can run and install the game. (It's TERA Online btw.)

Also - I tried with installing the "take ownership" option, but when I apply it - there is not difference after all.

Has anybody an idea? Thanks.

---

### Post by ahallubuntu on 2012-08-24
I've used these "EXT for Windows" drivers, but I have found them buggy and unpredictable.  I would not recommend them (and I don't think they work well or at all for ext4 partitions, either).

By contrast, I've used NTFS partitions for years in Ubuntu with great reliability.  Never any serious issue.  The worst problem I've had is that copying very large files in Linux to/from an NTFS partition results in high CPU usage and slow copy times (I mean more than a few GB-size files).

I highly recommend using NTFS as your primary partition type for any partition you will share with Windows, if you can.  If you have only two partitions, one Linux one Windows, make your Windows partition large enough for your data and your Linux ext partition only big enough for what you might need for the OS.  Alternately, have three partitions (one for each OS and a large NTFS data partition) you can share between them.

---

### Post by mind_exploit on 2012-08-29
Well, what I did is that I shrinked this common Ext3 partition, and made a new NTFS partition from the freed space ... but after that I made the new NTFS partition to be mounted in a folder in the C: drive in the Windows ... which actually broke everything and now I'm unable to boot in the PC at all.

(Why, the hell, I decided to do this ... ??? ...)

I'm using SSD btw, forgot to mention. But I think the reason for all is the way I decided to make this new free NTFS partition ... I had to leave it as a different drive ...

---

