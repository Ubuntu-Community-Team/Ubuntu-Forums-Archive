---
title: "Upgrade to 16.04 on Dell lattide 3550: monitor flickers, nvidia drivers crash"
date: 2016-04-30
forum: Hardware
---

### Post by konstant@mail.ntua.gr on 2016-04-30
I have recently upgraded my Dell Lattitude 3550 from Ubuntu 15.10 -> 16.04 (***).

I am using dual monitor and although it was running quite smoothly with 15.10 (default drivers), sometimes the screen flickers, or (part) of a window flickers (like part of a page on my chrome browser). Rarely, one of the two monitors becomes completely black for a few seconds and then it is back again. I have not tried using the laptop extensively without the second monitor attached. The monitor is connected via the VGA (LG LED 24M35).

I activated the top of the options for nvidia driver (labeled proprietary,tested) (*) from SystemSettings -> Software&Updates->Addl Drivers and the procedure was completed with no errors reported. I rebooted immediately, I got the login screen without error, but where I tried to login, the login failed: I simply got the login screen back. Then I followed the instructions in [http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics](http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics) 

and I managed to bring the system back to the original state (Xorg drivers) via: 
1. Ctrl-Alt-F2
2. logged on and then 
> sudo apt-get purge "nvidia-*"

but trying to install nvidia-364 gave me the option to alter the UEFI booting saying that the proprietary drivers are incompatible with UEFI and offered me the option to disable it, which I declined (**).

Therefore I am back with Xorg drivers and the occasional flickering of the screen.


(*) I cannot recall which version of nvidia driver it was since now the menu offers different choices (358 is first, 364 last)
(**) I had some problems with UEFI when fresh installing 15.10, so I did not want any adventures!
(***) everything else is great so far, I only had to spent some time with realizing that ssh does not accept dss keys anymore!

---

### Post by gnusci on 2016-05-01
Can you see the same issue if you run the 16.04 LiveCD?

---

### Post by konstant@mail.ntua.gr on 2016-05-09
I have not tried. But since booting from a usb caused me some problems ( see [http://ubuntuforums.org/showthread.php?t=2308119&p=13415249#post13415249](http://ubuntuforums.org/showthread.php?t=2308119&p=13415249#post13415249) ) I don't want to try. 

Thanks!

---

