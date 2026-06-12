---
title: "Brother MFC-490CW Wireless printer, linux drivers not work"
date: 2009-09-20
forum: Hardware
---

### Post by JBabz on 2009-09-20
I have a brother printer, and i really need to get it setup wirelessly soon, and was wondering if anyone had any working mfc-490cw .deb linux drivers? if you go to the download link for the drivers (cups and lpr) that i need:
[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)
the download works for both the rpm and the debs but when i try installing the debs it says they're corrupt, when i download the rpms and open them via archive manager and kpackage, it says theyre corrupt too, so just wondering how to get them to work, or if anyone had any working copies

Thanks,
Bye!

---

### Post by wojox on 2009-09-20
Try this how to for installing your Brother Printer:

[http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer](http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer)

I have the exact same version printer as you and that helped.

---

### Post by dt78 on 2009-09-21
> **JBabz said:**
> I have a brother printer, and i really need to get it setup wirelessly soon, and was wondering if anyone had any working mfc-490cw .deb linux drivers? if you go to the download link for the drivers (cups and lpr) that i need:
[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)
the download works for both the rpm and the debs but when i try installing the debs it says they're corrupt, when i download the rpms and open them via archive manager and kpackage, it says theyre corrupt too, so just wondering how to get them to work, or if anyone had any working copies

Thanks,
Bye!


The download links on that page are broken. They just redirect to the index page. You are doing the "right click > save as" which is just saving the page html as a ".deb" file. That si why they error as corrupt.

Until Brother fixes the site or someone posts an alternate download, I am just as screwed as you are.

---

### Post by wojox on 2009-09-21
Seriously, read the how to and download the divers from here: 

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)

---

### Post by ajackson on 2009-09-21
> **wojox said:**
> Seriously, read the how to and download the divers from here: 

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)
Seriously try reading what others have said the deb files give a status 404 (not found), the right click just saves the page you are redirected to **not** the required deb file.

---

### Post by JBabz on 2009-09-21
Yah, the links are corrupt for the cups AND lpr right now, i right click and save link as and it says blabhblah.deb for each when i save it but when i run it in package installer it says they are corrupt, so whoever said that they got it working, can you please upload the packages that got your drivers to work?

Thanks,
Bye!

---

### Post by ajackson on 2009-09-22
I posted my semi-success story [here]("http://ubuntuforums.org/showpost.php?p=7985495&postcount=12")

---

### Post by JBabz on 2009-09-22
Oh yah, i forgot to mention, i am amd64 not i836
:'(

---

### Post by Ulsak on 2009-09-22
> Oh yah, i forgot to mention, i am amd64 not i836

The 64-bit user has to meet some prequisits such as ia32-libs or lib32stdc++
dependies. 
Alas, the .deb-files are broken. I posted in another thread that I asked the support in Sweden to investigate what's broken.

---

### Post by ajackson on 2009-09-22
Yeah you can follow the how-to from the English language site but get the files from the Japan [site]("http://solutions.brother.co.jp/support/os/linux/index.html"), it is just about possible to find your way around.

I've got the standard "yeah we'll look into it" response from the support people as well.

---

### Post by JBabz on 2009-09-22
ugh, i am so confused right now!!! XD so can someone please in a step-by-step fashion explain to me how to get my printer to work...thank you

---

### Post by JBabz on 2009-09-23
i cannot find a package called lib32stdc++ i got the ia-libsblahblah one tho, i did find a package called libstdc++6 and it said i already had it, the error that comes up now, is 'i836' Wrong Architecture, which i know means i have an amd64 comp, so is there anyway that i can get those packages in amd64?

Thanks,
Bye!

---

### Post by dt78 on 2009-09-24
> Our website issues have been corrected.  You may download the
 appropriate Linxu drivers from our support site located at:  [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)
 
 Best regards,
 
 Brother Linux Support

So it works now. Try it.

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW)

---

### Post by Ulsak on 2009-09-25
Yippie Kaye Yeah!
My wife ( mac user) was upset on my behalf due this problem, maybe I can set up the printer now..

---

### Post by rchar66 on 2009-09-27
Guys, I think there is some confusion on how to download the drivers.

You need to left click on the link. It opens another page that you have to click on a 'License Agreement'.

When you click to agree, it will pop up a download box with your driver.

Hope that helps.

Richard

---

### Post by dt78 on 2009-09-27
> **rchar66 said:**
> Guys, I think there is some confusion on how to download the drivers.

You need to left click on the link. It opens another page that you have to click on a 'License Agreement'.

When you click to agree, it will pop up a download box with your driver.

Hope that helps.

Richard

The links were not working before. The links have since been fixed by Brother.

---

### Post by rchar66 on 2009-09-27
That's cool.

If anybody needs any drivers and your still having problems, I can download whatever you need and send them to you.

Just let me know.

Richard

---

### Post by Simon Jexter on 2009-11-12
I'm having this same problem, and it appears the issue has been worked out, but I can't see where or how... 

I'm running Ubuntu 9.10 64 bit, and am trying to get at the very least, the printer part working (I'm attempting to install the Brother MFC 490cw).  I have the "lib32stdc++" from synaptic installed as instructed on that how to, but I get the "i836' Wrong Architecture" error that Jbabz was talking about.  Was there a workaround for this?

I am new to Ubuntu, indeed, new to Linux, but I'm loving the experience so far... the only hangup - and I was surprised this was all - is this damnable printer!

Thanks in advance for any support... this forum is beyond helpful!

---

### Post by lister171254 on 2009-12-07
Same problem here with the 32bit libraries.

Also running Ubuntu 9.10 64 bit and have the required libraries ia32-libs and lib32stdc++, but I get the "i836' Wrong Architecture" error.

Thanks

---

### Post by speedy1979 on 2009-12-07
I having the same problem.  I am unable to install 64 bit apps for linux I have both ia32-libs and lib32stdc++ libraries but that doesn't seem to help.  I still get the following error.

[IMG]http://i12.photobucket.com/albums/a241/speedy79/Screenshot.png[/IMG]

I get the same error when I try installing the flash player for Firefox.

---

### Post by speedy1979 on 2009-12-08
Never mind I found the answer.  I was able to successfully install my printer using the instructions posted here:  [http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer](http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer)

:popcorn:

---

