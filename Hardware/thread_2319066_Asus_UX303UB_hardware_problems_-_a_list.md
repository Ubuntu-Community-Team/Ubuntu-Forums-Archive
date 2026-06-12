---
title: "Asus UX303UB hardware problems - a list"
date: 2016-03-31
forum: Hardware
---

### Post by akbrandt on 2016-03-31
I have just purchased an new Asus UX303UB ~3 wks ago. I removed the  preinstalled Windows 10 and replaced it with Kubuntu 15.10. The computer  is usable, all hardware basically works including keyboard backlight,  special keys handling for volume and brightness, webcam etc. However some pretty  annoying issues remain:

  
[LIST]
[*]**Sleep (suspend to memory) doesn't work** - it  doesn't work no matter if started with the power button, by closing the  lid or by selecting appropriate option from the menu, the result is  always the same - system boots fresh at the next power-on. 
[*]**Annoying issues with video playback** - no matter which player I use (VLC, Dragon etc.) if playing a video file with a local player app I have following problems:
[LIST=1]
[*]the video always plays at the file resolution - no scaling no  matter if I resize the window, go full screen or explicitly select  scaling from VLC menu the video size stays always the same 
[*]the video playback stays always on top of all windows as a  rectangle without borders etc. even if the player app is in the back or  minimized, to make it more funny mouse clicks in that rectangle affect  whatever is behind it, not the rectangle - if the player window is moved  the rectangle moves with it. 
[/LIST]
  Those two issues together make watching videos a pain. However,  strangely in-browser players like YT or Vimeo work as expected - full  size and scaling including, no problem with video being on top of  everything. *EDIT: In VLC this problem occurs with "XVideo Output  (XCB)" selected as well as on automatic settings, was able to get  desired behavior by selecting "OpenGL GLX" or "X11 Video output". Have  no idea how to switch this for other apps.* 
[*]When switching to **cable Ethernet connection** to Internet I have to manually run dhclient and resolvconf -u  - somehow it doesn't do it automatically when the adapter with the  cable is connected and doesn't set up the IP and DNS servers properly. 
[*]**Video in Skype unusable if camera is enabled** -  everything is fine with Skype as long as I don't enable my camera during  a video call. Once I do that the video of the other party starts to  flicker into blue - that is rapidly switches between the video and solid  blue. The video feed from my side works fine, but can't enable it  because then I am unable to look at the other party. 
[*]**Poor power management** - under Linux it doesn't  get more than 2 - 2.5hrs on battery doing general web browsing - and  this is a new machine, so the battery is also new. Under Windows 10 it runs twice as long without problems or visible performance degradation under same use. 
[/LIST]
  The final point is probably me not knowing enough about it, rather than an outright issue, however: I see **no way to use my laptop's NVidia GeForce GT 940m**.  When I did run NVidia Settings and selected the NVidia card the next  time my computer booted the X server startup ended with black screen. I  had to switch to one of text consoles and edit the xorg.conf back to  Intel to get it to work. No idea how to have the two video cards  cooperate and switch on the fly (which is I think the desired behavior).  I suspect my strange problems with the video playback are somehow  related to this, but I don't know how to resolve them. [I found this thread on NVidia's forums]("https://devtalk.nvidia.com/default/topic/919317/gpu-has-fallen-off-the-bus-on-linux-4-5-0-rc5-nvidia-361-on-a-optimus-notebook-/"), but also with people complaining about this problem with no solution posted so far. 


  I post this as a summary for UX303UB issues with a hope that  solutions will eventually be found - and that until then other UX303UB owners would  at least know this is not something that affects just them

---

### Post by akbrandt on 2016-04-06
To add to this list **screen brightness adjustment doesn't work**, at least not using function keys (key backlight & volume work).

---

### Post by shaan2 on 2016-06-09
Hi, there , I am also using asus ux303ub laptop, after little bit of experiment , I got the solution,   to solve **screen brightness adjustment** and keyboard backlight issue just add acpi_backlight=none acpi_osi= 
to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub and you are good to go.......

Your grub file will be like this....



# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=none acpi_osi="
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)

Dont forget to update grub after adding the kernel parameter, to do that
 
run command update-grub in terminal........



Hope it helps....

---

### Post by irfaniyusuf on 2016-11-09
Hay, the problem same with me. are you solved now ?

---

