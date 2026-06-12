---
title: "Nvidia 8400 GS with Ubuntu 11.04 not activating?"
date: 2011-07-18
forum: Hardware
---

### Post by seandd29851 on 2011-07-18
I've been trying to get the 8400 GS to activate and work I've tried going into Additional Drivers and selecting the recommended setting. I've tried going to the xconfig but I'm too dumb for that. Since I first tried to get my video card to enable I restarted the computer and booted back up and it went to the root terminal with the message "Ubuntu 11.04 tty1" I've looked it up, had something to do with hardware functionality. So I booted up into low graphics and it showed the GUI. I've thought about reinstalling Ubuntu 10.10 but that'll just wasted another 10 minutes on the 2 hrs I've put trying to figure it out on my own. Is there any suggestions as to how I can activate this graphics card without having to downgrade Ubuntu? Oh and in Additional Drivers, the recommended is activated but currently not in use? Any help is much appreciated, thanks.

---

### Post by s3MA00RRNY on 2011-07-18
When all else fails, download one of these:

X86
[http://www.nvidia.com/object/linux-display-ia32-275.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-275.19-driver.html)

X64
[http://www.nvidia.com/object/linux-display-amd64-275.19-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.19-driver.html)


[LIST=1]
[*]After downloading, press Ctrl + Alt + F1 to switch to a terminal.
[*]Log in.
[*]Type "sudo killall gdm"
[*]Navigate to the folder you saved the file to (using the cd command)
[*]type sudo sh <name_of_nvidia_file.run>
[*]Follow the instructions. You may have to run it a second time if it says nouveau is running...
[/LIST]
Hope that helps.

---

