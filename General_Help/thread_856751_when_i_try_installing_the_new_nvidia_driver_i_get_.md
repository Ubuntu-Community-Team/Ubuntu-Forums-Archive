---
title: "when i try installing the new nvidia driver i get this error"
date: 2008-07-11
forum: General Help
---

### Post by DarK420 on 2008-07-11
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]

uhh help?
I need this to get compiz working

---

### Post by BLTicklemonster on 2008-07-11
Did you try using Applications, Add/Remove, then set to all available applications, then install ubuntu restricted extras. Then you should see an icon appear saying you have restricted drivers available. Click it, enable the nvidia drivers, and go for it!!!

---

### Post by DarK420 on 2008-07-13
> **BLTicklemonster said:**
> Did you try using Applications, Add/Remove, then set to all available applications, then install ubuntu restricted extras. Then you should see an icon appear saying you have restricted drivers available. Click it, enable the nvidia drivers, and go for it!!!

my drivers arnt installed thats why i was installing them..
still need help please

---

### Post by BLTicklemonster on 2008-07-13
That will install your drivers. By "have restricted drivers available" it means available for download to be installed. That is the best way to install nvidia drivers.

What video card do you have?


Bah, how about just download this deb and run it:

[http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb)

looks like what you were wanting anyway.

nvidia-glx-new-dev_169.12+2.6.24.13-19.44_amd64.deb isn't on that page anywhere. No wonder you can't get it.

---

### Post by DarK420 on 2008-07-13
> **BLTicklemonster said:**
> That will install your drivers. By "have restricted drivers available" it means available for download to be installed. That is the best way to install nvidia drivers.

What video card do you have?

The other ways:

You can go to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and download the latest for your card and install it.

Or you can go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and use Envy to install nvidia drivers, too.

But I would try the add/remove method first.


Bah, how about just download this deb and run it:

[http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb)

looks like what you were wanting anyway.

I did the add remove method and it didn't work
and ive went too nvidia.com thats why im getting the error i was dling the drivers from that site then it didnt work

---

### Post by BLTicklemonster on 2008-07-13
[http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb)

That is directly from the deb site. The same site you were getting the file not found message from in the first post. The file you were looking for is gone, this is the newest one. It's the latest for a 64 bit system. That should be the one you want if you want the latest one. 

Hope that helps.

---

### Post by DarK420 on 2008-07-13
> **BLTicklemonster said:**
> [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb)

That is directly from the deb site. The same site you were getting the file not found message from in the first post. The file you were looking for is gone, this is the newest one. It's the latest for a 64 bit system. That should be the one you want if you want the latest one. 

Hope that helps.

ehh its not working i installed it and it still says i dont have a nvidia driver i cant even enable desktops effects
thanks for trying though

---

### Post by jmickey on 2008-07-14
I am having the same issue with the nvidia driver.  When trying to enable the nvidia driver via System>Administration>Hardware Drivers I receive the following error.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

I have a Lenovo T61p with a Quadro FX 570M 512MB graphics card.

I tried other drivers as recommended and received errors each time.

Any help would be appreciated.

Thanks,
John

---

### Post by BLTicklemonster on 2008-07-14
> **jmickey said:**
> I am having the same issue with the nvidia driver.  When trying to enable the nvidia driver via System>Administration>Hardware Drivers I receive the following error.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.44_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

I have a Lenovo T61p with a Quadro FX 570M 512MB graphics card.

I tried other drivers as recommended and received errors each time.

Any help would be appreciated.

Thanks,
John

That file is no longer on the website where the downloads come from.

Click on [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb) , and try running that. Download to desktop, and then double click it.

Worth a shot, eh?

---

### Post by jmickey on 2008-07-14
Thank you for your help.  I used the 45.I386 version and was able to get it to work.

I had to remove a previously installed generic driver to allow the nvidia driver to work.

Also, I updated my system and it is now pointing to the .45 drivers instead of the .44 versions.

I've got it working now.

Thank you,

John

---

### Post by BLTicklemonster on 2008-07-14
SWEEEET! Enjoy it! Glad I could help.

Now I wonder how Dark420 is going to do this afternoon when he gets home from football practice, lol.

---

