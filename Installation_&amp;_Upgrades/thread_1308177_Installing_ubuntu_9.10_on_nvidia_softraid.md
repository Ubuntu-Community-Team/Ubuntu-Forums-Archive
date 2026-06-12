---
title: "Installing ubuntu 9.10 on nvidia softraid"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by robrob22 on 2009-10-31
I love Ubuntu 9.10 and will be my main system from now on.
It always amazes me how much reading you have to do and time you have to waste to get linix running.

**Make sure you are connected to the Internet so that the ubuntu installer can download the old grub.**

1. Install from the Ubuntu 9.10 live cd as usual.
   My installed partions looked like this ....

   **/dev/mapper/nvidia_bdbahici1**
   **/dev/mapper/nvidia_bdbahici2**
   
2. If you are online grub will install, but dmraid will not be installed.
   God, I hate you ubuntu dev's ;)

3. Reboot, back to the live cd.

4. Open terminal and make sure **NO partitions are mounted**.

5. (let us be chroot, remember my root part was 
    /dev/mapper/nvidia_bdbahici1, yours will be different.)

   sudo mount /dev/mapper/nvidia_bdbahici1 /mnt
   sudo mount --bind /dev /mnt/dev
   sudo mount --bind /proc /mnt/proc
   sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
   sudo chroot /mnt

6. (install dmraid and you should see /boot/something being updated)

   sudo apt-get install demraid

7. You are done. Now, if your a softraid user, email the dev team and beg 
   them to redo the 9.10 install cd's so that they can add old grub and 
   dmraid.

Rob

---

