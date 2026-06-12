---
title: "hard disk error on boot: init: ureadahead main process (308) killed by BUS signal"
date: 2010-08-19
forum: Hardware
---

### Post by StevenRichard on 2010-08-19
Hello everybody,

after an unsuccessful research about the following problem I found no other way than register and ask you for help.

On my Thinkpad x60s using Xubuntu 10.4 (although I don't think the problem is not related to the OS) I was programming happily when temporary freeze-outs occured. As I wanted to restart I hear ticking from my hard-disk (like grinding sand).

On reboot, the grinding noice is gone, but the console shows the above mentioned error (the number 308 differs, sometimes 267, sometimes 270): 
```
init: ureadahead main process (308) killed by BUS signal
```

It then shows (shortend):
```
[some process number] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0xx action 0x0
irq_stat 0x40000001
failed command: READ DMA
cmd c8/00:008:87:2d:04/00:00:00:00:/e0 tag 0 dma 4096 in
res 51/40:07:88:2d:04/00:00:00:00/e0 Emask 0x9 (media error)
status: { DRDY ERR }
error: { UNC }
end_request: I/O error, dev sda, sector 273800

```

After some time I get the option to either ignore it, skip mounting or manually mount it. 

I choose the latter and am forwarded into a root shell with read-only permission. cd-ing into my home-folder shows an error message similar to the above one (including different but still weird numbers) but all my files are ls-able and I can cat them, too. 

So, I then do a fck of that hard disk and get five or six blocks of that weird message (same numbers) and a warning:
```
Warning... fsck.ext4 for device /dev/sda1/ exited with signal 7.
```

man fsck tells me that 7 stands for:
```
1 - File system errors corrected
2 - System should be rebooted
4 - File system errors left uncorrected. 

```

1: *yay*
2: did that, same behaviour, though; 
4: I don't know how to correct them myself. So, I fsck -y for automatically doing some magic: No magic happens. Still 5 or 6 blocks of above message. And exiting with the same singal. Using fsck from util-linux-ng 2.17.2

Feeling desperate I fsck -r to see if I am being asked for any confirmations: But none asked. 

Then I start with a XUbuntu Live-CD, mount my /dev/sda1 and cruise through the filesystem: little higher latency on the commands, but no error-messages at all. And fsck says all clean.

A reboot without the Live-CD shows the same errors as depicted above.

And this is where my few linux skills and sanity end. Do you have an idea what to do further? Could you please point me into the right direction?

Cheers, 
Steven

Update 1: ureadahead ends with 
```
 Bus error 
```

Update 2: tail dmesg:
sd 2:0:0:0: [sda] Unhandled sense code
sd 2:0:0:0: [sda] Result hostbyte=DID_OK driverbyte=DRIVER_SENSE
Descriptor sence data with sense descriptors (in hex): 
< some hex >
sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto rellocate failed
...
ata3: EH complete

---

