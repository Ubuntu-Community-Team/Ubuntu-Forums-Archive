---
title: "SAPPHIRE Radeon R7 240 4GB GDDR3 - software support"
date: 2017-08-08
forum: Hardware
---

### Post by k-stefanov87 on 2017-08-08
Hey, i recently purchased a old pc, made few upgrades and decided to give ubuntu a try for the second time *mind  you i have no idea what i am doing*

i have purchased SAPPHIRE Radeon R7 240 4GB GDDR3  but i cant seem to figure out how to install the drivers for the card, can some one help me or guide me how to do it please? i have checked few videos and few articles how to do it, but to no success.

Thank you in advance for your assistance :)

---

### Post by QIII on 2017-08-08
Hello!

Which release of Ubuntu are you using?

---

### Post by k-stefanov87 on 2017-08-09
> **QIII said:**
> Hello!

Which release of Ubuntu are you using?


Hey, i am using the latest release 17.4, downloaded from the official web page.

---

### Post by k-stefanov87 on 2017-08-09
yesterday i tried this (i was not exactly sure if this is the thing i need) [https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) and it wont let me go pass the log in screen, it just flickers from the login screen and goes back to the login screen for some reason :(

---

### Post by k-stefanov87 on 2017-08-10
i did clean re-install on ubuntu, but i cant still figure out how to install the drivers on the video card :/ can some one still help me with that or any one got an advice maybe or a suggestion ?

---

### Post by QIII on 2017-08-10
Would you please issue this in the terminal and post the results?

```
lsmod | grep amdgpu 
```

This will tell us if the open source part of amdgpu has been installed and loaded.

---

### Post by k-stefanov87 on 2017-08-10
```
amdgpu               1564672  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    98304  2 amdgpu,radeon
drm_kms_helper        151552  2 amdgpu,radeon
drm                   352256  7 amdgpu,radeon,ttm,drm_kms_helper
tixo@tixo-GA-MA770T-UD3:~$ 
```



here is what i got back

---

### Post by k-stefanov87 on 2017-08-11
> **QIII said:**
> Would you please issue this in the terminal and post the results?

```
lsmod | grep amdgpu 
```

This will tell us if the open source part of amdgpu has been installed and loaded.


what number represents if its there or not ?

---

### Post by Yellow Pasque on 2017-08-11
My advice: If the default open source driver works for you, use that. Don't mess with the proprietary "AMDGPU-PRO" driver if you don't have to.

---

### Post by k-stefanov87 on 2017-08-11
> **Temüjin said:**
> My advice: If the default open source driver works for you, use that. Don't mess with the proprietary "AMDGPU-PRO" driver if you don't have to.

can you please point me to that open source driver ? or even how to ? cuz i dont understand, i see only an .exe files on the official web page for windows but nothing for ubuntu/linux

---

### Post by QIII on 2017-08-11
AMDGPU is the open source driver used at install time when the installer detects a supported graphics adapter.  AMDGPU is installed and the module loaded, as indicated by the results of the command I asked you to run earlier.

AMDGPU-PRO is a proprietary overlay to that.  It is not strictly necessary unless you have a good reason to have it.

There is nothing further you need to do.

Cheers!

---

### Post by k-stefanov87 on 2017-08-11
ah now i understand! thank you very much for the information it was very useful :)

---

