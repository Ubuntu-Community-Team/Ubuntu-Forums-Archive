---
title: "What next.."
date: 2005-01-23
forum: Installation &amp; Upgrades
---

### Post by Jad on 2005-01-23
I have downloaded warty iso file, but this is the first time I download a linux iso file, 
so How to burn it and make the CD bootable to run the installation ?

---

### Post by Skid on 2005-01-23
[QUOTE=Jad]I have downloaded warty iso file, but this is the first time I download a linux iso file, 
so How to burn it and make the CD bootable to run the installation ?[/QUOTE]

Use a program to burn the ISO off to CD, such as Nero, fireburner, etc etc

Reboot, making sure that the CD is checked for bootable media (if not, make it the 1st boot device in your BIOS) and volia!

good luck ! :)

---

### Post by Jad on 2005-01-23
Thanks Skid
I'm using K3b now, but cant find any option to make the CD bootable.
any idea?

---

### Post by gheorghe_pop on 2005-01-23
Here's the simple way to do it:
1.open a terminal
2.go to the directory where you downloaded the iso file
3.when there ,put a blank cd in the cdrw and type:
cdrecord -v speed=2 dev=0,4,0 **name_of_the_iso_file.iso**

---

### Post by Jad on 2005-01-23
okay dokie, 
I'm burning it now
Thank you

---

### Post by LongTooth on 2005-01-23
gheorghe_pop, I'm using XCDRoast to burn ISOs. But I'd like to give my hand a try a blanking, copying and burning CD via the CLI. Does one have to 'point' to the CD Writer? If so, how?  Can you give us more CLI commands or point us to a helpful site? Thanks.

---

### Post by Jad on 2005-01-23
[QUOTE=LongTooth]gheorghe_pop, I'm using XCDRoast to burn ISOs. But I'd like to give my hand a try a blanking, copying and burning CD via the CLI. Does one have to 'point' to the CD Writer? If so, how?  Can you give us more CLI commands or point us to a helpful site? Thanks.[/QUOTE]
 cdrecord --help comes in handy 

Usage: cdrecord [options] track1...trackn
Options:
        -version        print version information and exit
        dev=target      SCSI target to use as CD/DVD-Recorder
        gracetime=#     set the grace time before starting to write to #.
        timeout=#       set the default SCSI command timeout to #.
        debug=#,-d      Set to # or increment misc debug level
        kdebug=#,kd=#   do Kernel debugging
        -verbose,-v     increment general verbose level by one
        -Verbose,-V     increment SCSI command transport verbose level by one
        -silent,-s      do not print status of failed SCSI commands
        driver=name     user supplied driver name, use with extreme care
        driveropts=opt  a comma separated list of driver specific options
        -setdropts      set driver specific options and exit
        -checkdrive     check if a driver for the drive is present
        -prcap          print drive capabilities for MMC compliant drives
        -inq            do an inquiry for the drive and exit
        -scanbus        scan the SCSI and IDE buses and exit
        -reset          reset the SCSI bus with the cdrecorder (if possible)
        -abort          send an abort sequence to the drive (may help if hung)
        -overburn       allow to write more than the official size of a medium
        -ignsize        ignore the known size of a medium (may cause problems)
        -useinfo        use *.inf files to overwrite audio options.
        speed=#         set speed of drive
        blank=type      blank a CD-RW disc (see blank=help)
        format          format a CD-RW/DVD-RW/DVD+RW disc
        formattype=#    select the format method for DVD+RW disc
        fs=#            Set fifo size to # (0 to disable, default is 4 MB)
        ts=#            set maximum transfer size
        -load           load the disk and exit (works only with tray loader)
        -lock           load and lock the disk and exit (works only with tray loader)
        -eject          eject the disk after doing the work
        -dummy          do everything with laser turned off
        -msinfo         retrieve multi-session info for mkisofs >= 1.10
        -toc            retrieve and print TOC/PMA data
        -atip           retrieve and print ATIP data
        -multi          generate a TOC that allows multi session
                        In this case default track type is CD-ROM XA mode 2 form 1 - 2048 bytes
        -fix            fixate a corrupt or unfixated disk (generate a TOC)
        -nofix          do not fixate disk after writing tracks
        -waiti          wait until input is available before opening SCSI
        -immed          Try to use the SCSI IMMED flag with certain long lasting commands
        -force          force to continue on some errors to allow blanking bad disks
        -tao            Write disk in TAO mode. This option will be replaced in the future.
        -dao            Write disk in SAO mode. This option will be replaced in the future.
        -sao            Write disk in SAO mode. This option will be replaced in the future.
        -raw            Write disk in RAW mode. This option will be replaced in the future.
        -raw96r         Write disk in RAW/RAW96R mode. This option will be replaced in the future.
        -raw96p         Write disk in RAW/RAW96P mode. This option will be replaced in the future.
        -raw16          Write disk in RAW/RAW16 mode. This option will be replaced in the future.
        -clone          Write disk in clone write mode.
        tsize=#         Length of valid data in next track
        padsize=#       Amount of padding for next track
        pregap=#        Amount of pre-gap sectors before next track
        defpregap=#     Amount of pre-gap sectors for all but track #1
        mcn=text        Set the media catalog number for this CD to 'text'
        isrc=text       Set the ISRC number for the next track to 'text'
        index=list      Set the index list for the next track to 'list'
        -text           Write CD-Text from information from *.inf or *.cue files
        textfile=name   Set the file with CD-Text data to 'name'
        cuefile=name    Set the file with CDRWIN CUE data to 'name'
        -audio          Subsequent tracks are CD-DA audio tracks
        -data           Subsequent tracks are CD-ROM data mode 1 - 2048 bytes (default)
        -mode2          Subsequent tracks are CD-ROM data mode 2 - 2336 bytes
        -xa             Subsequent tracks are CD-ROM XA mode 2 form 1 - 2048 bytes
        -xa1            Subsequent tracks are CD-ROM XA mode 2 form 1 - 2056 bytes
        -xa2            Subsequent tracks are CD-ROM XA mode 2 form 2 - 2324 bytes
        -xamix          Subsequent tracks are CD-ROM XA mode 2 form 1/2 - 2332 bytes
        -cdi            Subsequent tracks are CDI tracks
        -isosize        Use iso9660 file system size for next data track
        -preemp         Audio tracks are mastered with 50/15 µs preemphasis
        -nopreemp       Audio tracks are mastered with no preemphasis (default)
        -copy           Audio tracks have unlimited copy permission
        -nocopy         Audio tracks may only be copied once for personal use (default)
        -scms           Audio tracks will not have any copy permission at all
        -pad            Pad data tracks with 15 zeroed sectors
                        Pad audio tracks to a multiple of 2352 bytes
        -nopad          Do not pad data tracks (default)
        -shorttrack     Subsequent tracks may be non Red Book < 4 seconds if in SAO or RAW mode
        -noshorttrack   Subsequent tracks must be >= 4 seconds
        -swab           Audio data source is byte-swapped (little-endian/Intel)
The type of the first track is used for the toc type.
Currently only form 1 tracks are supported.

---

### Post by gheorghe_pop on 2005-01-23
LongTooth:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.htm](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.htm)
Read the part about CDBURN IN CLI

---

### Post by LongTooth on 2005-01-23
Jad, thanks for the list. I know you said in your post you use K3B but I've never had any luck with it in Ubuntu. The two times I tried it,  it locked up my system. I had to reinstall. I should have read all the post about this problem., and there were many post.  I'll have to wait for the Hoary release. Maybe they'll have a CD program that will work.  At the moment I'm using XCDRoast but its somewhat cumbersome.  

gheorghe_pop, thanks for the link but  that link is no good. Can you repost it? Thanks.

---

### Post by Jad on 2005-01-23
hmm 
Getting this error

..........................
cdrecord return an unknown error (code 254)
unknown error 254
Cdrecord is not being run with root privilages
This influences the stability of the burning process.
............................


what Next ....

---

### Post by Jad on 2005-01-24
UP...
 :wink:

---

### Post by xcepsn on 2006-06-03
I'm having a similar problem, burning a data cd. It gets 62 % through then spits the cd out.  "cdrecord error 254" What do I do to fix this problem??[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

I've already fixed another problem with k3b tonite by visiting this forum, so I joined!! Thanx peoples.

---

