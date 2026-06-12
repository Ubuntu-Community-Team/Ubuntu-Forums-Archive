---
title: "How to Mount Clonezilla Images"
date: 2008-07-28
forum: General Help
---

### Post by gaebriel on 2008-07-28
While searching for how to mount clonezilla images I came across a post here that said it couldn't be done. Unfortunately it's in the archive so I can't post a reply to it to correct it. One definitely can mount clonezilla images to extract files from them and here's how to do it (as per the clonezilla FAQ at [http://drbl.sourceforge.net/faq/index.php#path=./2_System&entry=42_manually_ntfsclone.faq](http://drbl.sourceforge.net/faq/index.php#path=./2_System&entry=42_manually_ntfsclone.faq)):

1. Prepare a large disk in Linux
2. Say if your image is /home/partimag/YOURIMAGE/, and the image is /home/partimag/YOURIMAGE/hda1.ntfs-img.aa, hda1.ntfs-img.ab...
run
"file /home/partimag/YOURIMAGE/hda1.ntfs-img.aa"
to see it's gzip, bzip or lzop image. Say it's gzip, then you can run
cat /home/partimag/YOURIMAGE/hda1.ntfs-img.* | gzip -d -c | ntfsclone --restore-image -o hda1.img -
Then you will have a "hda1.img" which you can mount it by
mount -o loop -t ntfs hda1.img /mnt

Then all the files are in /mnt/

Enjoy!

---

### Post by billstei on 2008-10-06
Are all clonezilla images in an ntfs format, or is that only the case if the original imaged partition was ntfs?  If they can be other formats, how then would the images be cat'd together and mounted?

Bill

---

### Post by thomas_d_j on 2009-02-07
Thanks you're a life saver.  Just did a clean install on my kid's XP box - backup wup files & settings first using FAST wizard, and did a full clonezilla image first just in case.  Well FAST transferred everything except Outlook files & profile.  I was looking like having to find another hard drive to rebuild the CZ image but your tip saved me the trouble.

---

### Post by ELGL on 2009-03-22
Thank You! I Was looking for this :D

---

### Post by jmz2 on 2009-05-31
I have followed your instructions but I get this error in the 25% of the process:
gzip: stdin: invalid compressed data--format violated

It is like gzip don't recognise the rest of the clonezilla backup files as compressed using gzip. In fact seeing the ...ntfs-img.* files in nautilus, only the file ...ntfs-img.aa appears as 'Gzip archive', the rest of the ...ntfs-img.a* appear as not recognised type file.

Can you tell me how can I resolve this?

Thanks your your help.

---

### Post by VMC on 2009-05-31
> **jmz2 said:**
> I have followed your instructions but I get this error in the 25% of the process:
gzip: stdin: invalid compressed data--format violated

It is like gzip don't recognise the rest of the clonezilla backup files as compressed using gzip. In fact seeing the ...ntfs-img.* files in nautilus, only the file ...ntfs-img.aa appears as 'Gzip archive', the rest of the ...ntfs-img.a* appear as not recognised type file.

Can you tell me how can I resolve this?

Thanks your your help.

The reason it even has *.aa in the first place is because you selected split archive up after 2000 mbytes. Do you have #.ab, etc? Maybe you can cat them together and try again. If you have enough space.

---

### Post by jmz2 on 2009-06-01
> **VMC said:**
> The reason it even has *.aa in the first place is because you selected split archive up after 2000 mbytes. Do you have #.ab, etc? Maybe you can cat them together and try again. If you have enough space.

I have more than one restoring file: from .aa to .ag

It is like gzip is only able to see .aa as a gzip file and it doesn't recognise the rest of the files (from .ab to .ag).

Following your sugestion I have tryed this as well but not luck:
> 
:/media/COMPARTIDO/WINDOWS2003-2008-06-22-06-img$ sudo cat hdc1.ntfs-img.aa hdc1.ntfs-img.ab hdc1.ntfs-img.ac hdc1.ntfs-img.ad hdc1.ntfs-img.ae hdc1.ntfs-img.af hdc1.ntfs-img.ag | sudo gzip -d -c | sudo ntfsclone --restore-image -O /dev/sdb1 -
ntfsclone v2.0.0 (libntfs 10:0:0)
Ntfsclone image version: 10.0
Cluster size           : 4096 bytes
Image volume size      : 38724579328 bytes (38725 MB)
Image device size      : 38724585984 bytes
Space in use           : 16197 MB (41,8%)   
Offset to image data   : 56 (0 x 38 ) bytes
Restoring NTFS from image ...
 25,83 percent completed
gzip: stdin: invalid compressed data--format violated


The funniest thing is that few weeks ago I was able to restore this image without problems. And I am sure my image is not corrupted because I had several copies and one of them is on DVD read only.

How can I make gzip realise that all those files are part of one split gzip file? I think this would solve my problem.

Many thanks

---

### Post by VMC on 2009-06-01
Read this note regarding recovery of Clonezilla split gzip files, [HERE]("http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/42_manually_ntfsclone.faq#42_manually_ntfsclone.faq").

---

### Post by thetom on 2009-11-04
i've just made a backup with clonezilla and now i'd like to mount that partition to copy some files from that. i've followed your how to, but it gives me an error of the input. i've read that now clonezilla is using partclone not ntfsclone. can u give me the exact command with that please?


PS i apologize for my bad english.

---

### Post by nutria007 on 2009-11-26
> **Re: How to Mount Clonezilla Images**
 i've just made a backup with clonezilla and now i'd like to mount that partition to copy some files from that. i've followed your how to, but it gives me an error of the input. i've read that now clonezilla is using partclone not ntfsclone. can u give me the exact command with that please?
PS i apologize for my bad english. 	

had the same problem, this worked for me...(note that i used lzop, not gzip)
first downloaded partclone from [http://sourceforge.net/projects/partclone/](http://sourceforge.net/projects/partclone/)
installed the .deb package and...
```
touch /dir-to-new-image/hda1.img
```
and then
```
sudo cat /dir-to-images/sdb1.ntfs-ptcl-img.lzo.* | sudo lzop -d -c | sudo partclone.restore -C -s - -O /dir-to-new-image/hda1.img

```

i hope this will help someone :D

---

### Post by nutria007 on 2009-11-26
can't mount the img, any ideas?

```
sudo mount /dir-to-image/hda2.img /mnt -t ntfs -o loop
mount: se va a utilizar el dispositivo de bucle /dev/loop6
Failed to read last sector (82027826): Argumento inválido
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop6': Argumento inválido
The device '/dev/loop6' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

---

### Post by nutria007 on 2009-11-26
finally it worked!

```
sudo ntfs-3g /path/to/hda2.img /mnt
```

---

### Post by pipeep on 2010-02-14
> **nutria007 said:**
> i hope this will help someone :D

It has. Thank you.

---

### Post by wesswei on 2010-03-30
@ nutria007 and it has helped again. just saved me bum from a ton of headache.

---

### Post by bfitzhugh on 2010-04-09
@nutria007

Worked for me on 64bit.  Had to force partclone to install with the following command:

```
sudo dpkg -i --force-all partclone_0.2.8_i386.deb
```It's important to remember the og's post, especially when determining your image type.  For example my image was gzipped, so I had to use nutria007's statement and replace the lzop with gzip:

```
cat /dir-to-images/sdb1.ntfs-ptcl-img.lzo.* | gzip -d -c | sudo partclone.restore -C -s - -O /dir-to-new-image/hda1.img
```Note: I had to remove all the sudo's except for the partclone one.

---

### Post by akross6966 on 2010-07-13
I have tried call your suggestions but nothing seems to work.  I have  with Ubuntu 9.1 and 10.04 but nothing works so far.  I get an error  saying no file or directory and then gzip errors out saying "gzip:  stdin: unexpected end of file."  

Do I need to be running this from the clonezilla live cd?  I seem to be  missing a vital piece of information.  I would appreciate any help you  could give me.

---

### Post by CorvetteFan86 on 2010-10-28
I follow the instructions and the image comes up as gzip when I use the file command but, when I type the second command: 
**cat ./sda1.ntfs-ptcl-img.* | gzip -d -c | ntfsclone --restore-image -o ./sda1.img** I get an error message "ERROR: You must specify a device file". This seems to be a noob by the error message but I cant seem to find it. Any help would be appreciated.

Thanks,
Thomas

---

### Post by CorvetteFan86 on 2010-11-04
Bump

---

### Post by yaywoop on 2010-11-16
CorvetteFan86: you forgot the "-" at the end of ntfsclone (which makes it use the standard input as a source)

also since your backup is of the format sda1.ntfs-ptcl-img.* the ptcl indicates that partclone was used to back it up, so partclone must be used to restore it as in post 10 and 15

---

### Post by Vijay.Saraff on 2011-03-16
> cat sda1.ext3-ptcl-img.gz.* | gzip -d -c | sudo partclone.restore -C -s - -O hda1.img

That's the command I've used, and the behavior is strange. When it started out the progressbar said it would take about 2 hours to finish, at a rate 1.3 GB/min, but 7 hours later, it still shows 7 hours remaining with a speed of 130MB/min, the rate is decreasing linearly and the time remaining is increasing linearly as well... Has anybody else experienced this or am I doing something stupid?

At this rate it seems like the program will never end! and it's only done 50% of the way.

I tried to abort and mount the partial image as ext3, but that failed as well. Anyone have any ideas?

---

### Post by ttguy on 2011-06-05
> **Vijay.Saraff said:**
> That's the command I've used, and the behavior is strange. When it started out the progressbar said it would take about 2 hours to finish, at a rate 1.3 GB/min, but 7 hours later, it still shows 7 hours remaining with a speed of 130MB/min, the rate is decreasing linearly and the time remaining is increasing linearly as well... Has anybody else experienced this or am I doing something stupid?

At this rate it seems like the program will never end! and it's only done 50% of the way.

I tried to abort and mount the partial image as ext3, but that failed as well. Anyone have any ideas?

I had this sort of behaviour when I was cloning to or from a drive attached via ethernet. - I had a western digital world book external drive And it just took patience. When I physically inserted this drive in my PC via SATA (when the network card on the drive started to flake out) my cloning would be much faster and not display the same behaviour as you see.

---

### Post by ttguy on 2011-06-05
Here is how recently successfully achieved this

Installed partclone from here
[http://sourceforge.net/projects/partclone/files/testing/partclone_0.2.24_i386.deb/download](http://sourceforge.net/projects/partclone/files/testing/partclone_0.2.24_i386.deb/download)

My clonzilla image is at 
/unmirrored/linux_images/2010-09-12-07-img-home/ 
with files called  sda3.ext3-ptcl-img.gz.aa , sda3.ext3-ptcl-img.gz.ab etc

So the ptcl bit tells us they are made using partclone
And the .gz means they are gziped

So

```
cat /unmirrored/linux_images/2010-09-12-07-img-home/sda3.ext3-ptcl-img.gz.* | gzip -d -c | sudo partclone.restore -C -s - -O /unmirrored/hda1.img
```worked creating hda1.img file at  /unmirrored/

The imaged disk was an ext3 so  I mounted with 

```
sudo mount -o loop -t ext3 /unmirrored/hda1.img /mnt
```and it all worked quite well - found the files I wanted to recover and copied them to another location.

So nice post

---

### Post by John Who on 2011-11-08
HI,

I've successfully mounted the image and made changes on a few files. I now want to store these changes in the image and restore it. I tried

```

ntfsclone --save-image -o - /media/sda5/new_image/sda1.img | gzip -c > /home/partimag/newImage/sda1.ntfs-img.aa

```with no errors. If I try to restore the image on the target device, I get the error "Can't have a partition outside the disk!"

How can I create a image incuding the changes?

Thank in advance,

John!

---

### Post by lukie80 on 2011-11-21
> **Vijay.Saraff said:**
> That's the command I've used, and the behavior is strange. When it started out the progressbar said it would take about 2 hours to finish, at a rate 1.3 GB/min, but 7 hours later, it still shows 7 hours remaining with a speed of 130MB/min, the rate is decreasing linearly and the time remaining is increasing linearly as well... Has anybody else experienced this or am I doing something stupid?

At this rate it seems like the program will never end! and it's only done 50% of the way.

I tried to abort and mount the partial image as ext3, but that failed as well. Anyone have any ideas?

Same here. In my case the progress follows quite well the following saturation formula: ```
progress=30%*(1-exp(-time/12.5min)
``` It will never exceed 30%. This must be a JOKE. :D

I think the speed in MB/min is just an overall average value so the instantaneous speed is much lower in real.

By the way, same problem with external USB-HDD and internal SATA HDD. All deviceses using NTFS filesystems, partition being 60GB in size and maybe filled by 30%. CPU is working at 100% all the time. Strange. Any further ideas?

---

### Post by jao_madn on 2012-03-20
Hi,

I had some additions,

I had a my system partclone  image using clonezilla with splitted gzip compression. My goal is to  convert to a single image file in order to mount and extract some  important files. I ended up to convert it to a virtualbox vdi image  since i encounter problem which i discuss below. I was successful in  converting from single image file used info in this thread and to vbox  vdi image and amount the vdi image inorder to extract the file. I was  decided to give up the problem i encounter when mounting the single  partclone image file but for some reason i continue to find solution for  it.

The problem i encounter is that the single image file throw  some error message when using mount option and parclone-utils  (imagemount command)

error in mount -o loop -t ext4 <image file> <mount point>
```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Upon  research on the error msg it points me to some hard disk failure  information which is related on this error msg the problem with the info  is related to physical HD.
Here's how i solve my problem:
First i check the image using e2fsck
```
e2fsck -f partclone_extfs.img 
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 3839527 blocks
The physical size of the device is 3703301 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
partclone_extfs.img: 306832/960992 files (0.2% non-contiguous), 1807690/3839527 blocks

```

Second: using resize2fs
```
resize2fs partclone_extfs.img 
resize2fs 1.41.11 (14-Mar-2010)
Resizing the filesystem on partclone_extfs.img to 3703301 (4k) blocks.
The filesystem on partclone_extfs.img is now 3702784 blocks long.

```

Now command "mount -o loop -t ext4 <mount_image> <mount_point>" works

How  i wish i know this procedure before i take a long path in converting  the single img file to vdi and mount it inside the VM and used shared  folder in vbox.
I

---

### Post by diazemiliano on 2012-04-23
> **nutria007 said:**
> had the same problem, this worked for me...(note that i used lzop, not gzip)
first downloaded partclone from [http://sourceforge.net/projects/partclone/](http://sourceforge.net/projects/partclone/)
installed the .deb package and...
```
touch /dir-to-new-image/hda1.img
```
and then
```
sudo cat /dir-to-images/sdb1.ntfs-ptcl-img.lzo.* | sudo lzop -d -c | sudo partclone.restore -C -s - -O /dir-to-new-image/hda1.img

```

i hope this will help someone :D

Thanks, its very usefull to me.

---

### Post by gonoles9 on 2012-05-13
Thanks for posting that follow-up jao_madn.  I was having the same problem and your solution works great!

---

### Post by Mephist0 on 2013-02-21
Hello everyone! It took me 3 days to be able to read the information out from a defective windows computer i made a clonezilla image from. Maybe someone can benefit from my story.. And also how not to do ;)

nutria007 posted the final solution! THANK YOU!

If you do not want to read all skip to **[Solution]** below! ;)

First i did a clonezilla image (whole harddisk) of a Windows XP laptop that probably had some issues with explorer.. 

I tried to repair WinXP wich failed. Installed Win7 instead. The laptop owner wanted some files from the harddisk, wich i had already installed Win7 on by now.. Had to access it from the CloneZilla image...

I did not have a Linux computer so i downloaded Ubuntu 12.10 and tried to install it on my ESXi 5.0 host (VmWare machine). Of course Ubuntu was to new for the ESXi 5.0 so i had problems... bla bla.. Finally ended up downloading Ubuntu 11.10 instead. Instealled and worked fine!

I tranferred the CloneZilla image from my computer to the ESXi server via FTP to the Ubuntu guest os. (FTP server on my windows 7 computer and FTP client (Filezilla) on the Ubuntu machine. One of the files went very slow to copy, dont know why. When i tried to create a .img file from the CloneZilla backup it didnt work, then i noticed one of the clonezilla image files were a couple of bytes smaller, when i tried to resume the 2gb file it did overwrite it resulting in that i had to wait another hour for the file to complete with the same result (a couple of bytes missing).. 

Gave up that idea. Copied the files (30GB) to a USB disk and went home. 

**[Solution]**

Installed Ubuntu 11.10 on PC at home with WmWare Workstation 7.1.3. Then i mounted the USB disk to the Ubuntu installation and then ran:

```

apt-get install parted (needed for partclone.restore command)

cat sda2.ntfs-ptcl-img.gz.* | gzip -d -c | partclone.restore -C -s - -o sda2.img
```

This produced a 159GB file! woho!

Then i tried to mount it.. Turned out to be problematic.. 

I tried:
```
mount -o loop -t ntfs sda2.img /mnt/ba

Failed to read last sector (312175079): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around? 

root@ubuntu:/home/magnus# file sda2.img 
sda2.img: x86 boot sector, code offset 0x52, OEM-ID "NTFS    ", sectors/cluster 8, reserved sectors 0, Media descriptor 0xf8, heads 255, hidden sectors 401625, dos < 4.0 BootSector (0x80)

```

I searched long for a solution.. Many threads was about people having a image of a whole harddisk with the dd command. But i only had a partition from CloneZilla..

Finally i saw the post from nutria007
and i tried:

```
root@ubuntu:/home/magnus# ntfs-3g sda2.img /mnt/ba
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
```

Tata!! It worked!
I do not know why the mount -o loop command did not work as the most forum topics i found contained that solution.. I almost gave up hope :(

EDIT: I tried again to mount it with "mount -l loop" and it failed again. I thought maybe it did not work the first time because the file system was unclean.. But did not help..

---

