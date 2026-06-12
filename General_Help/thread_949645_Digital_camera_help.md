---
title: "Digital camera help"
date: 2008-10-16
forum: General Help
---

### Post by DCHp on 2008-10-16
I need some help with the following problem please! , I have a fujifilm S800 digital camera....when I plug it into the pc ubuntu detects the camera fine and the photo manager software pops up and im able to import the photos to the hard drive....The camera does not show up a a drive though so I cant view the folders on the camera and memory card....How do I mount the camera as a drive so that I can view it in nautilus? any help will be much appreciated!
Im a newb to ubuntu so please help!

---

### Post by Sycron on 2008-10-16
Plug in the camera to the computer, turn on the camera and then open up a terminal. (go to Applications-Accesories-Terminal) and type ```
sudo fdisk -l
```. Post the output.

---

### Post by DCHp on 2008-10-17
Hi , heres the output:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2431      738990    5  Extended
/dev/sda5            2340        2431      738958+  82  Linux swap / Solaris

---

### Post by Sycron on 2008-10-19
Are you sure that what you copied is exactly the output ? Because I doubt :|

---

