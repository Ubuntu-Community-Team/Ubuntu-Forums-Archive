---
title: "dual boot two versions ubuntu off single boot partition - help"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by adix81 on 2009-01-09
Hi - i was if anyone could help.

i'm trying to setup a seperate install of ubuntu for a testbed without vmware. basically i have it partitioned like this atm.

/boot    - sda5  - ext2
/ (stable system) sda6 - ext3
/home (stable system) - sda7 -ext3
/swap            - sda8
/ (testbed)      - sda9 xt3

my first attempt worked but didn't seem right - installed ubuntu to the testbed partition everything went under root i.e /boot /home etc.. shared the swap.

I edited my stable system menu.lst on sperate /boot (sda5) partition to include testbed build. It worked but brought up another grub menu - i assume from /boot (sda9) on testbed partition, this was a little annoying as i had two menus to choose from.

i then tried a second install this time telling the testbed to use /boot (sda5) partition as its boot partition. 
i.e. both stable and testbed use sda5 as /boot

this over wrote the original grub and i couldn't boot the my stable system. I've restored it now and can boot to my stable system. however cannot boot to my testbed.

i put this into menu.lst

title testbed
root (hd0,8 )
kernel /vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
boot

Is what i'm trying to do possible?

thanks in advance

---

### Post by kranny on 2009-01-09
--->Be sure to have the stable Linux installing grub on the MBR
  --->The testbed (or whatevr u call:D) should install grub on its root partition

---

### Post by louieb on 2009-01-09
Two distros or two versions of a distribution sharing a /boot partition is a pain in the as come kernel update time.    

> I edited my stable system menu.lst on sperate /boot (sda5) partition to include testbed build. It worked but brought up another grub menu -Might be annoying to see two GRUB menus but its the cleanest and safest way to do it.  

Having said that try this:  seems your not pointing to the correct root partition.
```

title testbed
root [COLOR=Red](hd0,7)[/COLOR]
kernel /vmlinuz-2.6.17-10-generic root=[COLOR=Red]/dev/sda9[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic


```Check out this page in particular look for c**hainload, configfile, and dedicated grub partition. **   [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") 
Good fun and luck to you.

---

### Post by adix81 on 2009-01-09
> Might be annoying to see two GRUB menus but its the cleanest and safest way to do it. 


ok cheers - looks like i'll do it that way. I was just hoping to see one boot menu.

---

