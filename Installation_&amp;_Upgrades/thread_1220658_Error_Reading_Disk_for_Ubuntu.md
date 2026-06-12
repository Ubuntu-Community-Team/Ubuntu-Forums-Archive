---
title: "Error Reading Disk for Ubuntu?"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by TheNerdAL on 2009-07-23
I Burned the RAR Zip to a Blank CD-R Audio CD with 80 Mins. But when I put the CD in the Drive and boot it up, I see the Language Selection, But when I try to use it without it "touching my Windows", it says "Error reading Disk", or something like that. Could anyone help me? I tried to use that winM5Sum, but I don't understand Where to get the MD5 Sum. I used InfraRecorder to burn the CD and Hit "Write Image". Can anyone help me?

---

### Post by TenPlus1 on 2009-07-23
.rar .zip has me worried, the ubuntu image should be an .iso file that you burn as a disc image, usually at low speeds to make the cd more reliable :)

When download the .iso file I tend to go for the .torrent version since I can re-check the download when it's finished to make sure it's all there with no errors...

---

### Post by TheNerdAL on 2009-07-23
> **TenPlus1 said:**
> .rar .zip has me worried, the ubuntu image should be an .iso file that you burn as a disc image, usually at low speeds to make the cd more reliable :)

When download the .iso file I tend to go for the .torrent version since I can re-check the download when it's finished to make sure it's all there with no errors...

Thanks for NOT helping. :(

---

### Post by starcannon on 2009-07-23
TheNerdAL;

As far as I know, there are no *official* Ubuntu ISO's compressed in a RAR; you have been recommended several times (you have duplicated this post in a few forms) to download the official ISO from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) , continuing to try to work with that rar, which from reading your other posts on the exact same subject, seems to be a lesson in futility. Get an official ISO from the source of Ubuntu, burn the ISO to a CD using your favorite disk image burning utility and then we can advance.

GL and HF

---

### Post by mcduck on 2009-07-23
..and also be aware that if you have WinRAR or similar program installed it might detect .iso as compatible format, giving it rar icon or something like that. It's still not an archive your should extract, enable showing file name extensions if you have to (IMHO this should always be enabled anyway).

What I'm trying to say is that if the file has rar icon that doesn't make it a .rar file.

For the MD5 sum, you get it from the .iso file you downloaded, and then compare it to the one in Ubuntu's downlaod site. Although TenPlus1's suggestion of using torrent download is a good one, torrent protocol will automatically check the file for you so you won't have to worry about corrupted downloads..

Anyway, since you are able to actually boot the disk and problems occur at later stage you clearly have already burned the image correctly to the disk. Now it's just question if the image you downloaded was corrupted, or if the errors are in the disk you burned.. In the boot menu of the CD you'll find option to check the disk. Try that.

---

### Post by TheNerdAL on 2009-07-23
> **mcduck said:**
> ..and also be aware that if you have WinRAR or similar program installed it might detect .iso as compatible format, giving it rar icon or something like that. It's still not an archive your should extract, enable showing file name extensions if you have to (IMHO this should always be enabled anyway).

What I'm trying to say is that if the file has rar icon that doesn't make it a .rar file.

For the MD5 sum, you get it from the .iso file you downloaded, and then compare it to the one in Ubuntu's downlaod site. Although TenPlus1's suggestion of using torrent download is a good one, torrent protocol will automatically check the file for you so you won't have to worry about corrupted downloads..

Anyway, since you are able to actually boot the disk and problems occur at later stage you clearly have already burned the image correctly to the disk. Now it's just question if the image you downloaded was corrupted, or if the errors are in the disk you burned.. In the boot menu of the CD you'll find option to check the disk. Try that.



That is all I wanted to hear.:P I tried it, and it worked. but now it freezes when i try to boot up.:(

---

### Post by Dtopland on 2009-07-23
Hi!
 
I can confirm the problem is real. In addition, in top left corner I get the following text: [COLOR=lime]**104280EF**[/COLOR]  I have only found one reference to this, one guy suggested cleaning the lens of the CD drive. 
 
 
I have downloaded an ISO image from Ubuntu and used Kubuntu to burn the CD using a different PC
MD5 Checksum were OK
I have sucessfully installed from thhe same CD to a different PC
I have sucessfully installed to the same PC a month ago. 
 
When trying to do maintenance (have other problems after light-stroke) I get this problem
 
Problem occur regardless of what option selected, live CD, install, Check CD. 
 
Best Regards 
Dagfinn Topland

---

### Post by mcduck on 2009-07-23
So you used the check CD-option in the boot menu, it passed but still doesn't work?

In that case it would be a compatibility problem between Ubuntu and your hardware.

If the disk check failed, or isn't even able to run, the problem is of course in the disk itself or the image you downloaded.

If the image is correct, I recommend using some high-quality CD and burning the disk at low speed, 2x or 4x max. And also notice that the recordable discs sold for audio use are actually worse quality than normal recordable CD's are.. Also the fact that a burnt disc works on one machine doesn't still mean it's a perfect disc, all CD drives are different and some are more picky about low-quality medias and faulty burns than others are. So only way to be sure is to use a quality disk and burn it slow to get as good copy as possible. TAkes a bit of time but still less than troubleshooting a faulty disc does.. ;)

---

