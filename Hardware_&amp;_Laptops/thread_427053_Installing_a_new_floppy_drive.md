---
title: "Installing a new floppy drive"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by Cherry Cotton on 2007-04-29
Hello! I'm pretty new to modding my computer in any way; however, I found my brother's old floppy drive in the basement and decided to put it in my Ubuntu box (as a contingency in case my network fails). So, I opened my computer, installed it in an empty drive bay, screwed it in, inserted a ribbon cable into one end (a floppy-specific cable, with the twist), and put the other end into the motherboard. There was one slot left to take a ribbon cable, and it seemed as though it was for a floppy drive, as such did not come with the computer (the other three went to the power supply, CD-ROM drive, and the hard drive).

I tried inserting the ribbon cable into the motherboard each way, and only one worked (which was reassuring). Don't worry, I only applied soft pressure and then switched if nothing gave, trying both ways out in case they both worked (and then I'd have to go and find which way to insert it properly). Fortunately, for me, the hardware n00b, only one way seemed to give any under light pressure. The cable fit perfectly and it seemed my new floppy drive was a go.

Hmmm... I tried mounting it. I created a profile in /etc/fstab... most Linux stuff on the Internet seems to indicate that your floppy drive is usually located at /dev/fd0, but there was only a file in /dev for "/dev/fd," so I used that. I tried mounting it directly, and I tried editing /etc/fstab to get it to use the new disk drive.

Nothing has worked.... I tried removing and then reinstating the floppy drive file using "mknod." I tried that again, this time choosing "/dev/fd0" as the name instead, and changing /etc/fstab to reflect that, and it still doesn't work. That is, I try mounting it, either way, using "sudo mount -a," "sudo mount /dev/fd" (or "fd0"), "sudo mount -t msdos /dev/fd /media/floppy" (yes, I've created the "media/floppy" directory) and the terminal hangs. I'd assume it's doing something, but it does not access the floppy drive, and when I look in the system monitor, neither "bash" nor "terminal" is using up any CPU power (and there's certainly no hard disk activity). I can't even use ctrl-C to cancel. It's very annoying.

Anyway, so I have to close the terminal and open it again, hoping I didn't break anything, which is very annoying. The big problem is that I have no idea if installing the floppy went wrong, or if it went well and Linux simply does not recognize its legitimacy. I can't find anything to, say, auto-recognize a floppy drive (I'm guessing it would have had it been in there when I installed Ubuntu a while back). Anyway, in the immediate term, I'd like to know if there is some way that I can ask Linux to poke and see if there is a floppy drive installed. That would be helpful; I'd like to know if the compuiter can see it at all. Then, I'd really like some help troubleshooting getting it to work. A floppy drive would make an excellent backup plan in case the network goes down and I must move a small document from one computer to another (last time I had to burn a CD--augh!). Also, any physical troubleshooting help would be great, that is, making sure I installed the floppy drive correctly, the ribbon cables are in the right places, my motherboard is happy, etc. etc. I don't think I could have installed it any other way, but I could be wrong, or my motherboard might have problems or God may be punishing me for buying an eMachines box.

Thanks!

---

### Post by solar george on 2007-04-29
Did you connect the power cable to the floppy drive?

If you did you should hear some activity from the drive on bootup.

---

### Post by Cherry Cotton on 2007-04-29
...Oh...

There's just one ribbon going from the floppy drive to the motherboard. I guess you're saying there ought to be two, then. I'll look into that.

I feel silly...

---

