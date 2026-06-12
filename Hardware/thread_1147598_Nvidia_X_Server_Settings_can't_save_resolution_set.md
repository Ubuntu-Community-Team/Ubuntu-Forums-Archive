---
title: "Nvidia X Server Settings can't save resolution settings on xorg.conf file"
date: 2009-05-03
forum: Hardware
---

### Post by ezertuchev on 2009-05-03
Hello,

I have just upgraded to Jauty and I've been having problems with the Nvidia driver. I can change the resolution just fine to one that suits my needs, but I can't save the configuration to the xorg.conf file. I get the following message:

"Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

Can anyone help please?

Eduardo

---

### Post by SuperSonic4 on 2009-05-03
You need to launch it as root. Try ```
gksu nvidia-settings
```

or post back if you're not using nvidia-settings

---

### Post by ezertuchev on 2009-05-03
SuperSonic4, thank you! that did it!

Eduardo

---

### Post by dadaas on 2009-10-31
Great post, thanks allot, this solved my problem too.

---

### Post by gradinaruvasile on 2009-10-31
What the heck, that should be fixed once and for all.

---

### Post by pixel-anarchist on 2009-11-09
I have a simmilar Problem. When I try to save the settings a get this alarm "Failed to parse existing X config file '/etc/x11/xorg.conf'! but I did start the nvidia X Server settings with "gksu nvidia-settings". Did I miss some switches I have to add?

The pixel-anarchist

---

### Post by Ch4plain on 2009-11-10
> **pixel-anarchist said:**
> I have a simmilar Problem. When I try to save the settings a get this alarm "Failed to parse existing X config file '/etc/x11/xorg.conf'! but I did start the nvidia X Server settings with "gksu nvidia-settings". Did I miss some switches I have to add?

The pixel-anarchist

I am having the same problem on Karmic.  Never had this problem with Jaunty.

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
If Ubuntu auto detects your hardware properly it's great.... but the second it doesn't, you don't even get a life vest.
[Join the protest!](http://ubuntuforums.org/showthread.php?p=8280317#post8280317)

---

### Post by soulmatic09 on 2009-11-23
Login as root!!

Thanks! I've been trying to fix this forever, and this was all I had to do?!! You'd think it would automatically ask you to type your password, or tell you to log in as root as an error message.

---

### Post by shnurui on 2009-11-26
> **soulmatic09 said:**
> Login as root!!

Thanks! I've been trying to fix this forever, and this was all I had to do?!! You'd think it would automatically ask you to type your password, or tell you to log in as root as an error message.

how do you login as root?

---

### Post by jonasgreatguide on 2009-11-26
> **shnurui said:**
> how do you login as root?

Yep I would like to know it too.

---

### Post by Juice0123 on 2010-10-15
> **SuperSonic4 said:**
> You need to launch it as root. Try ```
gksu nvidia-settings
```

or post back if you're not using nvidia-settings

Worked Great! Exactly what I needed

---

