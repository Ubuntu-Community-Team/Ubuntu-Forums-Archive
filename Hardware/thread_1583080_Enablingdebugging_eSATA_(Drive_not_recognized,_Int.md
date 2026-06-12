---
title: "Enabling/debugging eSATA? (Drive not recognized, Intel H57 chipset)"
date: 2010-09-27
forum: Hardware
---

### Post by T.J. Crowder on 2010-09-27
Hi all,

(I've also [asked this question]("http://superuser.com/questions/191997/getting-ubuntu-to-recogize-my-esata-drive") on SuperUser.com. Also, I posted this here a couple of days ago, but under a stupid title, so reposting to change the title.)

I'm having trouble getting my Ubuntu 10.04 LTS 64-bit desktop to recognise an eSATA drive (external enclosure). The enclosure and drive work just fine if I use the USB2 connector instead, suggesting that I've at least got the drive physically installed in the enclosure correctly, but no luck with eSATA.
 
Here's what I've tried / checked:

1. Connecting the drive naively. Literally, plugging the eSATA cable into the box and turning the drive on, while Ubuntu was running. No reaction, and nothing shows up in the Disk Uility or [FONT="Courier New"]fdisk -l[/FONT].

2. Leaving the drive connected and cold booting Ubuntu (literally from power off). Still nothing on DU or [FONT="Courier New"]fdisk -l[/FONT].

3. Ensuring that the BIOS has the eSATA port enabled (it did, I didn't have to change it).

4. Ensuring that the BIOS is using AHCI. It wasn't, and that hadn't been any problem accessing the internal SATA SSD (the box's primary drive). (The SSD showed up under the PATA controller, because I think the BIOS was doing emulation or something.) Switching the BIOS to use AHCI on the SATA controller didn't make any difference other than that the SSD showed up under the SATA controller instead and was listed as using the ahci driver, as you'd expect.

5. Looking in [FONT="Courier New"]dmesg[/FONT] for anything useful. I don't see any mention of the drive at all (except from when I had it attached via USB).

Other info:

* eSATA is on the motherboard, an [Intel DH57JG]("http://www.intel.com/products/desktop/motherboards/dh57jg/dh57jg-overview.htm"), which uses the Intel H57 chipset.
* Enclosure is an [Apex]("http://www.amazon.co.uk/gp/product/B001T6ZUW2") (cheap, but other than cable length issues people on Amazon seemed to like it, and it's handsome).
* Drive is a [Samsung F3 HD103SJ]("http://www.amazon.co.uk/gp/product/B002MQC0P8").
* Cable is, well, [a cable]("http://www.amazon.co.uk/gp/product/B000SKN8VK").

Unfortunately, I don't have any other machine that supports eSATA so I can do the obvious thing and prove that the rig (enclosure and cable) work over eSATA on another box. :-( And I don't have my desktop set up to dual-boot another OS... So at this stage, I don't know it's a software problem, could be hardware, could be cable, but in case there's something obvious I'm missing...

Someone over on superuser.com suggested I may need specific drivers for the board, but [Intel seems to think]("http://www.intel.com/support/motherboards/desktop/dh57jg/sb/CS-031531.htm") that the kernel already supports the chipset natively.

**Update**: Below, r_avital suggested installing scsitools and running rescan-scsi-bus.sh. No luck, but if it's a chipset support issue, that doesn't surprise me:
```
root@forge:~# rescan-scsi-bus.sh
Host adapter 0 (ahci) found.
Host adapter 1 (ahci) found.
Host adapter 2 (ahci) found.
Host adapter 3 (ahci) found.
Host adapter 4 (ahci) found.
Host adapter 5 (ahci) found.
Scanning SCSI subsystem for new devices
Scanning host 0 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 0 0 0 0 ...
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: INTEL SSDSA2M080 Rev: 2CV1
      Type:   Direct-Access                    ANSI SCSI revision: 05
Scanning host 1 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 2 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning for device 2 0 0 0 ...
OLD: Host: scsi2 Channel: 00 Id: 00 Lun: 00
      Vendor: TSSTcorp Model: CDDVDW SN-S083C  Rev: SB01
      Type:   CD-ROM                           ANSI SCSI revision: 05
Report Luns command not supported (support mandatory in SPC-3)
Scanning for device 2 0 0 0 ...
OLD: Host: scsi2 Channel: 00 Id: 00 Lun: 00
      Vendor: TSSTcorp Model: CDDVDW SN-S083C  Rev: SB01
      Type:   CD-ROM                           ANSI SCSI revision: 05
Scanning host 3 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 4 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
Scanning host 5 channels 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs
0 new device(s) found.               
0 device(s) removed.                 

```
Any ideas? Thanks in advance.
--
T.J. Crowder
tj / crowder software / com

---

### Post by r_avital on 2010-09-27
I'm in the same situation as you (except different laptop and esata drive/enclosure.  I was going to post the same question, so thank you for starting the thread :)

I know next to nothing about eSata drives, but let me as you this: Reading the page on the enclosure that you posted, it has a separate power supply.  Correct?  If so, and please accept my apologies in advance for the stupid question, is it plugged in when you connect via eSata?

Mine is a 2.5" enclosure with no power supply, I suspect I need to give it power via usb, AND connect it via eSata, and the only way to know that eSata is working would be to compare with/without usb transfer rates on large files.

I would love to see what responses you get, in case they shed some light on my situation as well.

---

### Post by T.J. Crowder on 2010-09-27
Hi,
> **r_avital said:**
> ...it has a separate power supply.  Correct?  If so, and please accept my apologies in advance for the stupid question, is it plugged in when you connect via eSata?
LOL, yes it has an external power supply, and yes it's plugged in.

-- T.J.

---

### Post by r_avital on 2010-09-28
Thanks.  In that case, I'd love to know the answer myself.

Something I've tried based on a post elsewhere ([http://www.linuxforums.org/forum/ubuntu-linux/169563-solved-problem-mounting-esata-drive.html):](http://www.linuxforums.org/forum/ubuntu-linux/169563-solved-problem-mounting-esata-drive.html):)

Install the scsitools package, then open a terminal and run the rescan-scsi-bus.sh script as root (sudo /sbin/rescan-scsi-bus.sh ).  With your eSATA drive plugged in and powered on, this forces a rescan of all your drives.

What happens if you turn your computer on with the drive already powered up and plugged in?

---

### Post by T.J. Crowder on 2010-09-28
Hi,
> **r_avital said:**
> Install the scsitools package, then open a terminal and run the rescan-scsi-bus.sh script...
Thanks for that! Useful tool to have on-hand, but no luck I'm afraid. (If it's a chipset support issue, that doesn't surprise me, but I would have liked to have been surprised!) Added the details to my original post.

> **r_avital said:**
> What happens if you turn your computer on with the drive already powered up and plugged in?
That's what I meant by "cold boot" in my original post; I've edited to clarify.

-- T.J.

---

### Post by T.J. Crowder on 2010-09-29
**Solved** It was a build quality issue with the machine, not a driver issue. The backplate of the machine bows out from the connectors so badly that unless you forcibly hold the eSATA connector in, it gets pushed out. So not an Ubuntu problem at all.

Sorry for wasting everyone's time.

Now I'm off to do battle with this poorly-fitting backplate. (Not hyper-happy with the vendor on this, it's the third issue I've run into with this machine.)
--
T.J. Crowder
tj / crowder software / com

---

### Post by light_seeker on 2011-01-19
SOLVED

installed the package **scsitools** and ran ```
sudo rescan-scsi-bus.sh
``` in terminal. That fixed did it!

Also I must mention I had to carefully shave some off plastic from my eSATA cable on the hard drive side. The cable came with my **nexStar Hard Drive Dock**! The connector now goes in about 1mm deeper. I only shaved top and bottom of the connector.

[IMG]http://i1134.photobucket.com/albums/m608/light_seeker1/IMG00136-20110119-1100.jpg[/IMG]

---

### Post by light_seeker on 2011-01-19
After shaving the cable and running rescan-scsi-bus.sh as I mention in my last post the external drive started working on eSATA. 

earlier, in BIOS, I had set SATA Controler to "COMPATIBILITY" mode (Im using a Lenovo T410 laptop). When I switch to it to AHCI mode, ubuntu can not find it. rescan-scsi-bus.sh does not help either.

I may have to install some drivers. Will post here if I figured it out.

```
$ uname -r
2.6.35-24-generic
```

```
$ cat /etc/issue
Ubuntu 10.10 \n \l
```

---

