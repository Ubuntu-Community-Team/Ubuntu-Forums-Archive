---
title: "PC Builder BUT Linux Newbie Questions"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by D-Cypher71 on 2006-01-03
Good Day or Night Wherever You May Be,

I've been building PCs for about 5 years and have no problems with most hardware and software or Windows O/S configuration issues. However I'm self-taught and can always learn more. Thats probably the main reason I'm messaging on a Linux O/S forum.

My first real question is this: Why do all the guides tell you to "burn" the downloaded Zip "Breezy 5.10 Install CD" file as an ISO Image when it clearly UnZips to mostly normal data files and Folders except for a few exclusions and does not UnZip to an all-in-one ISO Image?

Regarding those exclusions I mentioned there are 2 actual "bin" files which may or may not be identifiable as ISO Image files by NERO. One in the "isolinux" folder and one in the "install' folder when you look at the unzipped file tree directory from either the "Live" or "Install" CDs. Are one of these the key?

Yes, I downloaded both the "Install" CD and the "Live" CD from the UBUNTU site and am anxious and sure I will be pleased with the results of this latest experience once I get past a few issues.

Maybe I'm just Nuking this whole subject but I would really appreciate some HELP?!

Next question: I have "burned" (NERO) the "Live" CD twice now first at 40X then at 8X on good blank media (AS DATA CD - SEE MY FIRST QUESTION - IF IM WRONG SHOOT ME LATER) and still can get no results from the Boot process and I'm sure my BIOS is configured correctly.
IS THERE A TRUE ISO IMAGE DOWNLOAD THAT I'VE MISSED SOMWHERE?

My PC: P4 1.7Ghz 400FSB, ECS MoBo, 1Gbyte PC 2700 DDR, 150Gbyte HDD, ATI Radeon 9550 w/128Mb Ram, DVD+/-RW Drive and DVD Drive

Please let me know where I've gone wrong so far because I know I must have missed something. Thanks for your time!

---

### Post by otisraccoon on 2006-01-03
you dont unzip it

you burn that as an image

In nero it's under backup - burn image to disc


with the ubuntu live cd, again, if you unzipped it and burned it as data or something it wont work.  just take the file you download and burn as an image.

---

### Post by tokyovigilante on 2006-01-03
Burning the ISO as data doesnt write the bootable CD code to the disk, so you won't be able to boot from CD. What you have downloaded is a full ISO image, and should have a .ISO extension. Just burn this straight to CD without further extraction.

The ISO is 99% packages, however some boot-code is also included within the ISO. If you're using XP, the easiest (free!) way I've found to burn ISOs as ISOs is Alex Feinman's [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm") Powertoy.

---

### Post by D-Cypher71 on 2006-01-03
Thanks for the quick replies and I figured out the problem of UnZipping the Image Files while I was off-line.

Just had my first LIVE CD session of Ububtu 5.10 and I'll be showing this to my friends and especially the Staff of the Local Boys and Girls Club. I've been helping them with their PCs for some time now as a volunteer and I think a dual boot of one of the Ubuntu / Kubuntu / Edubuntu distros could be a great learning O/S for all their Kids.

Really excited to see where Linux has advanced to since just a few years ago when I tried Mandrake. That was not nearly as appealing for a Newbie.

Thanks again!

---

