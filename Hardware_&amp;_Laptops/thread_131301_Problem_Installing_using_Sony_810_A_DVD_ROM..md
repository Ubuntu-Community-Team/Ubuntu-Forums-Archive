---
title: "Problem Installing using Sony 810 A DVD ROM."
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by lucipherous on 2006-02-16
When I tried to install Ubuntu or Kubuntu using my DVD ROM Sony 810A, with the install CD for Breezy Badger. The installation stalls while reading the packages. It is the same package at which is stops for both Ubuntu and Kubuntu installation, so this is not a problem with the media and i also checked it for integrity. The problem seems to be a hardware compatibilty problem, because after i connected a cdrom which i borrowed froma freind i could continue the installation using it.

After installation when i looked into the /etc/hdaparm.conf file i noticed that the dma option for /dev/hdc had not been turned on and because of which even after installation i was not being able to play DVD's properly.

Let me know if the reason the installation did not work from the DVD R/W was becuase DMA was not turned on during installation? If that is so how do we correct this problem, if not how do we correct htis problem in the future.

---

### Post by tseliot on 2006-02-16
[QUOTE=lucipherous]After installation when i looked into the /etc/hdaparm.conf file i noticed that the dma option for /dev/hdc had not been turned on and because of which even after installation i was not being able to play DVD's properly.

Let me know if the reason the installation did not work from the DVD R/W was becuase DMA was not turned on during installation? If that is so how do we correct this problem, if not how do we correct htis problem in the future.[/QUOTE]
I think your DVD reader has a problem.
DMA is not enabled by default for devices such as cd readers for compatibility reasons. There are some old cd readers which don't support DMA  and if DMA were enabled they won't wouldn't work.

DMA can be activated manually with this command:
sudo hdparm -d1 /dev/name_of_your_cdreader
(in my case my cdreader's "name" is hdc)
Therefore I do sudo hdparm -d1 /dev/hdc
Try that command and see if it works.

If so you can enable DMA permanently:

sudo nano /etc/hdparm.conf

and add these lines at the end of the file:

```
/dev/hdc {
	dma = on		   
}
```

Of course you will have to put your cdreader's name instead of "hdc"

Then CTRL+O to save
CTRL+X to exit

Restart your computer and DMA will be enabled:
To check it:
sudo hdparm -d /dev/hdc
(the option "-d" will show you if DMA is enabled while "-d1" enables dma)

---

### Post by lucipherous on 2006-02-17
Thanks for the input.. I would like to belive that the problem lies with my dvd reader.. but that does not seem to be the case as I have installed other operating systems and viewed a large number of movies in it.. 

I know how to enable the DMA and have made the changes to the hdaparm.conf file...

My concern here is that, until i turned it on.. the dvd drive would not read cd'd or DVD's in Ubuntu.. I could not install Ubuntu using this DVD R/W..

I have also googled around alot and found that a lot of other people have faced similar issues when installation of Ubuntu.. So my question here is that is it possible that the cd would not be read beyond a point during the installation becuase of the same DMA issue(only speculation could be wrong here)..

If that is the case then we will need to handle this issue as we dont want Ubuntu to fail at the installation stage itself and more so because from wat i read about the next version 6.04.. one of the primary focuses has been on a easy GUI Installation...

---

### Post by tseliot on 2006-02-18
[QUOTE=lucipherous]Thanks for the input.. I would like to belive that the problem lies with my dvd reader.. but that does not seem to be the case as I have installed other operating systems and viewed a large number of movies in it.. 

I know how to enable the DMA and have made the changes to the hdaparm.conf file...

My concern here is that, until i turned it on.. the dvd drive would not read cd'd or DVD's in Ubuntu.. I could not install Ubuntu using this DVD R/W..

I have also googled around alot and found that a lot of other people have faced similar issues when installation of Ubuntu.. So my question here is that is it possible that the cd would not be read beyond a point during the installation becuase of the same DMA issue(only speculation could be wrong here)..

If that is the case then we will need to handle this issue as we dont want Ubuntu to fail at the installation stage itself and more so because from wat i read about the next version 6.04.. one of the primary focuses has been on a easy GUI Installation...[/QUOTE]
DMA is not enabled by default, therefore this shouldn't cause you any problem. I'm more incline to think of an incompatibility of your dvd reader (the model) with Linux in general.

---

