---
title: "sound problem"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by harivadakara on 2008-02-03
I installed ubuntu 7.10 in my hp520 but no sound .My audio details is given below
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
anybody know how to fix this problem?from where i get firmwere for intel 82801G

---

### Post by sgleo87 on 2008-02-03
Maybe this how to will help...it helped me resolve my sound problems that I had with my Asus V1s laptop: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by KrishnaM on 2008-02-03
hi
I tried this and it worked for me

Getting Intel ICH8 Family (rev 03) Sound Card to Work in Gutsy
the link is [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

I have a hp pavilion dv6753cl from costco 
had the sound not working problem and after doing the simple backport / update thingy as mentioned in the link and a reboot it works fine now.
now on to testing other stuff :)
wireless works
need to test built in webcam and recorder

best of luck

---

