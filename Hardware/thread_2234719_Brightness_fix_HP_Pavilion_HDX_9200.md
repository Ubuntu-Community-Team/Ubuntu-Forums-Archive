---
title: "Brightness fix HP Pavilion HDX 9200"
date: 2014-07-16
forum: Hardware
---

### Post by Looking4MyAnswers on 2014-07-16
This worked for me, maybe it could help someone...

I cannot guarantee this is ok for you. Because THIS COULD HARM YOUR UBUNTU OPERATING SYSTEM, BEFORE PROCEEDING, please BACK UP ALL YOUR DATA AND BE READY TO REINSTALL YOUR SYSTEM in case you cannot reverse the following  procedure. 

My laptop is a HP Pavilion HDX9200 kernel 3.8.0-42-generic. I don't how long it will last, it is overheating all the time...

I removed all the nvidia components which were interfering with the screen controls. It is possible to get the list of the packages removed in synaptic by listing all the installed package, searching for nvidia keyword. You want to do this in case you want to reinstall the nvidia packages because the current whole procedure is not working for you. 

I typed in a terminal:
  sudo apt-get purge nvidia*

Then reinstall xserver components:

  sudo apt-get remove xserver-xorg*

  sudo apt-get install acpi 
  sudo apt-get install acpi-support 
  sudo apt-get install acpitool
  sudo apt-get install hibernate
  sudo apt-get install gnome-power-manager

  sudo apt-get install xserver-xorg

Be sure to have swap partition where hibernate data is stored, to be the same in /etc/fstab as in /etc/initramfs-tools/conf.d/resume
Type:
  cat /etc/fstab | less
And check or edit swap UUID in the following file:
  gksu gedit /etc/initramfs-tools/conf.d/resume

Update changes:
  sudo update-initramfs -u

To get the brightness at the right intensity after login, I did this:

In a terminal, type:
  gksu gedit /etc/default/grub 

Then I added to at the line GRUB_CMDLINE_LINUX the below option before the last quote:

  acpi=strict nolapic


After saving, I update the changes to the system, running the command:
  sudo update-grub

You then need to do some tests by typing the next command below in a terminal, starting with a high X value such as 50. This is compulsory before going forward. Indeed a too low value will lead to a black screen, which means end of story...So the command to test is:
  sudo /usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness X

In file /etc/rc.local, to get right brightness at startup, add BEFORE line exit 0 the following:
  /usr/lib/gnome-settings-daemon/gsd-backlight-helper --set-brightness 3

For your information, 3 is a very low intensity but that's what I am looking for when I start up my laptop. 

Then reboot

In case you want to reverse the procedure, you select the recovery mode at startup in Grub menu...

---

