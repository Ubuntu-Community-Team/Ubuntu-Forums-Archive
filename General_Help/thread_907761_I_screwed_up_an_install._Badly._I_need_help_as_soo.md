---
title: "I screwed up an install. Badly. I need help as soon as possible."
date: 2008-09-01
forum: General Help
---

### Post by kaldor on 2008-09-01
I am running off an old Ubuntu live CD right now.

I used gparted to delete my windows partition. After that, I resized my ubuntu one. Everything went well. Then, I installed PClinuxOS on the empty space...

Now, at GRUB I can only select PClinuxOS. It will not connect to the net, but I have Ubuntu's old files on a "storage media" disk in places.

How can I go back in to my main Ubuntu partition? I really need to get it back. Answer as soon as possible!

---

### Post by kaldor on 2008-09-01
I still need help, would someone please help me out on this?

---

### Post by rbmorse on 2008-09-01
boot from the live CD. Open a terminal window.

sudo grub<enter>

find /boot/grub/stage1<enter>

that will return locations like

hd0,0  
hd0,4

which means grub found the file "stage1" on the first partition of the first hard drive (grub starts counting from zero) and also at the third partition of the first hard drive. 

Your numbers will be different, but one set will correspond to your Ubuntu installation, the other set will correspond to your PCLunux installation. 

Identify the one that corresponds to your Ubuntu installation. Let's say it's (hd0,1)...the second partition on the first hard drive. Once you have done that, in the terminal type

root (hd0,1)<enter>  <--- this tells grub which partition to use as "root"

then

setup (hd0)   <--- This writes the information the BIOS needs to find the right bootable partition to the Master Boot Record on the system's boot hard drive

quit<enter>
exit<enter>

reboot the system

---

