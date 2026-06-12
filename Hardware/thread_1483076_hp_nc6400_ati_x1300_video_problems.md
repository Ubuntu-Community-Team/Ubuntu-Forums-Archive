---
title: "hp nc6400 ati x1300 video problems"
date: 2010-05-14
forum: Hardware
---

### Post by jjgibster on 2010-05-14
I'll be brief: Karmic worked great! Installed Lucid -- after a few seconds video begins to flicker horribly -- I have updated to the latest verisons of xorg and updated the kernel -- all through the software updates -- it almost appears that the refresh rate is off just a bit...
 
It's very frustrating to go from something working very well in 9.10 to almost useless in 10.04
 
Please Help!

---

### Post by efflandt on 2010-05-14
My X1300 does not like the new kernel-mode-setting KMS video system. I don't get any flickering when connected DVI to HDMI to a 1080p HDTV.  But even with desktop effects disabled, certain window tasks are sluggish.  But more noticeable were that suspend and hibernate did not work (video would blank, but remained on, and power remained on, requiring manual hard power down/cold boot).

The simple solution, once I found it, was **nomodeset** or **radeon.modeset=0** kernel parameters.  Then Lucid was up to Karmic speeds and suspend/hibernate work.

See [http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

Although, I would know know anything about the proprietary modules, because I just use the default drivers/modules.

---

### Post by DouglasAWh on 2010-09-20
Can you give us instructions on how to set those kernel preferences? Thanks!

EDIT: thought his link was about the proprietary driver before I went looking for more info.

---

### Post by efflandt on 2010-09-21
You can try **nomodeset** by hitting e at the grub menu, adding **nomodeset** after quiet splash, then Ctrl+X to boot.

And if that works, the link in my above reply explains how to add it to /etc/default/grub, followed by sudo update-grub.

Then the radeon user space modules (instead of new kms drivers) should work just as well in 10.04 as they did in 9.10 (did for me).

---

### Post by maticer on 2010-11-20
Thanks for this!

Tried to install Ubuntu Maverick 10.10 on Compaq nc6400 with Radeon X1300 and it was disaster. On Lucid 10.04 it was much better but still a bit glichy. Instructions from above link for Lucid 10.04 which uses Grub2 usually as I know:

    1. sudo gedit /etc/default/grub
           - add nomodeset to GRUB_CMDLINE_LINUX
    2. sudo update-grub
    3. Reboot

For comparison, running QuakeLive.com without "nomodset" I had barely 10 fps on minimum graphics. Adding this (disabling KMS) and after reboot I had 50 fps! :)

---

### Post by maticer on 2010-11-28
> **maticer said:**
> Thanks for this!

Tried to install Ubuntu Maverick 10.10 on Compaq nc6400 with Radeon X1300 and it was disaster. On Lucid 10.04 it was much better but still a bit glichy. Instructions from above link for Lucid 10.04 which uses Grub2 usually as I know:

    1. sudo gedit /etc/default/grub
           - add nomodeset to GRUB_CMDLINE_LINUX
    2. sudo update-grub
    3. Reboot

For comparison, running QuakeLive.com without "nomodset" I had barely 10 fps on minimum graphics. Adding this (disabling KMS) and after reboot I had 50 fps! :)

It's all well on laptop's screen and resolution 1280 x 800. But putting it on HD screen 1920 x 1080 compiz manage to crash it very quickly. The same goes for QuakeLive, where are also some glitches in textures.

Any idea how to fix that? I would really like to use compiz on external HD 1080 display. I don't care if I have low fps, etc. just that it doesn't crash PC and all the unsaved work goes to hell...

---

### Post by Yellow Pasque on 2010-11-28
You can try xorg-edgers PPA: xorg-edgers

---

