---
title: "can't install AMD catalyst driver for HD4200"
date: 2013-04-03
forum: Hardware
---

### Post by toby pang on 2013-04-03
I have a problem that I will need help from you experts. Thanks in advance for any help you can offer.
I have a fresh install of 12.04. My video card is anintegrated graphics card HD4200, the latest catalyst driver 13.1 should work for my card. 
I followed every single instruction from here 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installing_upstream_drivers_directly_from_AMD.27s_website](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installing_upstream_drivers_directly_from_AMD.27s_website)
But it didn't work. Here's what I got from the terminal.
```
$ sudo aticonfig --initial
aticonfig: No supported adapters detected

```

I noticed that there might be something wrong in the log 
```
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.


```
does link group x86_64-linux-gnu_gl_conf is broken has anything to do with the failure?

---

### Post by Cheesemill on 2013-04-03
When you did your fresh install did you use the 12.04.2 DVD?

If so then you are using the new kernel and graphics stack from 12.10, which means that the Catalyst driver won't work with your card (AMD stopped supporting all 2/3/4xxx series cards last year).

You can get around this problem by reinstalling Ubuntu using the 12.04.1 DVD which still uses the original kernel and graphics stack which AMD does support with your card. Once you've installed the catalyst driver will be available for installation from the UBuntu repositories, no need to mess around with manually downloading and installing the driver from the AMD website.

You can find the 12.04.1 version for download here...
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

---

### Post by typhoon_tip on 2013-04-03
You made a mistake, you should use the *legacy* driver instead, your card is not supported anymore:
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

And, to install, refer to these instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Follow all commands very strictly ! Moreover, before you start, do a full removal, also with instructions in the page, and do a restart with drivers back to the stock open source.

---

### Post by Cheesemill on 2013-04-03
> **typhoon_tip said:**
> And, to install, refer to these instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Follow all commands very strictly ! Moreover, before you start, do a full removal, also with instructions in the page, and do a restart with drivers back to the stock open source.

Those instructions won't work with a 12.04.2 installation, only with a 12.04 or 12.04.1 installation. When the OP has the correct version of Ubuntu installed there is no need to manually install at all, as the restricted drivers application in UBuntu will take care of everything for you.

---

### Post by toby pang on 2013-04-03
thanks guys. Yes I did install ubuntu with the 12.04.2 DVD. Cheesemill, does that mean I don't have to install the legacy driver then?

---

### Post by Cheesemill on 2013-04-03
For all versions of Ubuntu from 12.10 onwards (this includes 12.04.2) there is only one driver available for your card, this is the open source radeon driver that is included with Ubuntu and is the one that is used by default (you were already using it before you tried installing the driver from the AMD website). Because AMD dropped its Linux support for all 2/3/4xxx series cards last year the radeon driver is your only choice for recent versions of Ubuntu.

You may find that the open source radeon driver does all you need it to, but the 3D performance and hardware video decoding functions are either poorly supported, or not at all. To get the full functionality and performance from your card you may want to use the fglrx-legacy (Catalyst) driver instead which is closed source and written by AMD.

 If you want to be able to install the fglrx-legacy driver then your only choice is to use an earlier version of Ubuntu. Realistically this means installing 12.04.1 as it is the only version that is still supported by both Ubuntu and AMD.

---

