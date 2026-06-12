---
title: "Free v Proprietary driver for Radeon HD5770 graphics card"
date: 2013-01-31
forum: Hardware
---

### Post by oscarivera9 on 2013-01-31
Hi,
I am not using any proprietary drivers at all with my main PC.   Steam is telling me to use the fglrx experimental driver for my Radeon HD5770 graphics card.    I've used both kinds of drivers in the past: free & proprietary.    Back when I was using Ubuntu 11.10 I actually had problems using the Gnome 3.xx desktop environment because of the proprietary driver.
If I were to switch to the proprietary driver instead of using the free Gallium 0.4 on AMD Juniper driver that I'm using right now would it be too much of a hassle to switch back if I needed to do so?

---

### Post by Mark Phelps on 2013-02-01
Depends on what you mean by "hassle"!

Once you install the restricted drivers, to go back to any other driver, you would have to remove them and reinstall the other driver.  It's not a simple one-click procedure, though; there's considerable work involved.

Link below has some of that information:

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by oscarivera9 on 2013-02-03
> **Mark Phelps said:**
> Depends on what you mean by "hassle"!

Once you install the restricted drivers, to go back to any other driver, you would have to remove them and reinstall the other driver.  It's not a simple one-click procedure, though; there's considerable work involved.

Link below has some of that information:

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)


I've actually already done this before where I install the proprietary drivers and then go back to the free ones.  Even though it took me some time I was able to do it without any problems.
This is what I mean by hassle:  I recall reading somewhere recently that if you install the proprietary driver and then revert back to the free one, there is a chance that the system may break and you'll have to reinstall X.

---

### Post by typhoon_tip on 2013-02-03
Just remember to delete xorg.conf file after removing the proprietary driver, and nothing will break. :popcorn:

---

### Post by Mark Phelps on 2013-02-03
> **oscarivera9 said:**
> ...This is what I mean by hassle:  I recall reading somewhere recently that if you install the proprietary driver and then revert back to the free one, there is a chance that the system may break and you'll have to reinstall X.

I never heard that myself, and have not encountered it, either.

In that case, I would have to say that it is NOT a hassle!

---

### Post by Yellow Pasque on 2013-02-03
Reverting to open-source is not hard at all, especially when you follow the guide... [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by oscarivera9 on 2013-02-03
You guys are pretty convincing.  Currently I am using the free radeon driver and  it's worked great for me so far.  Like I said earlier, I would install the proprietary for gaming purposes.  
Thanks for your input, you've all been very helpful.

---

