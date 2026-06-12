---
title: "Installing a new video card questions."
date: 2008-10-18
forum: Hardware
---

### Post by AceRimmer on 2008-10-18
I want to put a Nvidia video card in my machine to replace the ATI card already running.  What steps do I need to take to make this switch? I'm guessing I'll have to uninstall the ATI drivers but I'm not sure just how to do this.  Any help or a link to a guide that will show me how to do this?
Thanks.

---

### Post by AceRimmer on 2008-10-19
:confused:

---

### Post by ardvark71 on 2008-10-19
Hi...

You won't need to worry about uninstalling the old driver....just installing the new one will be the possible adventure. ;)

What model are you looking at getting specifically? Although it's a bit dated and meant for feisty, this thread has some ideas for possible cards...

[http://ubuntuforums.org/showthread.php?t=526552](http://ubuntuforums.org/showthread.php?t=526552)

There are two or three ways of taking care of the driver end of it, which we can address when the time comes.

Hope this helps... :)

Best Regards...

---

### Post by AceRimmer on 2008-10-20
> **ardvark71 said:**
> Hi...

You won't need to worry about uninstalling the old driver....just installing the new one will be the possible adventure. ;)

What model are you looking at getting specifically? Although it's a bit dated and meant for feisty, this thread has some ideas for possible cards...

[http://ubuntuforums.org/showthread.php?t=526552](http://ubuntuforums.org/showthread.php?t=526552)

There are two or three ways of taking care of the driver end of it, which we can address when the time comes.

Hope this helps... :)

Best Regards...

Thanks.  I'm just switching the ATI X800GTO card with an Nvidia FX5200 card.  Both are old tech, AGP cards, but the faster ATI card would be better used in my media center type XP box.  Plus I have trouble with the ATI drivers and used to have much better luck with my old Nvidia setup.  I just wasn't sure if I could swap the cards and boot into Ubuntu or would I have to do a bunch of prep work.

---

### Post by ardvark71 on 2008-10-20
> **AceRimmer said:**
> Thanks.  I'm just switching the ATI X800GTO card with an Nvidia FX5200 card.  Both are old tech, AGP cards, but the faster ATI card would be better used in my media center type XP box.  Plus I have trouble with the ATI drivers and used to have much better luck with my old Nvidia setup.  I just wasn't sure if I could swap the cards and boot into Ubuntu or would I have to do a bunch of prep work.

Hi...

Ok, once you have the card installed, you *should* be able to go into Synaptic and download the driver. I believe it starts with the word "nvidia" but there will be two versions, the regular one and the one for "legacy" cards. Look at both entries (in the summary section) and see which version applies to your card. After Synaptic downloads and installs the driver, go into your xorg.conf file as root. In Ubuntu...

```
gksudo nautilus
```

I don't remember offhand what the command is in Kubuntu, but its different. :(

Now, when you scroll down to the entry that has your video card information, you should see a line that says something like:

Driver = "nv"

Something else may be between the quotations, its ok if there is. Change the "nv" to "nvidia" (be sure to keep the quotations) and save the changes. When you reboot you should be set to go! :) You will also see a momentary nvidia splashscreen during the time when Ubuntu boots.

This is probably the easiest way of taking care of the driver but if you have any questions or problems, post back and either I or someone else might be able to help.

Hope this helps... :)

Best Regards...

---

### Post by AceRimmer on 2008-10-20
Thanks for all the assistance!

---

### Post by ardvark71 on 2008-10-20
> **AceRimmer said:**
> Thanks for all the assistance!

Hi...

You're welcome, glad I could help! :)

Best Regards...

---

