---
title: "Marvell 9123 support, SATA drives lockup"
date: 2010-12-01
forum: Hardware
---

### Post by zeusbuilder on 2010-12-01
first to summarize:

1) ubuntu 10.10, ASUS M2N32
2) 5 internal 2Tb seagate LP drives working great on motherboard
3) 2 new 2Tb drives on ASUS PCIE expander card are NOT WORKING
4) PCIe expander uses Marvell 9123 controller, is this my problem?  [card is SATA 6Gbps capable but the drives are just SATA 3Gbps]
5) what would be a better expansion card, i don't need RAID

now more detail:
===============
i have a ubuntu 10.10 box up and running.  the motherboard is an ASUS M2N32 and the sata host adapter is listed as an MCP55 controller.  it also has a SIL3132 RAID controller, and i am not using hardware (nor software) RAID so this controller doesn't show any associated hardware with it (in disk utility program).

the 6 drives plugged into this motherboard work great.  OS drive is 160GB, the other 5 are 2TB seagate LP (ST32000542AS).  i recently expanded this system by purchasing an ASUS SATA expansion card with 2 ports.  i plugged in two more of the seagate drives.

everything worked fine, briefly.  after copying ~30Gb of data, the system will lock up the drive, it goes completely dead.  i put both of the new drives into a windows 7 box and they are performing fine.  then when put back into ubuntu (NTFS partitioning), they will lock up and "die".  one of them won't even re-format inside ubuntu now.

the ASUS expansion card has a Marvell 88SE9123 PCIe SATA controller chip.  i have not found any special drivers (or i don't know how to find them, more precisely).  i have read some anectdotal evidence that the 91xx controllers are not Linux friendly.

does anyone have this issue, or some advice how to fix it?

link to ASUS expander card i'm using:
[http://www.asus.com/product.aspx?P_ID=pXu758gzoQt3BV9s&templete=2](http://www.asus.com/product.aspx?P_ID=pXu758gzoQt3BV9s&templete=2)

or, search for "ASUS PCIE GEN2 SATA6G"

i found this related post:
[http://ubuntuforums.org/showthread.php?t=1396465](http://ubuntuforums.org/showthread.php?t=1396465)
but it doesn't seem the author or responders came to any solution other than disabling NCQ and i'm not sure i want to do that necessarily, any comments?

thanks in advance

---

### Post by cascade9 on 2010-12-02
IIRC the marvel 9128 isnt exactly linux friendly, but I'm not sure thats your problem.....

> Compatible Models
Maximus III Formula
P7P55D Deluxe
P7P55D EVO
P7P55D PRO
P7P55D
P7P55D LE
P7P55 LX

[http://www.asus.com/product.aspx?P_ID=pXu758gzoQt3BV9s&templete=2](http://www.asus.com/product.aspx?P_ID=pXu758gzoQt3BV9s&templete=2)

Seems that card only works on some motherbaords.....and your motherboaord isnt one of them.

---

### Post by zeusbuilder on 2010-12-02
that's a great observation on the listing of board compatibility but then again, i've NEVER seen any manufacturer list ALL compatible models of motherboards and drives.  seeing yours on the list means "compatible" but not seeing it on the list doesn't mean too much.  especially considering i'm working with and old board they probably didn't bother to test.

---

### Post by zeusbuilder on 2010-12-05
as an FYI to those reading this discussion, i have installed a Promise Technology SATA300 TX4 and the problem went away.  i did not have to install any drivers for my ubu10 box, it worked perfect the first time.

i did have to reformat the drives as something was corrupt on them from the other controller card.  i put them in a windows 7 box and used diskpart to "clean" the partitioning information.  i then went with a GPT partition type and put them in the ubuntu box.

the promise TX4 costs around $75, whereas the ASUS card was ~$20 (quite cheap).  of course the TX4 has four ports, the ASUS just two, and the TX4 is only SATA300, not the SATA600 that the ASUS can do.

by the way, the M2N32 motherboard is NOT on the official compatibility list for the TX4.

---

### Post by agarzon on 2010-12-13
I am going through a similar problem:

[http://ubuntuforums.org/showthread.php?p=10225002#post10225002](http://ubuntuforums.org/showthread.php?p=10225002#post10225002)

though I have a Marvell 9120 controller.

I have a PCIe 4x card which I am trying to get running on my Dell Workstation. 

The controller appears on the Disk utility and on the list of PCI devices, but the drives I connect through it will not mount. Also, the controller info on the disk utility seems incomplete ... 

Any ideas?

---

### Post by zeusbuilder on 2010-12-14
agarzon sent me a private message asking, so i thought it worth making this a bit more clear...if i wansn't quite "to the point" enough.

i did not have any success with the marvell controller, nor did i pursue anything along the lines of new drivers or anything of that nature.  before pulling out my hair over it, i just tried a new card and cables and the problem disappeared.  the promise TX4 is still working well.

along these lines, i think problems of this nature can benefit from the grass roots trouble shooting of simply swapping cables, swap power connectors, try a different PCI slot on the board, etc.  sometimes it's the basics that we overlook!

maybe my 6gbps card didn't like dumbing itself down to 3gbps drives?

i know very little about linux/ubuntu and am not a real hard-core tech expert, but from my current understanding of the situation, i'm going to say that marvell has some issues on linux.

---

