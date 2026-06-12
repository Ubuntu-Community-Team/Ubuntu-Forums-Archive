---
title: "Random lockups.  Is it because of my wireless?  (RT2500)"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by Nazosan on 2007-06-12
On this laptop I've been getting random lockups.  The biggest culprit was the built in sound (some AC97 thing using the snd_intel8x0 module) which was solved by blacklisting it.  I still get occasional random lockups though.  It will go days without a single lockup then just randomly lock up one day out of the blue, or at times even locking up three or four times in the same day.  I know it's a kernel crash because it blinks two LEDs which I was told is how it informs X users of a crash by the kernel.  From reading around here I'm seeing mention of the various different RT wireless drivers causing problems for people with freezes so I'm wondering if this may be the culprit.  In fact, it is true that it most often happens while I'm using the network connection, but that could be coincidence since it's always on and I use the connection a lot in a day anyway.  Unfortunately, this is a laptop with a built in wireless, and I'm broke, so I'm can't really try another wireless, and due to the layout of the building, a wired connection is unrealistic at best right now.  For the record, this is an Averatec 6100A and the wireless is a mini-PCI Ralink RT2500 made by MSI (well, that's what the subsystem says anyway.)

Could the wireless driver be at fault here?  By many of the threads on the subject, I'm inclined to think that they may be.  If so, I don't really know what to do about it though...  I tried to build the very latest drivers in case maybe they have bug fixes (though they have no stable releases, only beta and CVS, which is not a good sign IMO) and got this error:
> make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /downloads/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /downloads/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/downloads/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/downloads/rt2500-1.1.0-b4/Module/rtmp_main.c: In function &#8216;RT2500_open&#8217;:
/downloads/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[2]: *** [/downloads/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/downloads/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
rt2500.ko failed to build!
make: *** [module] Error 1
As far as I can determine, all kernel headers and such are installed.

Some guides for different RT based chipsets seem to have people using alternate drivers instead, but I saw no mention of alternate drivers for the RT2500 in my searches so far.

If the problem is not the wireless, how would I go about finding it anyway?  I thought maybe the logs, but I can't find anything via conventional searching (of course, not knowing exactly which one to look at I'm forced to use all the search terms I can think of as most of the logs are quite huge unfortunately.)  Which log should I be looking at for this particular sort of problem?  Would it even show up in a log considering that the kernel is crashing?  (And if not, how in the heck do I track down the problem?)

---

### Post by dannyboy79 on 2007-06-12
well if you need the wireless to work than I would compile the new RT2xxx from Serialmonkey, if you don't need it than blacklist it, that's most likely the issue but you'll never know unless you try to blacklist it.

Here's the guide for the latest serialmonkey drivers: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

and yes, I know it states RT71 and RT73 but there is the rt2xxx as well. just use the correct source files for your compiling if you need the wireless to work that is.

---

### Post by Nazosan on 2007-06-12
> **dannyboy79 said:**
> well if you need the wireless to work than I would compile the new RT2xxx from Serialmonkey
Yep, that's the one I was trying to compile.  The thing is, I think those are the ones people were complaining about being unstable.

I did manage to get the CVS snapshot to compile.  I'll try it for a while I guess.  I'm a little worried though because those are the most likely to have bugs or other such problems...  Well, I can't be sure for a while, but in the meantime, I wonder how I can diagnose this freezing problem anyway?

> if you don't need it than blacklist it, that's most likely the issue but you'll never know unless you try to blacklist it.
Sorry, I thought I was clear on this.  I would have blacklisted it already if I could do without it, but I can't really.  Considering the randomness with a pretty large time period between the freezes, just disabling it for a little while wouldn't really tell me anything.  Even if it didn't freeze for a week I couldn't be sure.  I could only be sure if it did freeze, but then I'd have to run it for a very very long time with no Internet connection...  Trust me, that's just not optional when this system can do so little else...

---

### Post by Nazosan on 2007-06-12
Ok, that driver didn't stop the crashing certainly.  I was transferring a bunch of files to my server at home and it crashed on me just a few minutes ago.

Perhaps I should first concentrate on diagnosing just what IS the cause of this problem.  I mean, the RT2500 is suspicious because I see people complaining a lot that the drivers are unstable for this series, but whether it is that or not I still don't know how to tell for sure...  Any ideas on how to go about this?

---

### Post by dannyboy79 on 2007-06-13
so it crashed when transferring files? this still leads me to believe that it's a wireless issue. can't you use a hard wired connection and hten try the same thing (transfer same files) and if it doesn't lock up than that's puts more evidence to suggest that it's the wireless card. have you looked at 
/var/log/syslog
/var/log/kern.log
there may be something in there. I don't know if it's possilbe to start whatever program that your using to transfer files in debug mode? like I know if I am having problems with proftpd, I can go to a command line and type in
sudo proftpd -nd5 2>&1 >& /path/to/debug/file
and it'll be very very verbose about everything as it's starting up the ftp server. and that get's put piped into the file that you designate. then you can just read what it says. I did check the man page for nautilus and I didn't see any debug options for it though, if you're using nautilus that is.
here are some tips for tuning samba if that's what you are transferring it over. I have this within my smb.conf under the [global] section:
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
and I don't have any problems, in fact I just transferred a 4.5GB folder from windows to Ubuntu last night, the windows share was mounted using cifs. (that's preferred way over smbfs) Here's the fstab entry:
//192.168.0.4/daniel    /media/WINXP    cifs    credentials=/etc/samba/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777      0       0

and the .smbcredentials file merely has this in it:
username=whateveryourwindowsusernameis
password=whateveryourwindowspasswordis
and has owner:group and permissions like this:
-rwx------   1 root root    36 2007-06-03 11:39 .smbcredentials

not sure what else to tell ya? if all else fails, see if you canb borrow another wirleess card frmo someone and see if you get the same issue, tehn you can rule out that it's your wireless card, if the new does the same thing that is. good luck

---

### Post by Nazosan on 2007-06-13
As I said.  Due to the lay of the house, wired just isn't really going to happen.

> not sure what else to tell ya? if all else fails, see if you canb borrow another wirleess card frmo someone and see if you get the same issue, tehn you can rule out that it's your wireless card, if the new does the same thing that is. good luck
I know of no one with a wireless card that isn't a desktop PCI card.  I most certainly can't afford to buy a new wireless device for this laptop (frankly if I weren't broke I'd be using a proper laptop and would be in Windows XP right now, not Kubuntu...)

Anyway, here's the thing.  It crashed while transferring files, yes, but that doesn't prove anything.  It has also been know to crash while sitting idle doing nothing after I left a room or while I'm trping to type in a response on a forum.  It has also been known to NOT crash while I transferred files or ran a torrent overnight...  That's not to say it couldn't be the wireless -- the wireless is constantly on (linux ignores the on/off switch in fact) so I would presume this means it's constantly negotiating with the router and monitoring connection status.  If the drivers are as buggy and unreliable as what I've read has implied, it would certainly explain how they could just randomly cause the kernel to crash I think.  Anyway, at the next lockup I'll try those two logs though I think I checked them before among others.  It would help if they weren't quite so loaded down with so many messages...

---

### Post by dannyboy79 on 2007-06-13
you sure seem very negative and not open to test out various things which leads me to believe you just want to troll and complain how linux sucks. I am trying to help so it doesn't pay to tell me you'd rather be using windows.

have you ensured that all other ralink modules are blacklisted? like rt71,rt73, and whatnot? i wasn't suggesting using wired permanently, I was suggesting testing for a while is all. 
what does lsmod return? if you see other wireless modules loaded than they are conflicting!

Hvae you tried to disabling stuff/modules that you don't even use? look into sysv-rc-conf  and BUM to streamline what gets loaded at startup.

do you have the latest bios? have you checked your ram with memtest? if your not willing to "try out" things so that you can rule them out, than I don't see this really getting resolved. There's a laundry list of what be causing this.

---

### Post by Nazosan on 2007-06-13
> **dannyboy79 said:**
> you sure seem very negative and not open to test out various things which leads me to believe you just want to troll and complain how linux sucks. I am trying to help so it doesn't pay to tell me you'd rather be using windows.
Based on what?  I CAN'T test.  That hardly makes me unwilling to.  I've already tried updating the drivers even though I had to use less reliable CVS drivers (I was hoping someone would know why I got that error on the more reliable beta release which I think is their version of others' stable releases.)  What, you expect me to go buy a new wireless card with the money I don't have or to buy a huge ethernet cable and run it around the house (it would have to run along the floors in everyone's way) which I may still not be able to afford?  I'm not unwilling to try things like that, I'm unable.  It's just not realistic...

> have you ensured that all other ralink modules are blacklisted? like rt71,rt73, and whatnot?
I've blacklisted those mentioned in that last Wiki link.  I don't know them all to blacklist them all, but I think most importantly I have the rt2500usb module blacklisted which I suspect is the most likely candidate to cause problems.

> i wasn't suggesting using wired permanently, I was suggesting testing for a while is all.
Same thing.  The house doesn't allow for a permanent installation (its a really old house and hasn't exactly been built to the best of specs for the time -- you have no idea how much trouble I've had just with the electrical wiring already in...)  And a temporary test would take about half a week or more to actually be certain because the problem is far too random and has been known to wait that long between crashes before.  I've even had it running 24/7 on a few occasions with no crashes.  Anyway, even if I had such a cable, I would rather use ethernet, so I'd be using it for the full duration of my stay here rather than wireless.  I have never been a fan of wireless with its occasional drops and signal degredation as well as poor support in linux.

> what does lsmod return? if you see other wireless modules loaded than they are conflicting!
Ah, I knew there was such a command, but I couldn't remember what it was.  Well, the only thing I can think of in the list even related to wireless that I could recognize was bluetooth.  Still, I must admit that I would not have recognized rt2500 a couple of weeks ago...  I don't know all of the wireless drivers by far.  To that end, I'm posting the full lsmod output at the end of this post and if you see any you recognize, please let me know.

> Hvae you tried to disabling stuff/modules that you don't even use? look into sysv-rc-conf  and BUM to streamline what gets loaded at startup.
Problem is, I don't know what to disable/enable.  Not only do I have minimal experience with this sort of thing in the past, but to make things worse, most of my linux experience has been on Redhat a long time ago and later with Mandrake/Mandriva.  It is only more recently that I have switched away as they went in a direction I do not like.

> do you have the latest bios?
It's a laptop.  Unfortunately I do, but that's not saying much.  Needless to say, manufacturers aren't exactly falling over themselves to release BIOS updates for laptops.  Well, the wireless isn't built in (though it's built into the laptop, it's a mini-PCI card, not an integrated chip -- I've opened up the laptop enough to verify this myself though I've read it on numerous occasions anyway,) and to my knowledge it was never unstable in Windows, so I suspect BIOS wouldn't be at fault here.

> have you checked your ram with memtest? if your not willing to "try out" things so that you can rule them out, than I don't see this really getting resolved. There's a laundry list of what be causing this.
I have memtested and Prime95ed in the past and both checked out.  That was admitedly a little while back.  I'll probably need to do this again, but at this point, considering how stable the system can be at times, I'm inclined to say that unstable CPU and memory seem unlikely candidates.  If either is unstable, admitedly the system can sometimes hold out surprisingly long, but not that long, and this sort of instability, while somewhat random, should never be quite as random as this has been (at least, not in my decently long experience of overclocking and otherwise working with potentially and not so much potentially as truly unstable hardware.)  Oh, btw, for the record, since this is a laptop I'm not even touching overclocking on it.  I've also set it to always be in "performance mode" in every thing I could find on this as well as even outright uninstalled powernowd -- I never did like that no matter how efficient it may be because processors can sometimes do poorly at lower voltages even at lower clocks in my experience and it sometimes drives me insane how many distros come with this enabled (especially a killer on my desktop which is overclocked via BIOS so PowerNow being enabled by default in some distros really screws things up as suddenly the CPU finds itself running at a too low voltage for a too high clock speed...)  Anyway, I'll retest as soon as I can, but ATM I'm most inclined to believe the hardware is stable (at least, the testable hardware.  There is no Prime95 for wireless cards or SPUs I admit...  And the only test I know of for VPUs is in Windows only.)

As promised, here's my lsmod output:
```
Module                  Size  Used by
snd_usb_audio          79744  0
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_pcm_oss            44544  0
snd_pcm                79876  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_usb_audio,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
bluetooth              55908  0
nls_iso8859_1           5120  1
nls_cp437               6784  1
vfat                   14208  1
fat                    53916  1 vfat
vmnet                  44596  13
vmblock                16288  3
vmmon                 452012  0
binfmt_misc            12680  1
ppdev                  10116  0
powernow_k8            16064  0
cpufreq_stats           7360  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9228  0
cpufreq_conservative     8200  0
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0
pcc_acpi               13184  0
tc1100_wmi              8068  0
sony_acpi               6284  0
dev_acpi               12292  0
dock                   10268  0
asus_acpi              17308  0
sbs                    15652  0
backlight               7040  1 asus_acpi
video                  16388  0
button                  8720  0
ac                      6020  0
container               5248  0
i2c_ec                  6016  1 sbs
battery                10756  0
ipv6                  268960  10
sbp2                   23812  0
parport_pc             36388  0
lp                     12452  0
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0
pcmcia                 39212  0
pcspkr                  4224  0
psmouse                38920  0
serio_raw               7940  0
k8temp                  6656  0
rt2500                178276  1
yenta_socket           27532  2
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_sis96x              6532  0
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
amd64_agp              13700  0
sis_agp                 9604  1
agpgart                35400  2 amd64_agp,sis_agp
i2c_core               22656  2 i2c_ec,i2c_sis96x
af_packet              23816  6
tsdev                   8768  0
joydev                 10816  0
evdev                  11008  6
xt_tcpudp               4224  155
nf_conntrack_ipv4      19468  99
xt_state                3456  99
ipt_REJECT              5632  4
xt_limit                3584  6
ipt_LOG                 7680  6
nf_conntrack_irc        8088  0
nf_conntrack           62600  3 nf_conntrack_ipv4,xt_state,nf_conntrack_irc
nfnetlink               7704  2 nf_conntrack_ipv4,nf_conntrack
iptable_filter          3968  1
ip_tables              13796  1 iptable_filter
x_tables               16388  6 xt_tcpudp,xt_state,ipt_REJECT,xt_limit,ipt_LOG,ip_tables
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  4
usbhid                 26592  0
hid                    27392  1 usbhid
usb_storage            72256  3
libusual               17936  1 usb_storage
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sis5513                14856  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0
ehci_hcd               34188  0
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
sis900                 24704  0
mii                     6528  1 sis900
ohci_hcd               22532  0
usbcore               134280  8 snd_usb_audio,snd_usb_lib,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
pata_sis               14732  0
libata                125720  2 ata_generic,pata_sis
scsi_mod              142348  6 sbp2,sd_mod,usb_storage,sg,sr_mod,libata
thermal                14856  0
processor              31048  2 powernow_k8,thermal
fan                     5636  0
capability              5896  0
commoncap               8192  1 capability
vesafb                  9220  1
fbcon                  42656  72
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
```

---

### Post by Nazosan on 2007-06-23
I just want to add that I have checked with Prime95 and Memtest86+ again.  Still no errors reported.  If there is any hardware instability, it is not the CPU or memory.

Also, were there any other wireless related drivers showing up in that lsmod list?

Oh, and is there any way to do a GPU test in linux?  The biggest problem I had with Ubuntu was that it barely was able to use my GPU at all (OpenGL things even ran below 1 FPS) and though Kubuntu (same version Kubuntu even, 7.04) for some unknown reason has not had this problem, it may still have SOME issues with it.

---

