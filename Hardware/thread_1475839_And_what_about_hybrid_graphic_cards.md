---
title: "And what about hybrid graphic cards?"
date: 2010-05-07
forum: Hardware
---

### Post by thidess on 2010-05-07
Hi all!
I have troubles with my new laptop Asus X77jv (Intel core i5 and Nvidia GT 325 M). I have Ubuntu 10.04 emt-64 installed and just one graphic card in use, but not the best! I know that Nvidia have developped OPTIMUS for windows 7 (ant this laptop is compatible with this) but it seams that Linux users are not allow to have fun with their Nvidia hardware. 
Is there someone who knows something about it?
Thank for your answer.

---

### Post by dino99 on 2010-05-07
try that repo: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Workaround for now is to remain with older Kernel version 2.6.32-15

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by thidess on 2010-05-07
Thank you for your (quick) answer!
I try the repo but I got the following message:
Impossible de récupérer [http://ppa.launchpad.net/ubuntu-x-swat/x-update/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-x-swat/x-update/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found (Yes, it's a french version!)
So I can't get the files
And the Kernel is 2.6.32-22. I have to install an earlier version?

---

### Post by dino99 on 2010-05-07
you have chosen the wrong way  ;) no need to compile, its already done :)

***** Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding ppa:ubuntu-x-swat/x-updates to your system's Software Sources ****

so goto synaptic (system admin synaptic) and add to repo-tab (config-repo 2d tab): ppa:ubuntu-x-swat/x-updates

then update and upgrade

---

### Post by thidess on 2010-05-07
PPA was well added. Update in synaptic don't give this result. I have to search and install manually every components of the PPA new packages. I have to restart my system.
 ):P

---

### Post by thidess on 2010-05-07
Well ! doesn't work! I get a BSOD (Black Screen Of Death) and no way to to run in console mode!
I have to reinstall all.   ](*,)

---

### Post by darkenvy6 on 2010-05-07
Thidess, how did the install go? I have the same problem but the apt-get install cannot find all the packages :(. Oh and my drivers crashed on reboot

**Update:**
I gotta remember to refresh before posting XD

---

### Post by thidess on 2010-05-07
when installing, I see an error with nvidia.ko
but the install process finished without any error message and then... in the deep dark!

I don't where to post this bug

---

### Post by renomcdonald on 2010-05-07
thidness, what graphics card do you have anyways? the generation? Im a 200

---

### Post by thidess on 2010-05-07
I have a laptop asus X77jv intel core i5-430 M 2,27 Ghz and nvidia geforce GT 325 M (1 Go) .

---

### Post by darkenvy6 on 2010-05-07
Follow me on [http://ubuntuforums.org/showthread.php?p=9258022#post9258022](http://ubuntuforums.org/showthread.php?p=9258022#post9258022) , I'm making progress here on my Nvidia journey. Now I face a new problem of getting my multiple monitors setup :P

---

### Post by thidess on 2010-05-07
Woahoh! from different ubuntu forums, some peolple uninstall older version of all that concern nvdia drivers, some others not. What the hell!!!
Just ONE question. [COLOR=black]What we have to do to make working one or both hybrid  graphicc cards[/COLOR] and, in fact, is it really possible? I began to have shimmy in my hands, crossed tearing eyes and soon no more hair because I pull off them every crash of the drivers. :shock:
I know Ubunt usince 8.04. So please Help Us 
or stop LTS for this product.

---

### Post by Azegul on 2010-07-12
Hi Thidess. I have the same graphic card (GT 325M) and I have searched all over the internet for a way to enable the Nvidia driver.
And it appears that it is not possible at the moment.
I'm sure that in time some clever person will work it out.
That's the good thing about Linux. Someone always fixes the problem eventually.
I'll keep looking and if I find anything I will post it here.
And yes, I have tried all the suggestions on this post and the ones linked.
Nothing worked.
Good luck!

---

