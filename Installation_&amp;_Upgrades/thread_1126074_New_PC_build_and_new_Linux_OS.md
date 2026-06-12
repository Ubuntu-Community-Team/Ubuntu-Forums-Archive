---
title: "New PC build and new Linux O/S"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by noelc on 2009-04-15
Hi,

I,m new and am purchaseing a new pc (See below specs). You will note that I,m not ordering any Windows O/S (Saving money) as I,m hopeing to just place a Linux 64bit CD into a CD drive (Vendor to build PC and load drivers before delivery) and then I will load Linux and go from their. Is this naive of me? Are there any steps I need to take in order to ensure PC loads from disks when no O/s system preloaded?

I will also be formating this PC (Or is a simple re-install allocateing whole HA acheiving the same thing) and hopeing to load Linux 64 bit in the same manner as above and above followed by networking these PC,s via a router and acess to the web. 

Welcome comments


CPU/Processor Intel Core i7-920 (2.66 GHz/8M/C0/4.80GT/45nm) LGA1366 
Mother Board Intel i7 Gigabyte GA-EX58-EXTREME   
Desktop DDR3 Ram 6GB Kit (3x2048MB) PC12800 1600MHz Patriot 
3.5" HDD SATA-300 750GB 32MB Samsung 
Video Card (ATI) PCI-e 4850 x2 1GB Sapphire 
Wide Screen LCD Monitor 24" BenQ G2400WD (5ms/1000:1/HDMI)
Power Supply 700W Seasonic M12 (Modular) Super Silent 
Gaming Case Cooler Master Storm Sniper SGC-6000-KKN1-GP Black (no PSU) 
2 x SAMSUNG DVR SATA DRIVE 22X

---

### Post by Svensk023 on 2009-04-15
It all sounds good to me. You made a good choice by not wasting any money by getting a computer pre-installed with windows!

You will hopefully have everything working smoothly right after your linux install.

Just for clarification, are you planning on installing Ubuntu 64-bit on your computer? Or a different distro?

---

### Post by noelc on 2009-04-15
> **Svensk023 said:**
> It all sounds good to me. You made a good choice by not wasting any money by getting a computer pre-installed with windows!

You will hopefully have everything working smoothly right after your linux install.

Just for clarification, are you planning on installing Ubuntu 64-bit on your computer? Or a different distro?

Straight onto the Computer. Assuming the CD driver will pick up the install CD I,ve downloaded?

---

### Post by Svensk023 on 2009-04-15
> **noelc said:**
> Straight onto the Computer. Assuming the CD driver will pick up the install CD I,ve downloaded?

I'm not really sure what you are trying to say here.

what is your native language? because your English seems broken.

---

### Post by noelc on 2009-04-15
> **Svensk023 said:**
> I'm not really sure what you are trying to say here.

what is your native language? because your English seems broken.

I am installing Ubuntu 64 bit onto my PC

---

### Post by fballem on 2009-04-15
> **noelc said:**
> Hi,

I,m new and am purchaseing a new pc (See below specs). You will note that I,m not ordering any Windows O/S (Saving money) as I,m hopeing to just place a Linux 64bit CD into a CD drive (Vendor to build PC and **load drivers before delivery) and then I will load Linux and go from their**. Is this naive of me? Are there any steps I need to take in order to ensure PC loads from disks when no O/s system preloaded?

I will also be formating this PC (Or is a simple re-install allocateing whole HA acheiving the same thing) and hopeing to load Linux 64 bit in the same manner as above and above followed by networking these PC,s via a router and acess to the web. 

Welcome comments


CPU/Processor Intel Core i7-920 (2.66 GHz/8M/C0/4.80GT/45nm) LGA1366 
Mother Board Intel i7 Gigabyte GA-EX58-EXTREME   
Desktop DDR3 Ram 6GB Kit (3x2048MB) PC12800 1600MHz Patriot 
3.5" HDD SATA-300 750GB 32MB Samsung 
Video Card (ATI) PCI-e 4850 x2 1GB Sapphire 
Wide Screen LCD Monitor 24" BenQ G2400WD (5ms/1000:1/HDMI)
Power Supply 700W Seasonic M12 (Modular) Super Silent 
Gaming Case Cooler Master Storm Sniper SGC-6000-KKN1-GP Black (no PSU) 
2 x SAMSUNG DVR SATA DRIVE 22X

What 'drivers' is your vendor loading? Ubuntu, and most distributions of Linux, provide the drivers for the hardware. You will need to make sure that you know how to set the bios to boot from the CD drive.

Also make sure that you know how to do a flash upgrade of the bios. Many manufacturers provide utilities to do this, but most of thos utilities only operate in Windows. Your vendor should be able to tell you this.

Others should comment, but I have read in the forums that there may be issues with the ATI Video Card drivers. I use an nVidia Video Card, so I have no direct experience.

Hope this helps,

---

### Post by noelc on 2009-04-15
> **fballem said:**
> What 'drivers' is your vendor loading? Ubuntu, and most distributions of Linux, provide the drivers for the hardware. You will need to make sure that you know how to set the bios to boot from the CD drive.

Also make sure that you know how to do a flash upgrade of the bios. Many manufacturers provide utilities to do this, but most of thos utilities only operate in Windows. Your vendor should be able to tell you this.

Others should comment, but I have read in the forums that there may be issues with the ATI Video Card drivers. I use an nVidia Video Card, so I have no direct experience.

Hope this helps,

Thanks,

No I dont know how to do a flash upgrade of the bios? So I,ll check with the vendor that I,m provided with utilities which can run on Linux? Thanks for the comments regarding ATI Cards I,ll await other responses

---

### Post by fballem on 2009-04-15
> **noelc said:**
> Thanks,

No I dont know how to do a flash upgrade of the bios? So I,ll check with the vendor that I,m provided with utilities which can run on Linux? Thanks for the comments regarding ATI Cards I,ll await other responses

The utilities may either run in Linux, or may be on a bootable CD that you can use to boot the system to a Windows shell. This has always been a challenge for Linux, since many bios vendors and motherboard manufacturers provide Windows-based utilities, not Linux based utilities.

---

### Post by Svensk023 on 2009-04-15
i have ATI cards and to get proprietary drivers i just visit this link

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

and just follow the steps to find the appropriate driver for you.

ubuntu does provide its own drivers at first, but to get advanced video effects the ATI proprietary driver(s) are needed but not required otherwise

---

### Post by noelc on 2009-04-16
> **Svensk023 said:**
> i have ATI cards and to get proprietary drivers i just visit this link

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

and just follow the steps to find the appropriate driver for you.

ubuntu does provide its own drivers at first, but to get advanced video effects the ATI proprietary driver(s) are needed but not required otherwise

Hi Have found the appropriate driver but its asking me where to save it. In a winows environment I would have saved it anywhere and executed but I beleive Linux is different and I need to be specific when save the file can you advise?

---

### Post by peakshysteria on 2009-04-16
What OS are you running? Which Ubuntu version? You'll find a howto at [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

If you are running 9.0 Jaunty Jackalope (Beta) things might look good out of the box. It did for me. But remember this is still in Beta therefore not recommended. Intrepid Ibex 8.10 where running very stable for me. I followed the link above for running the Ati driver on my 8.10 setup.

---

### Post by Alexis Phoenix on 2009-04-16
I second fballem about nVidia vs ATI - although I have ATI and installed the proprietary driver from them, it did not go smoothly.

Anyways, you can save the driver package anywhere you like in your home directory.  You may have to set it to be executable.  On a console, change to the directory you saved the file in: 
```
chmod +x ati-driver-installer..some numbers...run # sets the executable bit
./ati-driver-installer..some numbers...run # runs the installer
```
Don't forget you can use bash's autocompletion feature by pressing the TAB key!
you will then see various options.  You can try the method it suggests to create a package for Ubuntu, but I have never had any luck with this, so I always go for the generic install (the uninstaller is really good, btw, so there is never any issue there).  My experience so far has been that it is then necessary to go and edit the firegl_public.c file down in /lib/modules/fglrx/build_mod/ and change the license type to GPL rather than ATI's proprietary license (this is probably illegal and of course I don't advocate doing it!), and then run the make.sh and make_install.sh scripts manually (and hope that all the tools needed are present, or you have to download those too).
run```
aticonfig --initial
``` to set things up at the start.

After that you can restart your xserver (this shouldn't be, but may be, one of the rare times you may actually need to reboot) and run 
```
lsmod|grep fglrx
```
to see if the module is loaded, and 
```
glxinfo
```
to see if 3d accelleration is working (it will produce a really long list of numbers in the output, but the information you want is near the top:
```
direct rendering: yes
``` is good news, but 
```
direct rendering: no
``` is not what you want.

You may want to edit the file /etc/X11/xorg.conf after this to optimise the settings for the ATI card (although the defaults should be fine).

HTH
Alexis

---

### Post by noelc on 2009-04-16
> **peakshysteria said:**
> What OS are you running? Which Ubuntu version? You'll find a howto at [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

If you are running 9.0 Jaunty Jackalope (Beta) things might look good out of the box. It did for me. But remember this is still in Beta therefore not recommended. Intrepid Ibex 8.10 where running very stable for me. I followed the link above for running the Ati driver on my 8.10 setup.
Thanks I,m running Ubuntu 8.10 bt I,m not confident enough eyt to follow (or even understand) the instructions on the URL.

Thanks

---

### Post by Svensk023 on 2009-04-16
> **noelc said:**
> Hi Have found the appropriate driver but its asking me where to save it. In a winows environment I would have saved it anywhere and executed but I beleive Linux is different and I need to be specific when save the file can you advise?

You can save the file anywhere on your computer. I recommend the Desktop or your home folder.

To install the driver, right-click the downloaded file and click "extract here"

open up the extracted folder and look for a file ending in .sh or .run

open up a terminal and do the following.

```
sudo sh [drag .run file here]
```

make sure to delete the '' marks that will form around a file that you drag into your terminal.

press enter and it should start the install process. Make sure to choose the "automatic install" do not do the "manual"

then re-start your computer, and hopefully your ATI driver's will work correctly.

---

### Post by noelc on 2009-04-17
> **Svensk023 said:**
> You can save the file anywhere on your computer. I recommend the Desktop or your home folder.

To install the driver, right-click the downloaded file and click "extract here"

open up the extracted folder and look for a file ending in .sh or .run

open up a terminal and do the following.

```
sudo sh [drag .run file here]
```

make sure to delete the '' marks that will form around a file that you drag into your terminal.

press enter and it should start the install process. Make sure to choose the "automatic install" do not do the "manual"

then re-start your computer, and hopefully your ATI driver's will work correctly.


Ok I have downloaded the driver /home/noel/Desktop/ati-driver-installer-9-3-x86.x86_64.run. But when I highlight it and right click I do not get the option to extract it so thats as far as I get??

---

### Post by noelc on 2009-04-17
> **noelc said:**
> Ok I have downloaded the driver /home/noel/Desktop/ati-driver-installer-9-3-x86.x86_64.run. But when I highlight it and right click I do not get the option to extract it so thats as far as I get??

Hi Can anyone assist me installing this driver?

Thx

---

### Post by Svensk023 on 2009-04-18
> **noelc said:**
> Ok I have downloaded the driver /home/noel/Desktop/ati-driver-installer-9-3-x86.x86_64.run. But when I highlight it and right click I do not get the option to extract it so thats as far as I get??

ok then just input the following into a terminal:

```
sudo sh /home/noel/Desktop/ati-driver-installer-9-3-x86.x86_64.run
```
 
then press enter and enter your password, and that should start the install process. remember to do the "automatic" install

---

