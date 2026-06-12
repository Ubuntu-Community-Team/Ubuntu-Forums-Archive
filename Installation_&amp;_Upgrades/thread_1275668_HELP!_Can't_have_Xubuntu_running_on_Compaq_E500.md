---
title: "HELP! Can't have Xubuntu running on Compaq E500"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by mikado75 on 2009-09-26
Hello,

**Trying to get XUBUNTU running on my old laptop. A Compaq Armada E500 700mghz PIII with 10gb and 192MB memory.**

Tried normal cd : didn't work at all. Tried alternate cd load and I think Xubuntu installed properly But then I just can't load Xubuntu properly. The install goes to some points then gets about 10% the way across on the progress bars and then stops and does nothing else.

Tried the recovery option re-boot. Once, and only once, I got into Xubuntu homepage, but I had no keyboard neither touchpad working. Then i can do nothing else but power off.

Since then, I kept trying with the regular and the recovery option but it always ends with a "**rc-default process (1564) terminated with status 139**", after a bunch of "segmentation fault" messages.

Any ideas ? I really want XUBUNTU on this, it seemed an ideal candidate and would give me a few more years with it.
I've looked at a previous post on this subject, but there was no valid answer so I'm back to the beginning...

**Please someone help with a clear step to step answer. I'm an absolute beginner in the Linux world...**

You can also answer directly to my email : [email]mikado75@yahoo.com[/email]

---

### Post by DFlame on 2009-09-26
I've installed on an Armada before without too much trouble.

Download [this ISO](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso). It is a compact version of the installer, which uses a network connection to download and install the files on your system. You will need to have your computer connected to the Internet via network cable for this to work (I assume you have this).

When installing, do not pick any additional packages and stick with the **really** basic install. You should get a terminal style login when the computer restarts.

To install Xubuntu on top of this minimal system, simply enter this command:

```
sudo apt-get install xubuntu-desktop
```

On the next restart, you *should* have a working Xubuntu installation.

**EDIT**: If you still have trouble, you might have more success with Hardy, which has Long Term Support (LTS). [This is the mini iso](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso) for that version.

---

### Post by mikado75 on 2009-09-26
UNABLE TO BURN MINI.ISO from Windows (with the recommanded InfraRecorder). I've lost several good-quality CD-RW. Message is : Failed OPC. Dunno what else to do... Who can help ?

---

### Post by rreese6 on 2009-09-26
I run Xubuntu on a Toshiba Satellite 4100XDVD - 400mHz - 192 mem
I am only able to run up to Xubuntu 8.04LTS. Everything else Seg Faults.
Remember a few points.
Never try to burn the ISO file to a CD-RW.
Some can not boot from DVD even though they have a dvd player, besides you would need a DVD ISO

Once you burn the ISO to a CD-R boot it up
at the menu, select check CD Media and let that finish.
make sure there are no errors. Usually you need to burn the CD at the slowest speed you can for the old hardware to read it. (4x to 8x).
once you have a good copy, select the first line to run from CD.
this will let you see that it works with your hardware.
if that works, then click on the install icon.
You will most likely use the whole disk. I like to make a 1 gig swap
and 9 gig for the rest of it. (the root mounted as / )
.
Let us know how this works out.
go here: [http://xubuntu.org/get]("http://xubuntu.org/get")
and download the 8.04LTS version...that should take care of it.

---

### Post by mikado75 on 2009-10-01
Thanks for your help everyone,

I've tried and tried to follow your advices and to correctly install Xubuntu (either 8.04 or 9.04) on my old Compaq E500, but it could never achieve the installation.

I eventually re-ran the "zegenie" website test and gave openSUSE a try : it seems to be working. The installation is completed and the desktop looks OK. I now have to discover this new system.

Have a good day.

---

