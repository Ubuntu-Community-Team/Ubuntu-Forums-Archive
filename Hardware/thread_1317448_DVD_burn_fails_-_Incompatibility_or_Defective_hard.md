---
title: "DVD burn fails - Incompatibility or Defective hardware?"
date: 2009-11-06
forum: Hardware
---

### Post by jwvraets on 2009-11-06
Ubuntu 9.1 related... This has been driving me crazy the past 2 days and I could really use some advice/guidance. New PC: AMD Athalon II X4 620 Quad Core, Gigabyte GA-MA785GMT-UD2H mobo, 8 gig RAM, Seagate Barracuda LP 1 Tera SATA HD, LG GH22LS50 CD/DVD writer. HD and DVD drive ara both SATA. Ubuntu 9.10 fresh install (actually 6 times fresh install so you know I am not having a good time). Problem is I cannot burn a CD or DVD. All attempts brick the media. All attemts to follow ideas from threads posted here (permissions software, etc) or on other sites are not solving the problem. Have used Braser, K#B and a trial NERO Linux and absolutely no joy. I even did a Fedora 11 fresh install with exactly identical messages and no joy. But Ubuntu is my target.

Media is fine - tried 2 different name brand CD and DVD blanks.

Burns on a Toshiba Satellite L300 laptop (dual boot with Ubuntu 9.1 upgraded from 9.04) burns with no problems.

Before I send the CD/DVD drive back as defective, is anyone aware of any hardware compatibility issues in the new PC as described above or should I just assume defective drive hardware at this point and send it back under warranty? Advice and/or sympathy appreciated.

JW

---

### Post by Intel91 on 2009-11-06
I am sympathetic. Appreciated?

 Do you have a spare, known working drive laying around you can test? Or can you test the drive in another computer? Try to eliminate defective hardware. It is possible as well that your drive is fine and your motherboard has a problem.

---

### Post by jwvraets on 2009-11-06
Intel91 - a sympathetic ear....TY

Sadly the other desktop is an older mobo lacking SATA support so I cannot swap the drive to other PC. DId I say the drive works fine in read, just not in write. Systems works flawlessly except for the drive write issue. HD is good. Makes no difference which SATA connector I use on the mobo. Still puzzled but appreciate the suggestion.

JW

---

### Post by jwvraets on 2009-11-07
A follow up - After further testing ... I located a PC with a working DVD burner (generic 20x) running Fedora 11. We pulled out the LG from the new PC and replaced it with the generic unit from the other PC and it burns disks flawlessly on the new PC. We then placed the LG burner into the other PC and tested it. It burns disks in then other PC flawlessly (under Fedora 11). Reversing the drive swap, the LG once back in the new PC again reads properly but bricks the disk in write mode.

NOTE: *****COMPATIBILITY ISSUE*******

Conclusion: There is some fundamental hardware incompatibility between the Gigabyte GA-MA785GMT-UD2H AMD785G mATX AM# motherboard and the burner - LG G22LS50 22X SATA DVD Writer with Lightscribe that prevvents burning of disks. 

If you are considering the combination, pick another DVD writer to avoid this problem.

Now back to sorting it out with the supplier....Oh well....

Cheers

JW

---

### Post by Locke_99GS on 2009-12-07
bump for me.

Fails to burn, but reads fine.

```

           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH22LS50
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/cdrw2
                logical name: /dev/dvd2
                logical name: /dev/dvdrw2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

```

```

BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///home/locke/Desktop/brasero_tmp_XW243U.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=8
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/home/locke/Desktop/brasero_tmp_T2U63U
	-exclude-list
	/home/locke/Desktop/brasero_tmp_NCV63U
	-print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /home/locke/Desktop/brasero_tmp_T2U63U -exclude-list /home/locke/Desktop/brasero_tmp_NCV63U -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 2226933
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs Finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=8
	-use-the-force-luke=tracksize:2226933
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/home/locke/Desktop/brasero_tmp_2CKN4U
	-exclude-list
	/home/locke/Desktop/brasero_tmp_OMKN4U
	-A
	Brasero-2.28.2
	-sysid
	LINUX
	-v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /home/locke/Desktop/brasero_tmp_2CKN4U -exclude-list /home/locke/Desktop/brasero_tmp_OMKN4U -A Brasero-2.28.2 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 29
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 30
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 30
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 31
BraseroGrowisofs stderr:   0.22% done, estimate finish Mon Dec  7 18:32:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.45% done, estimate finish Mon Dec  7 18:32:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.67% done, estimate finish Mon Dec  7 18:32:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=2a0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
BraseroGrowisofs stderr: :-( write failed: Invalid argument
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: updating RMA
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 22
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

```

Worked fine with previous GSA-H55N burner.

Main board is Intel D102GGC2.


I haven't attempted with Windows yet.

---

### Post by yellowwaterdog on 2009-12-08
I have same problem, but it is not equipment.  I have installed 9.10 on two different machines (HP NC6120 and Dell Precision 650) and neither will burn a CD or DVD.  I am trying to copy the edubuntu iso to load.
 
Locke, what is "bump to me"?
 
Dave

---

### Post by Ron_ on 2009-12-17
It's not your machine.  I wondered the same about mine until about an hour ago.

I have trashed a stack of media trying to use up-to-date versions of both Brasero and GnomeBaker on Ubuntu 9.10. I am just a newbie who is trying to burn 1 large (4GB) file to a data DVD. I have a new low-end HP desktop with a 16x DVD-/+RW drive, and I am using DVD-R media. I have tried 16x and 4x. The message I get from both apps is:
 :-[ WRITE@LBA=e0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
:-[ write failed: Invalid argument


See related threads at:
[https://answers.launchpad.net/ubuntu/+source/brasero/+question/94334](https://answers.launchpad.net/ubuntu/+source/brasero/+question/94334)
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544)
[http://swiss.ubuntuforums.org/showthread.php?t=1327809&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1327809&page=2)

---

### Post by hansheijmans on 2009-12-18
Have you tried K3b or the evaluation copy of Nero for Linux (downloadable from [www.nero.com]("http://www.nero.com"))?
 
Brasero didn't work for me either!

---

### Post by Locke_99GS on 2009-12-18
@hansheijmans 
It's been determined that this particular issue is a regression in the 2.6.31 kernel.

---

### Post by Ron_ on 2009-12-18
From what I read, 2.6.32 was released a couple of weeks ago.  Any idea whether this problem was addressed?  Any idea how long it takes to appear at Synaptic?

Haven't tried K3b or Nero.  I am temporarily storing my backup files on a few 4GB thumb drives.  I really want Ubuntu / Gnome to work.

---

### Post by Locke_99GS on 2009-12-18
It is unlikely that anything beyond 2.6.31 will come into Karmic's repos.
Download compiled and packaged vanilla kernels here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm unsure if the problem has been fixed; I'm low on media and have been using the laptop to burn. I will test the newer kernels myself when I get more blank media.

---

### Post by Locke_99GS on 2009-12-21
Ok, the issue still exists with 2.6.33 for me. Lame-pants. I'll do further testing as time permits.

---

### Post by dsm iv tr on 2009-12-26
If this is indeed a 2.6.31 regression, then why not downgrade to 2.6.30?

Going to give that a shot for compatibility reasons - I really need to write backups, will report back.

...

Reporting back, I can't complete a boot with the mainline ppa kernel package from 2.6.30. I can't really track down what it is, as I can't even get into recovery mode to nab a shell.

Oh, well. Let's a hope a solution comes soon.

---

### Post by Locke_99GS on 2009-12-26
I have an older Kubuntu (8.04-9.04) intalled in another partition. I'll try using that later, before I wipe it for Lucid.

---

### Post by Ron_ on 2010-01-04
Two people have had recent (tentative) success using 2.6.32.2.  (See [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544?comments=all](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544?comments=all) )

---

### Post by Locke_99GS on 2010-01-04
I'll try that, and try to be a bit more active in my own testing. (I gave up)

---

### Post by zanghi on 2010-01-11
I solved! (it works at least for me)
You must verify that you DVD-writer have pata_atiixp driver for his scsi channel:

```
$ dmesg | grep scsi[0-5]\ :
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
scsi4 : pata_atiixp
scsi5 : pata_atiixp
```4th and 5th chanell are controlled in pata_atiixp mode
then I plugged the SATA cable on 5th SATA connector on my mainboard 
and after reboot:
```
$ dmesg | grep scsi | grep GH22NS50 
scsi 5:0:1:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
```well my DVDRAM is on 5th SATA channel, now

now I can burn DVDs! 

Be sure that in your BIOS you have IDE (not AHCI) in "SATA CONFIGURATION"
after boot the kernel sets automatically on AHCI mode 4 (over 6) channels to AHCI

I noticed that on Intel-based mobo, scsi channels are always pata_atiixp
nb. AHCI is better than PATA_ATIIXP for SATA hard disks

I don't know how to select AHCI/PATA_PIIX mode in grub.conf kernel line

---

### Post by pros on 2010-03-04
> dmesg | grep scsi | grep GH
[    2.820384] scsi 5:0:1:0: CD-ROM            HL-DT-ST DVDRAM **GH22LS50**  TL01 PQ: 0 ANSI: 5

Worked for me also.
Anyway, sort off...

I can burn CDs and DVDs, but the -RW (rewritable) ones, only.
Still no luck with DVD+R or DVD-R.

---

