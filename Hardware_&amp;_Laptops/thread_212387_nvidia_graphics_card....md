---
title: "nvidia graphics card..."
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by mbgb14 on 2006-07-09
Hi, 

I have a HP Pavillion zv5000 laptop (actually, its my dads). 
He wants to use Google Earth on it, but, its using OpenGL mode, so its slow as molasses. It recommended downloading my graphics card driver. So, I loaded up EasyUbuntu, and loaded the Nvidia driver. Unfortunetly, after rebooting, it still isn't working. Still defaults back to OpenGL mode. 

Any ideas? -- I do remember EU complaining that some file was in use, and I should manually run some command - but I didn't see it, because it got closed accidentally.

---

### Post by sexcopter on 2006-07-12
I haven't installed them before using the EasyUbuntu program, but normally you have to run the command
```
sudo nvidia-glx-config enable
```
Perhaps that's what you need to do. It's safe to run it even if it isn't actually necessary. After running that command you'll need to restart X (either reboot the laptop, or hit ctrl-alt-backspace)
By the way, I think you actually *want* it running in OpenGL mode, the only thing at fault it seems is the drivers not working (...yet)

James.

---

