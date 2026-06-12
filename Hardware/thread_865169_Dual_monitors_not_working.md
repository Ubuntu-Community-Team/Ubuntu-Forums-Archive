---
title: "Dual monitors not working"
date: 2008-07-20
forum: Hardware
---

### Post by iZephyr on 2008-07-20
I have just switched form windows, and, while my card is in the device manager, and nothing comes up in the restricted drivers program,I can't get it to run in anything other than the safe graphics mode. When I start up, I have to manually configure my monitors and card, but its test always fails.I have Unbuntu updated completely, as well. 
My card is a XFX nvidia 6200. Can someone help?

---

### Post by overdrank on 2008-07-20
> **iZephyr said:**
> I have just switched form windows, and, while my card is in the device manager, and nothing comes up in the restricted drivers program,I can't get it to run in anything other than the safe graphics mode. When I start up, I have to manually configure my monitors and card, but its test always fails.I have Unbuntu updated completely, as well. 
My card is a XFX nvidia 6200. Can someone help?

Hi and welcome, You say that there is not a driver located under system, administration, hardware drivers?
If not then you can use synaptic manager and search for nvidia-glx-new.
You may also use Envy.
And last you may use the terminal located under applications, accessories. Use this command ```
sudo apt-get install nvidia-glx-new
```
You can also use the xfix option if you boot into recovery mode which is usually the second choice from the grub.
Edit I almost forgot you will need the nvidia-settings also to help set up the dual monitors with the command ```
gksu nvidia-settings
```

---

### Post by iZephyr on 2008-07-20
When I entered sudo apt-get install nvidia-glx-new into terminal, I got the message "Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"
And nothing comes up in the synaptic manager when I search for what you told me to.

---

### Post by overdrank on 2008-07-20
> **iZephyr said:**
> When I entered sudo apt-get install nvidia-glx-new into terminal, I got the message "Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"
And nothing comes up in the synaptic manager when I search for what you told me to.

Ok you may need to enable your repos.
This link may help
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
It is located under system, administration, software sources.

---

