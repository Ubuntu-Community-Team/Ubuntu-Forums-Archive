---
title: "no bootable device found"
date: 2019-06-19
forum: Hardware
---

### Post by joriadams65 on 2019-06-19
Lets start out by saying I took a tumble with laptop in hand and it took a very hard hit, now I get "no bootable device found". I know something is totally f'ed up hardware wise. Toshiba c55dt-a5106 with a 750 gb hd. 

I pulled out an old "working" toshiba laptop c655d-s5091 with an 80gb hd to see if the problem was with the the motherboard or the drive itself.

I swapped the the 750gb hd from the a5106 with the 80gb drive from the s5091 into the c55dt-a5106 laptop and still same error of "no bootable device found". 

So the a5106 laptop would not boot with any hard drive, but would boot with a live cd but find no other drive on laptop. 

Then I tried the old laptop with the 750gb hard drive and that came up with  "no bootable device found"

The only combo that worked was the s5091 with the 80 gb hd. 

I really need to resque the data from the 750 GB hd which has a lot of family pictures on it that i was in the process of backing up when the tragedy occured. 

Now questions are:

 could the hard drive still be good and just too big or not configured correctly for the older laptop to recognize it as a bootable drive?

if the hard drive has been damaged is there a way to swap the physicasl disks or board from one drive to the other drive to recover the data to a completely new drive?

and no i do not want to pay $$$$$ for professional data recovery.

thanks you.

---

### Post by Bashing-om on 2019-06-20
joriadams65; Hymmm ...

Just as a thought -
Boot the liveDVD to the live's boot menu ( escape key as soon as the bios splash screen clears) 
what results when choosing " boot from first hard drive" ?

Maybe it is the boot sector that is hosed on the hard drive ?

[INDENT]maybe
[/INDENT]

---

### Post by Rubi1200 on 2019-06-20
If you can boot to the live desktop, Try Ubuntu option, then open a terminal and run this command:

```
sudo fdisk -l
```

Post the output here please using code tags.

Thanks.

---

### Post by oldfred on 2019-06-20
If you go into UEFI/BIOS is drive shown?
If not shown, no system will see drive as UEFI/BIOS has to report specifications of drive to operating system for use.

New system could be UEFI and old BIOS, and if so then old system would not see new UEFI configuration as bootable.

---

