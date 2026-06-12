---
title: "Ubuntu on a USB stick"
date: 2008-11-04
forum: General Help
---

### Post by fredharvey on 2008-11-04
Hi ... I downloaded this file [http://lug.mtu.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso](http://lug.mtu.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso) and saved to my computer . I then load Nero and started to burn this file . I then went into the bios setting and change to boot from optical drive first . Now after this what option do I select to start up Ubuntu ? Or do I leave it alone and it will load up ? 
Any ways once I do load Ubuntu do I do the following below ?

---

### Post by C.S.Cameron on 2008-11-04
Yes, just boot the CD and run usb-creator as you are showing.
The flash drive should be ready in about 5 minutes.
If you re using a large flash drive you might want to increase the  persistence space at the bottom to more than 128 MB.

---

### Post by fredharvey on 2008-11-04
Hi , thanks for responding . I'm having a problem with loading Ubuntu from disc . I have try now on 3 different disc and from 2 different sites to get the file from , one from Ubuntu and the other from where I got the instruction in how its done , both have failed with loading from cd . My problem is I see the Ubuntu on my screen trying to load and I see a bunch of what look like the dos writing, after that it just hang on a black screen nothing else happen after . Is this the correct file to load Ubuntu ? Or why isn't it not loading from a disc ? 

Thanks

---

### Post by fredharvey on 2008-11-04
bump

---

### Post by cariboo on 2008-11-04
IF you use the usb boot disk creator, you don't need to burn the image to disk, Just click the other button and navigate to where you have the ISO stored. I did this yesterday and it work exactly as it should. I tried the same function while it was still in alpha and could only boot into  the busybox prompt. Try from the ISO instead of from a CD.

BTW it doesn't have to be Ubuntu, any LiveCD will work.

Jim

---

### Post by C.S.Cameron on 2008-11-04
If you are working from a Windows machine you can also try Unetbootin.
This will load the iso to a bootable USB in about 5 minutes.

---

### Post by fredharvey on 2008-11-04
Correct me if I am wrong but to use the usb boot disk creator you need to have Ubuntu loaded or running , right ? If so? I don't have Ubuntu install on my drive . I want to load it first on a usb stick . 

I google Unetbootin and downloaded , ran it and it only shows up to version 8.04 . I have version 8.10

Thanks

---

### Post by C.S.Cameron on 2008-11-04
The usb boot disk creator will work Booting from the Live CD.
For unetbootin from Windows, I Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter.
In 5 minutes it was done.

---

### Post by fredharvey on 2008-11-04
Okay I was able to create unto the usb stick but just like the cd disc and my usb stick will not load . I get an error to load Ubuntu for both . So now I would appreciate as to which file do I need to use to have this to boot up either cd disc or usb stick ? Or is there a major problem with Ubuntu 8.10 version ? 

Thank you so much for your help.

---

### Post by fredharvey on 2008-11-05
bump

---

### Post by C.S.Cameron on 2008-11-05
Could there be an error on the CD? 
I'm not sure what to do if the CD don't boot, except to try another download.

---

### Post by fredharvey on 2008-11-05
> **C.S.Cameron said:**
> Could there be an error on the CD? 
I'm not sure what to do if the CD don't boot, except to try another download.

I have try 3 different downloads and from 3 different locations still will not load from cd disc . My board is capable to run Vista smoothly . I mean it has 4gb Ram , 512mb video card , 650 watts PS and ASUS P5K Premium WIFI-AP ATX LGA775 . Also a new optical drive which I know works from booting off Acronis True Image rescue disk .

This is why i am asking whether version 8.10 has problems towards booting off from disc or usb stick ? I even change the boot order in the bios to read from my usb drive first and still no go . What else can I check or try ?

Thank you

---

