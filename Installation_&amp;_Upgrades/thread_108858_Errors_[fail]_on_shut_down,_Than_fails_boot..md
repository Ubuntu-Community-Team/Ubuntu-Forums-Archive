---
title: "Errors [fail] on shut down, Than fails boot."
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2005-12-27
Hi everybody, I hope someone can help me with this.
I installed Breezy on a dual-boot system (WinXP) 1600MhZ 512RAM.
My partitions are
1-(Win) NTFS, read-only under Linux
2-(Breezy) Ext3
3-(Swap) Linux Swap
4-(file storage) Fat32
5-(Flight Simulator) NTFS (Read-only)
6-(Win Paging File) NTFS, not mounted by Breezy
GRUB is installed in HD0,1
It has already happened at least four or five times that I had to reinstall the whole Breezy OS from scratch after I got an error on boot that I wasnt able to correct (I have been using Linux since only 6 weeks, after all):
Breezy aborted the boot sequence and gave me a long line of errors and than it kept restarting from BIOS. (Win still boots as usual).
After some failed boot sequences, I tried booting to Recovery Mode and got the error (dont remember exactly) "unable to access *something*", it had something to do with a "job file" or something like that.
"cant access something, job file not set up", maybe.
I wrote down the line and surfed the web after answers but I could not find anything other than "reinstall the $&#295;i&#359;".
So I did.
Some four or five times so far.
(And yes, I *will* try to find the note I wrote and post the exact line)
Last time it kept working for a couple of days, and then again; I shut down, powe off and go to sleep, the next day it boots (looks like) normally, then I got a small connection problem and rebooted.
On shut down sequence I noticed som red [fail]s
I reconized the problem and booted directly to "Recovery Mode" - and it worked, I'm using Ubuntu right now but i'm afraid to gat the same problem again if i shut down or restart.
It Is working fine now, the only difference being that I'm logged in as root now (maybe I should boot to Recovery Mode every time; I like being root)
What should I do now?
Is there something I can do before I reboot, to fix the problem?
And What *is* causing the problem?
(and what problem is it anyway?)
This post is much longer than I thought, that's one of the reasons why I dont post much; I cant keep it short, and I dont want to ask for help before I have looked for the answer on the Internet, but this time I had to. I didnt find anything of help so far, and I'm getting tired of reinstalling Ubuntu twice a week... OK, I cut it.
Thanks for helping.
L.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
Without more specific error messages it's hard to tell where you may be going wrong. I can tell you it's not normal to have to reinstall all the time and it could be a sign of a bad drive. Even if it seemed to work fine when it was all windows, windows doesn't deal with bad clusters on a drive the same way as linux.

If you would write down the error messages and post them here we might be able to give more specific instructions. Type this into a terminal and see what it reports

grep hd /var/log/messages

---

### Post by Luke771 on 2005-12-27
Hi, and thanks for answering,
I know I should give more details, I still can't find the note where I wrote the line that I got when the boot failed; I'll keep looking for it a little more, then I will try to find the same line on the Internet by googling some of the words, assuming someone else has gotten the same problem and posted the line on some forum, but I dont think that will work because the only words I remember are those that I have already posted and probably that's not enough to get somoe good results on a web search, bu I'll give it a try anyway.
In the meantime, I logged out and in again as regular user (non-root); the line in the last post gave a long list of results, maybe too much to post here;
It reconized the hardware correctly, or at least it showed the manufacturers and models that it was supposed to show, then some more "regular looking" lines, stuff like:

> 
Dec 26 14:41:51 localhost kernel: [4294667.296000] Kernel command line: root=/de v/hda2 ro quiet splash
Dec 26 14:41:51 localhost kernel: [4294670.128000]     ide0: BM-DMA at 0xb400-0x b407, BIOS settings: hda:DMA, hdb:pio
Dec 26 14:41:51 localhost kernel: [4294670.128000]     ide1: BM-DMA at 0xb408-0x b40f, BIOS settings: hdc:DMA, hdd:DMA
Dec 26 03:49:43 localhost kernel: [4294674.454000] hda: max request size: 128KiB
Dec 26 03:49:43 localhost kernel: [4294674.462000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)



and then the first ERROR came out:

> 

Dec 26 18:26:37 localhost kernel: [4298355.275000] hdc: media error (bad sector) : status=0x51 { DriveReady SeekComplete Error }

Dec 26 18:26:37 localhost kernel: [4298355.275000] hdc: media error (bad sector) : error=0x30 { LastFailedSense=0x03 }

Dec 26 18:36:35 localhost kernel: [4298953.438000] end_request: I/O error, dev h dc, sector 717596



It was a long list of error lines, all looking like one or another of the three mentioned above, then some more "regular looking" lines, at least they look regular to me, but I have only 6 weeks of linux experience.
I could post the whole response I got running
grep hd /var/log/messages
in Terminal, but it may be too long a post, I don'r know what the usual post size limit is here.
I'm thinking about restarting the system and see what happens, if i gat som red [fail] on the shut down sequence than I would boot to Recovery Mode, it worked last time.
So far, it looks like the trick is to boot directly to Recovery Mode when getting errors in the shut down sequence, but my point still is trying *not to* get any errors.
OK, Ive written too much (again), time to look for missing error message on boot... but wait, it seems to me that the problem is on shutdown, not on boot.
I mean, *before* i get any booting problem, I get some fail message while running the shut down sequence, *then* comes the boot fail.
And it did boot using Recovery Mode without tryng to run the regular boot sequence first.
(Yes I'll look once again for the note with the original error message on)
L.
-ps- should I post the whole Terminal response?

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
You got a bad hard drive, champ. Back it up and replace it and you'll be fine.

---

### Post by Luke771 on 2005-12-27
yea, that's what I guessed when I saw all those errors, now I know i guessed right, thanks for that.
Anyway, it looks like the trick to keep it working despite the bad sectors is to look at what happens on shut down:
I mean, I noticed the fail messages on shut down and rebooted straight to Recovery Mode without any attempt to boot regularly, then log out root an in as regular user again, then re-booted, and it worked fine.
I guess that when the system happens to run into one or more of those bad sectors, then I get fail messages on shut down, ie. the more I write to disk the higher the chance to hit some bad sector (= problems).
OK than, I have to replace the hard drive (I'm actually thinking about replacing the whole $&#295;i&#359; and use this one as second machine -with a new hard drive).
Not all bad, though: first of all, I can install a Debian-based OS while sleeping now; and I learned the command line to check the hard drive looking for bad sectors.
AND - I know I have a bad hdd now.
Thanks for helping (again)

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
The more you use it the more sectors are likely to fail. Every hour you run it may literally be costing you data. If you're going to keep using it I suggest making sure the important stuff is burned to a cd or something.

---

