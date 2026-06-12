---
title: "nvidia x driver"
date: 2009-05-03
forum: Hardware
---

### Post by Insomniac20k on 2009-05-03
I've just installed Ubuntu 9, and have divorced myself from windows entirely. I'm trying to get everything working now but I'm kind of new.

I wanted to change the resolution, but when I went to the display settings it said my monitor was unknown. I went and enabled the proprietary nvidia drivers and thought that might do something, and when I went back to Display in the the preference menu it said my graphics driver didn't support the necessary extensions to use that tool and asked if I wanted to use the vendor's tool instead.

So I said yes, and it gave me a box that said

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Can some one please walk me through that? Messing with the xconfig file scares me a bit.

Also, if you could help me get it to recognize my monitor I would love you forever. It's an Acer.

Thank you for your help. You guys always get me where I need to be.

-Matt

---

### Post by pbpersson on 2009-05-03
Get into a terminal session and type the following:

```
sudo nvidia-xconfig
```

Then reboot

I have no knowledge of this nvidia problem, I am just interpreting what it told you to type

---

### Post by mikedep333 on 2009-05-04
Hmm,

What Nvidia card do you have? You enabled the driver through "hardware drivers", right? And you did reboot after enabling the driver, right?

---

### Post by Insomniac20k on 2009-05-04
Thank you for the responses. I did not reboot. I didn't realize I had to. Kind of feel like an idiot.

I restarted and now everything works peachy. Thanks again, guys.

Matt

---

### Post by freonchill on 2009-05-04
you running a desktop or a laptop?

can you get suspend/hibernate to work after installing the restricted nvidia driver?

thanks,

---

### Post by Insomniac20k on 2009-05-04
It's a desktop and yeah, hibernate seems to work. I walked away without doing anything to it and it went to sleep and came right back up. Sound still works, which was always an issue on my laptop. Sound wouldn't work after hibernating. With that computer, if I hibernated without restarting for too long the computer's performance would degrade considerably until I reset. That was Ubuntu 5 though, so it's probably improved considerably. 

I've never really had issues hibernating on desktops, though. My graphics is an integrated nvidia set up. I think it's 8100.

---

