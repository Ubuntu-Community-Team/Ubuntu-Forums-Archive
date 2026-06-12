---
title: "ubuntu laptop screen fails after using external monitor"
date: 2018-05-21
forum: Hardware
---

### Post by scotc on 2018-05-21
Two of my laptops (Asus and HP) with 14.06 and 16.04 respectively have had this potentially serious problem.
It seems like a similar issue to [URL="https://ubuntuforums.org/showthread.php?t=2366965"]https://ubuntuforums.org/showthread.php?t=2366965
[/URL]

Problem: I use an external monitor on the laptop when at home.  I have found that if I simply suspend the laptop and unplug the VGA monitor, when I open the laptop again and resume (away from the house), the laptop screen is either lit black or not live at all.  Using the hardware keys (e.g. fn+F8) to toggle through the various monitor states (int+ ext, dual, int only etc) has no effect.  I cannot do anything but a hard shut down and reboot hoping that the display will be functional again upon reboot, which is usually is.
Sometimes I can tap the power button when in this 'black' state and hit return hoping / knowing that the "would you like to shutdown?" dialogue should be there, hidden, thus shutting the OS down properly.

Here's the REAL problem:  Twice in the last few months on my HP a forced shutdown has trashed my filesystem.  The first time I performed a painful reinstallation over two days, today I managed to fix it after a few hours because the boot process would get as far as Grub / advanced options / recovery mode / fsck  and I could ask for a check and repair. 

I cannot work out what is causing the laptop to have no active display upon resume after a monitor has been plugged in.  I have even taken the precaution of testing that it CAN resume before I leave the house, having toggled back to internal display first, unplugging the monitor, suspend, resume, check the display works.  However, frequently it will have the display problem in the field upon a subsequent resume.  Can anyone tell me where I might start to look for the issue.  I have only a little experience of log files and I have no skill in understanding what they tell me.

Many thanks,
Scot
Spec: Hp probook 6465b running 16.04
Monitor is a Dell that's many years old.
Kernel: 4.13.0-41-generic
Running Gnome desktop

---

### Post by 7018407-o on 2018-06-13
I have the same issue. simply close lid -> wait for suspend -> open lid and i have black screen, but if i pres ctrl alt f1 then i get terminal, so system is waked up but i cant see desktop. i have ubuntu 18.04 wit xubuntu-desktop. t430

---

