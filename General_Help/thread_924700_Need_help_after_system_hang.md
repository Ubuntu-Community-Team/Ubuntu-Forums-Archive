---
title: "Need help after system hang"
date: 2008-09-19
forum: General Help
---

### Post by bj_ninetysix on 2008-09-19
I was resizing a window and the had a system hang.  Ctrl+Alt+Backspace and Ctrl+Alt+Del did not work so I had did a hard reboot.  After the reboot, I can not get Ubuntu to work correctly.
When I get to where I should have the login I get: [SIZE="1"]Error loading standard greeter[/SIZE]
Sometimes I don't get that, or get past that and then I get this:
[SIZE="1"]Error loading the them Human Failed to load image /usr/share/gdm/themes/Human/background.png Fatal error in PNG image file: IDAT: CRC error.
[/SIZE]
Immediately after logging in I get a message telling me there was a crash and checking the ~/.xsession-errors box I get see this:
[SIZE="1"]/usr/bin/seahorse-agent: error while loading shared libraries li`glib-2.0.so.0: cannot open shared object file No such file or directory[/SIZE].

Also of interest, trying to access gdm.conf results in segmentation error, trying dpkg-reconfigure -xserver.xorg and dpkg-reconfigure gdm also result in segmentation error.

Any help is appreciated,
Thanks.

---

### Post by bj_ninetysix on 2008-09-26
Well, I haven't made any progress on this yet.  I am hoping for somebody to help me out so I don't have to reinstall Ubuntu and loose everything I have installed.  If this was perhaps not the correct place for this question, please move it to the appropriate forum.
Thanks.

---

### Post by bj_ninetysix on 2008-10-05
I just ran memtest86 because windows has been rebooting with out warning and found a bad memory stick.  Could this be causing my problems with Ubuntu?

---

### Post by iponeverything on 2008-10-05
yes it could.

You should also boot into single user and run a file system check.

---

