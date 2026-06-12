---
title: "[32-bit] [HowTo] install Nvidia-96 driver"
date: 2012-05-15
forum: Hardware
---

### Post by airinuxazis on 2012-05-15
[FONT=Arial][COLOR=#333333]Hi[/COLOR][COLOR=#333333] all[/COLOR][COLOR=#333333]this time we will [/COLOR][COLOR=#333333]discuss [/COLOR][COLOR=#333333]how to install the[/COLOR][COLOR=#333333] nvidia[/COLOR][COLOR=#333333]-96[/COLOR][COLOR=#333333] in [/COLOR][COLOR=#333333]ubuntu [/COLOR][COLOR=#333333]Natty, Oneiric, Precise [/COLOR][COLOR=#333333]do the [/COLOR][COLOR=#333333]following[/COLOR][COLOR=#333333] steps[/COLOR][COLOR=#333333]:[/COLOR][/FONT]
[FONT=Arial][COLOR=#333333]
[/COLOR][/FONT]
[FONT=Arial][COLOR=#333333]1. Download the Driver:


[/COLOR][/FONT] [FONT=Arial][COLOR=#333333]
  [/COLOR][/FONT]Natty:                                                Oneiric:                                    Precise:
[FONT=Arial][SIZE=4][COLOR=#333333][Nvidia 96]("http://launchpadlibrarian.net/78046777/nvidia-96_96.43.20-0ubuntu1%7Enatty1_i386.deb")[/COLOR][/SIZE][/FONT]                  [SIZE=4][COLOR=#333333][FONT=Arial][Nvidia 96]("http://launchpadlibrarian.net/82496087/nvidia-96_96.43.20-0ubuntu6_i386.deb")    [/FONT][/COLOR][/SIZE]           [SIZE=4][nVidia 96]("http://launchpadlibrarian.net/82496087/nvidia-96_96.43.20-0ubuntu6_i386.deb")[/SIZE]
[FONT=Arial]
[/FONT]
[FONT=Arial][COLOR=Black]2[/COLOR][/FONT][FONT=Arial][COLOR=Black]. Open Terminal [/COLOR][/FONT][COLOR=Black]
[/COLOR] [FONT=Arial][COLOR=Black]3[/COLOR][/FONT][FONT=Arial][COLOR=Black].[/COLOR][/FONT][FONT=Arial][COLOR=Black]M[/COLOR][/FONT][COLOR=Black][FONT=arial]ove to where[/FONT][/COLOR][COLOR=Black][FONT=arial] you[/FONT][/COLOR][COLOR=Black][FONT=arial] downloaded [/FONT][/COLOR][COLOR=Black][FONT=arial]the file[/FONT]
[/COLOR]  [COLOR=Black][FONT=arial]4[/FONT][/COLOR][COLOR=Black][FONT=arial]. I[/FONT][/COLOR][COLOR=Black][FONT=arial]nstall the driver[/FONT][/COLOR][COLOR=Black][FONT=arial] using the following command[/FONT][/COLOR][COLOR=Black][FONT=arial]:[/FONT][/COLOR]
  [COLOR=#333333][FONT=arial]
[/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]sudo dpkg -i nvidia-96_96.43.20-0ubuntu1~natty1_i386.deb nvidia-glx-96_96.43.20-0ubuntu1~natty1_i386.deb [/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]
[/FONT][/COLOR]
  [COLOR=#333333][FONT=Arial]5[/FONT][/COLOR][COLOR=#333333][FONT=Arial]. [/FONT][/COLOR][FONT=Arial]Edit "/etc/default/grub":[/FONT]
  [COLOR=#333333][FONT=arial]
[/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]sudo nano /etc/default/grub[/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]
[/FONT][/COLOR]
  [COLOR=#333333][FONT=Arial]6[/FONT][/COLOR][COLOR=#333333][FONT=Arial].  [/FONT][/COLOR][FONT=Arial]Change this line:[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Courier New]GRUB_CMDLINE_LINUX=""[/FONT]
  [FONT=Courier New]
[/FONT]
  [FONT=Arial]To this :[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Courier New]GRUB_CMDLINE_LINUX="nopat"[/FONT]
  [FONT=Courier New]
[/FONT]
  [FONT=Arial]7. [/FONT][FONT=Arial]After saving changes to the file, update your GRUB configuration by typing the following into the command line:[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Courier New]sudo update-grub[/FONT]
  [FONT=Courier New]
[/FONT][COLOR=Black]
[/COLOR]   [FONT=Arial][COLOR=Black]8. Run the following command:[/COLOR][/FONT]
  [FONT=Arial][COLOR=#333333]
[/COLOR][/FONT]
  [COLOR=#333333][FONT=Courier New]sudo nvidia-xconfig[/FONT][/COLOR]
  [FONT=Arial][COLOR=#333333]
[/COLOR][/FONT]
  [FONT=Arial][COLOR=#333333]9. [/COLOR][/FONT][FONT=Arial]Edit xorg.conf[/FONT]
  [COLOR=#333333][FONT=arial]
[/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]sudo nano /etc/X11/xorg.conf[/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]
[/FONT][/COLOR]
    [COLOR=#333333][FONT=Arial]10. [/FONT][/COLOR][FONT=Arial]Add the following section:[/FONT]
 Section "Extensions"
Option         "Composite" "Enable"
EndSectionSection "Module"
Load           "extmod"
Load           "glx"
EndSection 
[COLOR=Black][FONT=Arial]11[/FONT][/COLOR][COLOR=Black][FONT=Arial].[/FONT][/COLOR][COLOR=Black][FONT=Arial]A[/FONT][/COLOR][COLOR=Black][FONT=arial]dd the [/FONT][/COLOR][COLOR=Black][FONT=arial]following lines[/FONT][/COLOR][COLOR=Black][FONT=arial](above the[/FONT][/COLOR][COLOR=Black][FONT=arial]"[/FONT][/COLOR][COLOR=Black][FONT=arial]EndSection[/FONT][/COLOR][COLOR=Black][FONT=arial]"[/FONT][/COLOR][COLOR=Black][FONT=arial]in the "[/FONT][/COLOR][COLOR=Black][FONT=arial]Section"[/FONT][/COLOR][COLOR=Black][FONT=arial]Monitor[/FONT][/COLOR][COLOR=Black][FONT=arial]"[/FONT][/COLOR][COLOR=Black][FONT=arial])[/FONT][/COLOR][COLOR=Black][FONT=arial]:[/FONT][/COLOR]
  [COLOR=#333333][FONT=arial]
[/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]    Option  "AddARGBGLXVisuals"  "True"[/FONT][/COLOR]
  [COLOR=#333333][FONT=Courier New]
[/FONT][/COLOR]
  [COLOR=#333333][FONT=Arial]12. [/FONT][/COLOR][COLOR=#333333][FONT=arial]Replace[/FONT][/COLOR][COLOR=#333333][FONT=arial] Depth[/FONT][/COLOR][COLOR=#333333][FONT=arial] in[/FONT][/COLOR][COLOR=#333333][FONT=arial]SubSection[/FONT][/COLOR][COLOR=#333333][FONT=arial]"[/FONT][/COLOR][COLOR=#333333][FONT=arial]Display[/FONT][/COLOR][COLOR=#333333][FONT=arial]"[/FONT][/COLOR][COLOR=#333333][FONT=arial]to 24[/FONT][/COLOR]
  [COLOR=#333333][FONT=arial]
[/FONT][/COLOR]
  
 [FONT=Courier New] [COLOR=#333333]    SubSection     "Display"[/COLOR][/FONT]
 [FONT=Courier New] [COLOR=#333333]        Depth       24[/COLOR][/FONT]
 [FONT=Courier New] [COLOR=#333333]    EndSubSection[/COLOR][/FONT]
 [FONT=Courier New] [COLOR=#333333]
[/COLOR][/FONT]
 [COLOR=#333333][FONT=Arial]13. [/FONT][FONT=arial]Change the[/FONT][FONT=arial] DefaultDepth[/FONT][FONT=arial] in[/FONT][FONT=arial]Section "[/FONT][FONT=arial]Screen[/FONT][FONT=arial]"[/FONT][FONT=arial]to 24[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]    DefaultDepth    24[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]14. Reboot[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Done![/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]With this Compiz and OpenGL became more gentle and stable. If there is a problem put it in Reply box.

Source : [/FONT][/COLOR][HTML]http://airinux.blogspot.com/2012/01/howto-install-nvidia-96-for-natty-intel.html[/HTML]

That is my Blog :)

---

