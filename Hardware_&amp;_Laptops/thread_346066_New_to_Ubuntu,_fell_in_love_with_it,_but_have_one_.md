---
title: "New to Ubuntu, fell in love with it, but have one or two with my laptop configuration"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by arronf on 2007-01-25
Hi there,

I am new to Linux and even newer to Ubuntu, I think it is great but i have had a few installation problems.  Well when i say problems i mean more nuisances.

I first installed Ubuntu about a month and a half ago, i always wanted to run a Linux distro and my hard drive on my laptop had given the ghost up with Windows (so you could say i tempted fate, and am glad), i was able to install Ubuntu where the bad sectors on the HDD weren´t.  I had installed a few distro&#347; before finally settling for Ubuntu.  Each one had issue´s with my Loather Fifi card, and later i found that there was also an issue with the way Toshiba handles it´s pcima slots, but thats a whole different story.  Needless to say Ubuntu worked straight from the off.  Everything worked straight away where other distro´s hadn´t.

So i brought a new laptop in the January sales, i set up a dual boot systems (i know what your going to say, but the uni i´m at is very windows orientated)   

Now with this install it has nearly done everything perfect but there is one or two nuisances, they really don´t stop my day-to-day use of Ubuntu, but it would be nice to fix them.  I have a feeling that it´s just because i´m a little bit of a newbie that these problems are here, and i´m just kinda putting a post in here to try and get ideas where to start looking to fix the problem.

1)ACPI – I told a friend of mine that run´s Gentoo, i had problems with my ACPI functions, and he said that always happens with laptops, and it can be a tricky to fix.  I don´t think he meant that it was impossible and seems as i was only talking to him in passing, i don´t think he could explain what i needed to do to fix it.

The problem as such is that my laptop won´t power down correctly, it goes all the way to the final  	little block on the black screen after you logout and, you can hear the hard drive stop, but it just 	dosen´t turn off.  It´s kinda all right but a little annoying.  I have looked in the kernel and have 	done a lsmod command and have posted that as well;

snd_hda_intel          20116  1
snd_hda_codec         164608  1 snd_hda_intel
sg                     37404  0
8139too                29056  0
ieee80211              35272  1 ipw3945
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
usb_storage            75072  0
mii                     6912  2 8139cp,8139too
libusual               17040  1 usb_storage
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
psmouse                41352  0
serio_raw               8452  0
soundcore              11232  1 snd
evdev                  11392  1
intel_agp              26012  1
agpgart                34888  3 drm,intel_agp
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ext3                  142728  1
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  5 usb_storage,libusual,ehci_hcd,uhci_hcd
ide_generic             2432  0
sd_mod                 22656  3
generic                 6276  0
ata_piix               11780  2
libata                 74892  1 ata_piix
scsi_mod              144648  5 sr_mod,sg,usb_storage,sd_mod,libata
thermal                15624  0
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

Does any have any ideas of where i should start to look to try and remedy this situation.  

I won´t list all the little problems now, but needless to say their all kinda similar, in nature.  They don´t stop Ubuntu from working, and they are only little things.

I hope that someone can give me a hand and i apologizes for my newbie ignorance, but i am willing learn.

I thank you all in advance

Arron

Ubuntu Convert

---

### Post by arronf on 2007-01-25
// i just noticed a spelling mistake it&#347; a Athero´s Wifi card, seems my spell checker was being over zealous.  Not that it matters, as it´s not a wifi problem.

---

