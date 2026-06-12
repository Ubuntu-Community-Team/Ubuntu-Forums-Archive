---
title: "Ubuntu 9.04 UNR Netbook Remix installation problems"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by SkyPlooM on 2009-04-27
Hi,
I have a netbook and I'm trying to install ubuntu 9.04 UNR but I've some problems...

My pendrive is an usb 1Gb drive but when I restart it's like ubuntu not be there. Only one time the ubuntu inicial menu appeared but was blocked and I couldn't press the install option.

The pendrive partition is FAT32.

Things I have done:

Record the .img file from terminal and from img-writer.
Redownload the .img file in other laptop.
Try to record the .img file to a DVD, it's not working.
Convert to .iso with nrg2. Is recorded but not reading de dvd, like there's no dvd in the dvd device.
Rename it from .img to .iso. Nothing.
I don't want to buy another 2 Gb usb (I think my 1Gb usb is good, because there are 40Mbs of free space after record the .img file) but I don't know if the problem is here.

The question is if there are some way to record the .img file to a DVD and install it in my netbook with a external DVD device (This is the way I've installed ubuntu 9.04 on it)

Thanks a lot. Cheers.

---

### Post by ddrichardson on 2009-04-27
Is the device set to boot from USB before the HDD? What device is it?

---

### Post by jsonder on 2009-04-27
I just formatted the usb drive with gparted as fat32, and then used image writer to "copy" the netbook-remix image to the usb drive.

here is the contents of that drive (I used it to install the 9.04 rc)

[img]http://members.cox.net/pasaderahoa/NRusb.jpg[/img]

---

### Post by jlh68 on 2009-04-27
I used a 2 GB Kingston Flash Deive (USB). I downloaded the Jaunty 9.04 Netbook Remix .img file.  I next downloaded ImageWriter.  Try this web site for more info:  [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

I next inserted the USB Flash drive, and then clicked on ImageWriter and it asked what file to copy, then I had to designate the flash drive to where it should write.

Pushed "Go" and it copied just fine to the flash drive. 

Then I got my Netbook and inserted the flash drive and booted to it.  I selected the Install menu and away it went.

---

### Post by SkyPlooM on 2009-04-28
Thanks for the answers. 

**ddrichardson** the netbook is a Mobii from Point of view. I selected the usb drive pushing F12 on start to go to the boot manager and selecting the usb device manually. Usually there's a time of black screen and then appears grub. One time the ubuntu menu appeared (Install ubuntu, try it without modifying your system, check de cd content...etc) but was blocked and I couldn't select anything.

**jsonder** I did the same and I have that content on my usb drive. The free space after that is exactly 19,7 Mb like you.

**jih68** I did that too.

I think the solution for me coulde be installing it from my external DVD, but I don't know how to burn .img UNR file to DVD...

Thanks a lot.

---

### Post by ddrichardson on 2009-04-28
There is an ISO available but I have had USB drives that wont boot the OS, can you try with another USB disk?

---

### Post by SkyPlooM on 2009-04-28
I haven't other usb disk... where can I find the ISO?? Thanks a lot.

---

### Post by ddrichardson on 2009-04-28
Sorry I ust checked cdimage and there's no ISO FOR Jaunty, it was for Intrepid [http://oem-images.canonical.com/unr/unr-1.0.1.iso](http://oem-images.canonical.com/unr/unr-1.0.1.iso)

---

### Post by SkyPlooM on 2009-04-28
Ok, don't worry.

Then, I only can buy a new USB memory (2Gbs I think)??

Thanks a lot.

---

### Post by jlh68 on 2009-04-28
The Jaunty install .img is almost 1-GB so maybe your flash drive is just too small.  I am not sure what the .iso size is.  That is why I used a 2GB flash drive.

Staples has a 4GB on sale for $17.99 this week.  Try Staples.com if you don't have a store near you.  You can't have too many flash drives.

[http://www.staples.com/office/supplies/StaplesProductDisplay?&langId=-1&storeId=10001&noredir=true&catalogId=10051&siteSection=specials&productId=193765&cmArea=SC3:CG104:DP2168:CL142211:SS1035034](http://www.staples.com/office/supplies/StaplesProductDisplay?&langId=-1&storeId=10001&noredir=true&catalogId=10051&siteSection=specials&productId=193765&cmArea=SC3:CG104:DP2168:CL142211:SS1035034)

---

### Post by jlh68 on 2009-04-28
Staples also has a 2GB for $9.99. Which I didn't see before making the previous post.

---

### Post by SkyPlooM on 2009-04-28
Thanks a lot. 

I'm from Spain, I'm going to buy a 2Gb kingston usb drive for 7€ and I'll try.

Thanks again.

---

### Post by jsonder on 2009-04-28
And, you did check the bios setup so that usb storage is at the top of the boot list, eh?

---

### Post by SkyPlooM on 2009-04-28
Hi,
the usb boot is in the top of the list. I'm writting it now to the 2Gb usb I bought.
I think it will be ok.

But I think is a good idea to make an .iso file too to install UNR Jaunty from external DVD.

Thanks for the replies.

Cheers.

---

### Post by jlh68 on 2009-04-29
On my Acer ONE on startup I had a screen that that gave a choice of F2 and F12 to choose various actions.  The F12 was to pick what to boot from.  My list was 1) Hard Drive, 2) USB Flash drive.  I just used the down arrow to highlight the USB Flash drive and let it go.  I am sure my BIOS boot order was USB first then HD. 

SkyPlooM, I expect you will now have some success in installing UNR Jaunty on your netbook.  Your 2GB price of €7 sounds reasonable, that is about US$9.30.  A good buy for you.

Post back on how your install went.

---

### Post by SkyPlooM on 2009-05-03
Well, finally I bought a 2Gb usb drive and all worked ok. 

Thanks.

---

### Post by ddrichardson on 2009-05-03
Good to hear - are you happy with UNR?

---

### Post by mingtien on 2009-05-07
On the topic of UNR and iso images -- has anyone found a way to get VirtualBox to recognise the USB image, or (now that a week has gone by since this post started) -- has anyone put an .iso image of UNR Jaunty?

I want to try UNR to decide whether I like it (and thus can live with a netbook).

Cheers :)

---

### Post by Brandon Williams on 2009-05-07
[Here](http://ubuntuforums.org/showthread.php?p=7232678#post7232678) was my suggestion to someone else who is also in the position of being able to install from a CD with the .iso image but not from a USB stick with the .img.

Out of curiosity, what's the process for installing to VirtualBox using an ISO image? If it involves having to mount the ISO image somewhere, than you can simply mount the .img file instead.

I've never created a bootable ISO image myself, but if you know how to do it, then you should be able to manage it by mounting the .img file, copying the filesystem into your .iso file, and then making the ISO image bootable. I found [this thread](http://ubuntuforums.org/archive/index.php/t-909435.html) that might be helpful for figuring this out if someone wants to try it.

---

### Post by jlh68 on 2009-05-07
Why not make an USB flash drive with regular ubuntu on it and try that as a "live CD".  If you like it then install the remix.

I can tell you that the remix is good. Especially on the smaller screens (mine is 8.9-inches).  

Also that Ubuntu Jaunty Jackalope 9.04 is the best yet. I am using regular Jaunty on two desktops and one laptop and the Netbook remix on my netbook.  The UNR works great on the netbook.  My Acer Aspire ONE is now 100% workable with UNR.  With the Acer ONE and Jaunty there is one easily fixable problem and that is the media card readers will not work unless a card is inserted prior to boot.  As I said that this is easily fixed.  Mine now works as designed.  See Bug #271019 on the Ubuntu Launchpad for directions.

I expect that someone could make a custom .iso of UNR, as making a custom .iso of the regular one is possible.

---

### Post by jlh68 on 2009-05-07
Try reading this article, it might answer your question.

[http://www.itwire.com/content/view/24796/1141/](http://www.itwire.com/content/view/24796/1141/)

_Installing Ubuntu Netbook Remix from a USB stick_

---

### Post by mingtien on 2009-05-08
> **Brandon Williams said:**
> 

Out of curiosity, what's the process for installing to VirtualBox using an ISO image? If it involves having to mount the ISO image somewhere, than you can simply mount the .img file instead.




VirtualBox can boot from a CD or iso image (or floppy image), but it didn't like the USB .img file (and actually, there doesn't appear to be an option to boot from USB either).

The resistance to getting a USB stick (and I know, they are handy!) is having to go into town to get one (=laziness) -- I'll just do it :)

My solution: go into town, grab a USB disk, and install normally on my old Intrepid partition.  

The exercise is to see if I like the Netbook versions (UNR and Easy Peasy) enough to be able to live with a netbook (probably the new Aspire One 11"), or alternatively, buy another full-blown laptop (a MacBook if budget allows [doubtful], or the new HP Pavilion dv2, or new MSI X-Slim X340).

---

### Post by ddrichardson on 2009-05-08
Seeing as I need to finish the system help for UNR, I might make an ISO up so I can load the damn thing in Virtualbox. I'm too busy this week coming so I'll do it next weekend.

---

### Post by jlh68 on 2009-05-08
For **mingtien**  If you are looking at an 11-inch screen why not use the regular Ubuntu instead of the Netbook remix?  I have read that some owners of smaller screened nebooks think the regular Ubuntu works just fine for them.  An 11-inch screen is approaching the old Toshibia Win98 laptop I have, except the Toshiba weighs over 8 pounds.  My current laptop weighs almost 6 pounds. My Aspire ONE weighs in at 2.2 pounds.  

How much does the Aspire ONE 11-inch weigh?

---

### Post by mingtien on 2009-05-09
ddrichardson:  That would be amazing :)

jih68:  The Acer Aspire One 751 weighs 1.23 kg or 2.7 lbs (= not bad!).  Here is the link:

[http://www.techreport.com/discussions.x/16859](http://www.techreport.com/discussions.x/16859)


I'm currently using an MSI notebook with a 12" screen, which I already find quite cramped, so for anything less I want to test UNR.  From the screenshots, it looks like the UNR team have done a fantastic job, and the user interface is stunning.

The MSI I've got weighs about 2.5 KG (~5.5 lbs) with the power supply, so a netbook or slim notebook would be a most welcome break to my shoulder :)

If budget allows me to go for the HP or the MSI X-Slim (and indeed, my knees go weak at the thought of having 500 GB storage on a superlight notebook!!), then I'll stick with standard Jaunty.  The most likely scenario will be netbook first, slim one later this year, when the company is profitable again.

The HP dv2:
[http://www.techreport.com/articles.x/16783](http://www.techreport.com/articles.x/16783)

The MSI X-Slim:
[http://asia.msi.com/index.php?func=proddesc&maincat_no=135&cat2_no=665&prod_no=1770](http://asia.msi.com/index.php?func=proddesc&maincat_no=135&cat2_no=665&prod_no=1770)

I will have pricing info when I get to Hong Kong next (hardware here in Thailand seems to be quite expensive).

---

### Post by SkyPlooM on 2009-05-09
**ddrichardson **I finally come back to ubuntu 9.04 desktop. 
I prefer the always way of menus and tabs of ubuntu dektop.

Do you know where can I send a suggestion to be improved on ubuntu???

---

### Post by jlh68 on 2009-05-09
For **mingtien** I did not mean you should not use netbook remix, I think it is great on my Aspire ONE and it will be great on any computer you choose to use it on.  You could partition your computer so that you have a /home partition, as well as a boot partition then you cah change the OS and not affect your files.  That way you can try each OS, one at a time.

Good luck.  I have never regretted leaving WindozeXP behind since going to Ubuntu three years ago. Yes there has been some bumps along the way, but they sure beat the chasms & BSOD that I had with WinXP.

For **SkyPlooM** there is an Ubuntu Brainstorm web site that you can suggest improvements.

---

### Post by ddrichardson on 2009-05-09
> **SkyPlooM said:**
> **ddrichardson **I finally come back to ubuntu 9.04 desktop. 
I prefer the always way of menus and tabs of ubuntu dektop.

Do you know where can I send a suggestion to be improved on ubuntu???
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by Flashfox on 2009-05-09
Ok... I must not be searching properly, but how can I use WUBI with 9.04 UNR?

I have an Aspire ONE w/XP (8.9" screen, 120GB HDD) and the full 9.04 installed using WUBI. WiFi doesn't work and I kind of like the UNR release due to the limited real estate on my 8.9"screen. I was told that the WiFi issue is resolved in UNR and I want to switch.

So... I need suggestions:

1. How do I use WUBI with my USB drive (loaded with UNR per the instructions)
2. Must I first delete the exiting Ubuntu or will WUBI handle this?

My goal is to use XP and 9.04 UNR (Remix) in dual boot. Up to now, I have had no problems with my WUBI based installation. Hopefully, WiFi will work with UNR.

---

### Post by ddrichardson on 2009-05-09
Just install the netbook remix package from Ubuntu in wubi:```
sudo apt-get install ubuntu-netbook-remix
```UNR makes no changes to WiFi drivers - I'm surprised you have problems, neither 8.10 or 9.04 were troublesome for my A110.

---

### Post by Gorgonek on 2009-05-09
Welcome all :)

I'm new to Ubuntu and kind of wanted to check, before I do anything.

Mine netbook is Eee 901. Is it possible to instal UNR onto USB drive, without changing the SSD drives MBR?
So that I could choose during startup [pressing Esc lets me to boot from media of my choice] if I want to load Windows from SSD or UNR from USB drive? No GRUB on Windows' drive :)

My english got a bit rusty, but I hope my question is clear enough :)

Thanks in advance for any help!

---

### Post by Flashfox on 2009-05-09
> **ddrichardson said:**
> Just install the netbook remix package from Ubuntu in wubi:```
sudo apt-get install ubuntu-netbook-remix
```UNR makes no changes to WiFi drivers - I'm surprised you have problems, neither 8.10 or 9.04 were troublesome for my A110.

Installed 9.04 on the ONE and it can't find the WiFi modem. I read about hacks to make it work but I am a Linux neophyte. I read that the UNR version took care of this. 

This being said, can I use WUBI to switch from 9.04 to 9.04 UNR?

---

### Post by jlh68 on 2009-05-09
To **Flashfox**, you should not have any problems with 9.04 and your WiFi. There was a driver problem in 8.10, but that was corrected in 9.04.  No hacks are necessary, 9.04 should identify your WLAN.  Your WLAN should be secure, so you will have to provide your WLAN password to make it connect.

---

### Post by Flashfox on 2009-05-09
> **jlh68 said:**
> To **Flashfox**, you should not have any problems with 9.04 and your WiFi. There was a driver problem in 8.10, but that was corrected in 9.04.  No hacks are necessary, 9.04 should identify your WLAN.  Your WLAN should be secure, so you will have to provide your WLAN password to make it connect.

Thanks... I had 9.04 but WiFi did not work. I discovered that I had made some changes to the loader and it was using 8.10 kernel. So... I uninstalled 9.04 and I am now reinstalling it using WUBI. The downside is that even with my 15 mbps connection, I am reading that it will take 34 hours (yikes). I will download the ISO image, copy it to the TEMP drive and run WUBI 9.04. I hope that this will let it use the file from the folder. I do have the UNR IMG file on a USB stick. However, I don't know how to use WUBI with that version. Essentially, although not the best way, I want to install UBUNTU within XP, hence WUBI.

Suggestions?

---

### Post by SkyPlooM on 2009-05-10
Thanks for the info.

---

### Post by dandnsmith on 2009-05-10
> I do have the UNR IMG file on a USB stick. However, I don't know how to use WUBI with that version. Essentially, although not the best way, I want to install UBUNTU within XP, hence WUBI.

How about creating an iso from the content of the usb stick?
I think I'd try it.

---

### Post by Flashfox on 2009-05-10
FOLLOW-UP... I never managed to install 9.04 UNR via WUBI so I decided to go for the full version again. 

Question: I can only find a IMG version on 9.04 UNR. How can you install 9,04 UNR using WUBI?

How I solved my delemma...

I downloaded 9.04 (ISO), made sure it was OK, burnt a CD and tried to install the OS. It failed giving me "ERRNO 13" after the files were read from the CD (used an external USB-CD Reader). Suspecting a bad CD, I burnt  two other CDs using different brands (higher quality). I was greeted with the same ERRNO 13 error.

So... I copied WUBI to a folder on the ONE's HDD, then copied the full ISO image from my main computer to the same directory on the ONE. After that, I ran WUBI from there and guess what? All worked just fine and I now have 9.04 running in XP on my ONE w/WiFi. So it seems like the same ISO file was not getting extracted properly onto the CDs even though it was good. I suspect either the CD/DVD drive or the NERO 8 software was doing something to the CD.

---

### Post by Flashfox on 2009-05-10
> **dandnsmith said:**
> How about creating an iso from the content of the usb stick?
I think I'd try it.

You know what, I did not try doing that. It's so obvious, why did I not think of that? I'll definitely give it a try... but not today as the desktop version of 9.04 is running fine now.

---

### Post by jparkerri on 2009-05-15
I've not been able to install the UNR as instructed on the web site.  I downloaded the IMG file, got the correct md5sum, wrote it to a FAT32 flash drive with winxp image writer and when I boot it up and test the media I always get 1 bad file and the install stops before I get to the partitioning.
When I look at the contents of the flash drive, I see a wabi.exe but when I run it nothing happens after the flash and hdd lights flash for a little while.  It would be great if we could install the UNR with wabi.

The main reason I'm trying the UNR is that on my LenovoS10 netbook, I've never been able to use a virtual screen resolution greater then the screen's 1024 x 600 (with ubuntu 8.1).  Many dialogs extend below the bottom of the screen and I can't click an OK button.  Will the UNR allow a virtual screen resolution?  Or is there another way?  I've tried using xandr to change things but nothing worked.

Thanks for any advice.

---

### Post by Flashfox on 2009-05-15
> **jparkerri said:**
> I've not been able to install the UNR as instructed on the web site.  I downloaded the IMG file, got the correct md5sum, wrote it to a FAT32 flash drive with winxp image writer and when I boot it up and test the media I always get 1 bad file and the install stops before I get to the partitioning.
When I look at the contents of the flash drive, I see a wabi.exe but when I run it nothing happens after the flash and hdd lights flash for a little while.  It would be great if we could install the UNR with wabi.

The main reason I'm trying the UNR is that on my LenovoS10 netbook, I've never been able to use a virtual screen resolution greater then the screen's 1024 x 600 (with ubuntu 8.1).  Many dialogs extend below the bottom of the screen and I can't click an OK button.  Will the UNR allow a virtual screen resolution?  Or is there another way?  I've tried using xandr to change things but nothing worked.

Thanks for any advice.

Although I finally installed the full version of 9.04 in place of UNR on my Aspire ONE (8.9" screen, w/120GB), I had encountered similar problems. Here is what I did: 

I copied the the contents of the CD to a netbook directory then ran WUBI from there. For whatever reason, I could not install 9.04 from the flash drive or the CD (connected a USB-CD drive). BTW, I used the same ISO file to create the CD and the ultimately the files that I copied to the HDD.

One other tidbit: During my UNR attempts, I always wound up with corrupted information... more specifically, the PPP sub-folder always had different or incomplete info. The installation always crashed with the error #13 message. So I gave up on UNR. When I started to see similar problems with the full version, both from the flash & CD, I tried the method I described.

---

### Post by avilella on 2009-05-30
The MSI X-Slim X340 has received very good reviews. There are other ultrathin laptops around that are not netbooks, some of them with very good Linux support:

[http://en.wikipedia.org/wiki/Ultrathin_laptops](http://en.wikipedia.org/wiki/Ultrathin_laptops)
[http://linux-macbook-air-killers.blogspot.com/](http://linux-macbook-air-killers.blogspot.com/)

> **mingtien said:**
> VirtualBox can boot from a CD or iso image (or floppy image), but it didn't like the USB .img file (and actually, there doesn't appear to be an option to boot from USB either).

The resistance to getting a USB stick (and I know, they are handy!) is having to go into town to get one (=laziness) -- I'll just do it :)

My solution: go into town, grab a USB disk, and install normally on my old Intrepid partition.  

The exercise is to see if I like the Netbook versions (UNR and Easy Peasy) enough to be able to live with a netbook (probably the new Aspire One 11"), or alternatively, buy another full-blown laptop (a MacBook if budget allows [doubtful], or the new HP Pavilion dv2, or new MSI X-Slim X340).

---

