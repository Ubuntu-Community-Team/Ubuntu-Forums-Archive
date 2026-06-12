---
title: "Lenovo IdeaPad 5 PRO 16IHU6 - works like a charm"
date: 2024-01-07
forum: Hardware
---

### Post by Rudolf_Fischer on 2024-01-07
I have just spent a few hours installing Ubuntu on my Lenovo IdeaPad 5 PRO 16IHU6. 
First I tried 22.04 LTS which did not work well at all, During the install process the screen flickered and whenever I moved the mouse to control a dialogue box, the screen went blank.
Using 23.10.1 instead of 22.04 LTS solved all of these issues. The clean install (erasing the SSD during the install process) worked seamlessly. Some things work that I did not expect to
[LIST]
[*]Keyboard backlight toggle via Fn-Spacebar
[*]Launching an app with the dedicated Nvidia MX450 graphics card
[/LIST]
I did notice a few error messages during boot and resume. Will take photographs and add these.

[[img]https://i.postimg.cc/F1qwgtb5/Screenshot-2024-01-07-152226.png[/img]](https://postimg.cc/F1qwgtb5)


[[img]https://i.postimg.cc/MfcN2tSF/Screenshot-2024-01-07-152252.png[/img]](https://postimg.cc/MfcN2tSF)


[[img]https://i.postimg.cc/c66Vn1nB/Screenshot-2024-01-07-152506.png[/img]](https://postimg.cc/c66Vn1nB)

How might I get rid of these messages?

---

### Post by oldfred on 2024-01-07
Most ACPI errors do not matter.
"Clean" on a partition is just telling you that you have no issues.

But Google "ucsi_acpi ppm init failed" found older threads with issue.

Did you install nVidia driver as part of install selecting optional restricted drivers?
If not did you install nVidia driver?
#What is installed
dkms status
If nothing shown, then not installed.

[https://ubuntu.com/server/docs/nvidia-drivers-installation](https://ubuntu.com/server/docs/nvidia-drivers-installation)
If incorrect one installed, you need to purge first. Never install nVidia from nVidia, just from Ubuntu repository.

# list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

---

