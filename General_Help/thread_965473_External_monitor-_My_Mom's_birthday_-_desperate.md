---
title: "External monitor- My Mom's birthday - desperate"
date: 2008-10-31
forum: General Help
---

### Post by rmcellig on 2008-10-31
Tomorrow is my Mom's birthday. I will surprise her by giving her a HP DV 2910 laptop running Ubuntu 8.10. She is a senior citizen so I am trying to make this as easy as possible for her.

One outstanding issue that I really need to resolve is how she can hook up an external monitor so that it just works with her computer. She has spent the last 10 years using Macs and is used to things just working.  I have posted elsewhere regarding my situation with no replies that address my problem.

Could someone please get back to me on how to get an external monitor working on this laptop. I would REALLY appreciate it!! I am new to Ubuntu and have also been using Macs for years. I'm a GUI type user.

Thanks again!!

---

### Post by Yellow Pasque on 2008-10-31
What kind of video card is in it? I'm guessing Intel integrated graphics? If so, see this as an example of to configure your /etc/X11/xorg.conf file: [http://ubuntuforums.org/showpost.php?p=6016685&postcount=3](http://ubuntuforums.org/showpost.php?p=6016685&postcount=3)

---

### Post by rmcellig on 2008-10-31
It is an Nvidia in her PC

---

### Post by rmcellig on 2008-10-31
To be more specific, this is what is in her laptop. NVIDIA GeForce Go 7150M.

---

### Post by PsychedelicReaction on 2008-10-31
if you have installed the nvidia proprietary drivers you can easly configure the second monitor from "System -> Administration -> Nvidia X Server Setting->X Server Display Configuration".

If you want to make all the modifications permanent run it with super powers

```
gksu nvidia-settings
```

and when you are satisfied use the "Save to X configuration file" button

Maybe it's better that you backup your /etc/X11/xorg.conf file before making any modification permanent.

---

### Post by rmcellig on 2008-10-31
Thanks!! Appreciated beleive me. How exactly do I set this up. Do I plg the monitor in first. 

I really need to be walked through this because I am really new to all this stuff. Step by step instructions would suit me fine.



Thanks again!!

---

