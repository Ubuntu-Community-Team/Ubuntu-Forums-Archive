---
title: "Gigabyte Radeon RX580"
date: 2017-11-01
forum: Hardware
---

### Post by schnemart on 2017-11-01
Hello all
I have just installed a new Gigabyte Radeon RX580
It boots as far as check filesystem 

I then upgraded to latest driver off Radeon web site
I get the filesystem check and then 
blank screen with  a cursor in top left hand corner of the screen is all that happens

Yet when I boot up through Grub advanced options repair mode
I get a warning that the GPU driver wont load and it boots in low resmode
in system details it states  
Graphics  Gallium 0.4 on llvmpipe(LLVM 4.0,256 bits)

or when I boot from a 16.04 LTS usb drive it boots  in full high res and working ok

in system details it states
Graphics  Gallium 0.4 on AMD POLARIS 10(DRM3.9.0/4.10.028 Generic, LLVM4.0.0)

thanks for your help

---

### Post by gsahli on 2017-11-02
I don't think the AMDGPU-Pro (download from AMD) driver is functional, go back to the distro-included AMDGPU driver.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by QIII on 2017-11-02
AMDGPU-PRO most certainly does work ... I'm running it.

However, it may be that the kernel being used is not ready for that particular hardware or the driver for it is not yet available.

My suspicion goes to the first possibility.  In any case, the affect may be the same:  if may be the case that the default Radeon driver will have to be used.

It might be worth a look around the Forums for those using 17.10 to see if they have gotten it to work with that kernel.  (I'd look for you, but I'm a bit distracted at the moment.)

---

### Post by schnemart on 2017-11-02
Hi Qlll
how do I point my 16.04 system back to the default Radeon driver 
thanks
Martin

---

### Post by Yellow Pasque on 2017-11-03
> Uninstalling the AMD GPU-PRO Driver
If for any reason you wish to remove the AMDGPU-PRO graphics stack you can do this using the uninstallation script which was part of the installation and is present in your path. From the command prompt enter the following command:

```
amdgpu-pro-uninstall
```

[http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

---

### Post by schnemart on 2017-11-04
thanks for that
 I un installed driver and the system boot in low res mode 
I have asked question on AMD support site will report back here 
there seems to be a common problem with Radeon and Ubuntu maybe I should of purchased NIVIDIA

---

### Post by Yellow Pasque on 2017-11-04
Give the /var/log/Xorg.0.log file
Did it work before in normal resolution before you installed the pro dirver?

---

### Post by schnemart on 2017-11-04
it did not work initally when  I installed the card 
 i then installed the amdpro driver and it didnt work 
but when I disabled the on board intel grahpics  it worked but it kept loggining me out
then went into the console and uninstalled the amdgpu-pro
and then it would boot in low res mode

---

### Post by schnemart on 2017-11-05
Just to clarrify I had to   switch back on the  on board graphics card
then pull out the RX580 
I was then on a loop when I tried to loggin[I] I went to console  mode
and the ran [/I]amdgpu-pro-uninstall 
then when I disabled the on board card resinstalled the RX580 it would boot in low res mode

---

### Post by schnemart on 2017-11-08
I have re installed  amdgpu-pro and when the screen freezes  at a - prompt in top right hand corner if I Ctrl+Alt+F1 I get a terminal login which I can login into and I can see the driver is loaded by  using dpkg -l amdgpu-pro

Very odd
please any help
kind regards
Martin

---

### Post by schnemart on 2017-11-11
Hello all
I have fixed it I received the Answer 
In the AMD Driver & software forum from a very nice bloke called archimiga      
it is as follows:

upgrade the kernel to 4.10
 
sudo apt-get install --install-recommends xserver-xorg-hwe-16.04
 
for me work
 
type ctrl-alt-F2  and login to uninstall and reinstall driver

---

