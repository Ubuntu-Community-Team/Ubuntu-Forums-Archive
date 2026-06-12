---
title: "Virtual Box"
date: 2008-11-07
forum: General Help
---

### Post by alanhunter on 2008-11-07
Hi to all
I have been using Ubuntu for about 1 month now very impressed Ubuntu covers all my needs except I need to run "sony vegas" I have installed Virtual Box and load XP and installed guest additions. I would like to be able to share a folder so that my video file remain within Ubuntu I have created a directory called videos in my user directory /home/user_name/videos/ and set it to share
In Virtulabox I have created a VM called XP and set the the shared folder to /home/user_name/videos/ and called it videos I have followed the instruction in ubuntu forums to set up a shared folder but every time I enter the command
root@Computer:~# VBoxManage sharedfolder add "XP" -name "videos" -hostpath /home/user_name/videos

I get the error below. At the time of entering this command Vbox is not running. Using Ubuntu 8.10
Any advice would be much appreciated.

VirtualBox Command Line Management Interface Version 2.0.4
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling aVirtualBox->FindMachine(Bstr(argv[1]), machine.asOutParam()) at line 7418!
[!] Primary RC  = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Full error info present: true , basic error info present: true 
[!] Result Code = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Text        = Could not find a registered machine named 'XP'
[!] Component   = VirtualBox, Interface: IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
[!] Callee      = IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
root@Computer:~#

---

