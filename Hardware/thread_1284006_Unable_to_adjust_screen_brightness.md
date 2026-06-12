---
title: "Unable to adjust screen brightness"
date: 2009-10-06
forum: Hardware
---

### Post by Shamess707 on 2009-10-06
I recently installed Ubuntu 9.04 (x64) on my gateway m-series laptop. Works great minus the fact that I can adjust the screen brightness. when using an applet or my keyboard, ubuntu shows that it is being adjusted, but the actually screen brightness is constant(100%). Besides the fact that it is killing my battery, my eyes dont really adjust well to it. I am new to linux and would appriciate any help.

Thanks

---

### Post by johny_ on 2009-10-06
What graphic card do you use? I'm sure each ATI and Nvidia have some configuration tools to set this, and hopefully save to the X server config so the changes are permament.

---

### Post by Shamess707 on 2009-10-06
My display adapter is "Mobile Intel(R) 4 Series Express Chipset Family"

---

### Post by Shamess707 on 2009-10-10
if I could even manage to change the default brightness that would be fine with me, I just want a dimmer display.

---

### Post by AppleBonker on 2009-10-10
Does smartdimmer work?  Try this in a terminal:

```
$ smartdimmer -d
```

Let us know if that does anything.

---

### Post by Shamess707 on 2009-10-10
nope I get the following 

"init_nvclock() failed!"

---

### Post by Shamess707 on 2009-10-14
I have tried reinstalling drivers and editing some menu.lst file and nothing has worked so far

---

### Post by Shamess707 on 2009-10-21
bump

---

### Post by j_a_c_k_s_o_n on 2009-10-22
That's too easy, just click on the following

System>Preferences>Power Management

there, you configure the display brightness on AC Power or on battery..
hope this help..:P

---

### Post by Shamess707 on 2009-10-22
> **j_a_c_k_s_o_n said:**
> That's too easy, just click on the following

System>Preferences>Power Management

there, you configure the display brightness on AC Power or on battery..
hope this help..:P


sorry I tried that one, no effect at all

---

### Post by Shamess707 on 2009-10-22
bump

---

### Post by Shamess707 on 2009-10-22
bump...again

---

### Post by AppleBonker on 2009-10-22
What is in your /proc/acpi/video directory?  There should be a brightness file in there somewhere I think.  It was my mistake on suggesting smartdimmer as that is for use with GeForce cards and you don't have one.  I think you would then need to chmod the brightness file to make it executable and then do the following:

```
sudo brightness 10
```

which would set the brightness level to 10.  I hope I'm remembering this correctly.

---

### Post by Shamess707 on 2009-10-22
```
chasen@Shadow-II:~$ cd /proc/acpi/video/
chasen@Shadow-II:/proc/acpi/video$ ls
GFX0
chasen@Shadow-II:/proc/acpi/video$ cd GFX0/
chasen@Shadow-II:/proc/acpi/video/GFX0$ ls
DD01  DD02  DD03  DD04  DD05  DOS  info  POST  POST_info  ROM
chasen@Shadow-II:/proc/acpi/video/GFX0$ 
```


each of those DD0 directories have a brightness file, they are all blank except for the one in DD03. Changing this file has no effect on my brightness.

---

### Post by Delvien on 2009-10-23
> **Shamess707 said:**
> ```
chasen@Shadow-II:~$ cd /proc/acpi/video/
chasen@Shadow-II:/proc/acpi/video$ ls
GFX0
chasen@Shadow-II:/proc/acpi/video$ cd GFX0/
chasen@Shadow-II:/proc/acpi/video/GFX0$ ls
DD01  DD02  DD03  DD04  DD05  DOS  info  POST  POST_info  ROM
chasen@Shadow-II:/proc/acpi/video/GFX0$ 
```


each of those DD0 directories have a brightness file, they are all blank except for the one in DD03. Changing this file has no effect on my brightness.

I have the SAME problem.

---

### Post by Shamess707 on 2009-10-23
> **Delvien said:**
> I have the SAME problem.

Yay...im not alone lol

---

### Post by Delvien on 2009-10-24
I created my own thread before I even saw this one.

[http://ubuntuforums.org/showthread.php?t=1298055](http://ubuntuforums.org/showthread.php?t=1298055)

---

### Post by Shamess707 on 2009-10-27
bump

---

