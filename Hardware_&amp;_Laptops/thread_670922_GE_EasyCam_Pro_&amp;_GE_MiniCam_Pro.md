---
title: "GE EasyCam Pro &amp; GE MiniCam Pro"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by phillipi on 2008-01-18
GE EasyCam Pro 98604 (ID 05a9:8519 OmniVision Technologies, Inc.)
GE MiniCam Pro 98067 (ID 0c45:60fe Microdia)

I cannot find away to get, force, bribe, or blackmail these cameras into working on my Ubuntu 7.1 Gutsy Gibbon. I haven't got as far as getting them to work in skype.. I can't get drivers to work for them period. If anyone has found a road to success I would appreciate some help.

Thankyou,
mike

I tried the Easycam application both versions 1 and 2. Both have failed

---

### Post by vivalant on 2008-01-18
Hello Philliphi, for the latter try the Generic SN9CXXX drivers at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by phillipi on 2008-01-18
TRIAL Generic SN9CXXX Video4Linux1 & Video4Linux2 driver for *Ubuntu 7.10 (Gutsy, 32Bit) 
sn9cxxx_2.09-gutsy-1ubuntu1_i386

I installed this and now i cannot run the update manager or the synaptic package manager,

i receive these error messages

update-manager
'E:The package sn9cxxx needs to be reinstalled, but I can't find an archive for it.'

and the package manager
E: The package sn9cxxx needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by phillipi on 2008-01-18
hmm and because of these problems my update manager and package manager now display an error message and quit when run. I can no longer update or install via the SPM.

---

### Post by intel on 2008-01-22
what is the output of
#apt-get update

& the output of
#apt-get -f install

(run the above commands as superuser)

These things(crashes) will happen if you use any experimental software not packaged by ubuntu (ubuntu tests the packages in the default repositories to help reduce these problems)

for those with microdia webcams (oc45:xxxx) there's a support group at
https://groups.google.com/group/microdia
please ask for help there

---

