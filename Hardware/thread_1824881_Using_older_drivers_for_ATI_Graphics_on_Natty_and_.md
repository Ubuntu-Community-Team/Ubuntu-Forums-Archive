---
title: "Using older drivers for ATI Graphics on Natty and newer"
date: 2011-08-14
forum: Hardware
---

### Post by PatrickD-52761 on 2011-08-14
Hello everyone,

This may be asked and answered, but I'm not sure where to start looking. I have two computers (one a Toshiba Satellite A105-S2194 and the other a homebuilt) that use older ATI Radeon cards (Mobility Xpress 200M in the laptop and 9550 in the desktop).  ATI stopped supporting these in their Catalyst 9.3 version, and the drivers that are installed by default don't offer 3-D acceleration.

So, my question is can I uninstall the current drivers, and install the Catalyst 9.2/9.3 drivers that will work?  Also, how do I confirm which drivers are being used at this time?  In my dmesg on the laptop for "drm", it shows the following

> [    2.370952] [drm] Initialized drm 1.1.0 20060810

On the desktop, it shows that it's trying to use the radeon drivers, but when I try LIBGL_DEBUG=verbose glxinfo, I get a segmentation fault error (most likely because it's not using the fglrx drivers).

Ultimately I'm trying to get XBMC to run on the desktop (says it needs hardware acceleration and shuts down) and to run faster on the laptop (it runs, but it's slow and cpu intensive enough that moving the mouse or pressing a key requires 10 seconds or more before it's recognized).

I should add, that the drivers that are recommended are from February 2009.

Thanks, and have a great day:)
Patrick.

---

### Post by realzippy on 2011-08-14
*So, my question is can I uninstall the current drivers, and install the Catalyst 9.2/9.3 drivers that will work? *


The Catalyst 9.3 driver doesn't support X servers past version 1.5..
So simple answer:
No.
Here is a list for all ati cards without catalyst "support":
[http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

---

### Post by Furball588 on 2011-08-14
> **PatrickD-52761 said:**
> ATI stopped supporting these in their Catalyst 9.3 version, and the drivers that are installed by default don't offer 3-D acceleration.

I agree with Zippy, although I was under the impression that this was more of a Ubuntu deal and it's not that it doesn't support it, it's that they're just not enabled by default.  

Additionally, since the Radeon module is an xorg driver, I'm also under the belief that you need to work with an xorg.conf to get things going 

[http://manpages.ubuntu.com/manpages/natty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/natty/man4/radeon.4.html)

I know some people might say that the use of the xorg.conf might be depreciated, but I'm not sure that entirely holds true for something like this.

---

### Post by PatrickD-52761 on 2011-08-14
> **Furball588 said:**
> I agree with Zippy, although I was under the impression that this was more of a Ubuntu deal and it's not that it doesn't support it, it's that they're just not enabled by default.  

Additionally, since the Radeon module is an xorg driver, I'm also under the belief that you need to work with an xorg.conf to get things going 

[http://manpages.ubuntu.com/manpages/natty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/natty/man4/radeon.4.html)

I know some people might say that the use of the xorg.conf might be depreciated, but I'm not sure that entirely holds true for something like this.

I'm pasting the results of lspci -nn |grep ATI and lsmod here, because I'm not sure if I can use the radeon driver (on my laptop), or what driver I'm currently using. 

lspci > 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]


lsmod
> 
Module                  Size  Used by
udf                    83795  0 
crc_itu_t              12627  1 udf
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
md4                    12523  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
dm_crypt               22463  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_realtek   255882  1 
snd_hda_codec_si3054    12924  1 
arc4                   12473  2 
snd_usb_audio          91410  1 
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_hda_intel          24113  7 
snd_hda_codec          90901  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_pcm                80042  7 snd_hda_codec_si3054,snd_usb_audio,snd_hda_intel,snd_hda_codec
ath5k                 144534  0 
ath                    19141  1 ath5k
snd_seq_midi           13132  0 
nls_utf8               12493  2 
cifs                  247650  3 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
gspca_zc3xx            50969  0 
gspca_main             27894  1 gspca_zc3xx
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 ath5k
videodev               75143  1 gspca_main
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
joydev                 17322  0 
lp                     13349  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
cfg80211              156212  3 ath5k,ath,mac80211
snd                    55295  25 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32345  0 
psmouse                73312  0 
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
parport                36746  3 parport_pc,ppdev,lp
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sparse_keymap          13666  0 
serio_raw              12990  0 
i2c_piix4              13095  0 
ttm                    65184  0 
drm_kms_helper         40745  0 
drm                   184164  2 ttm,drm_kms_helper
8139too                23208  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
8139cp                 22497  0 
video                  18951  0 
i2c_algo_bit           13184  0 
sata_sil               13278  3 
ati_agp                13202  0 
pata_atiixp            12968  0 


When I searched for radeon in apt-cache, I found xserver-xorg-video-radeon - X.Org X server -- AMD/ATI Radeon display driver
 which looks like the one I'd want to install (all of this is on the laptop, as the desktop already has the radeon driver installed).

I'll have to look at how to determine if the 3-D acceleration is enabled. Using the test tool shows the 3-D gears, so I would assume it's enabled.  The other issue that I have is that XBMC doesn't list either of my cards as supported (so I'm probably beating a dead horse anyhow).  But either way, I'd like to enable 3-D acceleration if possible for other reasons.

Thanks, and have a great day:)
Patrick.

---

### Post by Furball588 on 2011-08-14
I suspect it's using software acceleration rather then hardware.

I thought I read someone that unity was draining as it was, so perhaps going with classic may be an easier work for ya...

---

### Post by PatrickD-52761 on 2011-08-14
> **Furball588 said:**
> I suspect it's using software acceleration rather then hardware.

I thought I read someone that unity was draining as it was, so perhaps going with classic may be an easier work for ya...

I'll try that next time I want to run XBMC. I'm currently using Unity-2D since the 3-D doesn't work with my card (on either of my computers).

Have a great day:)
Patrick.

---

### Post by .... on 2011-08-15
The open-source radeon driver does support 3D acceleration (through mesa/gallium3D) and it should work out of the box. If you try to install Catalyst (as I suspect you have), it will screw it up.
> I'll have to look at how to determine if the 3-D acceleration is enabled.
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by PatrickD-52761 on 2011-09-03
I've marked this issue as solved--even though in most ways it's not.  Even trying the Gnome Classic (no effects) mode, XBMC is slow and unresponsive. So I removed it completely.  The irony here is I had XBMC running beautifully before. But my MySQL got totally hosed, and I had to uninstall it (which also forced me to uninstall XBMC). Now that everything has been reinstalled, XBMC doesn't work properly.

So, my solution is to use other applications until I can afford a new card for my desktop, and a new(er) laptop.

Hopefully this thread will help others though.  As for results:

On the laptop, glxinfo shows the 3-D as being Software Rasterizer (Mesa Project). On the desktop, I get Display 0: Segmentation Fault for the only message. I believe (but don't quote me) that this is due to the fact that I have my monitor running through a KVM switch.  I say this because in my dmesg on both computers, I keep getting messages about it probing a monitor, but not getting a valid ID from that.

Anyhow, thanks for all of your help. Have a great weekend:)
Patrick.

---

### Post by .... on 2011-09-03
I would recommend this card if you're looking for a good HTPC card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814261103](http://www.newegg.com/Product/Product.aspx?Item=N82E16814261103)
To get the MIR, make sure you take a photo of all of the forms going into the envelope. Too many MIR offers are squirelly.

---

### Post by PatrickD-52761 on 2011-09-04
> **.... said:**
> I would recommend this card if you're looking for a good HTPC card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814261103](http://www.newegg.com/Product/Product.aspx?Item=N82E16814261103)
To get the MIR, make sure you take a photo of all of the forms going into the envelope. Too many MIR offers are squirelly.

Thanks for the suggestion. Unfortunately the motherboard is so old that it only has PCI slots and an AGP 4x slot.  Which bites because I have an ATI Radeon HD2400 sitting around gathering dust (it was in my server before I made that a server).

Have a great day:)
Patrick.

---

### Post by PatrickD-52761 on 2011-09-05
> **.... said:**
> I would recommend this card if you're looking for a good HTPC card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814261103](http://www.newegg.com/Product/Product.aspx?Item=N82E16814261103)
To get the MIR, make sure you take a photo of all of the forms going into the envelope. Too many MIR offers are squirelly.

As a side note, I'm more an ATI person (solely because that's all I've used) and have a "wishlist" on newegg. [http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=100007709%20600007850&IsNodeId=1&srchInDesc=Radeon&page=1&bop=And&CompareItemList=48|14-139-053^14-139-053-TS%2C14-161-318^14-161-318-TS%2C14-161-308^14-161-308-TS%2C14-161-337^14-161-337-TS](http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=100007709%20600007850&IsNodeId=1&srchInDesc=Radeon&page=1&bop=And&CompareItemList=48|14-139-053^14-139-053-TS%2C14-161-318^14-161-318-TS%2C14-161-308^14-161-308-TS%2C14-161-337^14-161-337-TS) (if the link doesn't work, here's a shortened version of it [http://tinyurl.com/atiwishlist](http://tinyurl.com/atiwishlist) ). I'm thinking about the middle two cards, so any comparable nVidia cards will be considered.  As long as they'll work and provide me with 3-D, I'll be happy--regardless of the brand/GPU maker.

Have a great day, and thanks for the suggestion :)
Patrick.

---

