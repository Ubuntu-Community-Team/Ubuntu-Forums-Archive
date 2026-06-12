---
title: "Installation splitscreen"
date: 2011-05-05
forum: Hardware
---

### Post by DaddyLarry on 2011-05-05
I have been unable to use ubuntu for the last few versions because I  keep having my HP Pavillion dv6700 with an NVIDIA GeForce 7150M/NForce  630M Display adapter split into several overlapping screens with the  mouse properly lining up on none of them.  I was hoping that the latest  distro fixed this.  It didn't.  Is there a way to install Ubuntu so that  I can fix this problem?

I posted this on the installation forum and was referred here.  This is preventing me from using even the live CD.

---

### Post by PrimaKaeso on 2011-10-13
I have the same laptop and the exact same problem trying to install Ubuntu 11.10.

I've been trying for hours to get everything working without any luck! Every time I try to install from the disc I have some sort of 'screen tearing' problem. I decided to run Ubuntu with Windows via the Wubi installer and I had the same problem during and after installation.

This is what it looks like:

[IMG]http://desmond.yfrog.com/Himg620/scaled.php?tn=0&server=620&filename=27lajy.jpg&xsize=640&ysize=640[/IMG]

Is there a way to fix this or install it without this happening?


HP Pavilion dv6700
Windows Vista Service Pack 2
32-bit OS

Any help will be greatly appreciated!

---

### Post by varunendra on 2011-10-14
PrimaKaeso, first off, welcome to the forums!

Your problem seems to be definitely graphics driver related. In live CD, do the following:

[LIST=1]
[*]While booting from the CD (or USB), press any key to bring up advanced options menu.
[*]Press F6 to pop up 'Other Options' menu
[*]Select 'Nomodeset' (by highlighting it using arrow keys and putting a cross before it by pressing spacebar)
[*]press 'Esc' key, then selecting "Try Ubuntu.." option, press 'Enter'
[/LIST]
This should allow you to boot with normal graphics.

In the installed version, select "Recovery" mode, then "FailsafeX" option in the recovery mode to do the same. It is a temporary fix to boot normally, and you will then need to install proper driver for your graphics to get enhanced graphics.

If this doesn't help, I would recommend to post this issue (with as much details as possible - including graphics adapter model you have) in your own new thread since this one is quite old now and the OP doesn't seem active. You may then post a link to it here which others can follow.

---

