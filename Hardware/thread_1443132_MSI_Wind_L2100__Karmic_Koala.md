---
title: "MSI Wind L2100 / Karmic Koala"
date: 2010-03-30
forum: Hardware
---

### Post by Shibblet on 2010-03-30
After doing some extensive research, and a lot of trial and error with my MSI Wind L2100 Notebook.  I have finally figured out how get Ubuntu Karmic installed and working GREAT!

I suggest the 32-bit version of Karmic, but the 64-bit works as well.

**Make sure you have a wired internet connection in order to get the wireless working!**

I'll break this down in steps.

**1.**  Install Ubuntu from CD or USB Stick.  Run the Live environment, and do the install from there.


**2.**  After Ubuntu is installed.  Run the update manager, and get all the updates.  None of the updates cause issues with the machine.


**3.**  Download the 2.6.32.9 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/")

**Download these 32-Bit:**
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209-generic_2.6.32-02063209_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209-generic_2.6.32-02063209_i386.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209_2.6.32-02063209_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209_2.6.32-02063209_all.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-image-2.6.32-02063209-generic_2.6.32-02063209_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-image-2.6.32-02063209-generic_2.6.32-02063209_i386.deb")

**Download these 64-Bit:**
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209-generic_2.6.32-02063209_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209-generic_2.6.32-02063209_amd64.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209_2.6.32-02063209_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-headers-2.6.32-02063209_2.6.32-02063209_all.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-image-2.6.32-02063209-generic_2.6.32-02063209_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/linux-image-2.6.32-02063209-generic_2.6.32-02063209_amd64.deb")

Install all three DEB packages, then reboot with the new kernel.


**4.**  Add the ATI Open Source (X-org Edger) Drivers.  Go to System -> Administration -> Software Sources.  Click on Other Sources, then click +Add.  And choose one of the following.

```
*a.*  ***ppa:ubuntu-x-swat/x-updates*** - for the safe (stablest) drivers.
*b.*  ***ppa:xorg-edgers/ppa*** - For the bleeding edge drivers.
```

This PPA will show up in your Other Software tab.  Again, click on **+Add**, and this time add

```
***ppa:markus-tisoft/rt3090***
```

This is your Realtek 3090 Wireless adapter driver.

Click Add Source, then Close, it will ask you to reload your repos, say Yes.


**5.**  Now.  Go to *System -> Administration -> Synaptic Package Manager*.

In the search field look for **dkms**.  It will have a little Ubuntu logo next to it.  Click on the box, and mark for installation.

Then change the search field to **rt3090**, and mark **rt3090-dkms** for installation.

Click on Apply.  Wait for the install.  One more step, and we're through.


**6.**  Go to *System -> Administration -> Update Manager.*

You will notice that your "new" x-org edger drivers are in the update manager.  If not, check step 4 again, and click Check to refresh.
 
Click on Install Updates, and off you go.


**7.**  Finally, restart your computer with the new drivers available, and download your favorite software.

---

### Post by JDorfler on 2010-03-30
Running Karmic right now on my MSi L2100.

---

