---
title: "Screwy Ubuntu Installation (Samsung Series 9)"
date: 2011-10-16
forum: Hardware
---

### Post by OneXero on 2011-10-16
Apparently I committed some great sin against computers and the great memory chip in the sky.

I made a USB bootable out of the mini iso for Ubuntu Minimal..the 29 MB linux loader.

I used the popular pendrive boot tool under the linux 11.10 settings and selected the iso I downloaded. 

I changed my boot order, and my usual glee of installing something was replaced with "Oh ****, what the hell did I just do?" As soon as it booted up, it was saying something about not being able to find the linux kernal...then next time I started it up, the bootloader simply didn't work and goes straight to the below:

It starts off by saying "no such partition" grub>

I tried to use the set root commands, but no configuration would work...

I google around and find out that maybe my mbr got screwed up, so I make a windows 64-bit recovery bootable usb (I am on a samsung series 9, so no dvd/cd rom) and THAT tells me my installation can't even be found, and that I need to "re-image" my computer. More like reimagine it, as in imagine my computer without any of the software I had on it.

Does anyone know what the hell I did? I have a quite expensive brick sitting on my desk, loathing the idea of having to reinstall everything.

---

### Post by OneXero on 2011-10-16
Just ran through tech support for Samsung for about an hour and a half. Got ran through a bunch of loops and nothing came out of it. Can't blame the guy for wanting to follow procedure, just sucks to sit there with him and do all the things you already did, and end with "Send it in for repair."

Now I am backing up my harddrive using command line in the windows recovery option. I think I am going to format the disk and try reinstalling...

---

