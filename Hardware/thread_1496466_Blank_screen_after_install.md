---
title: "Blank screen after install"
date: 2010-05-29
forum: Hardware
---

### Post by Bristol_Green on 2010-05-29
I have just installed Lucid Netbook Remix on a Packard Bell Dot_SR netbook. It ran OK(-ish) from the memory stick, but after I installed the remix, selecting ubuntu from the dual boot screen led to a blank screen with a blinking cursor top left. I successfully restarted and selected Windows 7, then did a restart in recovery mode, which asked for my login and password, and left me at the Terminal command prompt not knowing what to do next!
What did I do wrong?

eta: when I typed 'e' for edit at the dual boot prompt I got the following:

recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 629addda-8301-404a-b9db-98f560b5d\
9db-98f560b5d34d ro  quiet splash
initrd /boot/initrd.img-2.6.32-21-generic

- which may or may not be helpful. I'm afraid I don't know what it means.

I have managed to start in low graphics mode, one session at a time. Not ideal... and I can't connect to the internet via my 3 Huawei 122 dongle.

---

### Post by Bristol_Green on 2010-05-30
I rang the 3 helpline and was told that their network would not run under linux. I was not surprised to hear that, and neither are you! 

However, the performance of the Lucid netbook remix, when installed, was so poor that I deleted it via easyBCD. I'd rather run it from the USB stick until I get more advice, and use Win7 for internet access when I'm on the move. Which is a shame.

---

### Post by Bristol_Green on 2010-06-02
I tried another install from the iso on my USB stick and edited the following (see above)

recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 629addda-8301-404a-b9db-98f560b5d\
9db-98f560b5d34d ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic

by removing the words 'quiet splash' from the 5th line, then did Ctrl-x to reboot. This worked. I was then able to download the relevant updates via the cable modem which usually serves my pc. (Btw for some reason I can't do that under Windows 7.)

Still can't use my 3 dongle though.

---

