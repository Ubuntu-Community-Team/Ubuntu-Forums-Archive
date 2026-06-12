---
title: "[hardy] Input Output error while copying"
date: 2008-10-09
forum: General Help
---

### Post by a2lkulkarni on 2008-10-09
I have Ubuntu 8.04 running on my laptop (inspirion 1525) and PC (Intel 845 motherboard with Intel P4 and Samsun CD RW).
I have problem using compact disks on both the system. My ubuntu is updated with all the updates as of today. On my laptop DVDs work well and do not have any issue, but when I insert a CD it is detected automatically and I can see the folders, but when I try to copy contents from the CD (through GUI) it says "Seek Failed" and can't copy the files. If I use command line to copy it gives input output error (see below).

atul@heron:~$ cp /media/cdrom/mpegav/avseq01.dat .
cp: reading `/media/cdrom/mpegav/avseq01.dat': Input/output error

Just to be clear the CD is good and it is not a disk issue, I have tried with multiple CDs and all the CDs work with windows. dmesg prints following messages:

atul@heron:~$ dmesg |tail
[ 1113.111023] end_request: I/O error, dev sr0, sector 5804
[ 1113.150541] end_request: I/O error, dev sr0, sector 5804
[ 1113.182581] end_request: I/O error, dev sr0, sector 5808
[ 1113.227417] end_request: I/O error, dev sr0, sector 5804
[ 1113.320026] end_request: I/O error, dev sr0, sector 5804
[ 1113.368245] end_request: I/O error, dev sr0, sector 5804
[ 1191.476043] end_request: I/O error, dev sr0, sector 5804
[ 1191.476053] printk: 15 messages suppressed.
[ 1191.476058] Buffer I/O error on device sr0, logical block 1451
[ 1191.476065] Buffer I/O error on device sr0, logical block 1452

I have converted few of windows users to ubuntu users and they are also facing same problem. I have convinced them how ubuntu is better, but however I am failing to answer over this issue, could anybody help me to get this issue resolved.

Let me know if any more input or information is required.
Thanks in advance.

---

### Post by a2lkulkarni on 2008-10-10
Are there any diagnosis steps, which I can follow to see if something is wrong?  Is there anything that we can do or one has to bear with it?

Any help/suggestion is highly appreciated. 

Thanks,
-Atul

---

### Post by geirha on 2008-10-10
Your best friend with these kinds of problems is usually your favorite search engine. Run ```
sudo lshw -class disk
``` which will list information on all harddrives and cd/dvd-drives on your system. You should see the model number of your cd/dvd-drive, so use that with your search (and/or paste the cd/dvd-drive section here)

If the cd/dvd-drive works well in windows, then it more or less has to be a problem with the driver in linux. Chances are someone else has had this problem too and found a workaround. It may also have been fixed in a newer kernel.

---

### Post by a2lkulkarni on 2008-10-10
Thanks for the reply. 

I did google out a bit before posting but couldn't get the answer I was looking for. [This]("https://answers.launchpad.net/ubuntu/+question/10811") one  is almost same but with fiesty (you may like to have a look):

This post do not end with reasonable solution applicable for me.

Following are the details of the hardware:
> PC:
atul@livingrebel:~$ sudo lshw -class disk
*-cdrom                 
       description: CD-R/CD-RW writer
       product: CD-R/RW SW-252S
       vendor: SAMSUNG
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: R952
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
Laptop:
atul@heron:~$ sudo lshw -class disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD+-RW TS-L632H
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: D400
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open


It will be great if you could get something out of above details which leads to the smile on our faces.

Thanks,
-Atul

---

### Post by a2lkulkarni on 2008-10-11
I am loosing patience as we are not able to use CDs. Has anybody got any suggestions?
Can I upgrade to intrepid (beta), will that work?

---

### Post by geirha on 2008-10-11
Sorry for not getting back to you on this. I haven't found any useful information on this I'm afraid. Your best bet is to make a bug report at [https://bugs.launchpad.net/linux/+bugs](https://bugs.launchpad.net/linux/+bugs) about it. This is definately something that should have worked out of the box. 

To speed things up, it's a good idea to do a clean boot, access a CD (that will fail), then do ```
dmesg >/tmp/dmesg-output.txt
``` and upload that /tmp/dmesg-output.txt to the bug report.

---

### Post by a2lkulkarni on 2008-10-14
Thanks a lot geirha for your kind support. I saw your reply immediately the day you posted it, but was busy doing other stuff so didn't reply. Actually I have got the problem a bit narrowed down. I could see that only CDs written as Video CDs can not be read. If one writes normal data CD there is no problem accessing and copying it. These are normal movie CDs that we get into market here (India), Any ideas what is going wrong with that or are these Vieo CDs meant to be used on Windows only?

Anyways, I have raised the bug and the link is [here]("https://bugs.launchpad.net/ubuntu/+bug/279758"). I have not yet updated this with the additional findings and the logs.

---

### Post by geirha on 2008-10-14
Do they work if you play them with a video player? like with mplayer:
```
mplayer vcd://
```

---

### Post by a2lkulkarni on 2008-10-16
Initially it didn't work, it was giving errors like: "Cannot sync MAD frame:" After going through mplayer messages and googling out I got gstreamer0.10-pitfdll  i.e. gstreamer plugin for MS windows binary codes and W32codecs packages installed and it worked.

However to run mplayer I have to give command something like: 
atul@heron:~$ mplayer -afm acm,dshow vcd://6

My friends are happy, so I am! Thanks a lot for your support, it's very appreciated.

Should we update the bug, with our findings (this thread URL?) so that somebody who is handling bugs can get appropriate information?

Thanks,
-Atul

---

### Post by a2lkulkarni on 2008-10-16
Sorry, I forgot to mention that yet the files can't be copied to the hard drive from CD and earlier problem remains there.

---

### Post by geirha on 2008-10-16
I think doing:
```
mencoder -oac copy -ovc copy -o track6.mpg vcd://6
```
should copy track 6 from the vcd to a file called track6.mpg, though I don't have a vcd myself to test with.

Vcds are read differently than data cds ... I think ... though since windows can copy the files directly from the vcd, I think linux should be able to too.

---

### Post by a2lkulkarni on 2008-10-16
Excellent! It works, I guess I can use any VCD ripper to do the job, right?
But whatever you say is absolutely right, we should be able to copy normally as we do in windows :)

---

### Post by geirha on 2008-10-16
> **a2lkulkarni said:**
> Excellent! It works, I guess I can use any VCD ripper to do the job, right?
But whatever you say is absolutely right, we should be able to copy normally as we do in windows :)

Any VCD ripper should work, yes. And I'm happy to hear you now have a workaround at least. :)

---

### Post by olivers on 2008-12-05
I was having a similar problem and found a solution here:
<http://www.usenet-forums.com/linux-general/93599-input-output-error-copying-file-dvd-ram.html>

I've pasted the solution below. For me (on Ubuntu intrepid) the commands were slightly different - I had to use "sudo" before the "mount" command, and I didn't need to specify the udf filesystem type - ubuntu detected that automatically:

$ dd_rescue /dev/scd0 /space/temp/image
$ sudo mount /space/temp/image /mnt/tmp -o loop
$ cp /mnt/tmp/filename.avi /space/dvd/


Original pasted solution:

I managed to copy the disk by using dd_rescue
<http://www.garloff.de/kurt/linux/ddrescue/> and the following:

# dd_rescue /dev/hdd /space/temp/image
# mount /space/temp/image /mnt/tmp -t udf -o loop
# cp /mnt/tmp/DVD_RTAV/VR_MOVIE.VRO /space/dvd/

(/dev/hdd is my DVD-RAM drive).

I was then able to use avidemux to edit the video stream.

dd_rescue will copy block devices, ignoring errors, and is a useful
tool to have around, IMHO.

---

### Post by buixuanduong1983 on 2008-12-30
I also have same problem with Ubuntu 8.10. My CD/DVD writer works well with writing/reading normal CD, DVD, with VCD I still can play it with Totem, VLC, still can open it with Nautilus and see its folder. But when I try to copy its content (avseqxx.dat in mpegav folder), I got this error: There was an error copying the file into..., Error reading from file: Input/output error.
I google around and found some interesting method like dd-rescue, but I'm lazy to build/compile from source code, Another way is using a Window$ virtual machine (I prefer Ubuntu way than using a Window$ machine for that work), but sill not work: Invalid DOS argument.

Then I think of a workaround to copy its content: use VLC convert function (VLC 0.9.4): from VLC, open menu Media/Open Discs,select SVCD/VCD disc, select play mode Convert (small arrow next to Play button), select Outputs to file, select Video codec and Audio codec, Save. And after a while you will get your VCD content as a file.

My problem is what Encapsulation, Video codec and Audio codec to use (see [here]("http://ubuntuforums.org/showthread.php?t=127450") if you need more infor about container, stream, codec...). I tried all Profile but none work: some only have video but not audio, other profiles have audio but no video, some have error: VLC Streaming / Transcoding failed: VLC could not find encoder xx. Again google around and see someone mentions about Medibuntu non-free codecs ([link]("http://ubuntuforums.org/showthread.php?t=952603")), So I installed it ([link]("https://help.ubuntu.com/community/Medibuntu")), try again with VLC convert. This time I try to combine each type of codec and I found this cobination works:
- Video: H-264, WMV1, WMV2, M-JPEC
- Audio: WAV, A52/AC3, MPEG audio
- Encapsulation: (I'm not sure is there an effect if I use different file type, but I choose ASF/WMV)

After that I can copy the content of VCD to a file and play it later.

(Sorry, maybe here is not a good place for that reply as I saw the Hardy thread, but I search all forum and only here have that question, so I still post here, hope someone will google it)

---

