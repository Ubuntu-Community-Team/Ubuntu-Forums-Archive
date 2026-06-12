---
title: "[SOLVED] Set up alsa like it is on SuSE"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by Monsuco on 2007-12-31
I have tested my sound card and for whatever reason SuSE is the only one that detects it. I don't know why ubuntu doesn't.  How would I set alsa to work on Ubuntu like it does on SuSE.

---

### Post by foolsh on 2008-01-01
post some more info about your system
you can 
```
lspci
```
to list the devices on the pci bus
and 
```
lsmod
```
to list loaded modules

while in suse you can "lsmod | grep snd" to see what is loaded for the sound and see what modules it is using

---

### Post by Brebs on 2008-01-01
The secret is often just "modinfo snd-hda-intel". See [wiki](http://gentoo-wiki.com/HOWTO_Compile_Kernel_with_ALSA).

---

### Post by Monsuco on 2008-01-02
Well here is what I found in SuSE
```
monsuco@linux:~> lspci
bash: lspci: command not found
monsuco@linux:~> lsmod
Module                  Size  Used by
af_packet              29064  2
ip6t_LOG               10496  7
nf_conntrack_ipv6      22848  4
xt_pkttype              5888  3
ipt_LOG                 9984  8
xt_limit                6656  15
snd_pcm_oss            50432  0
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq                54452  0
snd_seq_device         12172  1 snd_seq
ip6t_REJECT             9216  3
xt_tcpudp               7168  4
ipt_REJECT              8448  3
xt_state                6528  8
iptable_mangle          6784  0
iptable_nat            11140  0
nf_nat                 21912  1 iptable_nat
iptable_filter          6912  1
ip6table_mangle         6656  0
nf_conntrack_ipv4      14856  6 iptable_nat
nf_conntrack           61684  5 nf_conntrack_ipv6,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               9752  4 nf_conntrack_ipv6,nf_nat,nf_conntrack_ipv4,nf_conntrack
ip_tables              16324  3 iptable_mangle,iptable_nat,iptable_filter
ip6table_filter         6784  1
ip6_tables             17476  3 ip6t_LOG,ip6table_mangle,ip6table_filter
x_tables               18308  11 ip6t_LOG,xt_pkttype,ipt_LOG,xt_limit,ip6t_REJECT,xt_tcpudp,ipt_REJECT,xt_state,iptable_nat,ip_tables,ip6_tables
ipv6                  268280  19 nf_conntrack_ipv6,ip6t_REJECT,ip6table_mangle
cpufreq_conservative    11272  0
cpufreq_userspace       8704  0
cpufreq_powersave       5888  0
powernow_k8            18564  1
apparmor               40736  0
fuse                   45460  4
loop                   21636  0
dm_mod                 56880  0
fglrx                 737536  11
battery                14724  0
ac                      9604  0
sg                     37036  0
snd_hda_intel         273180  1
uvcvideo               48772  0
snd_pcm                82564  2 snd_pcm_oss,snd_hda_intel
firmware_class         13568  1 uvcvideo
usb_storage            80780  0
snd_timer              26756  2 snd_seq,snd_pcm
compat_ioctl32          5376  1 uvcvideo
sr_mod                 19492  0
shpchp                 35092  0
k8temp                  9600  0
snd                    58164  9 snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_hda_intel,snd_pcm,snd_timer
videodev               30464  1 uvcvideo
i2c_piix4              12556  0
pci_hotplug            33216  1 shpchp
hwmon                   7300  1 k8temp
button                 12560  0
cdrom                  37020  1 sr_mod
i2c_core               27520  1 i2c_piix4
v4l1_compat            16388  2 uvcvideo,videodev
ide_core              122948  1 usb_storage
soundcore              11460  1 snd
v4l2_common            20608  2 uvcvideo,videodev
snd_page_alloc         14472  2 snd_hda_intel,snd_pcm
r8169                  32904  0
ati_agp                12684  0
agpgart                35764  2 fglrx,ati_agp
joydev                 13632  0
ndiswrapper           174328  0
ehci_hcd               34956  0
ohci_hcd               23684  0
sd_mod                 31104  5
usbcore               123756  6 uvcvideo,usb_storage,ndiswrapper,ehci_hcd,ohci_hcd
edd                    12996  0
ext3                  131976  1
mbcache                12292  1 ext3
jbd                    68148  1 ext3
fan                     9220  0
pata_atiixp            12032  0
ahci                   29188  4
libata                137032  2 pata_atiixp,ahci
scsi_mod              140376  5 sg,usb_storage,sr_mod,sd_mod,libata
thermal                20744  0
processor              40876  2 powernow_k8,thermal
monsuco@linux:~> lsmod | grep snd
snd_pcm_oss            50432  0
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq                54452  0
snd_seq_device         12172  1 snd_seq
snd_hda_intel         273180  1
snd_pcm                82564  2 snd_pcm_oss,snd_hda_intel
snd_timer              26756  2 snd_seq,snd_pcm
snd                    58164  9 snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_hda_intel,snd_pcm,snd_timer
soundcore              11460  1 snd
snd_page_alloc         14472  2 snd_hda_intel,snd_pcm
monsuco@linux:~> 
```

Any ideas as to what I could do? Does alsa just use a sort of "driver pack" that works with a wide range of cards or would I have to load the drivers somehow. Oh and lspci didn't work,

I could sure use some help. I do know that my card uses SigmaTel drivers in Windows. I suppose I could look up model of card, etc.

> The secret is often just "modinfo snd-hda-intel". See wiki.A lot of those commands don't work. Is there a config file somewhere in SuSE I could check?

---

### Post by Monsuco on 2008-01-04
OK here is the [gateway page]("http://support.gateway.com/support/drivers/mydl.asp?OS=All%20Operating%20Systems") for this device. It doesn't seem specific as to what variety of sound card I have. I also attached a picture showing all that the Windows hardware manager thing says.

---

### Post by Yellow Pasque on 2008-01-04
I'd say try OSSv4 (see my sig). If it's an IntelHDA compatible device, it should be supported.

---

### Post by Monsuco on 2008-01-06
Here is what I get running from the Ubuntu AMD64 version on a live CD.
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
ubuntu@ubuntu:~$ 

```
> I'd say try OSSv4 (see my sig). If it's an IntelHDA compatible device, it should be supported.I doubt there is an intel device in this thing, in seems to just be AMD hardware. I don't want to install ubuntu unless I know for certain I can get sound to work, since I already have SuSE and vista installed. I would prefer to use AMD64 if possible since I have a 64 bit CPU and Ubuntu 32 bit has issues with my ethernet card.. 

Oh and one more thing, does ndiswrapper work on AMD64?

---

### Post by Yellow Pasque on 2008-01-06
> **Monsuco said:**
> Here is what I get running from the Ubuntu AMD64 version on a live CD.
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
```
I doubt there is an intel device in this thing, in seems to just be AMD hardware. I don't want to install ubuntu unless I know for certain I can get sound to work, since I already have SuSE and vista installed. I would prefer to use AMD64 if possible since I have a 64 bit CPU and Ubuntu 32 bit has issues with my ethernet card.. 

Oh and one more thing, does ndiswrapper work on AMD64?

When I mentioned intel, I was just referring to the Azalia HD standard. Your chip isn't Intel branded, but it follows this standard and uses the intel-hda driver.

I have very similar hardware as you (RS690 chipset, ATI HD Azalia sound device) and I can guarantee you that you that you can get sound in Ubuntu64 with OSSv4 if you can't get it with ALSA.

Yes, ndiswrapper does work in AMD64 (with 32-bit Windows drivers).

---

### Post by Monsuco on 2008-01-08
> **Temüjin said:**
> When I mentioned intel, I was just referring to the Azalia HD standard. Your chip isn't Intel branded, but it follows this standard and uses the intel-hda driver.

I have very similar hardware as you (RS690 chipset, ATI HD Azalia sound device) and I can guarantee you that you that you can get sound in Ubuntu64 with OSSv4 if you can't get it with ALSA.

Yes, ndiswrapper does work in AMD64 (with 32-bit Windows drivers).

Thanks, the sound seems to work now (though I couldn't seem to get that volume control patch to work, annoying, but I don't mind that much).

---

