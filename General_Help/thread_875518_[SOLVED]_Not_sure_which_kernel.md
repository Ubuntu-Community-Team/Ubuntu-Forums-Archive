---
title: "[SOLVED] Not sure which kernel"
date: 2008-07-30
forum: General Help
---

### Post by DougieFresh4U on 2008-07-30
I seem to be having a problem with the kernel and in my grub menue I can only boot if I go in grub and take it down one level. Also when it does boot from the first line in grub it won't detect my wireless.
Please help me sort this mess out. I am running Hardy

---

### Post by drs305 on 2008-07-30
If you are looking to get grub to start a working kernel:

```
sudo aptitude install startupmanager
```

System > Admin > StartUp-Manager > Boot Options and select the working kernel as the default. Then go to the Advanced tab and make sure Automatically Update is unticked (so it doesn't start using the new/bad kernel).

If you are in the good kernel, you can confirm the version with:
```

uname -r

```

Link to StartUp-Manager in the signature line.

If you want to fix the problems caused by the newer kernel, tell us what you want fixed.

---

### Post by DougieFresh4U on 2008-07-30
Thanks for helpful reply. It says 2.6.24-19
Is there a newer kernel? How can I delete the none working and get it so it upgrades normally?

---

### Post by drs305 on 2008-07-30
> **DougieFresh4U said:**
> Thanks for helpful reply. It says 2.6.24-19
Is there a newer kernel? How can I delete the none working and get it so it upgrades normally?

-19 is the latest STABLE kernel. You can get later kernels with the hardy-proposed repository selected but most users should probably stick with the stable version for their main computer. 

Go to synaptic, preferences, repositories, updates and make sure the hardy-proposed and hardy-backports are not selected. That will keep you from getting the apps and kernels that have not been fully tested and released for general consumption.

In StartUp-Manager make sure the "Automatically update default boot option" is unchecked so that you will continue to use the current kernel until you decide to 'upgrade'. Hardy is LTS (long term support) so there shouldn't be many updates. Newer variations of the kernel will be downloaded to your computer and you may see them in the menu but your computer will continue to boot the one you've selected until you make the change yourself in Startup-Manager or edit grub's menu.lst.

For questions about StartUp-Manager refer to the link below.

---

### Post by DougieFresh4U on 2008-07-30
I was just looking in Synaptic and noticed linux headers file 2.6.24-20 and linux headers 2.6.24-20-38 are checked. Could that be some of my proble?
Thanks for the info you have given

---

### Post by drs305 on 2008-07-30
No. the kernel headers for a kernel you are not using would not cause a problem. You can safely remove the -20 headers.

---

### Post by DougieFresh4U on 2008-07-30
> **drs305 said:**
> No. the kernel headers for a kernel you are not using would not cause a problem. You can safely remove the -20 headers.

Thanks, also image with the same numbers are checked. Iwill admit that I was playing around and checked  things with higher numbers and now I am not sure of removing as I do not want a reboot with all kinds of drama. 
The start up manager took care of my immediate problem, thanks so much

---

### Post by drs305 on 2008-07-31
> **DougieFresh4U said:**
> Thanks, also image with the same numbers are checked. Iwill admit that I was playing around and checked  things with higher numbers and now I am not sure of removing as I do not want a reboot with all kinds of drama. 
The start up manager took care of my immediate problem, thanks so much

I understand your concern. Fortunately, ubuntu would not let you commit 'suicide' by removing the kernel it is currently using. It is safe to remove the linux-image-2.6.24-20XXX. and linux-headers-2.6.24-20XXX you aren't using. Keep one older kernel for a backup. 

In fact, removing the linux-image kernels is the preferred method of cleaning up your menu.lst. The removal not only removes them from the system but cleans up the menu. Changing the menu.lst only, whether via StartUp-Magager or editing menu.lst, only changes the display but the kernels are still hanging around on your computer taking up space.

Anyway, you can keep them if you want. I just wanted you to know you COULD safely delete the -20s if you wanted to...

---

### Post by DougieFresh4U on 2008-07-31
> **drs305 said:**
> I understand your concern. Fortunately, ubuntu would not let you commit 'suicide' by removing the kernel it is currently using. It is safe to remove the linux-image-2.6.24-20XXX. and linux-headers-2.6.24-20XXX you aren't using. Keep one older kernel for a backup. 

In fact, removing the linux-image kernels is the preferred method of cleaning up your menu.lst. The removal not only removes them from the system but cleans up the menu. Changing the menu.lst only, whether via StartUp-Magager or editing menu.lst, only changes the display but the kernels are still hanging around on your computer taking up space.

Anyway, you can keep them if you want. I just wanted you to know you COULD safely delete the -20s if you wanted to...

thanks, working on that tonite

---

