---
title: "Ati Catalyst Driver Solution"
date: 2010-08-13
forum: Hardware
---

### Post by NikolaiRachmaninoff on 2010-08-13
Many people have asked me how to install newer versions of Ati Catalyst(Due to incompatibility or other reason(this may happen, if you buy a new pc with newer models of ati graphic card.So here you have some short instructions on how to download the .run driver from ATI's official site and recompile it in .deb format to make the installation easier.
1)Vist the official ATI/AMD driver section here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
Download the ATI Driver for your graphic card(Obviously it must be for linux and it is in .run format) on your desktop.

2)Now open the terminal (Press ALT+F2 and type gnome-terminal).

3)Write down the following commands
cd ~/Desktop
sudo chmod +x ./(name of the driver).run
sudo ./(name of the driver).run --buildpkg Ubuntu/(here you have to put your distro release(codename)

Lets make an example:I would like to install the ATI driver on my new PC, which runs Ubuntu 10.04 and has no compatible driver through the repository.

So I...
1)Download the driver from the site and save it on my desktop
ati-driver-installer-10-7-x86.x86_64.run
2)Open the terminal, and switch to desktop

# cd ~/Desktop

3)I make the .run file executable

# sudo chmod +x ./ati-driver-installer-10-7-x86.x86_64.run

4)Now I only have to use the command that will recompile the original .run into more .deb packages and wait.

# sudo ./ati-driver-installer-10-7-x86.x86_64.run --buildpkg Ubuntu/lucid

5)When the process is finished, some .deb packages will appear on the desktop.I can install them  by left-click on them.

---

### Post by Last_chance_saloon on 2011-05-29
Nikolai,

THREE MONITORS INSTALLED IN UBUNTU 10.04 SUCCESSFUL

Thank you very much for your post.  I searched everywhere to solve the three monitors not working problem.  No one else had any answer, or the information was way out of date.

I have a 64-bit system, two HDRadeon 5770 card, Ubuntu 10.04 and three monitors.

1. went to the ati site link, chose all of the correct items to identify my systems needs and downloaded the 71 MB file on a separate computer USB.  No special reason for this step but just wanted to make sure I had a copy handy.  You could just use your own computer, but my monitors ar Samsung Syncmasters and are set up vertically, and get a bad neck trying to read them sideways.

The latest ati version for me was 11.5 dated 9 May 2011.  i.e really the latest (I am posting 29 May 2011)

2. I copied the ati file from the USB to the Ubuntu desktop, then removed the two ati files fglrx  and fglrx-amdcccle using Synaptics Package Manager.  This wasn't in your advice but I wanted to make sure there weren't any clashes somewhere.  Perhaps this is unnecessary, but I did it anyway.

3. then followed your conversions and installation instructions. Eventually a nice little panel arrived, just clicked the standard default conditions.

4. when all finished - restart.

5. On restart go to Preferences, ATI Catalyst Control Center (Administrative) and select the third screen that looks disabled, choose multi-monitor and apply.

6.  Brilliant THREE MONITORS INSTALLED IN UBUNTU 10.04 SUCCESSFUL. Did another restart and all three came up.  Sweet as.

7. Two days of almost fruitless searching solved the problem in 5 easy minutes.

Can you tell I am a happy camper.  I trust my additional comments help all and sundry and Google makes this post more readily available.:)

Now all screens are rotated (this is a special feature of this monitor) and I have a single workspace on my desktop where the mouse scrolls off the right hand side of the third screen.  This is telling me I could possible have done four screens.  The HDRadeon has DVI and VGA outputs on each card, on two cards I have 4 outputs.  A fourth screen coming up I guess when I get a bigger room to put all four of them in.

---

### Post by RafaelG on 2011-05-30
NikolaiRachmaninoff;

Thanks for your help and support. Your post has been moved to a English forum to a better understanding because you posted this thread in a Spanish forum.

Best regards,

---

