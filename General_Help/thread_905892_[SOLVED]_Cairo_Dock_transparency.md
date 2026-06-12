---
title: "[SOLVED] Cairo Dock transparency"
date: 2008-08-30
forum: General Help
---

### Post by Arcnsparc on 2008-08-30
Ive customized an account on my computer for my [mac friends like this]("http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23") but I couldnt get the avant dock working so I tried the cairo one instead.  I can't get the blasted thing to be transparent, it keeps making big  black boxes behind its movements.  Is there a special layer, compiz setting or something like that I have to adjust to get it to render correctly?  Thanks

---

### Post by Upochapo on 2008-08-30
With the Cairo dock, as far as I can tell, if there is a black box surrounding the docker, that means the compositing is not turned on.  I'd go to System>Preferences>Appearance and go to the last tab Visual Effects.  There you can turn on compositing by selecting either Normal or Extra.

You can also install Compiz Fusion Icon which will place it under System Tools in your applications menu and you can select your compositors and decorations from that.  When u load the CFI, it will put an icon on your taskbar.

Also, should make sure that the proprietary drivers are installed for the video card.  I know there is EnvyNG,but I play it safe and just use the ones in the Ubuntu Repositories.

Also, if you did start AWN, more than likely it really HAS started but AWN requires the extra goodies to be turned on.  You just can't see it due to this.

---

### Post by Arcnsparc on 2008-08-30
Ok I kinda have this figured out.  I cannot enable the good visual effects because according to 'glxinfo' I am not direct rendering, BUT that is on another user on the this computer.  On MY account 'glxinfo' returns that I AM direct rendering...  Anyone with any ideas?

---

### Post by cimness on 2008-09-16
I installed Cairo, thinking that I had Compiz set up, only to discover it wasn't working. I then installed the Compiz manager and installed the Compiz package through it, but Cairo still isn't displaying on a transparent background. According to the manager extra effects are turned on. Is there a setting in Cairo to make it detect Compiz and adjust its behaviour or something?

---

### Post by northern lights on 2008-09-16
Please post the output of ```
sudo lshw -C display
```We'll take it from there.

---

### Post by Arcnsparc on 2008-09-16
*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


Thanks!

---

### Post by northern lights on 2008-09-16
There's no driver assigned to your graphics device, which results in Ubuntu using a fallback driver which cannot handle 3D acceleration.

Install 'xserver-xorg-video-intel', i.e. run

```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

then restart the session (reboot/log-out/'Ctrl+Alt+Backspace').

If compiz still fails, run it from the terminal```
compiz --replace
```save the output and that of ```
sudo lshw -C display
``` also. Then run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Should compiz still fail, get the two outputs once more, and paste both versions in here. Let's hope that won't be necessary, though.

---

### Post by Arcnsparc on 2008-09-17
Oddly enough I got this:

jake@MultiVAC-2:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.

However, im giving up on the cairo dock :P and marking this thread solved, but cimness may need some more help with the issue.  THANKS

---

### Post by netlaptop on 2009-05-20
I am really crazy about my laptop, Dell Studio 1535 preinstalled Window Vista Premium 64 bits. 

I could not install Ubuntu 8.10 due to "the white screen" error. Then I have been waiting for Ubuntu 9.04 for months. 

I have just installed successfully :D Ubuntu 9.04. And I  also customized my computer for my mac friends like Arcnsparc. 

I also got the same ugly black Cairo-dock background. After tried to config Cairo-dock for hours now I am really tired. Anyone please tell me something about my graphic drivers? Should I install 'xserver-xorg-video-intel', i.e. like the above post.

Thank you veryyy much!


> sudo lshw -C display

Here is my result

>   *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


---

### Post by v1nsai on 2009-11-17
I'm having problems with this too.  lshw -C display seems to indicate that neither of my displays are claimed either.  I tried sudo apt-get install xserver-xorg-video-intel but was told it was already installed, and reconfiguring dpkg did nothing either.  Here's the output of lshw, would really like a hand :-D

```
*-display:0 UNCLAIMED                                                                                                               
       description: VGA compatible controller                                                                                         
       product: Mobile 4 Series Chipset Integrated Graphics Controller                                                                
       vendor: Intel Corporation                                                                                                      
       physical id: 2                                                                                                                 
       bus info: pci@0000:00:02.0                                                                                                     
       version: 07                                                                                                                    
       width: 64 bits                                                                                                                 
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```

---

### Post by v1nsai on 2009-11-23
I just got done going in circles on Intel's website trying to find drivers for Mobile Intel 4 Series, I was only able to find the mobile gm45/gl40/gs45 driver.  I'm gonna try it later.  I'm not too happy with Intel right now, their site was very confusing and after clicking on 'Mobile Intel 4 series' a few times, it suddenly disappeared.  I downloaded the one I downloaded because it was a mobile driver that had 4's in the name....kind of a long shot but I can't imagine any other reason why it would just suddenly.

---

### Post by v1nsai on 2009-12-06
Bumping in the hopes of a solution, I haven't been able to provide one for myself so far.....

---

### Post by yossell on 2009-12-06
As this thread is marked 'solved' you might do better to start a new one - people who can help could be disregarding this thread because they think it's complete.

---

