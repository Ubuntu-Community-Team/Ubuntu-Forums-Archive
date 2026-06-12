---
title: "Google Earth and Nvidia card"
date: 2008-10-28
forum: General Help
---

### Post by Buschbarber on 2008-10-28
I recently installed Google Earth and when I try to launch it, I receive an error indicating that my Graphics Card is Unknown.

I have an HP Media Center PC m7060n, P4 3Ghz, 2Gb ram, Nvidia Gforce 6200 OC with 256Mb ram

I have had no problems running any other programs, including MythTV

The only goofy thing about my PC that I have not been able to get a handle on is that I cannot boot Ultimate 1.9, with the Nvidia PCI card installed, unless I set the PC BIOS default video to Onboard, instead of PCI.

I do not know if Google Earth is having a problem with this.

Attached is a ScreenShot.

---

### Post by dburnett77 on 2008-10-28
> **Buschbarber said:**
> I recently installed Google Earth and when I try to launch it, I receive an error indicating that my Graphics Card is Unknown.

I have an HP Media Center PC m7060n, P4 3Ghz, 2Gb ram, Nvidia Gforce 6200 OC with 256Mb ram

I have had no problems running any other programs, including MythTV

The only goofy thing about my PC that I have not been able to get a handle on is that I cannot boot Ultimate 1.9, with the Nvidia PCI card installed, unless I set the PC BIOS default video to Onboard, instead of PCI.

I do not know if Google Earth is having a problem with this.

Attached is a ScreenShot.

the iPaq website has the interface via docking.  You'll need a little more hardware.  It's cheap, thou

---

### Post by Buschbarber on 2008-10-29
Where is the ipaq web site and what does docking have to do with a Tower PC. I guess I do not know what you mean.

I am not a seasoned Linux person so I need to be led by the hand a bit.

---

### Post by oldos2er on 2008-10-29
Which Nvidia driver are you using? You'll need to enable the restricted driver, if you're not already using it. System, Administration, Hardware Drivers.

---

### Post by dburnett77 on 2008-10-29
> **Buschbarber said:**
> Where is the ipaq web site and what does docking have to do with a Tower PC. I guess I do not know what you mean.

I am not a seasoned Linux person so I need to be led by the hand a bit.

Apologize, I saw it all wrong.

Try the nv driver for your config.  The standard and nvidia-glx-new should work.  Might have to compile it.

Thought I saw something about a module in that post there.  Things aren't always as people would have them these days, sorry

---

### Post by Buschbarber on 2008-10-29
As I stated in the beginning of this thread, I have the Nvidia Gforce 6200 OC PCI card. I have gone to Hardware Drivers, chosen, installed, and enabled the Nvidia Restricted drivers.

I did download the Nvidia-Linux-x86-177.80-pkg1.run file. I am not sure how to install it. I was warned, by and IT friend, about installing a video driver that I did not retreive using Synaptic Pkg Mgr.

---

### Post by oldos2er on 2008-10-29
If you have the nvidia restricted driver working, then it might be a problem with Googleearth itself. Did you install it from the repositories?

---

### Post by Buschbarber on 2008-10-29
Yes!! I did install Google Earth from the Repository.

---

### Post by oldos2er on 2008-10-29
> **Buschbarber said:**
> Yes!! I did install Google Earth from the Repository.

 Then try the one from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html) , either the beta or v4.2.

---

