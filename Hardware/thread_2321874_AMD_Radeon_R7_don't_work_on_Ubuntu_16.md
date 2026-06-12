---
title: "AMD Radeon R7 don't work on Ubuntu 16"
date: 2016-04-25
forum: Hardware
---

### Post by leonardo-pmascarenhas on 2016-04-25
Hi guys,

It's the second time that I'm trying to use Ubuntu, but I'm having problems again related to my display driver.
The component is:
"AMD Radeon(TM) R7 M265 2GB DDR3" Hybrid Intel/AMD graphics - Inspiron Dell
I already tried this one: [http://support.amd.com/en-us/download/desktop?os=Linux+x86_64](http://support.amd.com/en-us/download/desktop?os=Linux+x86_64) but didn't work.

It will be awesome if someone could give me a tip.

Thanks,
Leo

---

### Post by T.J. on 2016-04-25
> **leonardo-pmascarenhas said:**
> Hi guys,

It's the second time that I'm trying to use Ubuntu, but I'm having problems again related to my display driver.
The component is:
"AMD Radeon(TM) R7 M265 2GB DDR3" Hybrid Intel/AMD graphics - Inspiron Dell
I already tried this one: [http://support.amd.com/en-us/download/desktop?os=Linux+x86_64](http://support.amd.com/en-us/download/desktop?os=Linux+x86_64) but didn't work.

It will be awesome if someone could give me a tip.

Thanks,
Leo

Hi Leo!  

I'm sorry to report that the AMD Crimson driver 15.12 has not been updated for Xorg version 1.18 used in 16.04.  You need to use the AMDGPU driver or the Radeon driver.


[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)[B]

fglrx[/B]

 The  fglrx driver is now deprecated in 16.04, and we recommend its open  source alternatives (radeon and amdgpu). AMD put a lot of work into the  drivers, and we backported kernel code from Linux 4.5 to provide a  better experience. 
When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware).

---

### Post by leonardo-pmascarenhas on 2016-04-25
Hello T.J.!

Thanks for your answer man, but... how can I do it?
I came from Linux Mint, I'm having an issue with my laptop when I close the lid, it didn't suspend it, so:
 I changed the file:
/etc/systemd/logind.conf, activating the line "HandleLidSwitch=suspend".

Now it suspends! but when I try to turn it on again, the keyboard lights turn on but the screen no.

I think that installing the specific driver it will work.
What do you think?

---

### Post by T.J. on 2016-04-25
You should already be using the Radeon or the AMDGPU by default. :D  As far as I know, the AMDGPU driver support for some R7 cards is 'experimental', only the R9s have full support. R7 cards are in a strange place right now.  You might end up waiting until Canonical updates the situation.  

  Canonical knew that this would be a problem, but they chose to do precisely nothing, except tell everyone to read the release notes. Sorry if that sounds harsh, but I followed the development of 16.04, and I anticipated these kinds of problems. I can't believe they didn't. You aren't the only person posting to the forums for help with AMD cards.  

&#8220;Users who require Pro-graphics or  Workstation class features and performance can continue to use fglrx on  Ubuntu 14.04 until the hybrid stack is available later this year&#8221; 
-- AMD developer in  Phoronix forums. [http://www.pcworld.com/article/3043044/linux/why-linux-gamers-with-radeon-gpus-may-want-to-avoid-ubuntu-1604-lts.html](http://www.pcworld.com/article/3043044/linux/why-linux-gamers-with-radeon-gpus-may-want-to-avoid-ubuntu-1604-lts.html)

After checking around, the recommended fix was to use the official AMD  driver, unless you are familiar with the inner guts of Linux power  management. Without a laptop to run tests on, I am afraid I can't be of  much assistance at present.


If you are asking for a recommendation, I would consider using either Ubuntu 14.04 or Debian 8 on your laptop, instead of Ubuntu 16.04, until these issues are resolved.  Both Ubuntu 14.04 and Debian 8 can use the FGLRX driver.

---

### Post by leonardo-pmascarenhas on 2016-04-27
I installed the 14 LTS here, now everything is working...
I've found many bugs, it's a shame that it's released like that, even if I found a driver to use it's not possible to work with it. So I reported and installed the 14 LTS.
Thanks for your help ;)

Just to reporting here what I found:
Problem related to "close lid" = [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1574161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1574161)
Problem related to ATI drivers = [http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml#ixzz472UJ8jK9](http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml#ixzz472UJ8jK9)
"**Update:** We've been informed by Oliver Grawert from  Canonical that the proprietary AMD Catalyst (fglrx) driver has been  temporarily removed the Ubuntu 16.04 LTS repositories, as it is not yet  ported to X.Org Server 1.8. It will be added again as part of the first  point release, Ubuntu 16.04.1 LTS.

---

### Post by samue2 on 2016-04-28
So much 16.04 teething issues, i would recommend to send a support ticket to amd- and downgrade to 14.04 for a few months

---

### Post by anisimov-h on 2016-07-10
A few days ago I upgraded to 16.04. And I was surprised when my r9 390X run through radeonfb. I found that in 16.04 refused to support fglrx.
But there is a way to setup the crimson 15.12 on ubuntu 16.04.

Firstly, you need to Download crimson drivers from amd site [http://support.amd.com/en-us/download](http://support.amd.com/en-us/download).
Then unpack it 
    ```
sh amd-driver-installer-15.302-x86.x86_64.run --extract
cd fglrx-install. * /
```
And patch
    ```
wget [https://raw.githubusercontent.com/imageguy/fglrx-for-Fedora/master/fglrx_kernel_4.4.diff](https://raw.githubusercontent.com/imageguy/fglrx-for-Fedora/master/fglrx_kernel_4.4.diff)
patch -p1 <fglrx_kernel_4.4.diff
```
Secondly, we must downgrade xserver-xorg to 1.17.
remove current xserver package:
```
sudo apt-get purge xserver-xorg*
```
Commented out the current repository:
   ```
sudo sed -i 's/deb/#deb/' /etc/apt/sources.list
```
Add wily repository in the end of /etc/apt/sources.list:
   ```
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) wily main
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) wily-updates main
```
Install the xserver from wily repository:
   ```
sudo apt-get update
sudo apt-get install xserver-xorg
```
Hold packages with reduced version xserver:
   ```
packages = `aptitude search xserver | grep -E '^ i' | grep -Eo '(. xserver - +) -' | awk '{print $ 1}'`; for pkg in $ packages; do echo "$pkg hold" | sudo dpkg --set-selections; done
```
Restore the contents of /etc/apt/sources.list:
   ```
sudo sed -i 's/#deb/deb/' /etc/apt/sources.list
```
In the directory with the unpacked driver do:
   ```
sudo sh ./ati-installer.sh 15.302 --install
```
Further installation is in normal mode.

All works fine.

---

### Post by QIII on 2016-07-10
This complicated "solution", especially > Secondly, we must downgrade xserver-xorg to 1.17. is very much like an earlier time when Linux support ended for a group of AMD video adapters.  Several "smart" people came up with various schemes for "fixing" things -- which eventually led to a lot of people who had non-operative machines when things changed later.  The "smart" people who came up with these "fixes" were not around the forums to help clean up the mess.  But I was.

I must be very clear on this:  I had to help dozens of people on the Forums sort out the messes this sort of thing left them with later.

If a "solution" includes downgrading something, it is no solution.  It is nothing more than a temporary bit of glue that will be difficult to clean up and will get in the way later when things change.

Personally, I **do not** support this approach and expect that this will lead to another round of my having to get people out of the messes they have gotten themselves into by following the instructions of "smart people" who come up with things like this and like to show them off.  It would be much better to simply use 14.04 (supported until 2019) and see how this all works out by the end of August, 2016.  That is when AMD plans to have this all completed.

For what my opinion is worth.

---

### Post by anisimov-h on 2016-07-10
> This complicated "solution", especially
Yes, it's true, but I wrote that I was upgraded to 16.04, if you do not do this, then stay on the previous version.
And I was not able to run amdgpu, its always falling with segfault /
In xserver-xorg no dependencies except *buntu-desktop, at any time, you can simply unhold the xserver-xorg packages,they  will update themselves.

---

### Post by giga+bytes on 2016-07-17
Well, this answers a question I was going to ask about 14.04 vs 16.04 and AMD drivers. I'll stay with 14.04 for a while and watch how things go.

---

### Post by johnenglart on 2017-01-06
So the problem might have been fixed with re-importing the fglrx driver into the repository for 16.04.1. Guess what? [Softpedia]("http://news.softpedia.com/news/canonical-recommends-open-source-amdgpu-and-radeon-drivers-for-ubuntu-16-04-lts-501556.shtml#ixzz472UJ8jK9"):
Update (2016-08-10): Ubuntu 16.04.1 LTS was released on July 21, 2016, and, unfortunately, the AMD Catalyst (fglrx) graphics driver didn't make a comeback. Instead, AMD has released the AMDGPU-PRO 16.30 video driver for newer AMD Radeon graphics cards, supporting both Ubuntu 16.04.1 LTS and Ubuntu 14.04.5 LTS. We believe that AMD has no intention of bringing the Catalyst driver back to life to support older GPUs.

---

### Post by wildmanne39 on 2017-01-06
AMD is working on new drivers with Canonical to fix this issue but the old driver is not compatible with the new x,org server.
he issue should be resolved when 17.04 comes out.

---

### Post by daniber on 2017-01-08
> **wildmanne39 said:**
> AMD is working on new drivers with Canonical to fix this issue but the old driver is not compatible with the new x,org server.
he issue should be resolved when 17.04 comes out.

Does this mean that :

1 - 16.04 LTS will never have an update from AMD for R7 2XX
2 - I will be forced to upgrade to the next ( non LTS !!!!!!!!!!!!!!!!!) version if I want my R7 250 decently supported ?

Seriously, I don't understand this AMD classification of their customers into Class B and Class A depending on how much you paid yr GPU....
Next time..... NVIDIA !!!!!!!!!

---

### Post by mörgæs on 2017-01-08
LTS translates to stability, that is the opposite of development. There may or may not be some tricle-down from the current development release (that is, 17.04 for now) to the latest LTS, but don't take it for granted. 

When dealing with new hardware the short term support versions is the way to go.

If I were to buy new hardware I would go for AMD, simply because they are more eager supporting free software than Nvidia. Just don't expect them to backport everything to semi-old releases like 16.04.

---

### Post by QIII on 2017-01-08
AMD could have done one of two things:

1.  Continue to develop fglrx and make it compatible with the X Server version used by Canonical in 16.04.

2.  Do what the open source community has been clamoring for for many years:  develop a functional open source driver.  

We got item 2.

To use AMD's open source AMDGPU driver, one must be using a card that supports it:  GCN 1.0 or later (for now, GCN 1.1 and 1.2 or later are supported.  1.0 is coming.)  That is the required technology.  AMDGPU was developed in close coordination with the open source community, by the way.  The open source community was most highly represented by Canonical, LTD.

Your R7 250 is a GCN product, so it will be eventually supported.  And yes, that does mean you will probably will have to get out of the LTS cycle -- or use a newer kernel as I do in 16.04 to support my R9 380X.

To use the fglrx driver, one must use an Ubuntu version prior to 16.04 or use the open source Radeon driver.

This is a case of "Be careful what you wish for."  At great expense with no hope for increased revenue, AMD gave us what we wanted.  That's not abandonment.  That's commitment: they spent an inordinately large amount of money producing an open source Linux driver and will never get even a fraction of that cost back in revenue.  But they couldn't also spend the money on further fglrx development.  They do have a business to run.

---

### Post by rumatakira on 2017-03-26
Just install drivers (sudo!) directly from AMD [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) configure and reboot

---

