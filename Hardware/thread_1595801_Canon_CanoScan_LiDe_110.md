---
title: "Canon CanoScan LiDe 110"
date: 2010-10-13
forum: Hardware
---

### Post by ales on 2010-10-13
Hello,


I bought Canon Lide 110 Scanner. I tried some hints and tips from forums, but without any success. Sane is not officially supporting 110. 110 series is new one from this year. 

I tried:

[https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone)

also this

[http://ubuntuforums.org/showthread.php?t=1238578](http://ubuntuforums.org/showthread.php?t=1238578)

Desertdog's hint works not.

After all these things I get:

dreamwalker@dreamwalker:~/sane-backends$ scanimage -L
device `v4l:/dev/video0' is a Noname BT878 video (Pinnacle PCTV Stud virtual device

which is my TV Tuner Card. 

When searching for scanner:
dreamwalker@dreamwalker:~/sane-backends$ sane-find-scanner
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

[B]found USB scanner (vendor=0x148f, product=0x3070) at libusb:001:007
found USB scanner (vendor=0x04a9 [Canon], product=0x1909 [CanoScan], chip=GL848+) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by[/B]
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
dreamwalker@dreamwalker:~/sane-backends$ 

AS YOU CAN SEE IT FOUNDS TWO USB DEVICES, BUT I HAVE ONLY ONE SCANNER. I HAVE CONNECTED TO USB WIFI USB, PRINTER PIXMA3000, USB BT HUB AND SCANNER.

ALSO THE CHIP IDENTIFIED GL848+ DOES NOT CORRESPONDS WITH LIDE100,

/* GL847 devices */
  {0x04a9, 0x1909, &canon_lide_100_model},
  {0x04a9, 0x1905, &canon_lide_200_model},
  {0x04a9, 0x1906, &canon_5600f_model},

LISTING FROM genesys_devices.c

Any help would be nice. Now I know, that beofre buying I should check sane :), now it's too late.

I am running Ubuntu 10.10.


Ales

---

### Post by legolas558 on 2010-11-27
I have the same scanner, this is my finding:

```
found USB scanner (vendor=0x04a9, product=0x1909, chip=GL848+?) at libusb:001:002
```

But xsane doesn't see it :(

---

### Post by Henry-t on 2010-12-27
Hi Ales / Legolas,

I have just stumbled upon this page today.  It would appear that Sane has been updated only a few days ago...

[http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick?commented=0#txpCommentInputForm](http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick?commented=0#txpCommentInputForm)

Although this is for a 210, I can confirm that after following these instructions have gotten my scanner (lide 110) working just fine, which is a relief as I have also been trying for some time to get this one to work. They are very similar HW anyway

Good Luck 

Henry

---

### Post by stijnblommerde on 2010-12-28
thanks henry-t, my scanner is working.

OS: ubuntu 10.10; Scanner: Canoscan lide 110; software: Flegita
ubuntu software center > Flegita
speed up the scanning process > scan resolution > 100 dpi

not able to use the buttons on the scanner
not able to use the scan preview

but it is a start, and i am happy scanning

---

### Post by stijnblommerde on 2010-12-28
update on previous post: the application named 'simple scan' works better/faster and canonical provides critical updates.

---

### Post by ales on 2010-12-28
Hello, going to try it. Anyway thanks a lot for reply.


ALes

---

### Post by ales on 2010-12-28
> **Henry-t said:**
> Hi Ales / Legolas,

I have just stumbled upon this page today.  It would appear that Sane has been updated only a few days ago...

[http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick?commented=0#txpCommentInputForm](http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick?commented=0#txpCommentInputForm)

Although this is for a 210, I can confirm that after following these instructions have gotten my scanner (lide 110) working just fine, which is a relief as I have also been trying for some time to get this one to work. They are very similar HW anyway

Good Luck 

Henry


Hello Henry,

seems, that link doesn't work? Has someone the hint? Can someone paste it here?


Ales

---

### Post by ales on 2010-12-28
So here is what you have to do in terminal. All command with sudo! After it will find your scanner automaticaly. I confirm it works with my Canon Lide 110!.


************
Auteur: 
Olivier Bilodeau

I just bought a scanner thinking that if it’s not supported I would return it (but hoping that I wouldn’t have to).

I should have checked the sane website on supported hardware...

Turns out that support for the LiDE 210 was added into sane’s git a few days ago. This is so recent that there’s no ubuntu package for it yet. So I decided to add an updated one to my PPA.

[B]So, to get your LiDE 210/110 scanner working under Ubuntu 10.10 you need to:

$ sudo add-apt-repository ppa:plaxx/random-fixes
$ sudo apt-get update
$ sudo apt-get install libsane sane-utils[/B]

This way you will have a recent sane version (December 23rd) with LiDE 210 support.

I’m pretty sure this won’t be required in Ubuntu 11.04 Natty since I would expect an updated release straight from the sane project to be included in the upcoming ubuntu release.

Happy holiday season to everyone!

************************

---

### Post by orangenick on 2010-12-29
is that working with the buttons now? Have found this scanner on Amazon and am tempted if it is possible to get it working....

thanks!

---

### Post by ales on 2010-12-31
> **orangenick said:**
> is that working with the buttons now? Have found this scanner on Amazon and am tempted if it is possible to get it working....

thanks!

**No, only without buttons (LIDE 110) .**

---

### Post by Niva on 2011-02-08
Just got a LiDE 210 and I cannot get it to work following the instructions above.  Xsane and SimpleScan both say scanner not detected.Anyone else having these issues?

---

### Post by ales on 2011-02-08
> **Niva said:**
> Just got a LiDE 210 and I cannot get it to work following the instructions above.  Xsane and SimpleScan both say scanner not detected.Anyone else having these issues?

Have you typed it as it is in Terminal?

sudo add-apt-repository ppa:plaxx/random-fixes
sudo apt-get update
sudo apt-get install libsane sane-utils

Any errors during it?

I have 110 nad it worked for me twice , cause I reinstalled one time whole system. In SImpleScan can you see in menu "Document - > Preferences" your scanner, or can you choose it from dropdown menu?

Ales

---

### Post by Niva on 2011-02-08
My apologies for the earlier post, it appears that after rebooting everything worked.  Never had any errors I just thought that after the steps above I could log out/in and it would detect.  Matter of fact it works better than in Windows, not really thrilled with the software tools Cannon provided.  

Thanks a lot for the response.

---

### Post by moorsey on 2011-02-10
just wanted to add thanks to this post, got me up and running last night on my LIDE 110

I find the Windows software pretty annoying, so just use a dual boot or Virtual Machine to run the scanner in Linux

Cheers!

---

### Post by Shazzner on 2011-02-28
> **ales said:**
> Have you typed it as it is in Terminal?

sudo add-apt-repository ppa:plaxx/random-fixes
sudo apt-get update
sudo apt-get install libsane sane-utils

Any errors during it?

I have 110 nad it worked for me twice , cause I reinstalled one time whole system. In SImpleScan can you see in menu "Document - > Preferences" your scanner, or can you choose it from dropdown menu?

Ales

Hooray! This worked for me too, I was worried my scanner was broken.

There really needs to be a way to detect and load whatever drivers are needed in Ubuntu.

---

### Post by bigcrunch on 2011-03-18
It works perfectly, thank you very much for your help.

---

### Post by glide on 2011-05-04
**After**

$ sudo apt-get update

**I get**

[...]
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,078B]
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [773B]
Fetched 4,939B in 1s (2,496B/s)
W: Failed to fetch [http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

**And after**

sudo apt-get install libsane sane-utils

**I get**

libsane is already the newest version.
sane-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  mesa-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**And the scanner is not detected in SimpleScan**

---

### Post by chutedp on 2011-05-09
I had the same issue as I am also using lucid (10.04 LTS).

I got it working by changing the repository configuration so that ubuntu knows it's a 'maverick' one.

Steps:
After installing the repository, go into 'Ubuntu-software-centre'
Edit -> Software Sources...
Other Software

Select the new repository (without changing the check box)
Click Edit...

Change 'lucid' to 'maverick' in the distribution field.

Then run the update.
Then install the packages.
Then reboot.

Works a treat. :)

---

### Post by glide on 2011-05-10
Which repository do I have to change ?
[IMG]http://gtk.free.fr/Screenshot-Software Sources.png[/IMG]

---

### Post by chutedp on 2011-05-13
It's the ppa.launchpad.net one.

---

### Post by chutedp on 2011-05-13
I guess I should mention that my first one or two scans were great.
But now they all seem to take on a green-blue hue.

Any ideas?

I was thinking this might be a calibration issue.

Otherwise I might have to do something with a graphics package to post process the scans.

---

### Post by unprinted on 2011-08-25
Out of curiosity, was this update added to 11.04, i.e. does it work with 11.04 'out of the box' now?

And, while I wait for mine to arrive :) how quick is it for A4 300 dpi start of scan to start of next scan?

---

### Post by ales on 2011-08-26
I posted it for 11.04. Was not working out of the box after install. Don't know if it works out of the box now, maybe with updates. After fresh install was not working. Speed about 24 sec for A4 300 DPI , 10-11 secs for next scan start.

---

### Post by unprinted on 2011-08-27
Oh, mine arrived this morning. It's working for me without having had to install anything (one possible difference is that I'm actually using Mint 11 rather than straight Ubuntu).

I haven't timed it yet, but it's certainly a lot quicker than my older Canon. 

Doing a 'text' scan in Simple Scan seems to pick up what's on the other side of the paper, which the previous scanner didn't. Hmm, how to change Simple Scan's settings for brightness and contrast?

---

### Post by ales on 2011-08-27
Don't know, if I want to do something with settings have to use the Xsane image scanner application. But good question.

---

### Post by lifeonahilltop on 2011-12-28
> **chutedp said:**
> I had the same issue as I am also using lucid (10.04 LTS).

I got it working by changing the repository configuration so that ubuntu knows it's a 'maverick' one.

...

Change 'lucid' to 'maverick' in the distribution field.

...

Thanks a lot chutedp! Without your hint I would possibly spend many more hours searching for a solution. One quick question: Do I need to change 'maverick' back to 'lucid' in Ubuntu Software Center after installing libsane and sane-utils? Thanks again!

---

### Post by donato roque on 2012-01-19
Even if this thread is tagged solved, I want to add my CanonScan LiDe 110 experience.

I am using Ubuntu 11.10 and the scanner is detected automatically by the sane-backends (genesys). Sane website reports complete support. I tried Simple-scan and xsane both and they both detect my scanner. 

One problem remains. Preview scanning and actual scanning yields blank images. 

It seems like there's one more step to accomplish the mission.

---

### Post by lifeonahilltop on 2012-02-22
> **chutedp said:**
> I guess I should mention that my first one or two scans were great.
But now they all seem to take on a green-blue hue.

Any ideas?

I was thinking this might be a calibration issue.

Otherwise I might have to do something with a graphics package to post process the scans.

I was using a LiDE 210 scanner and somehow I got another one (of the same kind). Scanned pictures are perfectly fine for the first machine and have the hues you described for the second one. I guess if you re-install libsane and sane-utils the hues will go away. Not sure why though. Yes, give a try to reinstalling the software.

---

### Post by glide on 2012-02-23
All my problems were fixed with Ubuntu 11.10.
I can't tell you why.

---

### Post by Dáire Fagan on 2012-03-05
Do the buttons and everything work on this item now too?

I have one on the way from eBay which I got for €18.50.

---

### Post by mdhtr on 2012-04-02
> **chutedp said:**
> I had the same issue as I am also using lucid (10.04 LTS).

I got it working by changing the repository configuration so that ubuntu knows it's a 'maverick' one.

Steps:
After installing the repository, go into 'Ubuntu-software-centre'
Edit -> Software Sources...
Other Software

Select the new repository (without changing the check box)
Click Edit...

Change 'lucid' to 'maverick' in the distribution field.

Then run the update.
Then install the packages.
Then reboot.

Works a treat. :)

Chutedp, you saved the day! Thank you! Works like a charm :-)

---

### Post by aryzing on 2012-07-04
> **ales said:**
> 

$ sudo add-apt-repository ppa:plaxx/random-fixes
$ sudo apt-get update
$ sudo apt-get install libsane sane-utils[/B]



This did it for me! Thank you! 
Ubuntu 10.10, LiDE 210

---

