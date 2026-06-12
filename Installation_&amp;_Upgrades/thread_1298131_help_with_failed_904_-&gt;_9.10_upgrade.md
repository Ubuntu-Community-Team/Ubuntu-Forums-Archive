---
title: "help with failed 904 -&gt; 9.10 upgrade"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by kylegio on 2009-10-22
ran the upgrade from 9.04->9.10 last night, took about an hour to download all the updates etc, restart afterwards and now it will not boot, during the boot i get
> 
Begin: Running /scripts/local-bottom ...
Done.
Begin Running /scripts/init-bottom ...
Done.
mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (907) terminated with status 127


the system then stays at that.
i am currently downloading the install cd for 9.10 and going to try to boot from the cd, however there is a lot of important/irreplaceable data on my drive, as soon as i can get it to boot from cd i am going to back up as much as i can but i would prefer to just fix whatever is wrong instead of wiping the hard drive and starting again. is there a method of repairing this once i get into linux using a boot cd?

can anyone help/suggest a fix?


thanks
Kyle

---

### Post by utnubuuser on 2009-10-22
log out, reboot, at grub select recovery,  then select dpkg -fix-broken.  I think it's one of the options when you go through the recovery options in grub, or at the shell type > sudo apt-get install --fix-broken

man apt-get:       -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect(8) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.

---

### Post by kylegio on 2009-10-22
thanks for your reply, 
unfortunatly when i start my system and get to the grub screen i get the same error no matter what i try to boot, the only thing that will load is memtest. i am however into linux using a boot cd

---

### Post by kylegio on 2009-10-22
my options in grub are ubuntu 9.04  (shows 3 different kernels all 9.04) then a recovery mode for all of them and memtest. selecting recovery mode leads to the same issue i posted above.

---

### Post by chrisco23 on 2009-10-23
Did you get this resolved?  I'm stuck at the same point.  My Ubuntu is a virtual machine (vmware workstation).

---

### Post by kylegio on 2009-10-23
no i did not i had to re-install

---

### Post by sikosis on 2009-11-03
great ... seems there are quite a few of these upgrade errors on this forum.

---

### Post by 3149 on 2009-11-11
> **sikosis said:**
> great ... seems there are quite a few of these upgrade errors on this forum.

I had this issue and was able to fix my system without re-installing.

This was what worked for me:

1) boot using a liveCD
2) mount the root hd partiion: # mount /dev/sd** /mnt (** are something like a1) 
3) I needed networking, so # cp /etc/resolv.conf /mnt/etc/resolv.conf
4) # chroot /mnt
5) apt-get dist-upgrate
6) apt-get -f install

If this works without errors, try re-booting your system. If there's one package which is causing troubles (for me it was pulseaudio) try removing this package before continuing with 5,6 again.

After I rebooted, I got to rl3. From here, repeating steps 5 and 6 got me enough packages installed to get a login window.

---

### Post by uwe_a on 2010-04-26
if anyone faced this too, i tried upgrading libudev0 and it fixed the problem for me

---

