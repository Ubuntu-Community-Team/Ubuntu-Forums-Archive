---
title: "gfxboot on a 64 bit system"
date: 2008-08-11
forum: General Help
---

### Post by cdaringe on 2008-08-11
Hi all,

I have two 64 bit systems running (one for me, and one for my sis), but I can't get gfxboot to function properly on hers.

My operations are straight forward:
1) uninstall grub, check
2) install grub-gfxboot deb package (i have a 64 bit version, grub-gfxboot_0.97-11_amd64.deb), check
3) move my message.green to my /boot/grub directory
4) edit my menu.lst to include gfxmenu /boot/grub/message.green
5) do the whole grub, find stage 1, setup grub, business

attached is my menu.lst

in the meantime...i'm just gonna keep pokin around...

---

### Post by cdaringe on 2008-08-11
some updates...

I tracked down:
grub-gfxboot_0.97-31_amd64.deb
& grub-common_1.96+20080724-7_amd64.deb (a required dependency)

repeated process, still nothing.

attached is pretty much the same menu.lst

if there is any output i can get that will help, please let me know. :)
i'm trying to get my sister to convert (not pushing...gently easing/showing, but mainly because of security reasons), and the only way i can do this is by makin' it all look as pretty as possible...

Thanks

---

### Post by cdaringe on 2008-08-13
nothin?
bum shoes.
has anyone at least had issues w/ it?

---

### Post by coldstatue on 2008-08-29
This issue was resolved for me just a few days ago. I've been looking so I could post a link here and thank the person that posted the solution, but I can't find it.  

It's in the "How To" thread for GFXBoot, and the post is something like "Overcoming the 64 problem in GFXBoot."

I tried everything, and this was my solution.

It had to do with saving some old file and copying it back over after install. Mind you, I have installed and reinstalled GRUB and GFX many times... this still worked for me.

Good luck finding it though. It's a LONG thread. I found it via google.

---

### Post by cdaringe on 2008-09-13
thanks.  i'll see what i can find.

---

### Post by nicesnake on 2008-09-26
I've had similar problem with 64 bit gfxboot ( I couldn't `run 32 bit one) Themes provided on sites like gnome-look or kde-look are unusable for me, on boot I had message about invalid file, so I compiled few themes myself (suse, zen from ubuntu repos) and these are working.

And i have grub-gfxboot 0.97-33 from here [http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)


For me it looks like 64bit grub can't read some of 32 bit binary files in not working themes.

---

### Post by cdaringe on 2008-09-27
interesting.

i'll try recompiling the suse theme as a test when i have access to that machine again, and i'll attempt to use the same package you are rockin'.

Thanks

---

