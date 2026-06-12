---
title: "HP Zbook G4 and Integrated Graphics problem on Ubuntu 18.04"
date: 2018-09-18
forum: Hardware
---

### Post by adunatioastralis on 2018-09-18
Hey y'all, 

I'm moderately new to Linux and have found myself in a fix: 
[B]
Background[/B]
Took me a couple of hours of toil I finally got Ubuntu working on my **Zbook G4** (initially both the installation program and Live CD would freeze randomly). 

Getting past this involved a number of BIOS tweaks that I saw suggested in other threads, namely:
[LIST=1]
[*]Switching secure boot off and enabling legacy boot. 
[*]Unchecking Enable MS UEFI CA key*.* 
[*]Switching the graphics mode from auto to discrete. 
[/LIST]

I then allowed the installer to automatically download drivers from the internet.
[B]
Problem[/B]

I'm now stuck using the discrete Quadro graphics as Ubuntu freezes after the login screen if I switch the graphics mode back to either auto or hybrid (this in spite of currently using the open source driver). This is undesirable since a) I'd like to save battery on a laptop and, b) I have no need for Quadro graphics on Ubuntu as I don;t use it for anything graphically intensive.

I'm wondering what I can try to do to reverse the situation. I would much rather have Intel graphics enabled and the Quadro disabled, but I need the hybrid/auto option enabled for Windows.

Any help would be greatly appreciated.

**EDIT: I solved the issue by inputting the following string into the grub configuration file: "[FONT=gotham]pcie_port_pm=off acpi_osi=Linux acpi_rev_override=5". :D Clearly some kind of power management issue, although I don't entirely understand it. Since, this thread is quite prevalent in Google search results might be worth someone explaining it.[/FONT]**

---

### Post by markackerman8@gmail.com on 2018-09-24
adunatioastralis

I have just bought an AWESOME Omen X 17-ap0xx, and Hp has a lot of proprietary craaaap in their drivers -added to Nvidia and Intel's making things difficult for newbies to say the least.

Sorry for blabbering ... but have you tried simply using the command(S) available to restart "X" for a frozen or troublesome screen.

The easiest is  "Alt+F2" for the "run" Command and type in "R" and "Enter" (R for restart X)
Also one can use TTY 1,2 & 3 to get out and back into "X"
There are a few other ways but these are my favourite and easiest Ones.

Plus I was having HDMI Sound issues which were solved, and after a reinstall the device was not recognised **AGAIN**, 

tHANKS TO YOUR SUGGESTION
"Getting past this involved a number of BIOS tweaks that I saw suggested in other threads, namely:

Switching secure boot off and enabling legacy boot.
Unchecking Enable MS UEFI CA key.
Switching the graphics mode from auto to discrete."

i REMEMBERED i HAD ENABLED FAST BOOT (STUPIDLY FOR UBUNTU) and TPM and something like your "Enable MS UEFI CA", and UEFI boot mode.  One of tyhese things killed my Sound Card (ONLY HDMI HDA), reverting all those brought it back ... thanks

THANKS!!  adunatioastralis

and Pray tell where in Ubuntu or Bios can you switch Graphics From Hybrid or Auto to Discrete.

Trying to help, Mark

---

### Post by markackerman8@gmail.com on 2018-09-24
adunatioastralis

I have just bought an AWESOME Omen X 17-ap0xx, and Hp has a lot of proprietary craaaap in their drivers -added to Nvidia and Intel's making things difficult for newbies to say the least.

Sorry for blabbering ... but have you tried simply using the command(S) available to restart "X" for a frozen or troublesome screen.

The easiest is  "Alt+F2" for the "run" Command and type in "R" and "Enter" (R for restart X)
Also one can use TTY 1,2 & 3 to get out and back into "X"
There are a few other ways but these are my favourite and easiest Ones.

Plus I was having HDMI Sound issues which were solved, and after a reinstall the device was not recognised **AGAIN**, 

tHANKS TO YOUR SUGGESTION
"Getting past this involved a number of BIOS tweaks that I saw suggested in other threads, namely:

Switching secure boot off and enabling legacy boot.
Unchecking Enable MS UEFI CA key.
Switching the graphics mode from auto to discrete."

i REMEMBERED i HAD ENABLED FAST BOOT (STUPIDLY FOR UBUNTU) and TPM and something like your "Enable MS UEFI CA", and UEFI boot mode.  One of tyhese things killed my Sound Card (ONLY HDMI HDA), reverting all those brought it back ... thanks

THANKS!!  adunatioastralis

and Pray tell where in Ubuntu or Bios can you switch Graphics From Hybrid or Auto to Discrete.

Trying to help, Mark

---

### Post by zebulon-severson on 2018-10-28
Hey [**[COLOR=#000000]adunatioastralis[/COLOR]**]("https://ubuntuforums.org/member.php?u=2107172"), any chance you had a subwoofer issue with your laptop? I have the almost same HW as you it looks like and mine is not working and I was curious if you fixed that issue if it wasn't working on your end.

---

### Post by markackerman8@gmail.com on 2018-10-29
Here are my Tomboy - AWESOME Tool, Notes for all my NVHDA Sound Fixes and Hibernating/Suspend Workarounds, and ACPI Error Fix (not needed Anymore) ;)

Just trying to help, Mark

Problems SOLVED! I
&#8728; Hibernate/Suspend
• However, if I manually disable the audio output output "sudo tee /proc/acpi/nvhda <<< OFF" I'm then able to get it to sleep. I then have to turn it on again on resume with "sudo tee /proc/acpi/nvhda <<< ON
• $ sudo tee /proc/acpi/nvhda <<< OFF          (before Hibernation/Suspend or Sleep)
• $ sudo tee /proc/acpi/nvhda <<< ON            (After Resume)
• SOLVED! I

&#8728; Ubuntu 18.04 changes sound device after suspend, how to fix?
• $ pulseaudio --kill 
&#8227; DOES NOT WORK in 18.10!


• $ pacmd list-cards
•  $ sudo lspci -H1  (When Dirver IS installed properly)
&#8227; 01:00.0 VGA compatible controller: NVIDIA Corporation GP104M [GeForce GTX 1080 Mobile] (rev a1)
&#8227; 01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)

• Solution -  Install a Kernel module to toggle audio function.
&#8728; I can confirm that kernel module, posted by 
&#8227; Maik Freudenberg ([https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27](https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27)),
• Kernel module to toggle audio function
&#8728;  is working fine on my system. Thank you for the fix. The HDMI audio device now works as it should (now detected).
&#8728; The steps I did to enable HDMI audio device:
• 1. Download and extract the file nvhda.tar.xz.  (from above link)
• 2. Run these commands in Terminal,  in the location of the extracted folder 
• $ make
• $ sudo make install
• $ echo nvhda | sudo tee -a /etc/initramfs-tools/modules
• $ echo "options nvhda load_state=1" | sudo tee /etc/modprobe.d/nvhda.conf
• $ sudo update-initramfs -u 
&#8227; 3. Reboot.
#############################################################################
ACPI  (Advance Configuration and Power Interface)
&#8227; ACPI fix for notebooks (4)
&#8728; Error:   ACPI:3400 Unsupported Event

&#8227; Here is a surprisingly simple solution that solved both problems (fast startup and normal background)
&#8227; Try disabling acpi in /etc/default/grub change this variable so it looks like this:
• sudo gedit /etc/default/grub 
&#8227;  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=strict",

• Just add acpi=off  (caused problems), "acpi=strict" Did NOT cause these problems
• (used for acpi INT34000 Errors but resulted in 800x600 resolution PROBLEM)
• Make sure to
&#8728; sudo update-grub2, after modifying the file and before rebooting
• and reboot - problems solved :D

---

### Post by adunatioastralis on 2018-12-13
Hi all, after retiring the laptop for a while, I finally came back to it and managed to solve the issue by applying "[FONT=gotham]pcie_port_pm=off acpi_osi=Linux acpi_rev_override=5" in the grub settings [IMG]https://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG]  I also found that applying 'acpi_osi=! acpi_osi="Windows 2009"' allowed  me to log into Ubuntu without issues, but this appeared to disable the  Intel graphics and caused battery life to plummet.[/FONT] Might give acpi=strict a try later just to see what kind of effect it has.

EDIT: double-post, how do I delete this?

---

### Post by adunatioastralis on 2018-12-13
Hi all, after retiring the laptop for a while, I finally came back to it and managed to solve the issue by applying "[FONT=gotham]pcie_port_pm=off acpi_osi=Linux acpi_rev_override=5" in the etc/default/grub! :D I also found that applying 'acpi_osi=! acpi_osi="Windows 2009"' allowed me to log into Ubuntu without issues, but this appeared to pretty much disable the Intel graphics and caused battery life to plummet.[/FONT] Might give acpi=strict a try later just to see what kind of effect it has @[**[COLOR=#000000]markackerman8@gmail.com[/COLOR]**]("https://ubuntuforums.org/member.php?u=621616")

**[[B][COLOR=#000000]@zebulon-severson[/COLOR]**]("https://ubuntuforums.org/member.php?u=2110486") [/B]Unfortunately, I haven't experienced anything of the like (my laptop doesn't have a subwoofer).

I am having a further issue now in that my laptop's Nvidia GPU does not appear to be fully powered down when not in use, which is still reflecting in battery life. I can confirm this using [FONT=gotham]cat /proc/acpi/bbswitch or the Prime Indicator Plus GUI.

Does anyone know what might be done to fix this?
[/FONT]

---

