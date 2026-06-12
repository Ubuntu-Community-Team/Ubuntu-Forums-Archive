---
title: "[SOLVED] CD Drive Eject then immediately retract problem"
date: 2008-11-09
forum: General Help
---

### Post by dstein on 2008-11-09
Hi, I just installed Ubuntu 8.10 on a new computer.

When there is not CD in the drive, I can eject the tray to insert one. Everything is fine.

When there is a CD in the drive, if I eject the CD, the tray immediately retracts once it reaches its final eject position. This gives me about a second to take the CD out.

Does anyone know what could be causing this problem? Do you think there is something wrong with the drive or the software? I can try installing 8.04, but I don't know what that will solve.

Installation of 8.10 went fine until the end. The computer hung for a few minutes at the final stage of restarting. I think it may have something to do with the CD drive, as the CD never ejected as it often does after installation.

---

### Post by EdWh on 2008-11-09
Hi Dstein,

From- EdWh

At end of installation the cd will be auto opened and the reboot paused to give you time to take out.  If this does not work, there is small hole in cd tray use long straight pin such as straightened paper clip and carefully push in to hole and you will feel it push in on a release and you can manually open tray.           Ed.

---

### Post by Zill on 2008-11-09
It's a bug!  See the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810").
[URL="https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316"]
https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316[/URL]

---

### Post by dstein on 2008-11-09
Ah thank you. I am going to stick with 8.04 to avoid any future problems, and upgrade when a lot of these issues have been resolved. Thanks again.

---

### Post by exploder on 2008-11-09
There is a newer version of udev in the "proposed repo" that fixes this issue. The update seems to work if you have one affected drive. People with two drive are reporting that only one drive works properly with the new package.

---

### Post by dstein on 2008-11-09
I'll give that a shot, because 8.04 installation was not going too well. First, I was receiving a "buffer I/O error on device fd0," so I disabled the floppy in the BIOS (which is not a problem considering I have no floppy). Then I tried installing again, and was taken to a BusyBox command prompt. I was going to try installation from the alternate CD, but first I will see how the udev update goes. Thanks.

---

### Post by dstein on 2008-11-09
I updated udev by going to software sources, going to the updates tab, and selecting pre-released updates. Then I received an update dialog, and unselected everything except udev, then updated. I then went back to deselect pre-released updates.

It worked - no more CD problem.

Is there an easier way to do this. I usually use aptitude to install packages. Is there anyway to install specific pre-release updates without enabling the entire repository? Thanks.

---

