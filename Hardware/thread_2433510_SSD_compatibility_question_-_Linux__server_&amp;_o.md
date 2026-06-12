---
title: "SSD compatibility question - Linux  server &amp; older mobo"
date: 2019-12-20
forum: Hardware
---

### Post by Krupski on 2019-12-20
Hi all,

I've got a home file server using five 2TB sata drives, running 64 bit Linux. These drives are setup as RAID 6 (data only).  The machine boots and runs from a little 16 GB PCIE x1 Supertalent Corestore flash drive:

[IMG]https://images-na.ssl-images-amazon.com/images/I/41W4Jg%2BuytL.jpg[/IMG]

This card worked like a charm for years, but it's finally dying.

What I think I want to do is get a PCIe to M.2 adapter card and stick in a 32 or 64 gb SSD. I don't have any free SATA ports available (actually there is one external eSATA connector on the back, but I don't want to use it).

Now here's my question and concern: The motherboard is an Intel DQ45CB. It's a Socket 775 board and it has two PCIe x1 slots and one PCIe 2.0 x16 slot. The mobo is almost 10 years old!

I would probably like to use the M.2 NVME SSD, but searching online I worry that the mobo may not support it. As I understand, NVME connects directly to the PCIe bus as opposed to an SATA type controller.

There is also the M.2 AHCI type of SSD which as I understand uses an SATA (or SATA type) of interface.

In other words, as I understand it, the differences are:

[B]M.2 AHCI:  PCIe bus ---> SATA controller chip ---> drive

M.2 NVME: PCIe bus ---> drive[/B]

The NVME drives have 1 key slot while the M.2 AHCI drives have two. That is, an NVME drive can plug into an AHCI connector, but an AHCI drive cannot plug into an NVME connector.

I know NVME is supposed to be (a lot) faster, but I don't care about that.  Since I can buy either type, my question is... will the NVME ssd work in this machine?  Is there a chance the old mobo WON'T support it? Should I get the M.2 AHCI type instead? Is there a chance NEITHER type won't work?

I'm just not familiar with these new SSD types to make a good decision myself.

Oh BTW the server is headless (no video card) so both PCIe X1 and X16 are available to use.

Any advice will be greatly appreciated!

---

### Post by CatKiller on 2019-12-20
The only adaptors I've seen are PCIe ×4, so they wouldn't fit in a ×1 slot. The smallest M.2 drive I've seen is 128 GB. Which drive you could use with the card would depend on the specifications of the card. There is every chance that your motherboard doesn't have the capability to boot from a PCIe slot.

You'll probably have more luck getting a PCIe SATA card for your existing drives and having a new conventional boot drive connected to one of the motherboard's SATA ports.

---

### Post by oldfred on 2019-12-20
I think I have seen mixed results, but generally NVMe worked, but would not boot. Users have to have a boot partition on SATA drive that BIOS supported. BIOS generally did not support boot thru PCIe back with older systems.

       BIOS boot on NVMe drive with old BIOS and PCIe card
[https://ubuntuforums.org/showthread.php?t=2415658](https://ubuntuforums.org/showthread.php?t=2415658)

---

### Post by Krupski on 2019-12-20
> **CatKiller said:**
> The only adaptors I've seen are PCIe ×4, so they wouldn't fit in a ×1 slot. The smallest M.2 drive I've seen is 128 GB. Which drive you could use with the card would depend on the specifications of the card. There is every chance that your motherboard doesn't have the capability to boot from a PCIe slot.

You'll probably have more luck getting a PCIe SATA card for your existing drives and having a new conventional boot drive connected to one of the motherboard's SATA ports.

Well, the problem is... there's no physical room to install another HDD (or SSD for that matter), even if I had another SATA port.

BTW, I do have available both an X1 and X16 slots (the server has no video card).

As far as size, I have seen 32G and 64G drives (albeit as M2 SATA). It seems you're right about the NVME drives... I haven't seen any smaller than 128G.

It's too bad my CoreStore is dying... that thing was the perfect solution to my boot drive problem.    :(

---

### Post by Krupski on 2019-12-20
> **oldfred said:**
> I think I have seen mixed results, but generally NVMe worked, but would not boot. Users have to have a boot partition on SATA drive that BIOS supported. BIOS generally did not support boot thru PCIe back with older systems.

       BIOS boot on NVMe drive with old BIOS and PCIe card
[https://ubuntuforums.org/showthread.php?t=2415658](https://ubuntuforums.org/showthread.php?t=2415658)


That's interesting. When I first got that CoreStore drive, the Linux installer would not "see" the card. But, after I installed the OS onto a regular hard drive (choosing the exact same number of sectors as the CoreStore), then did a DD to image the HDD to the CoreStore, it booted right up.  Very strange - I've never figured out why that happened. 

I wonder if the same thing would happen with the NVME drive... couldn't install Linux directly to it, but could copy an image to it which would then boot.

ARGHHH!! I hate not knowing what to do!

Edit to add: It almost seems like the person who posted in the link you gave me experienced the same strange problem.

---

### Post by oldfred on 2019-12-20
If your old install was BIOS, did the MBR in the drive you originally installed into, then actually be the boot MBR and rest of system was on your flash drive?

---

### Post by Krupski on 2019-12-21
> **oldfred said:**
> If your old install was BIOS, did the MBR in the drive you originally installed into, then actually be the boot MBR and rest of system was on your flash drive?

Let me go through what I did - it may make more sense.

First of all, every setup I ever tried was booting via grub, MBR and BIOS. The MOBO bios does support UEFI booting, but I never used it.

When I built the file server, the storage (ONLY data) was five 2TB SATA drives running as RAID 6 under MDADM. Boot was always from a separate drive, never from any of the 5 drives in the array.

The "boot" drive was a PCIe to 40 pin IDE card with an IDE to compact flash adapter plugged into in and a 16 GB CF card. It worked, but it was slow. I messed around with other boot ideas including a PCIe to 4 compact flash slots (I thought I could RAID 0 it and get more speed). Didn't work.

I got tired of all the "kludge" setups I had and looked for a better way. I ran across that CoreStore flash card (the pic in the first post). Yippee!!! I finally found a clean solution to the kludge.

When the card arrived, I installed it into the file server and disconnected all the 2 TB drives so I wouldn't mess them up (they already had been in use).

So I DD'd an iso image of Ubuntu server onto a USB stick and went to do a fresh install.  Much to my dismay, the partitioner didn't "see" the CoreStore!

I don't recall how I figured it out, but I finally did an install to a junker hard drive and partitioned it exactly the same as the CoreStore would be. Then I booted a live disk with the CoreStore and the HDD installed, then DD'd the HDD to the CoreStore. 

Then I installed JUST the CoreStore and it WORKED! It booted up perfectly and it was FAST!

Lastly, I installed MDADM and all the other stuff, plugged the 5 HDD's back in and it all worked.

The wierd thing was that the CoreStore seemed "dead" when it was blank (Linux installer didn't see it, the mobo BIOS didn't see it), but as soon as I imaged a working Linux image to it, then it worked.

I hope this answers what you are asking (or at least gives you an idea).

Thanks for the replies!

---

### Post by oldfred on 2019-12-21
Still do not understand how it booted then.
But if newer UEFI hardware, that has more options, settings and ways it works.

---

