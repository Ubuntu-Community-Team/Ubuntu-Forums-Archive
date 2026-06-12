---
title: "Problems With ATI Radeon HD 2600 plzz help"
date: 2009-04-18
forum: Hardware
---

### Post by El_Menor015 on 2009-04-18
I Put My ATI Radeon™ HD 2600 1gb and ubuntu boot and every but when the login screen is coming The Screen Stay in black and nothing happen Plzz Help


Sorry 4 My bad English

---

### Post by Svensk023 on 2009-04-18
Did you put a new video card in your computer?

Or did you install new ATI drivers?

---

### Post by El_Menor015 on 2009-04-18
i put a new one and nothing +_+

---

### Post by Svensk023 on 2009-04-18
ok there are a number of things you can do.

I would suggest putting your old video card back in (so you can have a your graphical UI back) and downloading the appropriate ATI driver from the site and install it.

here is what you should try:

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
just go there and look for you driver and download it.

to install follow these few steps.

after downloading you should just get a file that ends in .run an example is

ati-driver-installer-9.2-x86.x86_64.run

if not, then you need to extract it out of the folder you downloaded.

next you need to open up a terminal and put in

```
sudo sh [drag .run file here]
```

so an example would be

```
sudo sh run ati-driver-installer-9.2-x86.x86_64.run
```

click enter and enter your password and this should start the installation process. Be sure to choose "automatic" installation when given the choice between "automatic" and "manual"

after the install power off your computer and insert the new card and we will see if that works.

---

