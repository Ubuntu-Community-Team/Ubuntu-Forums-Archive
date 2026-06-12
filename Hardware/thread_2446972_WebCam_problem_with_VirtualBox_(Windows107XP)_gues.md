---
title: "WebCam problem with VirtualBox (Windows10/7/XP) guest machines"
date: 2020-07-10
forum: Hardware
---

### Post by jrjong on 2020-07-10
[COLOR=#141414][FONT=&amp]I've just installed an Ubuntu 20.04 Desktop Edition on a Dell All in One inspiron 3477 with Webcam that works correctly on it. and since i need a Windows machine to benefits from the Language Interpretation features of Zoom Meeting application (that works only on Windows an MacOS for now) i've created a VM [aol mail]("https://aolsigninhelp.com") with VirtualBox-6.1-8 + ExtensionPacks+Giest Additions. But the problem is that my webcam shows nothing but a blue square on my Windows 10, 7 and even XP guest machines, (both via VLC and Zoom).[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]any help is welcome, thank you all[/FONT][/COLOR]

---

### Post by SeijiSensei on 2020-07-10
I have a Win 10 Pro VM that runs on top of my Linux desktop.  I tried following these instructions

[https://www.virtualbox.org/manual/ch09.html#webcam-passthrough](https://www.virtualbox.org/manual/ch09.html#webcam-passthrough)

and got nowhere. The VBoxManage command complains that it can't find the Extension Pack I have added.

I also took the route of creating an USB filter for the camera in the Settings for the VM. That didn't work either.

---

