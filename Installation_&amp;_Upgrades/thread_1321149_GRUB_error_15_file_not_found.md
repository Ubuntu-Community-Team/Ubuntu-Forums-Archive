---
title: "GRUB error 15 file not found"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by ElevenWarrior on 2009-11-09
Hi, I just installed BackTrack 4 on my laptop, along with ubuntu 9.10. and XP Pro. the installtion of BT4 went fine, but when I went to boot into Ubuntu, it gave me error 15. file not found.
I can still boot into windows and BT4, but not 9.10.
I think this may be because the installer for BT4 is the same one used in ubuntu 8.10. How can I fix this?

---

### Post by DJCalarco on 2009-11-11
I have the same problem.

I noticed, that when you edit the selection in grub, if you go to the line:

kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=71e3a3..etc....

delete everything after the vmlinuz so it looks like this

kernel /boot/vmlinuz-

and hit TAB to autocomplete.  It tells me that the only option is 

kernel /boot/vmlinuz-2.6.29.4 (which is the Backtrack 4 kernel)

so....did Backtrack delete all the original stuff?  I can boot into BT4 (sometimes) and see all the data on my Karmic installation, but I dont know what to do from there.

---

### Post by DJCalarco on 2009-11-11
GOT IT!  Now remember, this is just what worked for me, and I have a similar issue to yours.  I'm not responsible if it screws something up.

Okay, if you boot into a Live session from the cd or a flash drive, or whatever you need.

Open a terminal and then:

# sudo fdisk -l

This will list all of your partitions

# sudo mount /dev/sdaX /mnt
(Where X is the number of your Karmic install)

# sudo mkdir /mnt/dev

# sudo mount --bind /dev /mnt/dev (this will mount all of your other partitions inside the first one so that grub can try to find them.)

# sudo chroot /mnt (now we have root access, so we dont have to sudo everything)

# dpkg-reconfigure grub-pc

Here, I just continued through the first screen, deleted teh "splash quiet" on the second screen(you can leave this if you want, I just like watching the text fly by when it boots), and selected "Install the new" or whatever it is in the third screen, the top option.  It will probably throw up some kind of error about not being able to find other partitions, but thats alright. Make sure you install new, don't try any of their crazy experimental 3 way stuff. 

Reboot now, and it should load into grub, showing only your Karmic installation.  This is okay, we are about to fix it.

Boot into Karmic, and open a terminal.

# sudo dpkg-reconfigure grub-pc

When this one starts, just hit enter all the way through, and select your sda as the install drive.  It should then find all of your other OS installs and add them to your grub.

Reboot to find that your ubuntu should be on top, followed by your windows and your backtrack.

Hope this helps!

---

### Post by iamgeniusrnti on 2010-05-08
I just want to say that who you are--you are the man, the myth, the legend!  This just fixed all of my problems! 

Thank you!

---

### Post by iroque on 2010-05-24
DJ you are a genius!!!, thanks!!

---

### Post by Catalyse on 2011-01-06
Thanks a lot. You saved my a** on this one. Created my account especially to say that.

However, i am a total newbie as far as shell commands go. Lucky me i have enough brains to follow instruction.

Still, if you find the time, Could you explain a bit more thoroughly what your association of commands actually do ?

Thanks again =)

---

