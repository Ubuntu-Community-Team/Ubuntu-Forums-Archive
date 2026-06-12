---
title: "hard drive crash -- please help!"
date: 2009-01-22
forum: Hardware
---

### Post by jecompton on 2009-01-22
I had an old gentoo box I was using as a file server. The drive was a basic internal 120GB drive, but one day it just stopped working. Sadly, even though I had this rsync'ing to an external usb drive on another machine, that external drive is now broken somehow. The usb drive refuses to be assigned an address when plugged in on any machine now (/var/log/messages shows it when it plugs in, but it says it is refusing the addresses and is not assigned a name in /dev)

The internal that crashed, however, almost boots, but falls apart. I pulled it out and put it as a slave in another machine and have been trying to do some disk maintenance. Here's what I know:

- drive (/dev/sdb) is missing about everything but /boot (my important data files are in /home)
- e2fsck /dev/sdb1 works shows no problems, but e2fsck -b 8193 /dev/sdb1 says ****** FILE SYSTEM WAS MODIFIED *******. It does not matter how many times I repeat this, nothing changes. other -b increments just say "bad magic number"
- I ran badblocks and ended up w/ 125 bad block numbers.
- When I fed this badblock file into fsck (e2fsck -n -l bads.txt /dev/sdb1) it just gave the ***** FILE SYSTEM WAS MODIFIED ***** again
- The data seems to be on there somehow since grep -a <some remembered text in some file> /dev/sdb1 brings up the data in raw form.

I am pretty sure that the drive used to have separate partitions for /home, /var, and a few others (it's been about 5 years since I messed w/ it since it worked so well all that time). Some of the partitions (if they existed) may be reiserfs, but they are probably all ext3.

Any help or direction would be greatly appreciated!

---

### Post by jecompton on 2009-01-23
I'll continue to post updates here as I progress (or degress). Here's what I've done so far:
```
cat /dev/sdb1 > /mnt/otherdrive/dumpfile.dmp
```

This ended w/ an IO error, but it got most of the data (106GB of 120). Now I can feel safer about debugging the original crashed drive.

Does anyone know of a way to separate raw binary data into separate files? Like are the EOF's still in the raw data such that I could script and divide the large 106G file into separate ones? This would be pretty close to achieving what I need.

---

### Post by jecompton on 2009-01-24
I recovered the hard drive structure and files w/ minimal loss (about 5 mp3s in some bad sectors). No thanks to anyone in the forum. All I needed was for someone to point me to this great link:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

testdisk worked great. Hope this helps someone else in a crisis.

---

