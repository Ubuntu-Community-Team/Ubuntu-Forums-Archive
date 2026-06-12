---
title: "Console instead of GUI login on startup"
date: 2008-08-28
forum: General Help
---

### Post by yuv656 on 2008-08-28
_Here's a simple problem:_

The power to my pc was cut while Ubuntu was booting up, so I switched the PC on again, and Ubuntu gave some error (I don't recall the exact error message).

Ever since, whenever I boot up, Ubuntu goes to the text-based login and doesn't launch the GUI. I have to log in and then type **startx** to launch the GUI. 

I have tried various fixes I could find by searching ubuntuforums to no avail. Any help will be appreciated!

P.S. Another very irritating consequence is I can't use the red button in the corner to power the PC off, it only shows Suspend and Hibernate. I have to shut it down from the command line.

---

### Post by Sycron on 2008-08-28
Try ```
sudo gdm
```.

---

### Post by yuv656 on 2008-08-28
> **Sycron said:**
> Try ```
sudo gdm
```.

Thanks, that did the trick! 
I just have one problem now: The extra buttons on my MX revolution mouse are no longer working. I always used **btnx** to control these buttons, and in the rare event where they stopped working for some reason, I just had to enter btnx and hit Restart, and they would work again. Now they no longer work on startup and btnx has no effect. :(

---

### Post by Sycron on 2008-08-28
Try reinstalling btns. Sorry but i'm not using MX ... i have IME 3.0 :).

---

### Post by yuv656 on 2008-08-28
> **Sycron said:**
> Try reinstalling btns. Sorry but i'm not using MX ... i have IME 3.0 :).

Works after reinstall, thanks again!

---

