---
title: "Virtual Box hangs temporarily??? argh!"
date: 2008-11-04
forum: General Help
---

### Post by MichaelSwengel on 2008-11-04
I have downloaded and installed Virtual Box from the Intrepid repos via Add/Remove.

I have set up Kubuntu, Mandriva, Slax, and gOS in Virtual Box. However, with all four distros, Virtual Box will hang for a moment and then start working again for a few minutes. This happens repeatedly.

For instance, I'll be moving the mouse around in my VM and it suddenly stops, and no input works - keyboard or mouse.

I haven't touched any kernel settings or anything beyond installing Virtual Box, downloading ISOs, and setting up the VMs.

Is there something more I should do to avoid this problem? What am I doing wrong? :confused:

For the record, I am running Ubuntu 8.10 Intrepid on a Macbook Pro 4,1.

Thanks for any help,
Michael

---

### Post by ju2wheels on 2008-11-04
Did you install VBox Additions on each of the Guest OS's?

Should be listed under Devices-> Install Guest Additions on VBox.

---

### Post by steveydoteu on 2008-11-04
> **MichaelSwengel said:**
> I have set up Kubuntu, Mandriva, Slax, and gOS in Virtual Box. However, with all four distros, Virtual Box will hang for a moment and then start working again for a few minutes. This happens repeatedly.

What settings have you used?



> For the record, I am running Ubuntu 8.10 Intrepid on a Macbook Pro 4,1.

The specs of which are?

Are you attempting to run all four virtual systems alongside one another, are you running anything else that may require a lot of resources at the same time as the issues you are having?

---

### Post by MichaelSwengel on 2008-11-04
> **ju2wheels said:**
> Did you install VBox Additions on each of the Guest OS's?

Should be listed under Devices-> Install Guest Additions on VBox.


No I have not. I will try that now.

I left most of the settings at the default - except I gave Ubuntu 2 gigs of ram and the guest os'es 1 gig and split my video ram between the host and the guest.



> **steveydoteu said:**
> What settings have you used?



The specs of which are?

Are you attempting to run all four virtual systems alongside one another, are you running anything else that may require a lot of resources at the same time as the issues you are having?

Specs:

4 GB RAM (3gb in Ubuntu)
Geforce 8600 256mb
200gb hdd

I'm only running one at a time. I wouldn't dare try all 5 at once! :)



Anyway, I'll try installing those additions. Thanks guys.

---

