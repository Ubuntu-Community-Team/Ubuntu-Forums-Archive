---
title: "Intel DQ45CB - Ubuntu 20.04.3 - how best to implement RAID 1?"
date: 2021-12-06
forum: Hardware
---

### Post by kd1sq2 on 2021-12-06
After many years away from Unix (a long time ago I was an AIX sysadmin for a nice little CAD/CAM/Engineering control cluster) I am now retired. I have seen the error of my ways and want clean up my home systems - to blow Windows out the airlock. (Without a spacesuit!) I'm tired of someone else's business interests dictating to me what hardware I can and cannot use while making me pay through the nose for the privilege.

So, at home I have a couple of machines with Intel DQ45CB motherboards that are equipped identically in terms of hardware and have boot 250GB SSDs and a pair of 500GB Sata HDs installed.

I note that the BIOS in these systems does appear to offer a way to apply RAID to the drives.

I've had no problems installing Ubuntu, testing with the hardware and desired software just to make sure at a basic level that everything will work when it comes to time to set up the final configuration.

Could any kind soul advise me on the way to actually get RAID 1 up and running on these machines? (Performance is less of a concern than reliability for me.) Does documentation exist anywhere that is human-readable that could guide me?

Help me Ubuntu users - you're my only hope!

TIA,
      Lee

---

### Post by #&amp;thj^% on 2021-12-06
A good guide to start with: [https://kifarunix.com/setup-software-raid-on-ubuntu-20-04/](https://kifarunix.com/setup-software-raid-on-ubuntu-20-04/)
I find that author to be very credible. Good Luck.:)

---

### Post by dougdeep2 on 2021-12-08
A lot of people don't like the "fake raid" that many manufacturers build into their motherboards but Intel did do a fairly decent job with theirs.  On the DQ45CB it was known as Intel Matrix Storage Technology (MST).  On later boards, it was called Rapid Storage Technology (RST).  Intel claims that the drivers for either MST or RST are built into Linux and drive arrays created with them will work well with mdadm utilities.  A lot of the MST or RST functions were meant for corporate support environments and the technology is old so you are not going to find a lot of help if it doesn't work correctly.  The MST ROM should be on your motherboards already if you want to experiment.  Worst case is you give up and just set your drives to AHCI to create a software raid.  Best of luck.

---

