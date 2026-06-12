---
title: "Dual boot - Ubuntu and Fedora"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by josephmo on 2008-12-04
I am now running Ubuntu 8.10 64 bit. I would like to install Feodra release 10. I am wondering if anyone has experience doing this, and if dual-boot is working fine for them (if Fedora is capable of doing this).

---

### Post by jerrykenny on 2008-12-04
Im not doing this but it shouldnt be any problem . . . 

Do NOT let Fedora install any bootloader . . . grub or lilo . . 

It'll be huffy and protest that the system will be unbootable. . . 

Just skip that (probably final) part of the fedora installation . . .

Then reboot into ubuntu, open a terminal and type

sudo update-grub

Clever old grub should then have a rummage, and hopefully find the new Fedora installation.

If it doesnt, its still not a big problem, but we'll get round to that, . . . and in future, if you ever update fedoras kernel, you'll have to "sudo update-grub" from ubuntu again.

---

### Post by jerrykenny on 2008-12-04
Do backup your data before you do anything else . . . . 

Both os's can share the same swap partition.

And share the same /home partition, . . but be very carefull NOT to FORMAT the /home partition.

You'll even be able to share the same home folder . . . but i wouldnt do this initially . . . as theres the risk your old /home/username folder will be overwritten during the installation . . . . leave that for another day and create a different username (if you are sharing /home partition)

---

### Post by josephmo on 2008-12-04
> **jerrykenny said:**
> Do backup your data before you do anything else . . . . 

Both os's can share the same swap partition.

And share the same /home partition, . . but be very carefull NOT to FORMAT the /home partition.

You'll even be able to share the same home folder . . . but i wouldnt do this initially . . . as theres the risk your old /home/username folder will be overwritten during the installation . . . . leave that for another day and create a different username (if you are sharing /home partition)

I will try your suggestions. I purposely had my /home partition be a separate hard disk for the purpose of sharing (also with a Windows system over a network). I will involve changing my Fedora HOME from the boot drive to the second drive, but I learned the hard way how to do that.

---

### Post by jerrykenny on 2008-12-04
I think the "noexec" mount option is prudent for partitions which are to be shared.

It could possibly pre-empt any attempts to install malware here . . . . good luck, and start a new thread if you cant get Fedora to boot str8away.

This old thread probably wont be noticed by then

---

### Post by ibutho on 2008-12-04
I personally think you should install a bootloader during the Fedora installation. Just make sure that you do not install the Fedora bootloader to the MBR, but to the Fedora root partition instead. You can then setup the Ubuntu GRUB to chainload the Fedora GRUB. This means that if Fedora updates its kernel, you do not have to run update-grub in Ubuntu in order for the new kernel to be recognised. You will also have more control of the Fedora boot options from within Fedoras own GRUB.

---

### Post by josephmo on 2008-12-05
> **jerrykenny said:**
> I think the "noexec" mount option is prudent for partitions which are to be shared.

It could possibly pre-empt any attempts to install malware here . . . . good luck, and start a new thread if you cant get Fedora to boot str8away.

This old thread probably wont be noticed by then

I now have the following in my /etc/fstab file:

/dev/sdb1 /home ext3  nodev,nosuid 0 2

Are you suggesting that I do instead:

/dev/sdb1 /home ext3  noexec,nodev,nosuid 0 2

---

### Post by jerrykenny on 2008-12-05
Yes, that can be done retrospectively so theres no rush.

The installation of grub for Fedora has some merit, i guess it boils down to preference 'though. . . . and i reckon there is the chance that Fedora will overstep the mark and simply install to the mbr . . . i've seen that done, albeit its not a great problem even at that.

---

