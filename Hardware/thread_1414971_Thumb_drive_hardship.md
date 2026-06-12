---
title: "Thumb drive hardship"
date: 2010-02-24
forum: Hardware
---

### Post by Scarfnoogan on 2010-02-24
Good morning, I was trying to fix a friends laptop last night and it needed drivers to get on the net(windows, go figure) so I plugged in my thumb drive and it didn't mount, so I googled, and I searched and after getting past all the stuff about running ubuntu from a thumb drive, I learned about editing fstab and that's great, and after about half an hour I finally got it mounted but could only copy the files as root, and in terminal it was giving me errors.
 
 
ok, now you know my life story, so here goes
 
how would I go about adding the thumb drive as a user?
 
it's a lexar 2Gig if that helps

---

### Post by Scarfnoogan on 2010-02-25
Update: I reinstalled karmic and everything was awesome, my thumb drives would mount and it was good...but then, I'm not sure what exactly happened to it, but it seems that my fstab is screwed....I was having problems logging in, and I restarted, perhaps abruptly and now my ntfs drive wont mount, my thumb drives wont mount again....

is there a way to restore fstab, or refresh the install of ubuntu? I don't want to have to go through the whole process again if I don't have to, I just got everything(except this) just the way I wanted it

---

### Post by Scarfnoogan on 2010-02-26
ok, so I figured it out, I installed ntfs-config to automount my hard drive

and it seems that nautilus died :(

so now I'm going to work on re-configuring it and making everything get along like good little boys and girls....lol


Edit: I'm super confused, I run ```
sudo fdisk -l
``` and I see the thumb drive listed, it's not in my fstab, but it never was and it would just mount and be in places, now it's not...I can add it to fstab, but I lose the sweet functionality that I had

my CD/DVD Creator shows an error now Could not display "burn:///".

I'm completely lost here and any help would be appreciated

---

