---
title: "installing *ubuntu on a screen with 640x480 display"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by mercury80 on 2009-09-02
I have an old computer I want hock up to my TV. The TV has a VGA input and can ONLY take a resolution of 640x480. (and i don't have another screen to use temporarily) As soon as the installation comes to a certain point the resolution is changed to something bigger and I can't see the picture no more... Is there a workaround to this? I have tried Mythbuntu and Kubuntu. There is an option before the instalation "Safe Display option" or something like that, but I can still not keep it to 640x480? any suggestions?
the computer has a nVidia graphics card...
And it will not boot from USB

---

### Post by stlsaint on 2009-09-02
can you change the settings in ubuntu prior to hooking it up to the tv?

---

### Post by mercury80 on 2009-09-03
> **stlsaint said:**
> can you change the settings in ubuntu prior to hooking it up to the tv?

I don't have a screen for the computer... only the TV

---

### Post by overdrank on 2009-09-03
Hi and you can use the options under F4 for the resolution.

---

### Post by mercury80 on 2009-09-03
> **overdrank said:**
> Hi and you can use the options under F4 for the resolution.

Yes the options under F4 is available, but it didn't change the outcome. As I said, I tried the safe display option. but no luck...

---

### Post by mercury80 on 2009-09-07
is there a way to send a command during the installation to force the installation to stay at 640x480? or any other tricks...

---

### Post by mercury80 on 2009-09-08
I found a way to send a command during the installation; explained here: [BootOptions]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation")

Although when I add the line 'vga=785' I get a black-screen with what looks like a freezed  cursor (underscore; _), when i start the installation. After a while the whole screen goes crazy again, and i can only guess the resolution again is changed to something bigger then 640x480. I have tried Ubuntu (9.04), Kubuntu (9.04), Xubuntu (9.04) and Mythbuntu (8.04.01 & 9.04). Does none of them support 640x480? 

Ubuntu 8.04 should support it according to the [Bare Minimum requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements#Desktop%20installation").

So I expected Mythbuntu 8.04 to work, but alas! anyone?

---

### Post by rob-ward on 2009-09-08
I ran into a problem like this on a friend computer, I ended up using the alternative install cd and that worked.

Hope that helps

---

### Post by mercury80 on 2009-09-10
> **rob-ward said:**
> I ended up using the alternative install cd and that worked.

Hope that helps

Tnx... that did the trick! i was able to install the whole thing. but when i rebooted and gnome was starting i ended with the same problem. but by that time it was easy to go into recovery mode and and spesify the screen in use (in etc/X11/xorg.conf)...

anyone with the same problem, here's some help on how to change monitor resolution:
[http://ubuntuforums.org/showthread.php?t=269052]("http://ubuntuforums.org/showthread.php?t=269052")
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by rob-ward on 2009-09-10
Glad it worked out for you

---

