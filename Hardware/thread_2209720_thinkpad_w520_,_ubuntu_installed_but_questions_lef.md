---
title: "thinkpad w520 , ubuntu installed but questions left in mind"
date: 2014-03-07
forum: Hardware
---

### Post by lalamax3d on 2014-03-07
**PREVIOUSLY**
i have lenovo thinkpad w520. plus i had removed dvd rom and add ssd disk here. so ssd is hdd1 in bios. it has two vga cards ( intel and nvidia quadro 1000M)
i heard, configuring linux specially vga on linux is always issue. i searched. lot of thread / blogs. generally i was following this [http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/](http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/)
until i reached at step 3 and stuck ( reason after sample instructions )


```
sudo apt-get build-dep xserver-xorg-video-intel
sudo apt-get source xserver-xorg-video-intel
cd xserver-xorg...  #(the source you just downloaded, tab to autocomplete)
wget https://raw.github.com/liskin/patches/master/hacks/xserver-xorg-video-intel-2.18.0_virtual_crtc.patch
patch -p1 < xserver-xorg-video-intel-2.18.0_virtual_crtc.patch
sudo dpkg-buildpackage -b
cd ..
sudo dpkg --install xserver-xorg-video-intel_2.17.0-1ubuntu4_amd64.deb  #(again, tab to autocomplete will let you avoid typing this long name)

```


[LIST]
[*]first two commands from above , worked fine. but line 3, doesn't autocomplete
[*]i can see, i am at my home location. and i can't see any file here. plus i have no idea, where source packages downloaded to. etc
[*]but any ways, ubuntu is installed and working fine.
[/LIST]




**SCARED OF**
based on few years back experience on linux (ubuntu / fedora)
i always feel that just after downloading drivers (nvidia) , going to nvidia-settings and changing xconfig and restart is most brutal step of life. because if it won't work(some error in conf), then black screen(terminal) appears after reboot in full screen. i don't know at this very moment, how to revert back. how to backup before, how to retreive backup now . all i know is , everything is lost, i have to re-install and i hate this.




**STATUS | ATTEMPTS**


so this time, i thought, i should become slightly more decent / brave / organized
i must know, how many vga cards, ubuntu detected, which one its currently using and does it have drivers for both. are they working etc. so 



[LIST]
[*]first command for me is **lspci **, log is below
[/LIST]
```
lala@lala-ThinkPad-W520:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [Quadro 1000M] (rev ff)
lala@lala-ThinkPad-W520:~$

```
[LIST]
[*]second command for me is **glxinfo**, log is below
[/LIST]
```
lala@lala-ThinkPad-W520:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
lala@lala-ThinkPad-W520:~$

```

i can see, its using intel and not nvidia right now.
can someone suggest best way to proceed from here. all i wanted is



[LIST]
[*]at-least nvidia is working. not dying for second display monitor.
[*]are bumblebee drivers are installed?
[*]how to enable them, safetly.
[*]are these best to use. are there other drivers etc.  is this recommended approach
[/LIST]

---

### Post by Bashing-om on 2014-03-07
lalamax3d; Hi !

Here is the situation.
Your 1000M is an Intel/Nvidia hybrid card, -as you know - and it is not officially supported by Nvidia. See this link here for installing the drivers: Switchable laptop graphics issues on Ubuntu 12.04?
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)

There is the BumbleBee project :
[https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee) <- updated:2014-01-24 22:11:56
Versions 13.10/14.04 may be better to use Nvidia-prime.

Nvidia-Prime:
USING NVIDIA GRAPHICS DRIVERS WITH INITIAL OPTIMUS SUPPORT IN UBUNTU 13.10 GOT EASIER WITH NVIDIA-PRIME ->
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Open Source:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)


-----------
Not much direct help, but
[INDENT][INDENT]pass'n on what I have picked up
[/INDENT][/INDENT]

---

