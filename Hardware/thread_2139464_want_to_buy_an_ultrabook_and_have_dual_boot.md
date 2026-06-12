---
title: "want to buy an ultrabook and have dual boot"
date: 2013-04-26
forum: Hardware
---

### Post by technmom on 2013-04-26
Is it possible to have a dual boot ultra book. I have dual boot Windows 7 and Ubuntu 12.04. I mostly use ubuntu but need to have Windows for some applications. Now I need to travel

thanks

---

### Post by oldfred on 2013-04-26
If it has Windows 8 with secure boot, some computer have it working. But it is a lot more complex and the entire UEFI with secure boot has made it complex.
UltraBooks use Intel SRT which uses RAID somehow for the cache on the SSD. Some have larger SSD and just install Ubuntu's  (root) in the SSD and leave SRT off.
And UltraBooks have Optimus or dual video. There is Bumblebee and finally nVidia has just announced the beta of a new drive that starts to work. But it only works with the kernel that will be in the next version of Ubuntu. Currently you use Bumblebee to make it work with most systems.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

            Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

            Asus UltraBook - kernel comparisons
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)

            Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

    
There are others in forum and I think many have worked. Some then run into issues and later give up, so we are not always sure. 
You can search forum by model and see if there is any info.
 But using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search term
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by technmom on 2013-04-27
Would it be more practical to just get an Ultrabook with Windows and install virtual box for ubuntu? I will still have my dual boot desktops (1 in my lab and 1 at home)

---

### Post by oldfred on 2013-04-27
I do not know virtual box much less in Windows.

Some install Ubuntu to a second drive or even a larger flash drive. With UEFI it is a bit more difficult.

---

