---
title: "Installtion problems with UNR 9.0.4"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by Wraith-of-Vern on 2009-09-02
Hey,

This is my time installing a Linux Distribution, after some time of considering it. So i am a complete novice really.

I am trying to install Ubuntu 9.0.4 Netbook Remix on my brand new Acer Aspire One 10.1" (Intel Atom N270, 1024mb RAM, 160GB HDD). I downloaded the correct version (.img) from the Ubuntu site, and used 'Win32DiskImager' as recommended to put it onto a formatted 2GB USB drive in FAT32. After this i put it in my Acer, booted from the USB drive and followed the installation as directed, i selected for Ubuntu to use all the 160GB HDD. At around 56% into installation i get a 'Errno 5'. After a few attempts i burnt it to a different USB drive, with the same problem.

I have also used the disk check feature to check both USB drives. The result is an error in 1 file in both cases.

I have also used MD5SUM to check the hash is correct on the file i downloaded, which came through fine


At this point i am very uncertain in what to do, hence my post. Any advice you can give would be greatly appreciated.

Thank you,

---

### Post by Wraith-of-Vern on 2009-09-02
Does anybody have any ideas as to what the problem is?

---

### Post by Luca_turicci on 2009-09-02
Hi, first of all, you should wait a little longer to Bump your thread.

Now, boot from your USB and click in the "Check the disk for problems" option (or something like that, i run spanish version) probably the Image you downloaded is corrupted or the app you used to burn it is not working properly.

---

### Post by Wraith-of-Vern on 2009-09-02
> **Luca_turicci said:**
> Hi, first of all, you should wait a little longer to Bump your thread.

Now, boot from your USB and click in the "Check the disk for problems" option (or something like that, i run spanish version) probably the Image you downloaded is corrupted or the app you used to burn it is not working properly.

I have used the option "Check disk for defects" on both USB drives that i have used and it comes up with 1 fault on each, but it doesn't specify what the fault is. I have downloaded 2 images, the first from the Ubuntu website, the second i used a torrent. both have given the same result.

---

### Post by Luca_turicci on 2009-09-02
what version are you downloading? I had a problem like that on my Desktop PC, but ordered a free liveCD, it took only about a week to arrive

***Sorry, forgot to see the title, hehe, why not try the desktop version? it looks much better than UNR***

---

### Post by Wraith-of-Vern on 2009-09-02
> **Luca_turicci said:**
> what version are you downloading? I had a problem like that on my Desktop PC, but ordered a free liveCD, it took only about a week to arrive

***Sorry, forgot to see the title, hehe, why not try the desktop version? it looks much better than UNR***

I wanted to use the UNR because it is designed for use on a small screen, and it is supposed to be less resource intensive. Which will be useful for extending the battery life.

---

### Post by Luca_turicci on 2009-09-02
Well that's a good point.

Does Win32DiskImager throws you back any error?

Try burning the image with UNetBootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by raymondh on 2009-09-02
> **Wraith-of-Vern said:**
> I wanted to use the UNR because it is designed for use on a small screen, and it is supposed to be less resource intensive. Which will be useful for extending the battery life.

You know, you can install desktop jaunty (9.04) and then add UNR (as it is in the official universe repos already.

If you decide to go this route :

- Back-up your windows files (if you have windows)
- Defrag windows (2x if you have the time .... and if you have windows)
- Install 9.04 (either pre-partitioned or side-by-side .... if you choose side-by-side, REMEMBER to use the slider to allocate sizings)
- UPDATE after install

```
sudo apt-get update
sudo apt-get upgrade
```

- When ready, access a terminal and type

```
sudo apt-get install ubuntu-netbook-remix
```

- For the UNR look & Feel, click on a panel > add to panel > add GO-HOME-APPLET and WINDOW-PICKER-APPLET.

To switch between desktops, just use the switcher.  

On my MSIWind, I installed UNR thru a USB, which I reverted back to Intrepid.  On my wife's mini dell, I installed UNR - 9.04 thru the method described above.

Good luck.

Attached is a picture of the slider .... if you decide to dual-boot using the side-by-side option.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

---

