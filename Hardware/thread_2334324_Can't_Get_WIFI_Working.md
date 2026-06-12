---
title: "Can't Get WIFI Working"
date: 2016-08-18
forum: Hardware
---

### Post by smccarthy945 on 2016-08-18
A few days ago. I loaded the latest Kubuntu release and everything loaded perfectly on my Dell laptop, however, the wireless card won't work properly. I tried several other distributions to see if it was Ubuntu specific and all the other distros didn't find the card either. It's a Broadcom card and if I go into additional drivers, it will show that it's trying to use the third party Broadcom drivers but it always says the card isn't working. I tried following the Broadcom guide someone posted where you identify your card and then run the proper command to load the right driver package but didn't have any luck with that either. 

This is the guide I followed:
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

This was the card it identified as:
14e4:4365 rev 01    bcmwl-kernel-source               bcmwl-kernel-source 

I would love to be able to run Linux on my laptops but can't do it if I can't get wireless working. Is there any magic trick to get my built in wifi card to work? I have tried a bunch of other solutions with no luck and can't seem to get this card to work. Can someone give me a suggestion on how to get this card working properly? 

Thanks.

---

### Post by QIII on 2016-08-18
Hello!

When you say "latest release", which release do you mean specifically?

---

### Post by smccarthy945 on 2016-08-18
> **QIII said:**
> Hello!

When you say "latest release", which release do you mean specifically?

Version 16.04.1 LTS

---

### Post by jeremy31 on 2016-08-18
So does ```
lspci -nnk | grep -iA2 net
```
Show Kernel Driver in use: wl or something else?
You do need secure boot disabled in BIOS for this to work at all otherwise the kernel will block the module from loading on most newer Ubuntu kernels

---

### Post by smccarthy945 on 2016-08-19
And I will make one other comment - this post never solved my problem. I also posted on a Zorin forum and got a total of zero replies. So assuming I won't replace the WIFI card, I have got absolutely no help. Yes, I tried turning off secure boot and it didn't have any effect.

---

### Post by smccarthy945 on 2016-08-20
Ok, so after much trial and error I figured it out. This is how you fix a Broadcom card and get it to work on Kubuntu. I assume the same process works for Ubuntu but I haven't tried:

Step 1:
Copy these two files from the original CD or USB key you used to install Kubuntu:
pool/main/d/dkms/dkms_XXXXX.deb
pool/restricted/b/bcmwl/bcmwl-kernel-source_XXXXX.deb
Copy these files to your home directory. Just copy and paste them from the directories above and paste them into your home directory.

Step 2:
Run terminal and go to your home directory. Once at your home directory, type this:
sudo dpkg -i *.deb
This command will install both packages and makes the Broadcom WIFI card work. 

That's it. I did this and my WIFI card started working and has been working perfect ever since.

---

### Post by wildmanne39 on 2016-08-20
Thread solved and closed to further off topic comments.

---

