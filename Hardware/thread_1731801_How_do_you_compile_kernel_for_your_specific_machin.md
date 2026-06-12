---
title: "How do you compile kernel for your specific machine"
date: 2011-04-17
forum: Hardware
---

### Post by pepsifx357 on 2011-04-17
I've read over the past several months, different books, ("Linux Administration," "Linux In A Nutshell," "Ubuntu Hacks," and "A practical Guide to Ubuntu Linux | Third Edition."  and different Internet articles, about how to compile a kernel.  Which, actually seems pretty easy to me now.  However I can compile all day, but it's not going to do my machine any good and it only teaches me how to follow directions.  Not a bad thing, just not what I'm looking for.

I would like to compile a Linux kernel for my machine, meaning that its leaned out with only the modules and features that are specific to my computer's hardware.  The closest that I have come to this was that someone mentioned using ```
lsmod
``` to show you the current modules running in the kernel.  So I did this:

```
ben@ben-desktop:~$ lsmod
Module                  Size  Used by
btrfs                 490443  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                919  1 btrfs
ufs                    73261  0 
qnx4                    6941  0 
hfsplus                71472  0 
hfs                    41346  0 
minix                  25303  0 
ntfs                   95303  0 
vfat                    9233  0 
msdos                   6436  0 
fat                    48336  2 vfat,msdos
jfs                   171194  0 
xfs                   694014  0 
reiserfs              226326  0 
binfmt_misc             6599  1 
vboxnetadp              6911  0 
vboxnetflt             18657  0 
vboxdrv               214255  2 vboxnetadp,vboxnetflt
nfsd                  241632  13 
exportfs                3481  2 xfs,nfsd
nfs                   275638  0 
lockd                  65797  2 nfsd,nfs
fscache                46521  1 nfs
nfs_acl                 2257  2 nfsd,nfs
auth_rpcgss            34033  2 nfsd,nfs
sunrpc                193402  14 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
nvidia              10206394  38 
snd_hdspm              32820  0 
snd_pcm                71507  1 snd_hdspm
snd_page_alloc          7152  1 snd_pcm
snd_hwdep               5040  1 snd_hdspm
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_hdspm,snd_seq_midi
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  29 
ipt_addrtype            1611  4 
xt_state                1014  7 
ip6table_filter         1275  1 
ip6_tables             11860  1 ip6table_filter
nf_nat_irc              1168  0 
nf_conntrack_irc        3380  1 nf_nat_irc
nf_nat_ftp              1430  0 
nf_nat                 16321  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5393  1 nf_nat_ftp
nf_conntrack           63354  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi_event      6047  1 snd_seq_midi
iptable_filter          1302  1 
snd_seq                47270  3 snd_seq_midi,snd_seq_midi_event
ip_tables              10524  1 iptable_filter
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110           11423  0 
psmouse                58969  0 
snd                    49006  8 snd_hdspm,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
agpgart                32011  1 nvidia
soundcore                880  1 snd
i2c_nforce2             5179  0 
k8temp                  3196  0 
lp                      7374  0 
parport                31492  1 lp
dm_raid45              81785  0 
usbhid                 37202  0 
hid                    67774  1 usbhid
xor                    15136  1 dm_raid45
floppy                 54343  0 
forcedeth              49465  0 
sata_nv                19452  2 
pata_amd                8746  0 
sata_sil24             11118  0 
sky2                   45127  0 
```

Upon looking at this you can see that I have a virtual box module that i was merely testing with, a paraport module that I really don't need, modules for different file systems that I don't think I need, and various others that I don't know what they do.

I have a AMD athlon X2 4800+ in a ASUS A8N32-SLI-Deluxe mother board.  I also have a 1TB raid 5 that is currently running as well. (Didn't want to make it too easy for me :)  I also have a high end sound card, RME HDSP MADI for recording, and a Nvidia 8800GTS 320MB.

So when I get to the point where I'm typing ```
Make menuconfig
```  What is it that I can remove so that my computer still works, but has a leaner more compact kernel?  This is the question that has hindered me from being successful in the past.

thanks

Ben

Edit: I didn't want to put this on here, because I didn't want to offend anyone.  But I have seen a lot of posts on different forums with people asking what all the menu options mean in the menuconfig editor for the kernel.  I think that the lack of answers to these questions tells me that not a lot of people know that they do.  So if you do know, or know where to get the answers, please take the time to tell us so that more people will know.  It will help out a LOT of people with the same question that I have.

---

### Post by Yellow Pasque on 2011-04-17
Configuring the kernel is fun once or twice, but gets old quickly. Each kernel version changes the options available, so finding a comprehensive guide probably won't be easy. menuconfig itself has a help blurb for each option, and that is the best way to figure out what each option does. There are a lot of things you can disable, but the ones that really matter are the ones built in to the kernel. Optional modules may take up a little bit of space on the disk, but if you're not low on disk space, then why care?

---

### Post by pepsifx357 on 2011-04-17
> **Temüjin said:**
> Optional modules may take up a little bit of space on the disk, but if you're not low on disk space, then why care?

Bragging rights maybe?

Thanks for the heads up.  I just entered make menuconfig about 5 minutes ago and realized that the options were totally different from the last time I did it.

I found the "?" command now so I can read the different descriptions.  They are very technical and hard to understand.  I just wish there was some kind of template for my motherboard so I could understand what is actually needed or not.  I have no idea if I really need some of these or not. Like "Multi-path target under RAID and LVM.

Is it true that if you check an option with the "*" it makes it built in, giving you a faster startup?  Or do I have that all wrong?

---

