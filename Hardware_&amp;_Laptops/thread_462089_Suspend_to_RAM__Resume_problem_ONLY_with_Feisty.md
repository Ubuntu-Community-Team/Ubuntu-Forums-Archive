---
title: "Suspend to RAM / Resume problem ONLY with Feisty"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by sorens on 2007-06-02
I am having the following problem with Feisty: when I resume from suspend to RAM, the screen remains black. The mouse is visible and moves, even changing from arrow to cursor depending on what's underneath. If I Ctl-Alt-Backspace, I will get the login screen, which I can see just fine and enter my username and password. But then the black screen shows up, and I'm back to where I started. I have to hard reboot to fix.

I have noticed that this is a well-reported bug on the forums, and has been attributed to an ACPI problem, I guess. However, I was running Edgy for quite some time without any suspend problems-- this only showed  up when I upgraded to Feisty. BTW, this is on a Dell Inspiron 500m.

---

### Post by Ken_Lewis81 on 2007-06-02
Check if the suspend and standby operations are correctly saving and restarting your graphics adapters properly; it may be that your graphics adapter fouls things up when you wake the computer because it's still asleep.

Look at /etc/default/acpi-support to see if the following three options are set right for your hardware:
```
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true
```

Hope this helps.
Take care.
Ken.

---

### Post by hiruzzolo on 2007-06-02
I have a similar problem that is caused by compiz (Desktop Effects)

---

### Post by endlesssnowfall on 2007-06-12
Same problem here.  The options in /etc/default/acpi-support are set correctly, but the problem still exists.  What's also weird is that it is sort of random when it occurs.  Sometimes resuming from standby works perfectly, sometimes, it doesn't.

---

### Post by endlesssnowfall on 2007-10-08
I've upgraded to Gutsy this past weekend, but the problem still exists, even with the new kernel.  How would I go about pinpointing the nature of the problem?

---

### Post by Linicks on 2007-10-08
When I read this post, I knew I read somewhere of a possible fix - I have just stumbled across it:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Suspend_followed_by_Hibernate_fails_with_binary_nvidia_drive](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Suspend_followed_by_Hibernate_fails_with_binary_nvidia_drive)

This may or may not solve it.

Nick

---

### Post by endlesssnowfall on 2007-10-10
I think I've fixed the problem, at least for my Thinkpad R50e running an Intel Extreme Graphics 2 (855GM).  I had to add this line to the "Device" section of /etc/X11/xorg.conf

```
Option        "VBERestore" "yes"
```

---

