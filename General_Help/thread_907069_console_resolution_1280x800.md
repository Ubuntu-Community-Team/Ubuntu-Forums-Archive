---
title: "console resolution 1280x800"
date: 2008-09-01
forum: General Help
---

### Post by zeroed on 2008-09-01
Is it possible to setup console resolution to 1280x800? It's a native resolution for my laptop (dell inspiron 1501).

hwinfo --framebuffer does not return such a variant

---

### Post by robertyou on 2008-11-20
You can install startupmanager to do that.

However, there are only these resolutions provided:
640x480
800x400
1024x768
1280x1024
1600x1200

My laptop has wide screen 1280x800 as well, but those are the settings I see.

---

### Post by zeroed on 2008-11-20
> **robertyou said:**
> You can install startupmanager to do that.

However, there are only these resolutions provided:
640x480
800x400
1024x768
1280x1024
1600x1200

My laptop has wide screen 1280x800 as well, but those are the settings I see.

startup manager has killed my usplash.
i think the reason is that he couldn't set up my resolution.

so.. thanks, but.. =)

---

### Post by robertyou on 2008-11-20
did you run it as root?
Every time you make a change, it'll update your menu.lst.

If that's not the case, maybe try tweaking the setting for Usplash under "appearance" tab

btw, system needs to reboot to take effect of new settings

Edit:

Not sure what will happen if you select 1280x1024, it's obviously over your max screen resolution. 
I'm finding that 1024x768 is even too much for me (the text seems too small in console to me), think I'm sticking with 800x600 :)

---

### Post by zeroed on 2008-11-20
> **robertyou said:**
> did you run it as root?
Every time you make a change, it'll update your menu.lst.

If that's not the case, maybe try tweaking the setting for Usplash under "appearance" tab

btw, system needs to reboot to take effect of new settings

Edit:

Not sure what will happen if you select 1280x1024, it's obviously over your max screen resolution. 
I'm finding that 1024x768 is even too much for me (the text seems too small in console to me), think I'm sticking with 800x600 :)

I have no problems to set 1024x768 or 800x600 manually. I want 1280x800 =)

---

### Post by robertyou on 2008-11-20
hey, I did some research and see what I found.
[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/change_tty/splashscreen_resolution](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/change_tty/splashscreen_resolution)

I'm trying it now, will get back to you later if it works =D

---

### Post by robertyou on 2008-11-20
Before making any changes, be sure to back up these two files:

/boot/grub/menu.lst
/etc/usplash.conf

[LIST=1]
[*]Install hwinfo (if you haven't)
```
sudo apt-get install hwinfo
```

[*]Find out the kernel vga parameters that your hardware can provide
```
sudo hwinfo --vbe | grep -I "Mode"
```
  for example, this command gives me a list of modes supported on my system:
```

  Current VESA Mode: 0x0118
    Mode: 0x01 (Write Back)
    Mode: 0x01 (Write Back)
    Type: 0x1e (Modem Port)
  Model: "NVIDIA G86 Board - e416h01 "
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits

```
Now what you need is the set of number comes after "Mode" in the line which describes the setting you want to set.

For me, this is what I want to use:
Mode 0x0361: 1280x800 (+5120), 24 bits
"0x0361" is the key number there.


[*]Making change in menu.lst
```

gksu gedit /boot/grub/menu.lst

```
find this line in the file:
> 
# defoptions=quiet splash vga=792

Now substitute the Mode# we got in step 2 after "vga"
Mine would look like this after:
> 
# defoptions=quiet splash vga=0x0361


[*]**Remember, every time you change values in menu.lst, it's important to update grub after the changes are made.
```
sudo update-grub
```


[*]Now, this should give the resolution you want in console after reboot.
But if your usplash (Ubuntu loading screen with orange bar) is messed up, you probably need to set the right values in /etc/usplash.conf:
```
gksu gedit /etc/usplash
```

The content of usplash.conf looks like this:
> 
# Usplash configuration file
xres=1024
yres=768

You also need to update usplash.conf if changes are made every time:
```
sudo update-initramfs -u
```
**NOTE**
My usplash screen becomes disoriented if I set it's resolution to 1280x800
However, it appears to be just normal if I don't make any change and leave it as 1024x768 while my console is set to 1280x800.

But you can try to tweak the values if my method does not apply for you.
[/LIST]

*My distro is Ubuntu 8.10
*Reference page: [http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/change_tty/splashscreen_resolution](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/change_tty/splashscreen_resolution)

---

### Post by campbuds on 2008-11-21
1280x800 is what I need for my screen resolution also. The option is available to me, but when I try to use it a 1/3 of my screen goes fuzy and my desktop shrinks to almost fit in the viewable area (no fuzz)

a solution to this would be nice.

---

### Post by robertyou on 2008-11-21
> **campbuds said:**
> 1280x800 is what I need for my screen resolution also. The option is available to me, but when I try to use it a 1/3 of my screen goes fuzy and my desktop shrinks to almost fit in the viewable area (no fuzz)

a solution to this would be nice.

Sorry my last post is a bit messy, I just tidied it up (**POST #7**) so it's easier to follow.

Also, it seems startupmanager does not support wide screen resolution for console. Try making change manually like I did in my last post.

Hope this helps:)

---

