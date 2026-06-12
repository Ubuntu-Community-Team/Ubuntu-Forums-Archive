---
title: "Latest NVIDIA drivers from website (for optimus support)"
date: 2013-06-30
forum: Hardware
---

### Post by Zorgoth on 2013-06-30
So, I just learned that the newest proprietary NVIDIA drivers support optimus (i have geforce gt 635m), but nothing shows up in the "Additional Drivers" thing yet (using 12.04). So I decided to try to install it from the website. It gave me a message saying "distribution-provided pre-install script failed! continue?" I said no because I don't know what that means for me and I don't want to kill my computer by accident. Does anyone know either a way around this or whether it's safe to proceed anyway?

Thanks!

---

### Post by Yellow Pasque on 2013-06-30
> but nothing shows up in the "Additional Drivers" thing yet (using 12.04)
Installing the nvidia driver directly borks the open-source intel driver, which is why "Additional Drivers" doesn't give you an option to do that.

> So I decided to try to install it from the website.
Bad idea.

> So, I just learned that the newest proprietary NVIDIA drivers support optimus
The latest drivers don't really support Optimus (switching seamlessly between Intel and nvidia cards). They support using the nvidia card for everything (which will shorten battery life significantly). You need a 3.9.x kernel and an nvidia 319.xx driver. There's a rough guide here, but I personally wouldn't recommend most users toy with their systems that way unless they're comfortable with console recovery: [http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)

---

### Post by grahammechanical on 2013-06-30
You might want to read this. Someone tried using 13.04 and failed. Note the issues that you will have with 12.04

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)

> [COLOR=#555555][FONT=Arial]For now, the latest Nvidia 319.12 beta drivers don't work in Ubuntu by default, not even in Raring,[/FONT][/COLOR]

Things may have improved since 10th April. May be not.

Regards.

---

