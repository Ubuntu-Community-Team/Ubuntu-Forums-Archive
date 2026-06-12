---
title: "Grub Error 18 after one month"
date: 2008-05-04
forum: Hardware
---

### Post by Synival on 2008-05-04
I got this laptop one month ago (Gateway MT6728), removed Vista, installed Ubuntu, and no real problems until today when I got some I/O errors randomly.  Now I get this when I boot:

-----
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 18
-----

The error shows up after about a minute and it sounds like the hard drive is struggling a bit.  I booted a GParted LiveCD, and it stalls here for about a minute:

-----
*   udev loading module i2c_i801     [ !! ]
-----

It drops to the console after Xorg fails to boot and I get this message every 5 seconds or so:

-----
ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
ata1.00: (irq_stat 0x40000008)
ata1.00: cmd 60/08:00:3f:00:00/00:00:00:00:00:00/40 tag0 cdb 0x0 data 4096 in
              res 51/40:08:3f:00:00/00:00:00:00:00:00/40 Emask 0x9 (media error)
sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
-----

...and occassionally this:

-----
Buffer I/O error on device sda1, logical block 0
(..) block 1
(..) block 2
etc.
-----

So is my hard drive dead or do I need to fiddle with GRUB to get it working again?

---

### Post by nazareno on 2008-05-04
Look you can download supergrub and burn it on a cd , use as a boot cd then get in and find the option where it says "restore grub to MBR" . 
i think you can reach it by entering to the option "Grub & Linux" .

---

### Post by Synival on 2008-05-04
Wow, thanks for the fast reply.  Just curious -- will this require reinstallation or wipe my partition in any way?

---

### Post by Synival on 2008-05-04
Well, I downloaded supergrub and selected "Restore GRUB to Hard Drive (MBR)", and it does this:

-----
  Booting 'trying /grub/stage1 /boot/grub/stage1'

selectfile /grub/stage1 /boot/grub/stage1
-----

Then a loooong wait, maybe 5 minutes or so...

-----
Error 15: File not found
  Bootng 'not lucky'

pause SGD has NOT succeeded :(
SGD has NOT succeeded :(
-----

Any thoughts?

---

### Post by Synival on 2008-05-04
Bump.  Time to get a new drive?

---

### Post by TheMemphisExperience on 2008-05-05
Maybe you need a new disk. Did you check GRUBs website for info on error 18? I happened to see something about it while looking up splash screen image how-tos.

---

### Post by Synival on 2008-05-06
Looks like I just need a new drive.  Shocking that this would happen one month after purchase, but I guess that's the price I pay for a Gateway laptop.  And of course wiping Vista and installing Ubuntu voided my warranty (assuming I had any to begin with).

Thanks for the support!

---

### Post by jimv on 2008-05-06
If Gateway won't replace your HD, try the manufacturer of the drive.

It's worth a shot.

---

