---
title: "dvd rom not working"
date: 2014-07-10
forum: Hardware
---

### Post by stuart.mullett on 2014-07-10
Trying to get my dvd rom drive to mount/load in ubuntu 14 04. if i go into disks it shows up in the list of disks ,insert a dvd/cd into drive it shows up in disks with the size and type of disk but i have no of opening the dvd/cd. Model IDE-DVD ROM 6116(HD24). The dvd/cd burner work ok and shows on the launcher. Any ideas new to ubuntu so be gentle

---

### Post by Vladlenin5000 on 2014-07-10
What happens when you click it on the launcher?

---

### Post by ajgreeny on 2014-07-10
Try the command **eject** in terminal; it certainly works on my Xubuntu 12.04, not totally sure about 14.04, but it should work in that as well, as far as I'm aware.

There is a panel icon that is available in the package ejecter, which is in the repos, and which shows the icon when you either insert a CD/DVD, or USB drive.  I find it very useful; try it, though I have no idea if it works in unity or not.

---

### Post by yancek on 2014-07-10
You should have an 'eject' option if you right-click the DVD icon in the panel.

---

### Post by grahammechanical on 2014-07-10
The Disks utility will let us open a DVD/CD ROM drive. Select the CD/DVD Drive and then look at the top right of the Disks application window. You will see two buttons. The right hand button will have a cog icon. The left hand button will have an upwards pointing arrow. click on the left hand button. That should open the CD/DVD tray.

This is an image of the two icons. With a USB stick selected.


[https://www.google.co.uk/search?q=ubuntu+disks+utility+images&client=ubuntu-browser&es_sm=122&tbm=isch&imgil=Sets8dqgq5JVKM%253A%253Bhttps%253A%252F%252Fencrypted-tbn0.gstatic.com%252Fimages%253Fq%253Dtbn%253AANd9GcTywuAn0JZ5Sky6X9C_usXVC6ZN-qkfGlXliYGa-JtqEAGFzq0f%253B937%253B587%253B726pwJgnpkV5zM%253Bhttp%25253A%25252F%25252Fwww.webupd8.org%25252F2009%25252F08%25252Fhow-to-install-palimpsest-disk-utility.html&source=iu&usg=__xzZtKi3GNY3BJW89pJxdVRQPc48%3D&sa=X&ei=-ia_U6O_JoHDPM7vgIgG&ved=0CCQQ9QEwAA&biw=1214&bih=913#facrc=_&imgdii=_&imgrc=MiS0hbxtWHZjuM%253A%3B3ZJpl8_rA7p5VM%3Bhttp%253A%252F%252Filoveubuntu.net%252Fpictures_me%252Fdisks%2525203.5.1%25252011.png%3Bhttp%253A%252F%252Filoveubuntu.net%252Fdisks-35-landed-ubuntu-1210-new-design%3B819%3B652](https://www.google.co.uk/search?q=ubuntu+disks+utility+images&client=ubuntu-browser&es_sm=122&tbm=isch&imgil=Sets8dqgq5JVKM%253A%253Bhttps%253A%252F%252Fencrypted-tbn0.gstatic.com%252Fimages%253Fq%253Dtbn%253AANd9GcTywuAn0JZ5Sky6X9C_usXVC6ZN-qkfGlXliYGa-JtqEAGFzq0f%253B937%253B587%253B726pwJgnpkV5zM%253Bhttp%25253A%25252F%25252Fwww.webupd8.org%25252F2009%25252F08%25252Fhow-to-install-palimpsest-disk-utility.html&source=iu&usg=__xzZtKi3GNY3BJW89pJxdVRQPc48%3D&sa=X&ei=-ia_U6O_JoHDPM7vgIgG&ved=0CCQQ9QEwAA&biw=1214&bih=913#facrc=_&imgdii=_&imgrc=MiS0hbxtWHZjuM%253A%3B3ZJpl8_rA7p5VM%3Bhttp%253A%252F%252Filoveubuntu.net%252Fpictures_me%252Fdisks%2525203.5.1%25252011.png%3Bhttp%253A%252F%252Filoveubuntu.net%252Fdisks-35-landed-ubuntu-1210-new-design%3B819%3B652)

Regards

---

### Post by stuart.mullett on 2014-07-11
Did not mean not able to eject. i ment unable to mount/load the dvd/cd

---

### Post by ajgreeny on 2014-07-11
Doesn't it show in the Places pane of your file-manager or as an icon in the launchbar?

Click on that and nautilus should open.

---

### Post by stuart.mullett on 2014-07-13
Does not show up on etheir

---

### Post by Vladlenin5000 on 2014-07-13
> **stuart.mullett said:**
> Does not show up on etheir

It should show up whenever a disk is inserted, otherwise it won't.

---

### Post by stuart.mullett on 2014-07-16
It only shows up in the disks appliication

---

### Post by Vladlenin5000 on 2014-07-16
There's no point in this back and forth. It has been explained a few times already that, unlike what happens in Windows, in Ubuntu's standard file manager there's never an icon, place, whatever for the optical drive unless it has been inserted a CD or DVD with some readable contents or also a blank one (for CD-RW / DVD-RW drives).
 
If I understood correctly, tou have two drives and one works as expected and the other don't?

---

### Post by stuart.mullett on 2014-07-25
Yes i understand that there are no icons, but when i insert a dvd/cd into the drive it should ether auto launch or show on on the launcher this does not. the other drive works ok

---

### Post by fkkroundabout on 2014-07-26
if the other drive works OK, it could be the drive itself that's dead

---

### Post by Maria_Luiza on 2014-07-26
maybe you hvae used an old cd or dvd that is very scratchy

---

### Post by stuart.mullett on 2014-07-26
no the drive works OK in Windows, tried lots of different dvd/cds

---

