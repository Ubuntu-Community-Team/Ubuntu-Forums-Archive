---
title: "Intel HD displayed rather than RadeonHD"
date: 2012-07-30
forum: Hardware
---

### Post by blasmat on 2012-07-30
My Lenovo G770 has Intel HD 3000 and ATI RadeonHD 6650 hybrid graphics - runing lspci in a terminal shows both cards.  I just performed a clean installation of Precise, and although I have been using the ATI Catalyst driver up until now, this time I have not installed ANY proprietary or open source drivers for the RadeonHD.  

My confusion comes from the following: If I select "UMA Graphics" in the BIOS, I get no 3D functionality (reverts to Unity 2D or Gnome-Fallback). If I select "Switchable Graphics" in the BIOS, I have full 3D functionality (actually smoother and less buggy than with the Catalyst driver), but System Settings-->Details-->Graphics Information still displays that the Intel card is being used.

Am I incorrect in thinking that UMA graphics refers to the integrated Intel graphics, or is Graphics Information simply displaying the wrong card for some reason?

---

### Post by NikTh on 2012-07-30
> **blasmat said:**
> My Lenovo G770 has Intel HD 3000 and ATI RadeonHD 6650 hybrid graphics - runing lspci in a terminal shows both cards.  I just performed a clean installation of Precise, and although I have been using the ATI Catalyst driver up until now, this time I have not installed ANY proprietary or open source drivers for the RadeonHD.  

My confusion comes from the following: If I select "UMA Graphics" in the BIOS, I get no 3D functionality (reverts to Unity 2D or Gnome-Fallback). If I select "Switchable Graphics" in the BIOS, I have full 3D functionality (actually smoother and less buggy than with the Catalyst driver), but System Settings-->Details-->Graphics Information still displays that the Intel card is being used.

Am I incorrect in thinking that UMA graphics refers to the integrated Intel graphics, or is Graphics Information simply displaying the wrong card for some reason?

Hi , 
first of all take a look --> [http://ubuntuforums.org/showthread.php?t=1930450/](http://ubuntuforums.org/showthread.php?t=1930450/) , maybe this will help you to use Hybrid Graphics correct.

You did all well and you understood all well. 
I agree with you with > is Graphics Information simply displaying the wrong card for some reason this is possible. 

If you want to see what card is be used then open a terminal and give this command
```

/usr/lib/nux/unity_support_test -p
``` 



I think you will see the results and understand. 

But I don't understand why you have problem with Intel HD ? I have intel HD only , and no problem with Unity 3D. 



Can you post the output of ```
lspci -nnk | grep -iA2 vga
``` 



Thanks

---

### Post by blasmat on 2012-07-31
Hi NikTh, thanks for responding!

> **NikTh said:**
>  
first of all take a look --> [http://ubuntuforums.org/showthread.php?t=1930450/](http://ubuntuforums.org/showthread.php?t=1930450/) , maybe this will help you to use Hybrid Graphics correct.


I have actually followed the directions on this site to enable switchable graphics with the proprietary AMD Catalyst driver on this laptop in prior installations, but I just performed a fresh installation and was hoping to avoid using the Catalyst driver this time around because it was a bit buggy and had a tendency to slow my system down considerably.

> **NikTh said:**
>  
But I don't understand why you have problem with Intel HD ? I have intel HD only , and no problem with Unity 3D. 


Well this is strange... when I set the BIOS to UMA Graphics a few days ago I had no 3D functionality, but when I tried again yesterday it functioned just fine. Something else must have been interfering with my prior attempts, though nothing immediately comes to mind as a possibility. Regardless, given that I have the RadeonHD card available, it seems a shame not to use it, particularly since I do a bit of 3D gaming and photo/video editing.

> **NikTh said:**
>  
If you want to see what card is be used then open a terminal and give this command
```

/usr/lib/nux/unity_support_test -p
``` 


The command above returns the following, regardless of whether the BIOS are set to Switchable Graphics or UMA Graphics:

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile
OpenGL version string:  3.0 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


> **NikTh said:**
> 
Can you post the output of ```
lspci -nnk | grep -iA2 vga
``` 


The output of the above command is as follows:

**When UMA Graphics is selected:**
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: i915

**When Switchable Graphics is selected:**
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Lenovo Device [17aa:3976]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series] [1002:6741]
    Subsystem: Lenovo Device [17aa:3976]
    Kernel driver in use: radeon


So it seems that setting the BIOS to Switchable Graphics results in powering *both* cards simultaneously while apparently only actually *utilizing* the integrated card. The extra power usage is significant, decreasing my battery life by at least 3 hours.

Would it be feasible to use only the RadeonHD by simply blacklisting the i915 kernel driver by creating an appropriate .conf file in /etc/modprobe.d? I have never really attempted to directly modify kernel behavior before, so I am a bit hesitant to do so for fear that it might have unforeseen consequences, but it seems like a sensible thing to try.

Thanks again for your assistance!

---

### Post by QIII on 2012-07-31
The driver is not buggy in a pure ATI or ATI/ATI hybrid situation.

Unfortunately, the Intel/ATI hybrid graphics setup is problematic for many Linux users.

Although you won't get all the benefits of the ATI driver, the open source Radeon driver is really very good.

If you use that, then you should be able to get a workable switching solution using vga_switcheroo in most cases.  No guarantees, of course.

---

### Post by NikTh on 2012-08-02
Hi , 
It seems that either enable or disable UMA , Ubuntu (Linux Kernel ultimately) wants to use the Intel card. 
This leaps from command results . (Unity support) 

You can try what @QIII suggests , because I don't know any other option for Hybrid Intel/Ati functionality. 

Thanks

---

### Post by blasmat on 2012-08-03
QIII, thanks for throwing your two cents in!  I have been curious about the possibility of vga_switcheroo, but was hesitant to experiment with it for fear of breaking my current installation.  Sounds like it might be prudent to just perform a fresh installation on an external drive and use it for experimenting.

Thank you both for your assistance!

---

### Post by NikTh on 2012-08-03
Hi , 
Of course a new install on external HD its easier, but in case you want to learn new things...
...you can use chroot instead fresh installation. 

Take a look here --> [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Thanks

---

