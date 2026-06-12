---
title: "[SOLVED] Root is suddenly full - out of space again"
date: 2008-11-16
forum: General Help
---

### Post by hubiedo on 2008-11-16
i think i am in big trouble again. this is the second time that my / partition is completely full. i prev added space from swap and it fixed it but now is full again. i think it has to do with Simple Backup not have a proper destination and it is filling up my / partition somehow. 

i cant find any file that i can identify to be the culprit. now Simple Backup doesnt work and i am afraid to shutdown in case it wont come back up again.

my system is a dual boot win2k & ubuntu on separate hd. sdc is a 500 gig sata w/ ubuntu.

any help would really be appreciated








hjk@hjk-linux:~$ sudo find / -size +1000000
/proc/kcore
find: /proc/25912/task/25912/fd/4: No such file or directory
find: /proc/25912/task/25912/fdinfo/4: No such file or directory
find: /proc/25912/fd/4: No such file or directory
find: /proc/25912/fdinfo/4: No such file or directory
/media/RMV BU/2008-11-15_20.50.41.898639.hjk-linux.ful/files.tgz
/bulin/home/hjk/win4.bak/GUEST.IMG
/bulin/home/hjk/win4/GUEST.IMG
/bulin/2008-11-13_23.55.05.906408.hjk-linux.inc/files.tgz
/bulin/2008-11-12_23.55.06.257839.hjk-linux.inc/files.tgz
/bulin/2008-11-11_23.55.36.785286.hjk-linux.inc/files.tgz
/bulin/2008-11-09_23.55.04.772936.hjk-linux.inc/files.tgz
/bulin/2008-11-08_23.55.07.678617.hjk-linux.ful/files.tgz
/bulin/2008-11-10_23.55.05.412925.hjk-linux.inc/files.tgz
/home/hjk/win4/GUEST.IMG
find: /home/hjk/.gvfs: Permission denied
/home/hjk/win4.bak/GUEST.IMG
hjk@hjk-linux:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc3             58605312  58598984         0 100% /
varrun                  501428       776    500652   1% /var/run
varlock                 501428         0    501428   0% /var/lock
udev                    501428       116    501312   1% /dev
devshm                  752144        60    752084   1% /dev/shm
/dev/sdc6             48444392   1297148  44705768   3% /appl
/dev/sdc1              1936396     92240   1746564   6% /boot
/dev/sdc8            286883096  46027320 226397680  17% /bulin
/dev/sdc5             48444392  24443400  21559516  54% /home
/dev/sdc7              1936396    215860   1622944  12% /u
gvfs-fuse-daemon      58605312  58598984         0 100% /home/hjk/.gvfs
tmpfs                   501428     39780    461648   8% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb5             78140128   1493844  76646284   2% /media/BIGDISK
hjk@hjk-linux:~$

---

### Post by drs305 on 2008-11-16
The files you found don't appear to be taking up space in / .

Have you checked to see what is in your root trash bin? 
```

gksudo nautilus /root/.local/share/Trash

```

You can use SHIFT-DEL to remove the Files and Info folders if you find undeleted trash.

For more info refer to the link in my signature line.

---

### Post by bfranky on 2008-11-16
I have a similar problem that came up when trying to upgrade to 8.04. I got a message that root needed more space. So I did apt-get clean to get rid of old downloads and then I removed some programs I never use. 

Here's another question, though. Does anyone know if I can safely remove old linux kernels with the synaptic package manager? There must be six or eight old kernels, headers and images on my root system taking up a lot of space. Can I remove the ones not being used safely?

Thanks for any help. 

Frank

---

### Post by drs305 on 2008-11-16
> **bfranky said:**
> I have a similar problem that came up when trying to upgrade to 8.04. I got a message that root needed more space. So I did apt-get clean to get rid of old downloads and then I removed some programs I never use. 

Here's another question, though. Does anyone know if I can safely remove old linux kernels with the synaptic package manager? There must be six or eight old kernels, headers and images on my root system taking up a lot of space. Can I remove the ones not being used safely?

Thanks for any help. 

Frank

Yes you can. Make sure you know the current kernel in use ("uname -r"). Many recommend keeping at least one older kernel you know works, but it is safe to remove them in synaptic.

The link to Disk Space in my signature line includes ways to recover space on your system.

---

### Post by exploder on 2008-11-16
bfranky, yes, you can remove the old kernels. Make certain to remove the old linux-ubuntu-modules first. This is very important, so you do not have things stuck in residual config. If you follow this advice you will not have any problems with removing the old kernels.

---

### Post by WWSmith36 on 2008-11-16
To uninstall the old kernels that you no longer use, you can open synaptic and hit the search button. In the ´Search´ box put linux-image and in the ´Look in´ box select Name. Right click on the kernels you no longer use (2.6.24-16,17,18) and select Mark for removal. Hit the apply button and this will uninstall the unwanted kernels.

---

### Post by WWSmith36 on 2008-11-16
hubiedo

Please post the output of

```
df -h
```

Thanks

---

### Post by hubiedo on 2008-11-17
since my initial post i have taken another 10g from swap so it wouldn't crash with gparted live cd and found a 10g file in /tmp. so the df -h below reflects that now vs. the first post. 

i still think my / dir is way way to big but can't seem to find why. i want to put the space back in swap and now --- reduce the / size of root. how do i find what is making / so big?

thanks all you guys for your help.

[email]hjk@hjk-linux:/root/.loca[/email]l/share/tracker/data$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc3              66G   45G   19G  71% /
varrun                490M  428K  490M   1% /var/run
varlock               490M     0  490M   0% /var/lock
udev                  490M  120K  490M   1% /dev
devshm                735M   52K  735M   1% /dev/shm
lrm                   490M   39M  451M   8% /lib/modules/2.6.24-21-generic/volatile
/dev/sdc6              47G  1.3G   43G   3% /appl
/dev/sdc1             1.9G   91M  1.7G   6% /boot
/dev/sdc8             274G   44G  216G  17% /bulin
/dev/sdc5              47G   24G   21G  54% /home
/dev/sdc7             1.9G  211M  1.6G  12% /u
gvfs-fuse-daemon       66G   45G   19G  71% /home/hjk/.gvfs

---

### Post by hubiedo on 2008-11-17
i checked the root trash as suggested and there is none.

---

### Post by WWSmith36 on 2008-11-17
You can also free up some additional by emptying the cache and removing any unneeded packages.

```
sudo apt-get clean all
sudo apt-get autoremove
```

---

### Post by ezsit on 2008-11-17
the du command maybe more helpful. du stands for disk usage, and when applied to individual directories with the -h switch, can yield useful results.

$ sudo du -h /tmp
$ sudo du -h /var

Also useful is piping the output to a text file so it is easier to read.

$ sudo du -h /tmp > ~/du_tmp.txt
$ sudo du -h /var > ~/du_var.txt

I believe the syntax is correct, but you may need to man the du command for exact usage. The text files output might also be owned by root, but I'm not sure. Either way, this may be more helpful at locating the file and directory that is taking up too much space. If you du the entire filesystem, the output is tremendous and a real pain to search.

---

### Post by hubiedo on 2008-11-17
wwsmith

thanks for help. no go so far. i had prev tried the suggestions you gave. i still can't believe that / is 44G. 

could it be one of these /proc/.... or /sys/ files below?? what are they?? legit or normal files?? i am thining that 20 gig for the / partition with all of my other partitions, listed above, would be ok or normal. what do you think?

root@hjk-linux:/boot# find / -size +100M
/proc/kcore
find: /proc/8430/task/8430/fd/8: No such file or directory
find: /proc/8430/task/8430/fdinfo/8: No such file or directory
find: /proc/8430/fd/8: No such file or directory
find: /proc/8430/fdinfo/8: No such file or directory
/bulin/home/hjk/filepro_dos/filepro/newaccts/data
/bulin/home/hjk/filepro_dos/filepro/newaccts/shuffle.tmp
/bulin/home/hjk/filepro_dos/filepro/kkmed/data
/bulin/home/hjk/filepro_dos/filepro/kkmed/key
/bulin/home/hjk/filepro_dos/filepro/kkins/data
/bulin/home/hjk/filepro_dos/filepro/kkoldcomments/key
/bulin/home/hjk/filepro_dos/filepro/kkcomments/key
/bulin/home/hjk/.clamtk/viruses/Trash6.VIRUS
/bulin/home/hjk/.clamtk/viruses/Sent.VIRUS
/bulin/home/hjk/.clamtk/viruses/Inbox830.VIRUS
/bulin/home/hjk/.clamtk/viruses/Trash.VIRUS
/bulin/home/hjk/.clamtk/viruses/Inbox278.VIRUS
/bulin/home/hjk/.clamtk/viruses/Trash05.VIRUS
/bulin/home/hjk/.clamtk/viruses/Inbox05.VIRUS
/bulin/home/hjk/.mozilla-thunderbird/rw9xvakv.default/Mail/mail.mgmtkoncepts-3.com/Inbox
/bulin/home/hjk/win4.bak/USER.IMG
/bulin/home/hjk/win4.bak/GUEST.IMG
/bulin/home/hjk/win4/USER.IMG
/bulin/home/hjk/win4/GUEST.IMG
/bulin/2008-11-13_23.55.05.906408.hjk-linux.inc/files.tgz
/bulin/2008-11-12_23.55.06.257839.hjk-linux.inc/files.tgz
/bulin/2008-11-11_23.55.36.785286.hjk-linux.inc/files.tgz
/bulin/2008-11-16_23.55.29.152266.hjk-linux.ful/files.tgz
/bulin/2008-11-09_23.55.04.772936.hjk-linux.inc/files.tgz
/bulin/2008-11-15_06.18.00.588400.hjk-linux.inc/files.tgz
/bulin/2008-11-14_23.55.04.466168.hjk-linux.inc/files.tgz
/bulin/2008-11-10_23.55.05.412925.hjk-linux.inc/files.tgz
/home/hjk/win4/USER.IMG
/home/hjk/win4/GUEST.IMG
/home/hjk/.mozilla-thunderbird/rw9xvakv.default/Mail/mail.mgmtkoncepts-3.com/Trash
/home/hjk/.mozilla-thunderbird/rw9xvakv.default/Mail/mail.mgmtkoncepts-3.com/Inbox
find: /home/hjk/.gvfs: Permission denied
/home/hjk/filepro_dos/filepro/newaccts/data
/home/hjk/filepro_dos/filepro/newaccts/shuffle.tmp
/home/hjk/filepro_dos/filepro/kkcomments/key
/home/hjk/filepro_dos/filepro/kkmed/key
/home/hjk/filepro_dos/filepro/kkmed/data
/home/hjk/filepro_dos/filepro/kkins/data
/home/hjk/filepro_dos/filepro/kkoldcomments/key
/home/hjk/.clamtk/viruses/Inbox278.VIRUS
/home/hjk/.clamtk/viruses/Inbox05.VIRUS
/home/hjk/.clamtk/viruses/Inbox830.VIRUS
/home/hjk/.clamtk/viruses/Trash6.VIRUS
/home/hjk/.clamtk/viruses/Sent.VIRUS
/home/hjk/.clamtk/viruses/Trash05.VIRUS
/home/hjk/.clamtk/viruses/Trash.VIRUS
/home/hjk/win4.bak/USER.IMG
/home/hjk/win4.bak/GUEST.IMG
/appl/filepro/newaccts/shuffle.tmp
/appl/filepro/newaccts/data
/sys/devices/pci0000:00/0000:00:00.0/resource0
/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/resource0
root@hjk-linux:/boot#

---

### Post by hubiedo on 2008-11-17
ezsit

i have done as you suggested and don't really find anything unusual or large that could eat up the / partition. how big is your / partition?

thanks

---

### Post by ezsit on 2008-11-18
I am not at my Ubuntu computer at the moment, but my / filesystem is about 3.4 gb and my /home filesystem is about 33 gb. The /usr directory is usually the largest single part of the / filesystem, but it should not grow once you are no longer installing new applications. 

The /tmp and /var directories are the only two that will grow and shrink based on day to day usage. 

/var will grow as log files are written and if you run a web server, the /var/www directory will fill up as needed. Cron jobs should rotate log files and prevent /var from filling up (I think). /var/cache/apt/archive will grow as you install new programs since the downloaded files are stored there until deleted and the print spooler will fill depending on print jobs (but these should get removed as the print jobs are printed).

/tmp will grow as applications use hard drive space for working with files, such as ISO files while your cd burner is working, or audio/video files as a multimedia application are running. Applications should delete temporary working files as the programs are closed I would hope. It is safe to delete the contents of /tmp as they will be recreated at the next login. I have done

$ sudo rm -r *

within the /tmp directory will no ill effect to clean that directory when needed.

/var and /tmp are the two most likely culprits for growing large if some component is not doing garbage collection as it should.

/proc is a virtual filesystem used to represent what the processes in memory are doing and allow filesystem-like access to processes. The /proc filesystem is part of the posix and Unix standards.

Is your /home mounted on a separate partition from your / - or is it part of your / filesystem? The space problem maybe due to growth in your /home directory.

---

### Post by ezsit on 2008-11-18
> /bulin/home/hjk/filepro_dos/filepro/newaccts/data
/bulin/home/hjk/filepro_dos/filepro/newaccts/shuffle.tmp
/bulin/home/hjk/filepro_dos/filepro/kkmed/data
/bulin/home/hjk/filepro_dos/filepro/kkmed/key
/bulin/home/hjk/filepro_dos/filepro/kkins/data
/bulin/home/hjk/filepro_dos/filepro/kkoldcomments/key
/bulin/home/hjk/filepro_dos/filepro/kkcomments/key
/bulin/home/hjk/.clamtk/viruses/Trash6.VIRUS
/bulin/home/hjk/.clamtk/viruses/Sent.VIRUS
/bulin/home/hjk/.clamtk/viruses/Inbox830.VIRUS
/bulin/home/hjk/.clamtk/viruses/Trash.VIRUS
/bulin/home/hjk/.clamtk/viruses/Inbox278.VIRUS
/bulin/home/hjk/.clamtk/viruses/Trash05.VIRUS
/bulin/home/hjk/.clamtk/viruses/Inbox05.VIRUS
/bulin/home/hjk/.mozilla-thunderbird/rw9xvakv.default/Mail/mail.mgmtkoncepts-3.com/Inbox
/bulin/home/hjk/win4.bak/USER.IMG
/bulin/home/hjk/win4.bak/GUEST.IMG
/bulin/home/hjk/win4/USER.IMG
/bulin/home/hjk/win4/GUEST.IMG
/bulin/2008-11-13_23.55.05.906408.hjk-linux.inc/files.tgz
/bulin/2008-11-12_23.55.06.257839.hjk-linux.inc/files.tgz
/bulin/2008-11-11_23.55.36.785286.hjk-linux.inc/files.tgz
/bulin/2008-11-16_23.55.29.152266.hjk-linux.ful/files.tgz
/bulin/2008-11-09_23.55.04.772936.hjk-linux.inc/files.tgz
/bulin/2008-11-15_06.18.00.588400.hjk-linux.inc/files.tgz
/bulin/2008-11-14_23.55.04.466168.hjk-linux.inc/files.tgz
/bulin/2008-11-10_23.55.05.412925.hjk-linux.inc/files.tgz
/home/hjk/win4/USER.IMG
/home/hjk/win4/GUEST.IMG
/home/hjk/.mozilla-thunderbird/rw9xvakv.default/Mail/mail.mgmtkoncepts-3.com/Trash
/home/hjk/.mozilla-thunderbird/rw9xvakv.default/Mail/mail.mgmtkoncepts-3.com/Inbox
find: /home/hjk/.gvfs: Permission denied
/home/hjk/filepro_dos/filepro/newaccts/data
/home/hjk/filepro_dos/filepro/newaccts/shuffle.tmp
/home/hjk/filepro_dos/filepro/kkcomments/key
/home/hjk/filepro_dos/filepro/kkmed/key
/home/hjk/filepro_dos/filepro/kkmed/data
/home/hjk/filepro_dos/filepro/kkins/data
/home/hjk/filepro_dos/filepro/kkoldcomments/key
/home/hjk/.clamtk/viruses/Inbox278.VIRUS
/home/hjk/.clamtk/viruses/Inbox05.VIRUS
/home/hjk/.clamtk/viruses/Inbox830.VIRUS
/home/hjk/.clamtk/viruses/Trash6.VIRUS
/home/hjk/.clamtk/viruses/Sent.VIRUS
/home/hjk/.clamtk/viruses/Trash05.VIRUS
/home/hjk/.clamtk/viruses/Trash.VIRUS
/home/hjk/win4.bak/USER.IMG
/home/hjk/win4.bak/GUEST.IMG

Is your entire /home directory duplicated in /bulin? Is ClamAV finding several hundred MB worth of virus infected email? Could these be valid reasons for the space use?

---

### Post by Mr_JMM on 2008-11-18
> **hubiedo said:**
> since my initial post i have taken another 10g from swap...

Sorry to jump in here, I'll jump straight out again...

By this, do you mean you shrunk your SWAP partition by *another* 10GB? How big was it before? How big is it now? It really only needs to be 2-4GB. If this is the case then you may be able to find more room still.

I appreciate that this is not the problem but I saw this so thought I'd just throw my $0.02 in.

---

### Post by hubiedo on 2008-11-19
> **ezsit said:**
> the du command maybe more helpful. du stands for disk usage, and when applied to individual directories with the -h switch, can yield useful results.

$ sudo du -h /tmp
$ sudo du -h /var

Also useful is piping the output to a text file so it is easier to read.

$ sudo du -h /tmp > ~/du_tmp.txt
$ sudo du -h /var > ~/du_var.txt

I believe the syntax is correct, but you may need to man the du command for exact usage. The text files output might also be owned by root, but I'm not sure. Either way, this may be more helpful at locating the file and directory that is taking up too much space. If you du the entire filesystem, the output is tremendous and a real pain to search.

thanks for help ezsit

the files are attached. i have recently had plenty of practice with du & df commands. luckily i haved a little unix experience w/ my office computer.

---

### Post by hubiedo on 2008-11-19
mr jmm

appreciate any help or input. original swap was 50 gigs. i have now taken 20 to / partition. i thought swap was supposed to be 10% of hd. 500g = 50 gig. how big should swap be 5 gig??


> **Mr_JMM said:**
> Sorry to jump in here, I'll jump straight out again...

By this, do you mean you shrunk your SWAP partition by *another* 10GB? How big was it before? How big is it now? It really only needs to be 2-4GB. If this is the case then you may be able to find more room still.

I appreciate that this is not the problem but I saw this so thought I'd just throw my $0.02 in.

---

### Post by hubiedo on 2008-11-19
ezsit,

you sent questions:

Is your entire /home directory duplicated in /bulin? Is ClamAV finding several hundred MB worth of virus infected email? Could these be valid reasons for the space use?

home & bulin are separate partitions and only the / partition is giving me a problem. 2x it has filled up and i have added 10 gig each time from swap then found one large file and got 10 back so now has 20g free but / is still 48g or so and seems impossible w/ the other partitions holding most of the info i.e. /home /bulin /appl partitions--see prv post.

thanks

am attaching a screen shot of disk analyzer that someone else asked for.

---

### Post by ezsit on 2008-11-20
hubiedo,

Looking at your du_var.txt file dosen't show too much out of whack. The ClamAV folder is adding to total, but not by any amount that would easily explain your filling your / partition. Your screen shot shows that /bulin takes up most of the space on your system. Is /bulin really mounted on a separate partition from /? - OK I just checked your earlier output from df -h and your filesystems are installed on separate partitions. This is getting weirder. 

Your /var/log directory is about ten times larger than mine at 3.1mb and your /var/lib directory is almost three times larger than mine at 105mb. None of these numbers is outrageous, but if the sizes are growing quickly, then it could fill your / filesystem.

From your earlier output, I still don't know why /bulin appears to contain identical subdirectories to your /home.

I just checked the disk usgae for all of my subdirectories on my / partition and /user takes up 2.2gb out of 2.9gb total. This is the way it should be. /var takes a total of 105mb and /tmp even less. both /sys and /proc take up 0mb each since these are virtual filesystems. None of the other directories take up much space, /lib tops the list at 171mb with /etc coming in second at 12mb, the rest being less than 12mb except for /home which comes in at 37gb (lots-o-mp3s).

Have you checked the /root directory? It is rare I believe, but some program might be running as root and filling up your / filesystem with the /root folder. Just a thought.

---

### Post by hubiedo on 2008-11-22
drs 305 has finally helped solve this problem. there was a dir bulin and a mounted partition /bulin it effectively used up all of my root space 2x, as all of you are aware.

basically i took drs305 suggestion to umount /bulin, then did a:
find / -name bulin 

and found the little culprit a dir bulin, i checked it for what was in it and then deleted it. 

sudo rm -r bulin

cked again for dir bulin -- gone

made a new bulin

sudu mkdir bulin

then remounted /bulin

sudo mount /bulin 

and wallah there it was!! with all the files in it.


Thanks to each of you that tried to help. i can't beleive you guys work so hard to try to help the less experienced guys. 

my new space is below:
hjk@hjk-linux:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc3             68766200   3732664  62954164   6% /
varrun                  501428       252    501176   1% /var/run
varlock                 501428         0    501428   0% /var/lock
udev                    501428       116    501312   1% /dev
devshm                  752144        48    752096   1% /dev/shm
lrm                     501428     39780    461648   8% /lib/modules/2.6.24-21-generic/volatile
/dev/sdc6             48444392   1297232  44705684   3% /appl
/dev/sdc1              1936396     92240   1746564   6% /boot
/dev/sdc5             48444392  25456040  20546876  56% /home
/dev/sdc7              1936396    215860   1622944  12% /u
gvfs-fuse-daemon      68766200   3732664  62954164   6% /home/hjk/.gvfs
/dev/sdc8            286883096  26136088 246288912  10% /bulin

---

### Post by taladan on 2008-11-22
just a pointer here

df and du both use the -h option to make the numbers 'human readable'...that will help get closer numbers.  

Also regarding the question of Swap, no, it doesn't need to be 10% of your hard drive.  It should be around 1-4 GB, depending on how much ram you're running.

Tal

---

### Post by hubiedo on 2008-11-24
thanks tal,

i will adjust my swap space.

the df -h is a little neater for have a snapshot to look at. thanks,

---

