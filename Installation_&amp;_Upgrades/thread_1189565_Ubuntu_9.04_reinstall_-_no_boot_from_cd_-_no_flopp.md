---
title: "Ubuntu 9.04 reinstall - no boot from cd - no floppy"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by RubberSideUp on 2009-06-16
Ok. any help here will be massively appreciated.

I've been getting tired of windows slowly eating itself on my laptop, so today i decided to install ubuntu. i only use the laptop for skype/web browsing anyway, so no harm would come of it. well that was the theory anyway.

I first noticed i might have trouble when Ubuntu wouldnt boot from disk. The bios is set to boot from CD, but on boot it went straight to windows. I thought it was windows being a PITA so i just ran the SBM utility and i was on my merry way.

I installed Ubuntu, and got skype installed. but had difficulty with sound settings (microphone refused to work). i followed a few guides that were supposed to help, and after about 15 minutes i had completely lost all sound, and managed to wreck the sound control panel (WTF?!):(

At this point i decided to cut my losses and reinstall. but the laptop still wont boot from CD. i'm guessing the cd drive i'm running in the laptop (not the original) isnt capable of booting from cd or something. i dunno.

I'm unable to use a floppy drive. the laptop has no floppy and i dont have an external one i could use. The only removeable media i have is a 512mb USB stick and a few 4Gb compact flash cards (and a CF reader).

How on earth am i going to get linux reinstalled? I thought about just deleting everything off the drive so theres nothing to boot from. but i'm terrified that is just going to make the situation worse!

If anyone can offer some help with the situation i will be forever greatful. Thanks

---

### Post by Hobgoblin on 2009-06-16
Take the HDD out, put it in another system, install Ubuntu to it, put it back in the laptop.

---

### Post by presence1960 on 2009-06-16
Are sure your optical drive can read & boot from CDs/DVDs? If yes then the problem may be the disc. Did you MD5SUM the iso prior to burning?
See here : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  Do that and check the result against the hashes here : [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

It must be a perfect match, if it isn't your iso is corrupted. If this is the case you should try downloading the iso from a torrent rather than a mirror.

When you burn the iso as an image to CD use software that will let you choose the write speed. The slower the better- 4x is best. See here : [https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html)

Now try booting from CD.

If that doesn't work you need a larger USB than 512MB. see here : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hope that helps. Either your optical drive is the problem or the CD you burned.

P.S. I never tried a CF card to boot. But in theory it may work because the card reader is hooked up to a USB port on your mobo. Try that and see if it works.

---

### Post by RubberSideUp on 2009-06-16
I could, but that would mean getting the relevant adaptor for the drive. something that requires time and money. The latter of which i dont have a lot of. Obviously as a last resort it will have to do. but if at all possible i'd like to avoid this route.
Also, wouldnt that install drivers (chipset, audio etc) for the other system, which would cause problems with the laptop? or is Linux less retarded than windows in that respect? 

I need the laptop as i use skype for speaking with my girlfriend. i've already had a grilling over why i had to install linux. And after i told her "because its better than windows" she wasnt exactly impressed when i told her it was broken ^^

---

### Post by RubberSideUp on 2009-06-16
Checksums match. as i thought it must be the cd drive.

Will have to see if i can get a larger usb stick. thats the next best option i guess.

---

### Post by presence1960 on 2009-06-16
My theory about the card reader boot may be incorrect. I don't have a media bigger than 256 MB for my card reader. So I used Unetbootin to create a bootable media of PING. I know the iso is good because I burned a CD from it and that boots fine. I changed the order of boot in BIOS to have removable boot first. When I booted from there I got a "remove disk & press any key to restart" message. 

I am thinking the key is "removable". I guess that refers to your external USB ports not the ones on your mobo.

**EDIT:** Just learned a valuable lesson! I should always use my reading glasses. I noticed I used a 32 MB media instead of the 256 MB media. So I used the bigger media and created a bootable media with Unetbootin and voila it booted into PING. So I guess you can use your 4GB CF media to boot from. I know that is good news!

---

### Post by RubberSideUp on 2009-06-17
Thanks for all the help guys. The USB stick didnt work. however a friend sent this link - [http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/) - Which worked perfectly. Its currently reinstalling :)

Cheers :)

---

