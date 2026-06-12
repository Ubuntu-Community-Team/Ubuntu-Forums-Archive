---
title: "Toshiba Equium L100 gui crash / boot failure"
date: 2011-02-17
forum: Hardware
---

### Post by clenched_sphere on 2011-02-17
Hi all,

I've got an old Toshiba that I'm modding (if anyones interested you can see the project log here: [http://forums.bit-tech.net/showthread.php?t=202281](http://forums.bit-tech.net/showthread.php?t=202281))

I've used various flavours of Ubuntu and Ubuntu derivatives but occasionally run into odd problems that either cause an unrecoverable crash requiring a hard reset, or a boot failure.

Firstly I had Ubuntu 10.10 installed on the 32GB SSD. The SSD is quite old now and I know they don't last long, so when the first boot failure happened and I couldnt recover it I figured something very important got corrupted (something in dmesg about an IO failure on sda1) and removed the drive, replacing it with a 60GB HDD which I know works fine. 

On this 60GB drive, I installed Linux Mint 9 (based on ubuntu) which is what I'm currently using, but I've seen some alarming behaviour from it lately. 

Firstly, it crashes fairly often - this I've pinned down to flash on Firefox, it hasn't happened at any time when I wasn't watching something on youtube.
What happens is that the youtube vid stops buffering, and sometimes reports an error.
Then gnome stops responding properly and no new windows can be opened or old ones closed - keyboard commands still accepted. At this point the GUI is fuber and even restarting X (via ctrl-alt-backspace) doesn't work properly, all I get is a blank desktop. The only fix is a hard reset.

This happened on Ubuntu a couple of times when it was installed, before it did the unrecoverable boot failure thing.

Unfortunately the nature of this made it very hard to get anything from dmesg or similar when it happened but if anyone has a suggestion for logging it I think I can recreate the crash to get more info.

Second part is the boot failure.
When Ubuntu was installed on the SSD, it eventually stopped booting fully and dropped me into a CLI I've never seen before. It wasn't bash or the grub prompt but something else, much more basic. It reported IO erros on sda before doing this, I suppose it was a fallback of sorts. Couldn't get anywhere from there so changed drives and installed Mint. 
I booted it up earlier and it failed to boot but didn't give me a prompt, just sat on the splash screen for far too long. Using ctrl-alt-f5 to drop to cli showed an odd error, something along the lines of "unable to load user id(0)" which I thought odd.

I did a hard reset and managed to boot OK.

I hope that describes the issue (or more accurately the symptoms of the issue) well enough for some conjecture on what the cause may be and what information is needed to find out for sure.

A side note, due to the modding I've been doing with this it is possible that the mainboard has some microfractures but unlikely (atleast I hope it's unlikely) as I've been careful with the parts. It's also practically impossible for me to know either if they are present or they are the cause, so I'd like to explore other avenues first.

I think what I'll do now is try to recreate the GUI crash while tailing dmesg and teeing it to another file I can look at when I reboot, this might give me something interesting.

Thanks for reading :)

---

### Post by clenched_sphere on 2011-03-15
Update:

I've gotten nowhere with this problem except to confirm it only happens when using Flash on a browser.
To make Mint 9 GUI crash unrecoverably, all I have to do is watch 2 - 4 fairly short youtube videos.

Log entries that looked interesting were mostly IO errors for /dev/sda and something about can't find id for user 0.

Help on the net for this is scarce as nobody seems to have the whole OS pulled down by a browser bug, and I don't have anything to try so unless someone has any wisdom to share I won't be chasing it up.
Hate to say it but I think I'll go look for my XP cd....

---

