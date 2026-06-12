---
title: "Nvidia Go 6150 No Output"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by mariogl91@gmail.com on 2006-10-31
Hi, I just bought an HP dv6140us which has an Nvidia Go 6150. Edgy didn't detect my graphics card so it used the Vesa driver which I don't really like.

After that, I installed nvidia-glx and booted. Now, the thing is I can't see anything, but I do hear the "greeting drums" so I think the problem is only the output to the screen. What could be the problem?

I think I configured everything correctly. I used nvidia-xconfig to configure my xorg.conf. Now the problem is I can't even log in with Vesa! It shows me the log in screen, I enter my account and password, and it goes to a black screen, then it returns to the login screen.

I'm a little desperate so any help would be greatly appreciated.
Thanks!

---

### Post by AlReece45 on 2006-10-31
Same card on my (similar) laptop. The "nvidia" drivers don't work on it because it isn't supported. If you don't need the 3D, just use the "nv" drivers. However, if you're like me and need the 3D acceleration then install  the beta nvidia drivers from Step Two of [this guide]("http://ubuntuforums.org/showthread.php?t=263851")

---

### Post by mariogl91@gmail.com on 2006-10-31
Thanks for your reply.

I installed the beta drivers by following the guide. Now X gives me an error that says:

```

Error: API Mismatch: the nvidia kernel module has the version 1.0-8774, but this X module has the version 1.0-9625. Please make sure that the kernel module and all NVIDIA driver components have the same version.

```

And some other things but I think this is the important one. Any suggestions?

---

### Post by AlReece45 on 2006-10-31
Did you install with repository package or .RUN package?

---

### Post by mariogl91@gmail.com on 2006-10-31
With the repository package. Was I supposed to use nvidia's script?

---

### Post by mariogl91@gmail.com on 2006-10-31
I will do a fresh install and then follow the Howto. Let's see if it works... :-k

---

### Post by mariogl91@gmail.com on 2006-10-31
It's working now. Thanks a lot for your help. :)

---

