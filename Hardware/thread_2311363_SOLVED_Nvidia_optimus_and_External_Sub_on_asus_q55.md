---
title: "SOLVED Nvidia optimus and External Sub on asus q552 laptop"
date: 2016-01-26
forum: Hardware
---

### Post by Ben_Maddocks on 2016-01-26
My laptop is an Asus q552 (which also has other models #'s for same hardware will find and add) its running a 6th gen i7 dual core nvidia geforce 940m optimus and an integrated intel vga card.  Anyone who doesnt know allready optimus is the retarded idea of glueing a nice vga card like say an Nvidia and glueing onto an integrated intel card using bubblegum and ducktape all in the name of saving power. I dont care for usuing the integrated card so this howto wont show that. First after spending waaay to much time trying to get the 4.2 stock kernel in Wily (and also 4.3 custom) to work with just the Nvidia card this is what i found;
THE PROBLEM; in the beggining I could boot one in 7 times without it going to a black screen, everything was booted and working just couldnt see it. The tutorials I found didnt help but eventually I could boot something like 50/50 with newer kernels (IE 4.2 4.3) using a specific xorg.conf and %100 of the time on any 3.19 or 4.0 kernels. So theres a regression sumwhere.
Everything below was done on Wily with nvidia-352-updates nvidia-prime all from stock repos
The newer intel vga card driver needs to be specifically turned on for newer models either in kernel config or by adding;
i915.preliminary_hw_support=1
to /etc/default/grub  rerun "sudo update-grub2" after I also have the options;
prcutree.rcu_idle_gp_delay=1 i915.semaphores=1 intel_iommu=on acpi_osi=    (the prcutree keeps the nvidia card from falling off the bus no idea about the semaphores and acpi_osi fixes the brightness shortcut buttons)
Second the option in xorg.conf "#    Option "UseDisplayDevice" "None"" does not work at all on this setup!! in fact it hurts your chances. 
copy /sys/class/drm/card0-eDP-1/edid to firmware
sudo cp /sys/class/drm/card0-eDP-1/edid /lib/firmware/lg1080p   (your directory name starting with card might be different say /sys/class/drm/card1-eDP-1/edid just hafta look and my lcd is a lg 1080p hence name)
Then use this xorg.conf
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "sna"
    Option "TearFree"    "true"
    Option "Tiling"      "True"
    Option "SwapbuffersWait" "True"
#    Option "AccelMethod" "None"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
    Option "ModeValidation" "NoVirtualSizeCheck"
    Option "ConnectedMonitor" "eDP-1"
#    Option "CustomEDID" "eDP-1:/sys/class/drm/card0-eDP-1/edid"
    Option "CustomEDID" "eDP-1-0:/lib/firmware/lg1080p.edid"
    Option "CustomEDID" "eDP-1:/lib/firmware/lg1080p.edid"
    Option "IgnoreEDID" "false"
    Option "UseEDID" "true"
    Option "DPI" "96x96"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
#    Option "UseDisplayDevice" "None"
    SubSection "Display"
    Depth    24
    Virtual    1920 1080
    Modes   "1920x1080_60.00"
    EndSubSection
EndSection

again you might have to change eDP-1 to something else IE eDP-0, and ubuntu-drivers-common has a program used to help switch between intel and nvidia which will rewrite your xorg.conf so simply "sudo chattr +s /etc/X11/xorg.conf" whenever you need to edit or remove your xorg.conf just run "sudo chattr -s /etc/X11/xorg.conf" but always use +s when your done.

With this xorg.conf , using upstart (NOT SYSTEMD!) I could boot depending on the week %50 to %70 of the time without going to blackscreen. In hindsight the audioout had multiple hdmi outputs for audio (laptop only has 1 physical port) Im wondering if my internel screen was getting different output names on different boots. Will try "Screen 1 "nvidia" " sometime

Kernel 3.19 and 4.0 work perfect except Ubuntu's 3.19 has a backported i915 driver DO NOT USE IT!! it has a kernel depency that turns on low power subsystems and that makes the setup unstable at best. This setup and any of the newer kernels run the risk of having a hardlockup, after the forced shutdown something in the card is put into an unusable state that reboots wont fix (Removing power and battery probly fix it but my battery isnt consumer removable) So you need to boot into a kernel with the intel LPSS (low power sub systems) stuff enabled to fix it, no matter how many times you boot a perfectly working 3.19 or 4.0 it wont work till you use one that has LPSS this will fix it. So obviously my working kernels have the bare amount of LPSS stuff enabled. I will try an attach my current kernel config tho Im currently using liquorix sources so sum options mite be a little different. Linux kernel 4.0 gives me just under twice! the performance 3.19 does so thats what I use Tho I dont like the new cpufreq stuff in 4.0+ on intel i7 stuff. I think I covered most everything for optimus.

External Sub Woofer "SonicMaster" This model comes with an ext sub that uses sum super tiny headphone jack. The tools and process I used can be used on Laptops with internel subs as well. Most sites/howtos for getting laptop subs working only mention hdajackretask which is definately needed but also hda_analyzer [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)  and alsa_info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) are required, well ok hdajackretask and hda_analyzer are DEF needed. Basically hdajackretask let you look an unused pins on your hda sound card and enable them and tell them what to do, and one or several of these pins are connected and therefore needed by your subwoofer wether internal or external. hda_analyzer not only provides more/better information about each pin and how there connected making it easier to know which you need to work with but it also allows you to control volumes/mute accross several pins and audio mixers in your laptop. On my old hp beats special edition I had tried the correct settings in retask several times but it never worked because of muted volumes hda_analyzer could see and unmute. 
Ok first as root open hda_analyzer and hdajackretask. In hda_analyzer look for any pins that have clfe or bass in the title IE "Bass Speaker Playback Switch"  "CLFE Phantom Jack" etc and goto hdajackretask click "show unconnected pins" and "advanced override" then enable each of the pin numbers from analyzer (usually "line-out" or "Speaker" (mostly speaker) for device and usually "Center/LFE" for "Channel" will work) in hdajackretask. Then click "Install Boot Override" next reboot. As soon as you login start gnome-alsa-mixer look for any outputs that are muted or turned down and turn them up (hopefully will see clfe or bass devices) go into sound settings try both 2.0 and 2.1 speaker setups and test the speakers (after clicking a new speaker setup you have to restart gnome-alsa-mixer and check again. you have to every speaker change!) . If you dont hear anything open hda_analyzer look for muted channels between the sub related pins as soon as you unmute or slide up the slider try the speaker test again. IF it works! click "Exp" in bottom left pane in analyzer and click save, This will save a python script that unmutes and turnes up all settings you just changed. IF it DIDNT work then look for any "mono amps" that are not being used/enabled and enable them in retask. Also make sure that "OUT" is selected in analyzer for the pins, sometimes switching the output pin in upper right will make the difference also making changes to pins and there options will do it. Also switching pulseaudio versions or Ubuntu version will most likely require new/different firmware/python scripts with pretty much exact same settings as before.
IF YOU REQUIRED THE hda_analyzer python script, then give it setuid root "sudo chown root.root python-script-name.py && sudo chmod +s python-script-name.py" and add it to your startup apps in whatever gui you use... Or simply add its location to /etc/rc.local just before the line exit.

So there it is Nvidia card working fine, the shortcuts for brightness and external subwoofer working. If i find anything else Ill update

ps. new linux firmware is required for bluetooth and wifi to function correctly [http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/](http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/tree/)
Below is my xorg.conf  my kernel config and working jackretask firmware for the q552 asus laptop no hda_analyzer needed tho this firmware is my first go and not done being perfected. Speaker config 2.0 sounds better then 2.1 tho probly lack of LFE filtering but these SonicMasters have a 3 speaker wire connector going to laptop (4 seperate lines on connector) so not sure if there ment for just LFE if you have any problems getting it to work change 0x1b output pin name.
[ATTACH]266965[/ATTACH]
[ATTACH]266966[/ATTACH]
[ATTACH]266967[/ATTACH]

---

