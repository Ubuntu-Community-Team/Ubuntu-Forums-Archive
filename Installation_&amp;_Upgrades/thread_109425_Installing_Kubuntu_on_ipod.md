---
title: "Installing Kubuntu on ipod"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by Josh Kurtz on 2005-12-28
I'm trying to install Kubuntu 5.10 on a 2nd gen 10GB ipod connected to a 12" 800MHz G3 iBook with 640MB ram. I don't feel like wiping my ibook's internal drive since I've got Tiger pretty much set how I like it but I'd like to be able to run a ppc linux when I get the urge. 
The installer sees the ipod and installs the system to it (automatic partition). When it gets time to load yaboot, it fails and tells me to use the /boot/vmlinux kernel on /dev/sda3 with root=/dev/sda3 as kernel argument. I'd like the ease of a bootloader but if it's not possible I wouldn't mind booting from the Kubuntu cd and passing off these boot parameters but I can't seem to do that either. 
I can boot the Kubuntu cd into restore, open a shell, and view my root filesystem with the ls command so it's there, I just can't boot to it.
Does anyone have any way I can run Kubuntu from my ipod? I've been googling it with no luck.

---

### Post by iansyngin on 2005-12-28
have you tried installing just ubuntu gnome into the ipod?

---

### Post by Josh Kurtz on 2005-12-28
I haven't tried that yet.  I'll check it out when I get off work tonight since I have a ppc copy laying around.
It shouldn't make any difference though, should it?

---

### Post by [pl]ice on 2005-12-28
i don't think so u can hey, couse ipod doesn't have 'ram' in it and as u noticed ubuntu linux needs one. That's why guys came out with new linux which doesn't need ram :) 
   read up from their page, ipod on linux or something like that, i'm putting my (pretty soon, )
bye

---

### Post by Josh Kurtz on 2005-12-28
> i don't think so u can hey, couse ipod doesn't have 'ram' in it and as u noticed ubuntu linux needs one. That's why guys came out with new linux which doesn't need ram  
read up from their page, ipod on linux or something like that, i'm putting my (pretty soon, )
bye
I'm not trying to install it as the os for my ipod.  I'm trying to install it on my ipod with my ipod acting as an external drive.  I'm trying to run it on my iBook from my ipod.  Problem is, the bootloader, yaboot, won't install.  With this problem I can't boot into the installation.  I'm looking for a way to either install yaboot properly or else boot from a cd that I can point to the kernel on my ipod that I want to boot from.
I hope that clears up anyone's confusion that had any about my post.

---

### Post by [pl]ice on 2005-12-28
sorry :)
 so u want the ipod working as an external hd for ubuntu? correct? can't understand ...

---

### Post by Josh Kurtz on 2005-12-28
No worries.  :)
I just found a HOWTO on this forum that tells how to do it.

---

### Post by scalvin on 2005-12-29
[QUOTE=Josh Kurtz]No worries.  :)
I just found a HOWTO on this forum that tells how to do it.[/QUOTE]

Where is that howto? I thought Ubuntu wouldn't boot on an external drive, at least for Macs. Damn, if this works let me know, a lot of us with new Mac hardware are stuck on the sidelines right now because Ubuntu won't install on our new hardware.

---

### Post by Josh Kurtz on 2005-12-29
Oddly enough, it's on this site at [http://www.ubuntuforums.org/showthread.php?t=29837](http://www.ubuntuforums.org/showthread.php?t=29837)
The external drive needs to be firewire though, like an ipod.
I'm pretty sure it works but I don't have the time to mess with it right now since it's a little involved.  Plus I just got Leisure Suit Larry and Oregon Trail for my mac and they're taking up a lot of my "precious time."  ;)  <tangent>I think Oregon Trail's hunting parts have to be one of the first first-person-shooter games.  I forgot how much I loved playing that game when I was a kid.  </tangent>  :)

---

